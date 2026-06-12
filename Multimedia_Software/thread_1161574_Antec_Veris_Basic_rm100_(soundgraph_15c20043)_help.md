---
title: "Antec Veris Basic rm100 (soundgraph 15c2:0043) help"
date: 2009-05-16
forum: Multimedia Software
---

### Post by speed32219 on 2009-05-16
Here is the output of:
uname -r
2.6.27-11-generic

lsusb
Bus 002 Device 004: ID 15c2:0043 SoundGraph Inc. 

# check for usbhid driver for the 15c2:0043 iMON device
sudo mount -t usbfs none /proc/bus/usb
sudo cat /proc/bus/usb/devices

# I found that the soundgrpah 15c2:0043 had the usbhid drivers loaded
# So I removed them by the following:

sudo nano /etc/modprobe.d/usbhid
# Added the following line to the usbhid file and saved
options usbhid quirks=0x15c2:0x0043:0x0004
#Then ran this to update
sudo depmod -ae
sudo update-initramfs -u
#Then rebooted and check drivers again, no drivers listed for
# the soundgrpah 15c2:0043 device. Now ready to install new drivers.
 

This newer device is only supported with lirc-0.8.5pre1 and lirc-0.8.5pre2 drivers per lirc documentation.

Here are the steps I am using trying to install the drivers.

cd /usr/src
sudo apt-get update
sudo apt-get remove lirc
#I have module-assistant installed
sudo m-a update
sudo m-a prepare
#link the headers to the linux directory
ln -s linux-headers-2.6.27-chw-4 linux
#Double check that no ".ko" or ".so" files exist for lirc_imon or imonlcd
#If you find some, move them out of the way by adding say ".old" to the #file name
sudo find / -name lirc\_imon\* -print
#Get and unpack the latest lirc I have tried pre1 and pre2: 
cd /usr/src
sudo wget [http://www.lirc.org/software/snapshots/lirc-0.8.5pre1.tar.bz2](http://www.lirc.org/software/snapshots/lirc-0.8.5pre1.tar.bz2)
sudo tar jxvf lirc-0.8.5pre1.tar.bz2
cd lirc-0.8.5pre1
#Configure it by executing the following and choose "Driver #Configuration" then "USB Devices" then "Soundgraph iMON IR/LCD" 
sudo ./setup.sh
And before I can get to the make commands I get Makefile errors in the configure.  Many, many makefile errors, here are just two of many.

config.status: creating drivers/lirc_dev/Makefile
config.status: WARNING:  drivers/lirc_dev/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_imon/Makefile
config.status: WARNING:  drivers/lirc_imon/Makefile.in seems to ignore the --datarootdir setting

You will have to use the lirc_imon kernel module. 

Anyone point me in the right direction with the makefile errors.  Do I need to update to a newer kernel.  I went from 2.6.27.7 to 2.6.27.11 and still have the same errors. If I continue on with the installation, I do not get /dev/lirc0 or /dev/lirc1 device which means no dev drivers.

Any suggestions would be greatly appreicated.

---

### Post by shabazzk on 2009-05-26
usbhid takes over my device no matter what, how do I get it not to on Jaunty?

I tried the following commands you posted above (I was full of hope):
```
sudo nano /etc/modprobe.d/usbhid
# Added the following line to the usbhid file and saved
options usbhid quirks=0x15c2:0x0043:0x0004
#Then ran this to update
sudo depmod -ae
sudo update-initramfs -u
#Then rebooted and check drivers again, no drivers listed for
```

To my dismay, usbhid was still listed as the Driver for my IR device :(
```
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

It has a TERRIBLE grip, the likes of which I have never seen. Someone please help me! Also, I'm using kernel:
```
uname -a
2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

```

---

### Post by tji on 2009-06-03
I am trying to get a very similar Antec Veris IR receiver working in Ubuntu 9.04.   I think mine is the external version and yours is the drive bay version.   Mine shows as USB ID  15c2:0042.   

By default, usbhid grabs the device, and two devices are created /dev/hidraw0 and hidraw1.

Even in this case, lirc_imon and lirc_dev are also loaded.  But, the expected lirc devices aren't created in /dev (instead, the hidrawX devices are created).

I tried a few config options in  /etc/modprobe.d/usbhid.conf.  I have seen people recommending both "usbhid usbhid.quirks" and "usbhid quirks", so I tried both:
options usbhid usbhid.quirks=0x15c2:0x0042:0x0004
options usbhid quirks=0x15c2:0x0042:0x0004

With the second version above, usbhid ignores the IR receiver.   But, it also ignores my USB mouse.  And, the lirc_imon behavior doesn't change..   /dev/hidraw0 & 1 are gone, but the lirc device still doesn't show up.


Has anyone got these devices working?
Can I get usbhid to ignore the IR receiver and leave the mouse alone?
Do I need to update lirc, my kernel, or other components?

---

### Post by shabazzk on 2009-06-03
Here is the reason the lirc devices may not show in /dev:

> When you are using devfs or sysfs with your kernel, the /dev/lirc device node will disappear again once you reboot your machine. In that case the LIRC kernel module will generate the required entry every time it is loaded. But the device node won't be visible as /dev/lirc, but might be located in a different location like e.g. /dev/lirc/0. Please be aware of this fact when starting programs that access the device node like mode2 or lircd. You will have to use the --device command line option of these programs to point them to the correct location. When using sysfs together with the udev daemon you should copy the lirc.rules file located in the contrib directory of the source package to /etc/udev/rules.d/. This will make sure that the device node will be created.

I also think that lirc has not been updated, in fact these new release are simply patches (well this may be a bit harsh).

I've spent the last month trying to get this to work and have gotten nowhere. While I've learned a lot about Ubuntu and lirc I feel that I will not get this to work with lirc being so outdated. I am currently looking into what it will take to update the code and change it over to C++.  To do this I will need to know the following:
- Writing device drivers
- Ins and outs of Ubuntu
- Dust off my old C++ books
- Contact the previous lirc devs and get the down-lo
Any help would be greatly appreciated.

Our devices are patched in the new version of lirc (0.8.5). But I did not have much success installing it using 'speed32219' instructions above. Will have to find the proper way to install it.

---

### Post by tji on 2009-06-04
I spent a little time last night playing with this.    I installed the latest version of lirc from lirc.org.   

I followed the instructions here:  [https://wiki.ubuntu.com/LircHowto](https://wiki.ubuntu.com/LircHowto)
You just need to adapt it to the current version of the kernel you are using.

I also had to do an "apt-get install dialog", which is used in the lirc setup, and then lirc built with no problem.


It built the new modules, and I rebooted.    Now, I am getting /dev/lirc0 and /dev/lirc1, so the new modules appear to be working fine.   (I do a manual "modprobe usbhid" to enable my mouse).


I tried 'irw' to see if lirc was receiving the commands, but didn't get anything.    So, my next step is to modify the lirc configuration.    I'll post more info as I have time to work on this.

---

### Post by rabidblackwing on 2009-06-04
[shabazzk]("http://www.uluga.ubuntuforums.org/member.php?u=813796"), 

I am in the same boat as you, no matter what line I put in the usbhid.conf file usb still takes control of my Imon (0043 version).  I even went so far as to blacklist usbhid and it still takes control. I also seem to have the same image version as you: 2.6.28.11.  Have you had any luck yet with getting usbhid to let go of the Imon...it is becoming a real PITA.

TJI, what version of the kernal are you using (uname -r)?  

I am suspecting that the complete ignore of the quirk command may be a bug with 2.6.28.11 (I am hoping I am wrong and that somebody else that was able to get usbhid to let go of the Imon is running 2.6.28.11).

Is there anyway to completly remove usbhid as I do not need it anyway or is there a way to downgrade kernal versions through apt-get or something?

Thank You.

---

### Post by tji on 2009-06-04
I am using the standard 9.04 kernel, 2.6.28-11-generic.

My /etc/modprobe.d/usbhid.conf file looks like this:

options usbhid quirks=0x15c2:0x0042:0x0004


You also have to run the following commands after updating that file:

sudo depmod -ae
sudo update-initramfs -u

---

### Post by shabazzk on 2009-06-05
> **rabidblackwing said:**
> [shabazzk]("http://www.uluga.ubuntuforums.org/member.php?u=813796"), 

I am in the same boat as you, no matter what line I put in the usbhid.conf file usb still takes control of my Imon (0043 version).  I even went so far as to blacklist usbhid and it still takes control. I also seem to have the same image version as you: 2.6.28.11.  Have you had any luck yet with getting usbhid to let go of the Imon...it is becoming a real PITA.

TJI, what version of the kernal are you using (uname -r)?  

I am suspecting that the complete ignore of the quirk command may be a bug with 2.6.28.11 (I am hoping I am wrong and that somebody else that was able to get usbhid to let go of the Imon is running 2.6.28.11).

Is there anyway to completly remove usbhid as I do not need it anyway or is there a way to downgrade kernal versions through apt-get or something?

Thank You.

Well good news: This morning I completely removed lirc 0.8.4a and then, I also decided to give the usbhid.conf file one more try.

```
sudo gedit /etc/modprobe.d/usbhid.conf
```
And changed the quirk to:
options usbhid usbhid.quirks=0x15c2:0x0043:0x0004

which I got from tji, saved and closed. 

```
sudo depmod -ae
sudo update-initramfs -u
```

Then rebooted.

Good news is that usbhid let go of the imon device :)
```
sudo mount -t usbfs none /proc/bus/usb
sudo cat /proc/bus/usb/device 
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```

Bad news, my mouse and keyboard didn't work :( I had to remote in from another linux box in order to fix.
```
T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c517 Rev=38.10
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```

The quirk seemed to ignore the device parameters, and acted more like it was blacklisted. I will play with the quirk some more to see if I can get the right combination.

Also, once I do get the usbdriver to release the device, I'm afraid that lirc 0.8.4a will NOT work properly for this device. However, lirc 0.8.5 does support this device naively, so I will try that version instead. Be warned, as there is no deb package for it; so I'll have to figure out how to install it manually.

---

### Post by shabazzk on 2009-06-06
Well... I got usbhid to not load for my IR device one time, after that, no matter what I tried the IR had the usbhid driver loaded. So I'm proceeding to reinstall the OS. But 9.10 instead.

Well... I've learned alot about Linux is the past 2 months, I just downloaded the Alpha 1 Release of 9.10 x86_64 Alternate and was able to get through the install without have to search online and post in a forums. I also thing I kept my media partition in tact and it will show up when the install completes. I'm hoping that lirc 0.8.5 will be in the repositories, if not, then I will try to install it. Hopefully I will not have problems with getting usbhid to release the lirc device either.

---

### Post by tji on 2009-06-06
> **shabazzk said:**
> However, lirc 0.8.5 does support this device naively, so I will try that version instead. Be warned, as there is no deb package for it; so I'll have to figure out how to install it manually.

I posted some info on how to do this earlier in the thread:   [http://ubuntuforums.org/showpost.php?p=7400160&postcount=5](http://ubuntuforums.org/showpost.php?p=7400160&postcount=5)

The page linked there covers the requirements very well.

---

### Post by shabazzk on 2009-06-08
Great news, I got it working. usbhid is no longer hogging my IR device and LIRC is installed and loaded for it. I cannot use irrecord for some reason, but was able to use mode 2 to test the remote, and it captured all the keys on the remote. Now I have to find the lircd.conf one of the devs made for my remote, or make my own the hard way using another lircd.conf as a guide and then copy & paste the keys into the file using mode 2.

I will admit that I did a fresh install of Ubuntu 9.10 Karmic, and updated the system then installed lirc 0.8.5. The key was getting usbhid to release the device.

Putting the quirk "options usbhid usbhid.quirks=0x15c2:0x0043:0x0004
" in to the file "/etc/modprobe.d/usbhid.conf"

This only worked one time for me last time, which is why I did a fresh install, this time. So I made sure I installed lirc 0.8.5 properly, before I rebooted. There was also another guide I found about how to install app in Ubuntu, which helped me also make a dep package for my install so I can easily install/uninstall it at will. If your willing, I can upload it somewhere and you can try it (PM me). At your own risk of course. Plus it is not complete as I had to manually install some config files afterwards. But I can supply this also. 

I will also supply all the steps I took to install it manually, I kept good record of everything I did to get it to work this time :)

---

### Post by eti.que on 2009-07-01
XBMC not being supported yet on Karmic, I unfortunately cannot upgrade.

Did anyone manage to make some progress on Jaunty?

Thanks!

---

### Post by tji on 2009-07-01
I ended up ditching the Antec rather than fighting to figure out the config.

I also have a HDHomeRun tuner device, which I forgot that it had a built-in IR receiver that is Lirc compatible.   So, I got that working instead.

I'm sure the Antec can be made to work, but it wasn't worth the time & effort for me to do that.

---

### Post by jayboi on 2009-07-28
> **eti.que said:**
> XBMC not being supported yet on Karmic, I unfortunately cannot upgrade.

Did anyone manage to make some progress on Jaunty?

Thanks!

XBMC, although not officially supported on Karmic does work.  I'm rebuilding my htpc now on an ion board with Karmic and the SVN ppa of xbmc.  No issues so far with xbmc.

---

### Post by eti.que on 2009-07-28
Great to know !

You use the repository of Jaynty?

---

### Post by frdrk on 2009-08-12
anyone got this to work yet? I installed lirc 0.8.5 on ubuntu 9.04 and got it to work somewhat with word2, but nothing else :\

---

### Post by eorndil on 2009-08-12
> **shabazzk said:**
> Great news, I got it working. usbhid is no longer hogging my IR device and LIRC is installed and loaded for it. I cannot use irrecord for some reason, but was able to use mode 2 to test the remote, and it captured all the keys on the remote. Now I have to find the lircd.conf one of the devs made for my remote, or make my own the hard way using another lircd.conf as a guide and then copy & paste the keys into the file using mode 2.

I will admit that I did a fresh install of Ubuntu 9.10 Karmic, and updated the system then installed lirc 0.8.5. The key was getting usbhid to release the device.

Putting the quirk "options usbhid usbhid.quirks=0x15c2:0x0043:0x0004
" in to the file "/etc/modprobe.d/usbhid.conf"

This only worked one time for me last time, which is why I did a fresh install, this time. So I made sure I installed lirc 0.8.5 properly, before I rebooted. There was also another guide I found about how to install app in Ubuntu, which helped me also make a dep package for my install so I can easily install/uninstall it at will. If your willing, I can upload it somewhere and you can try it (PM me). At your own risk of course. Plus it is not complete as I had to manually install some config files afterwards. But I can supply this also. 

I will also supply all the steps I took to install it manually, I kept good record of everything I did to get it to work this time :)


Hello !

I'm stuck.... I have the same problem you resolved. When I put "options usbhid usbhid.quirks=0x15c2:0x0043:0x0004
" in to the file "/etc/modprobe.d/usbhid.conf"

My IR works with the goods drivers (lirc_imon) but I have no mouse and keyboard. hen I want to launch usbhid module manually, I have an error wich is (in dmesg): 

Unknown parameter `usbhid.quirks'

I don't know what to do :/

---

### Post by shabazzk on 2009-08-12
Well...my RMAd rm100 IR will be here tomorrow, and of course I will try to install it. If it works I'll post the steps I took to get it to work. Plus I can PM someone who also got it to work to help if I need it.

---

### Post by frdrk on 2009-08-15
hm, I installed lirc-0.8.5 and got this semi-working.. it seems as if different keypresses are sent to different lirc-devices.. in my case the signals for the left, right, down and up buttons ends up in /dev/lirc1 but the menu- and back-button ends up in /dev/lirc0 in irrecord.

also the bundled lircd conf for rm100 in 0.8.5 didnt work, so I made my own with irrecord for just the direction buttons which looks like this;

```
begin remote

  name  test
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  16
  post_data      0x15B7
  gap          111978
  toggle_bit_mask 0x4000

      begin codes
          KEY_RIGHT                0x2BA5
          KEY_LEFT                 0x29A5
          KEY_UP                   0x2AA5
          KEY_DOWN                 0x2895
      end codes

end remote
```it works in xbmc, but the signals are sent two times for every time i press a button. also, if i press at button that are beein sent to /dev/lirc0 it stops working, and I have to manually open /dev/lirc0 once with ex irrecord and close it, then the lirc1-buttons starts to work again.

edit: got all this working in gentoo with lirc-0.8.5, now returning to ubuntu 9.04 i can't get the module to work properly. gah.

edit2: ok, I've got this all working.. but you'll need lirc-0.8.5 I'll post it all in the morning.

---

### Post by shabazzk on 2009-08-15
Well, lirc installed (0.8.5 from Ubuntu debs intended for Karmic) fine, and is ready to go, but usbhid driver loads for my Antec basic after disabling the usbhid quirk. Using the usbhid quirk disables my mouse and keyboard, so I removed it (using a PS/2 keyboard). So I have a dilemma. How does everyone else get this working without disabling  their USB mouse and keyboard.

Why does usbhid grab every damn thing I plug into the USB ports?:lolflag:

Quirk I used:
```
1. sudo gedit /etc/modprobe.d/usbhid.conf
2. paste:
	options usbhid usbhid.quirks=0x15c2:0x0043:0x0004

3. Save and close
4. sudo depmod -ae
5. sudo update-initramfs -u
6. Reboot your computer.
```

Also frdrk, I can confirm that different key presses are sent to different lirc-devices (0 and 1). Just experimenting until you post your solution.

---

### Post by frdrk on 2009-08-16
Ok, so here's how its done;

first off you need lirc **0.8.5**. i did a dist upgrade to 9.10 alpha to get the package, I'm sure you can install it from source in 9.04 also or use the karmic packages somehow.

second you need to somehow make the usbhid let go of the device, temporary I used the quirks posted earlier in this thread to disable it completely, rendering my usb keyboard and mouse useless.. doesnt matter really now that the remote is working anyways :]. you can always ssh into the box and modprobe usbhid after boot if you need it.

the module you need for lirc 0.8.5 is the one called just **imon**.
```
$ lsmod | grep lirc
lirc_imon              16228  1
lirc_dev               10996  3 lirc_imon
```by now you should be able to use mode2 to recieve some signals. as established earlier the remote sends its signals to two different devices, /dev/lirc0 and /dev/lirc1. the keys sent to lirc0 is ENTER, MENU and BACK.. the rest are sent to lirc1. this kinda breaks mode2, because if you use it on lirc0 and press a key other than the ones that sends signal to lirc0 it wont respond to any more keypresses.

so what you need to do here is to have two lircd-processes connected with eachother, with separate configurations for lirc0 and lirc1. the config bundled with lirc 0.8.5 was way off so I did my own;

```
lirc0.conf

begin remote

  name  rm100
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x20000
  gap          111979
#  toggle_bit_mask 0x28
  toggle_bit_mask 0x140000

      begin codes
          KEY_ENTER                0x28
          KEY_MENU                 0x65
          KEY_BACK                 0x2A
      end codes

end remote
``````
lirc1.conf

begin remote

  name  rm100
  bits           24
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  8
  post_data      0xB7
  gap          111979
#  toggle_bit_mask 0x4000
  toggle_bit_mask 0x0

      begin codes
          KEY_LEFT                 0x29A515
          KEY_UP                   0x2AA515
          KEY_RIGHT                0x2BA515
          KEY_DOWN                 0x289515
          KEY_SUSPEND              0x288195
          KEY_VOLUMEUP             0x28A395
          KEY_VOLUMEDOWN           0x28A595
          KEY_CHANNELUP            0x289395
          KEY_CHANNELDOWN          0x288795
          KEY_PLAYPAUSE            0x2A8315
          KEY_MUTE                 0x2B9595
          KEY_PREVIOUS             0x298315
          KEY_NEXT                 0x2B8315
          KEY_GOTO                 0x2AB195
          KEY_POWER                0x9115
          KEY_SUSPEND              0x8195

      end codes

end remote

```the tuned toggle_bit_mask is to disable the double keypresses.

then you need to start two lircd processes and link them together;
```
lircd --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --listen=8765 lirc0.conf
lircd --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --output=/dev/lircd --connect=localhost:8765 lirc1.conf

$ tail -n4 /var/log/daemon.log
Aug 16 20:45:12 htpc lircd-0.8.5[13740]: lircd(default) ready
Aug 16 20:45:12 htpc lircd-0.8.5[13742]: lircd(default) ready
Aug 16 20:45:12 htpc lircd-0.8.5[13740]: accepted new client from 127.0.0.1
Aug 16 20:45:12 htpc lircd-0.8.5[13742]: connected to localhost
```now fire up irw and see if all the keys are working as they should, fix your Lircmap.xml and you're good to go.

---

### Post by eorndil on 2009-08-18
I have finally removed all lirc files and reinstalled the 0.8.5 from CVS.

I still have to disable usbhid, then I have no keyboard and mouse... but it's not a matter anymor (SSH). Fortunately, I have an USB DVB receiver and it works because it's not a USB HID ;)

I have now one /dev/lirc0 and no lirc1.  All the remote key are recognize with /dev/lirc0.

I can say It works good for me.

---

### Post by frdrk on 2009-08-18
> **eorndil said:**
> 
I have now one /dev/lirc0 and no lirc1.  All the remote key are recognize with /dev/lirc0.

I can say It works good for me.

Hm, kinda strange you dont have the double devices both me and shabazzk got. 

is this the device you got?: 
[IMG]http://www.kustompcs.co.uk/acatalog/5496.jpg[/IMG]

edit: might be that 0.8.5 CVS has fixed the double device-thingy and is able to use only /dev/lirc0, didnt cross my mind earlier.

---

### Post by shabazzk on 2009-08-18
I have the internal version of that frdrk. 
[IMG]http://www.kshabazz.net/images/stationBasic.jpg[/IMG]

Well, I'm having a few problems. Mainly I don't know where to put the lirc configs as the hardware.conf in /etc/lirc seem to get ignored. I also took a look at the lirc init script, and there are testing code in there that I don't think should be. So when I get home tonight, I'm going to follow your instructions to the letter frdrk. If that doesn't work, then I will try to install from CVS.

Hey can you supply step by step instructions on what you did? Could help others.

MAN, I would REALLY love to see this thread marked solved. But LIRC needs a MAHJOR overhaul, and I don't think the current developer has time.

---

### Post by eorndil on 2009-08-20
Yes Frdrk, I have the device you show.

For the config file, I don't really know where lirc take it.

First, I have put the path in the hardware.conf but when I've made "irw", I have seen that the key I was pressing were taken from another config file, the one  I did before with lirrecord (wich wasn't the good one) ...

So, I have wrotten another init script who launch :

lirc -d /dev/lirc0 $path_for_lirc_config_created

and I have removed the lirc init script (in  /etc/rc2.d).
By this way, I think the hardware.conf is ignored but I'm not sure.

---

### Post by eti.que on 2009-09-03
Hi all,

In my case (Karmic minimal + XBMC) the quirks doesn't do anything... I just cannot get rid of usbhid.

Any advice?

Thanks!

---

### Post by duckdown on 2009-09-21
Bump for help :(

I am also using an Antec MultiMedia Station E-Z, listed as Bus 005 Device 002: ID 15c2:0042 SoundGraph Inc.

Most of the things I have read in this thread haven't worked for me or are too complicated for me (I am a novice user)

I am using Ubuntu 9.04.1

If anyone has one of these devices (They are readily available everywhere here in Canada for only 25 bucks) it would really be ideal to get this thing working

If anyone can help me out or point me in the right starting direction it would be greatly appreciated

thanks!


cheers

---

### Post by CrazyDave on 2009-09-22
Hi Guys,

I've an Antec Micro Fusion 350 Remote with this RM100 control. It works pretty fine with Ubuntu 8.10 and XBMC.

I used the guides that you'll find in the XBMC Forum: [http://xbmc.org/forum/showthread.php?t=40290&highlight=antec+micro+fusion](http://xbmc.org/forum/showthread.php?t=40290&highlight=antec+micro+fusion). There you should find all your answers!

However my question to you is about the remote itself - I think that the battery runs out very fast so that sometimes the buttons will not work until i reinsert the battery. Did any of you guys had the same expirience. I may also have a defective contact in the remote so I also tried to configure a Logitech Harmony with the RM100 Config but I never had any luck.

Maybe someone has an idea?!

Cheers,
David

---

### Post by skdevnath on 2009-09-30
I was able to make my remote working fine with the help of this thread as well other threads in ubuntu forum.

Thanks for the instructions.

:guitar:

Now the LCD part of Antec Fusion 350 RM100 

[IMG]http://www.newegg.com/Product/ShowImage.aspx?CurImage=11-129-046-03.jpg&Image=11-129-046-02.jpg%2c11-129-046-03.jpg%2c11-129-046-04.jpg%2c11-129-046-05.jpg%2c11-129-046-06.jpg%2c11-129-046-07.jpg%2c11-129-046-08.jpg%2c11-129-046-09.jpg%2c11-129-046-10.jpg%2c11-129-046-11.jpg%2c11-129-046-12.jpg%2c11-129-046-13.jpg&S7ImageFlag=0&WaterMark=1&Item=N82E16811129046&Depa=1&Description=Antec%20Black%20M%20FusionRemote%20350%20Micro%20ATX%20Media%20Center%20%2f%20HTPC%20Case[/IMG]
[IMG]http://www.newegg.com/Product/ShowImage.aspx?CurImage=11-129-046-03.jpg&Image=11-129-046-02.jpg%2c11-129-046-03.jpg%2c11-129-046-04.jpg%2c11-129-046-05.jpg%2c11-129-046-06.jpg%2c11-129-046-07.jpg%2c11-129-046-08.jpg%2c11-129-046-09.jpg%2c11-129-046-10.jpg%2c11-129-046-11.jpg%2c11-129-046-12.jpg%2c11-129-046-13.jpg&S7ImageFlag=0&WaterMark=1&Item=N82E16811129046&Depa=1&Description=Antec%20Black%20M%20FusionRemote%20350%20Micro%20ATX%20Media%20Center%20%2f%20HTPC%20Case[/IMG][http://www.newegg.com/Product/Product.aspx?Item=N82E16811129046&Tpk=antec%20350](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129046&Tpk=antec%20350)


I followed following instructions with no success.

[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)
[http://xbmc.org/forum/showthread.php?t=40290&highlight=antec+micro+fusion](http://xbmc.org/forum/showthread.php?t=40290&highlight=antec+micro+fusion)
[http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474)

I have questions
  - Manufacturer of LCD is Veris or imon or Veris is model name ?
    So fare I install all deriver and config etc with imon as mentioned in above threads. 
  - Any one of you make it work ?

---

### Post by CrazyDave on 2009-09-30
> **skdevnath said:**
> I was able to make my remote working fine with the help of this thread as well other threads in ubuntu forum.

Thanks for the instructions.
Now the LCD part of Antec Fusion 350 RM100 

I followed following instructions with no success.

[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)
[http://xbmc.org/forum/showthread.php?t=40290&highlight=antec+micro+fusion](http://xbmc.org/forum/showthread.php?t=40290&highlight=antec+micro+fusion)
[http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474)

I have questions
  - Manufacturer of LCD is Veris or imon or Veris is model name ?
    So fare I install all deriver and config etc with imon as mentioned in above threads. 
  - Any one of you make it work ?

1) Soundgraph is the manufacturer
2) Maybe [http://codeka.com/forums/viewtopic.php?f=3&t=22](http://codeka.com/forums/viewtopic.php?f=3&t=22) will help you

My LCD works well! I also can display the Icons (but that's XBMC related [http://xbmc.org/forum/showthread.php?t=55696](http://xbmc.org/forum/showthread.php?t=55696)).

---

### Post by skdevnath on 2009-10-01
> **CrazyDave said:**
> 1) Soundgraph is the manufacturer
2) Maybe [http://codeka.com/forums/viewtopic.php?f=3&t=22](http://codeka.com/forums/viewtopic.php?f=3&t=22) will help you

My LCD works well! I also can display the Icons (but that's XBMC related [http://xbmc.org/forum/showthread.php?t=55696](http://xbmc.org/forum/showthread.php?t=55696)).

Thanks for the link. I tried it again (looks same to earlier link), however this time I tried after removing the lcdproc and previously downloaded source code config etc etc. I just see time getting displayed. 

I think my piece is defective one. I will call the customer support tomorrow. My 30 days purchase period is over for newegg RMA :(

---

### Post by CrazyDave on 2009-10-04
> **skdevnath said:**
> Thanks for the link. I tried it again (looks same to earlier link), however this time I tried after removing the lcdproc and previously downloaded source code config etc etc. I just see time getting displayed. 

I think my piece is defective one. I will call the customer support tomorrow. My 30 days purchase period is over for newegg RMA :(

You'll need a program that tells the imon what it should display. For example if you use XBMC you have to set the LCD settings to to lcdproc.

---

### Post by shabazzk on 2009-10-06
Heres a Tut that may help!

[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)

---

### Post by speed32219 on 2009-10-10
I have this working just fine for the past couple of months.  Of course it took me 2 weeks to get it working.  I was under the impressions that this device would only support the antec rm100/200 remote.  But the literature states that it is mce compatible, so a MS MCE should work with it.

I have not been able to get it to work, so I am just using the RM100, but it is a pain, I need more hard and soft keys.

Here is some info from the new lirc 8.6.x release
* added support for putting iMON receviers into MCE/RC6 mode
* added input subsystem mouse device support to iMON driver
* [B]improved iMON driver to handle dual-interface iMON devices
    via a single lirc device, reducing configuration complexity
[/B]
 SO, it looks as if now it should suuport MCE remote as well as combining dual devices (lirc0/1) into only 1.
I
  Anyone try it yet?

I'm going to start on it and hopefully the gremblins will stay away.  I don't have the time right now to spend on it.

---

### Post by shabazzk on 2009-10-11
Yeah, I remember trouble shooting this with Antec support guy. I remember having to boot into windows 7 and change the remote to MCE mode to test the rm100 remote which turned out to be busted. After they RMA'd I left the IR in RM100 mode, just until I get rm100 working. Then I will program the logitech harmony 550 as an MCE. However, I'm still struggling with rm100.

---

### Post by speed32219 on 2009-10-13
"However, I'm still struggling with rm100"

I thought you had it going by now.  What are you struggling with.  I can post the lirc0, lirc1 and lircd.conf if you want it.

The RM100/200  is fully working with Ubuntu 8.10 Intrepid, and previous releases ONLY! (THE Antec Veris Basic supports the rm200 also, but my URC MX810 does not support those remotes, arrgggghhhh)

I spent a whole day trying to get it to work with Jaunty.  Jaunty is broken, it has a problem in that it will **NOT**, release the usbhid driver.  Well, it does if you remove ALL hid devices including keyboards/mouse. 

I installed Jaunty on a 8GB flash to check the usbhid problem.  Next weekend I will install 8.10 on the flash and try the new LIRC 8.6.x drivers.  If I get it working, I will post back.

---

### Post by frdrk on 2009-10-20
> **speed32219 said:**
>  * [B]improved iMON driver to handle dual-interface iMON devices
    via a single lirc device, reducing configuration complexity
[/B]
 SO, it looks as if now it should suuport MCE remote as well as combining dual devices (lirc0/1) into only 1.
I
  Anyone try it yet?
 

Yeah I did a dist-upgrade and suddenly my dual-interface lirc config stopped working. Noticed that there was only /dev/lirc0 and redid my config via irrecord, works great.

---

### Post by shabazzk on 2009-10-20
I just installed the ati drivers on 9.10 last night, so I hope to get lirc working tonight. 

Question, has anyone been able to use the antec remote config that ships with lirc? Or has every one had to make their own?

I installed lirc 0.8.6 on 9.10, however I do NOT get /dev/lirc0. I checked the log and saw this:

```
[    8.732580] lirc_dev: IR Remote Control driver registered, major 61 
[    8.736345] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
[    8.736381] usbcore: registered new interface driver lirc_imon
```

---

### Post by jfacemyer on 2009-10-24
Hey, shabazzk, any development?  I'm waiting for the official release (and some time :), but I'm hoping it will work (just bought the Basic).

---

### Post by shabazzk on 2009-10-25
I'm working on it now. The problem I'm having right now is that after I installed lirc from synaptic, and rebooted, I still do not have /dev/lirc0 device. 

After reading the configure documentation, it stated that lirc needs exclusive access to the device and that there may be a conflict with HAL. Sure enough there was, and there was an easy fix to that, but now it seems that usb drivers are still loaded for it even though I got HAL to ignore the device.

So I need to do some more reading, unless someone can inform me how to fix this problem. 

Once I get usb drivers not to load for the IR device, I am sure it will work with no problems.

---

### Post by frdrk on 2009-10-31
> **shabazzk said:**
> I'm working on it now. The problem I'm having right now is that after I installed lirc from synaptic, and rebooted, I still do not have /dev/lirc0 device. 

After reading the configure documentation, it stated that lirc needs exclusive access to the device and that there may be a conflict with HAL. Sure enough there was, and there was an easy fix to that, but now it seems that usb drivers are still loaded for it even though I got HAL to ignore the device.

So I need to do some more reading, unless someone can inform me how to fix this problem. 

Once I get usb drivers not to load for the IR device, I am sure it will work with no problems.


Great job man :].

---

### Post by tji on 2009-11-03
I re-tried my Antec Veris receiver ( 15c2:0042 ) with Ubuntu 9.10, and it recognized it out of the box,  no config tweaking needed.

Unfortunately, the RM100 remote wasn't fully recognized.  The Enter key works, but none of the others had any response.   I haven't yet debugged it.

---

### Post by kreedtek21 on 2009-11-04
tji,

Re: "The Enter key works, but none of the others had any response.", when this happens to me, I find it is because HID still has a hold of the device.

I am still struggling to get usbhid to ignore it.  If I do a manual unbind, then lirc_imon grabs it and all works well.

---

### Post by hopwon on 2009-11-04
> **kreedtek21 said:**
> tji,

Re: "The Enter key works, but none of the others had any response.", when this happens to me, I find it is because HID still has a hold of the device.

I am still struggling to get usbhid to ignore it.  If I do a manual unbind, then lirc_imon grabs it and all works well.


Dude, how did you do the unbind? I'm struggling getting consistent results.

---

### Post by Plaguester on 2009-11-07
I'm also looking for help with this. I have an Antec Veris Basic (rm100 remote) internal device. After following some of the directions above, I have the Back, Enter, and Menu buttons working in XBMC. I tried adding the quirks line into /etc/modprobe.d/usbhid.conf, but lost mouse/keyboard support.

If anyone has made any progress or has any ideas, please let me know.

---

### Post by jfacemyer on 2009-11-12
I also have not been able to get the quirks to work, or hid to let go (except with a udev rule, but then you can't do anything with it!!)

Seriously - what's the "rule" that makes usbhid stop touching my hardware?  

Anybody?

Nobody?

Bueller?

---

### Post by tji on 2009-11-12
I also have not been able to make usbhid ignore the Veris, and would be interested in a reliable way to control this.

---

### Post by shabazzk on 2009-11-12
I was able to unbind usbhid from the veris, but I had some stability problems when I tried to bind lirc to it, meaning I did something wrong.

Here is a good start to learn how to unbind and bind drivers in linux user space.

[http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)

Note: I'm learning so much, but feel like I am way off somehow. Wish some linux Guru would help us.:popcorn:

---

### Post by sparkey on 2009-11-12
So I am in basically the same boat.

Device exists:

  lsusb
  ...
  Bus 005 Device 014: ID 15c2:0042 SoundGraph Inc. 

Dmesg:

  [ 6789.394233] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
  [ 6789.394298] usbcore: registered new interface driver lirc_imon

sudo /etc/init.d/lirc start

 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...done.

ls /dev/lirc*

  /dev/lircd



No lirc0 ... anyone having any luck with this issue?

---

### Post by shabazzk on 2009-11-13
> **sparkey said:**
> So I am in basically the same boat.

Device exists:

  lsusb
  ...
  Bus 005 Device 014: ID 15c2:0042 SoundGraph Inc. 

Dmesg:

  [ 6789.394233] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
  [ 6789.394298] usbcore: registered new interface driver lirc_imon

sudo /etc/init.d/lirc start

 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...done.

ls /dev/lirc*

  /dev/lircd



No lirc0 ... anyone having any luck with this issue?


Well...GOOD NEWS!

I just figured a solution to unbind usbhid and then bind lirc to the Antect Veris basic in Ubuntu 9.10 that will work, and have come here to share. Be warned, you will have to do it again if you restart your machine. At least until I right a script that will run on boot, or someone lets us know a better way.

This can be confusing at first, I spent a week getting familiar with udev system and sysfs, as I have found out that Ubuntu 9.10 has started to discontinue HAL support. Which is a good thing. 


Step 1: Install tree from Synaptic Package Manager.

Step 2. Well mount the usbfs so we can see where our device is located in the sysfs heirarchy:
```
sudo mount -t usbfs none /proc/bus/usb/
sudo cat /proc/bus/usb/devices

```
[IMG]http://www.kshabazz.net/usbhid_loaded_antec.png[/IMG]

Note: This method for finding sysfs path may be faulty. As for the '1' before the period below, that comes from the #EPs number on the corresponding lines.

Step 3. Time to unbind the usbhid driver from the Antec Veris Basic device.
```
echo -n [COLOR="Magenta"]5[/COLOR]-[COLOR="Blue"]3[/COLOR]:1.[COLOR="Lime"]0[/COLOR] | sudo tee -a /sys/bus/usb/drivers/usbhid/unbind
echo -n [COLOR="Magenta"]5[/COLOR]-[COLOR="Blue"]3[/COLOR]:1.[COLOR="Lime"]1[/COLOR] | sudo tee -a /sys/bus/usb/drivers/usbhid/unbind
```

Step 4. Now bind the lirc_imon device to the Antec Veris Basic, but before you do, you should have installed lirc at this point.
```
echo -n 5-3:1.0 | sudo tee -a /sys/bus/usb/drivers/lirc_imon/bind
echo -n 5-3:1.1 | sudo tee -a /sys/bus/usb/drivers/lirc_imon/bind
```

Step 5. If you're like me, you didn't have lirc0 after installing lirc, so this may help, otherwise you may receive an error if you run this command:
```
sudo mknod /dev/lirc0 c 61 0
```

Step 6. You can run the following command(s) to verify things are as they should be:
```
sudo cat /proc/bus/usb/devices

tree /sys/bus/usb/drivers/lirc_imon/

dmesg | grep lirc
```

Step 7. Most importantly you should be able to run irw and test your remote. 

Note: However, if you do NOT have a working /etc/lirc/hardware.conf or /etc/lirc/lircd.conf, then you need to fix them. I had the default setup from the install, so mine just started working after performing the above.

---

### Post by Plaguester on 2009-11-14
Apparently mine was 4-6:1.0 despite the output from /proc/bus/usb/devices

Here is how to make a startup script so that you don't lose it on reboot.

1. Save the following text as fixIR.sh, but replace the device ID with your own.
```

#! /bin/bash
echo -n 4-6:1.0 > /sys/bus/usb/drivers/usbhid/unbind
echo -n 4-6:1.1 > /sys/bus/usb/drivers/usbhid/unbind
echo -n 4-6:1.0 > /sys/bus/usb/drivers/lirc_imon/bind
echo -n 4-6:1.1 > /sys/bus/usb/drivers/lirc_imon/bind

```

2. Run the following.
```

$ sudo cp fixIR.sh /etc/init.d/.
$ sudo chown root:root /etc/init.d/fixIR.sh
$ sudo chmod +x /etc/init.d/fixIR.sh
$ sudo update-rc.d fixIR.sh defaults 98 02

```

ta da!

---

### Post by shabazzk on 2009-11-14
This is great, we finally did it. I will probably install the official release of ubuntu 9.10 today, as I am still running the beta. I will definately use this init script.

Does anyone have a working .lircrc file for xbmc? How am I supposed to know what to put for the prog and config values to control xbmc?

Has anyone else noticed that the exit button has different codes for when it pressed and released?
One is mapped to rm100 and the other rm200. :]

---

### Post by Plaguester on 2009-11-14
I'm working on getting it working in XBMC and will post the mappings when finished.

---

### Post by Plaguester on 2009-11-14
OK, got XBMC working.

1. By default, some of the buttons show up on RM200 and some on RM100. This is annoying, so we'll fix it:

```

# save your old config
cd /usr/share/lirc/remotes/imon
sudo cp lircd.conf.imon-antec-veris lircd.conf.imon-antec-veris.original

```

Now open lircd.conf.imon-antec-veris in your favorite editor as root and replace its contents with the following:

```

begin remote

  name   	AntecVeris
  bits                  64
  eps                   30
  aeps                 100

  one              0     0
  zero             0     0
  gap               139998
  ignore_mask 0x0000000000000301
  min_repeat             1
  toggle_bit             0

      begin codes
          KEY_EXIT                 0x2881d5b700000201 # AppExit
          KEY_POWER                0x289115b700000201 # Power
          Go                       0x2ab195b700000201 # Go
          KEY_MUTE                 0x2b9595b700000201 # Mute
          KEY_VOLUMEUP             0x28a395b700000201 # VOL +
          KEY_VOLUMEDOWN           0x28a595b700000201 # VOL -
          KEY_CHANNELUP            0x289395b700000201 # CH +
          KEY_CHANNELDOWN          0x288795b700000201 # CH -
          RightMenu                0x0200006500000201 # Right Menu
          KEY_ENTER                0x0200002800000201 # ENTER
          KEY_BACKSPACE            0x0200002a00000000 # Backspace
          KEY_UP                   0x2aa515b700000101 # Pad Up
          KEY_LEFT                 0x29a515b700000101 # Pad Left
          KEY_ENTER                0x0200002800000000 # ENTER
          KEY_RIGHT                0x2ba515b700000101 # Pad Right
          KEY_DOWN                 0x289515b700000101 # Pad Down
          KEY_REWIND               0x298315b700000101 # Rewind
          KEY_PLAY                 0x2a8315b700000101 # Play
          KEY_FASTFORWARD          0x2b8315b700000101 # Fast Forward
      end codes
end remote

```

2. Now edit the /usr/share/xbmc/system/Lircmap.xml file as root and add the following remote definition:

```

<remote device="AntecVeris">
	<power>KEY_POWER</power>
	<select>KEY_ENTER</select>
	<back>KEY_BACKSPACE</back>
	<menu>KEY_EXIT</menu>
	<mute>KEY_MUTE</mute>
	<pageplus>KEY_CHANNELUP</pageplus>
	<pageminus>KEY_CHANNELDOWN</pageminus>
	<volumeplus>KEY_VOLUMEUP</volumeplus>
	<volumeminus>KEY_VOLUMEDOWN</volumeminus>
	<more>Go</more>
	<title>RightMenu</title>
	<play>KEY_PLAY</play>
	<forward>KEY_FASTFORWARD</forward>
	<reverse>KEY_REWIND</reverse>
	<left>KEY_LEFT</left>
	<right>KEY_RIGHT</right>
	<up>KEY_UP</up>
	<down>KEY_DOWN</down>
</remote>

```

3. Reboot (or restart lirc, then restart XBMC).

Now to get my universal remote working...

---

### Post by sparkey on 2009-11-15
Followed your instructions and now everything is working great!  I can finally retire my homebrew USB keyboard-hack remote :) 

When I saw keycodes finally output in irw I have to say I got a little misty!  Thanks again shabazzk, Plaguester and everyone else who has been fighting with this for so long.

---

### Post by jfacemyer on 2009-11-16
Sweet!  Unfortunately I don't have time to try it out, but it looks like it shouldn't be a problem.

It would be better to be able to include some sort of rule to keep usbhid from binding in the first place, though.  Is this sort of thing possible?

(Not complaining, but a better way would be preferable.)

Thanks for all the brain-bashing you did, shabazzk (and others)!  Awesome!

---

### Post by dude051 on 2009-11-16
After some research, its much easier, and more proper, to use the udev system to accomplish the unbind of the usbhid driver which will allow the lirc_imon driver to bind to it when it loads thereafter.

As root, make the following file and add this single line of code:

~$ sudo nano /etc/udev/rules.d/99-imon.rules

```
SYSFS{idVendor}=="15c2", SYSFS{idProduct}=="0042", MODE="0666", PROGRAM="/bin/sh -c 'echo -n $id:1.0 >/sys/bus/usb/drivers/usbhid/unbind;\
echo -n $id:1.1 >/sys/bus/usb/drivers/usbhid/unbind'"
```

Your idProduct may vary, and can be checked using the following:

xbmc@XBMCLive:~$ sudo lsusb | grep "ID 15c2"
Bus 004 Device 002: ID 15c2:0042 SoundGraph Inc.

This pulls out the the vendor id and you can see the Bus and Device location, as well as it's ID which is the idVendor:idProduct. These are the values used by the udev script to match the device when started.

What this script does NOT do (and neither does any other way that works by unbinding the usbhid module) is re-claim the device on resume from S3 suspend. After the resume, the usbhid driver grabs it again! Overall, this has to be submitted as a bug so that a patch can be made against the usbhid module to blacklist these devices in quirks...

-- Also, just for kicks the tree command is nice, but you can also just nicely ls the location to see the driver bindings:

xbmc@XBMCLive:~$ ls -lR /sys/bus/usb/drivers/lirc_imon/
/sys/bus/usb/drivers/lirc_imon/:
total 0
lrwxrwxrwx 1 root root    0 2009-11-16 20:33 4-1:1.0 -> ../../../../devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0
lrwxrwxrwx 1 root root    0 2009-11-16 20:33 4-1:1.1 -> ../../../../devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.1
--w------- 1 root root 4096 2009-11-16 20:33 bind
lrwxrwxrwx 1 root root    0 2009-11-16 20:33 module -> ../../../../module/lirc_imon
--w------- 1 root root 4096 2009-11-16 20:33 new_id
--w------- 1 root root 4096 2009-11-16 20:33 uevent
--w------- 1 root root 4096 2009-11-16 20:33 unbind

Verify device location and binding (don't forget to escape the ':'):

xbmc@XBMCLive:~$ dmesg | grep 4-1\:1.0
[    2.591153] input: HID 15c2:0042 as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input6
[    8.998610] input: iMON PAD IR Mouse (15c2:0042) as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input8


All done :)

---

### Post by shabazzk on 2009-11-18
> **dude051 said:**
> After some research, its much easier, and more proper, to use the udev system to accomplish the unbind of the usbhid driver which will allow the lirc_imon driver to bind to it when it loads thereafter.

As root, make the following file and add this single line of code:

~$ sudo nano /etc/udev/rules.d/99-imon.rules

```
SYSFS{idVendor}=="15c2", SYSFS{idProduct}=="0042", MODE="0666", PROGRAM="/bin/sh -c 'echo -n $id:1.0 >/sys/bus/usb/drivers/usbhid/unbind;\
echo -n $id:1.1 >/sys/bus/usb/drivers/usbhid/unbind'"
```

Your idProduct may vary, and can be checked using the following:

xbmc@XBMCLive:~$ sudo lsusb | grep "ID 15c2"
Bus 004 Device 002: ID 15c2:0042 SoundGraph Inc.

This pulls out the the vendor id and you can see the Bus and Device location, as well as it's ID which is the idVendor:idProduct. These are the values used by the udev script to match the device when started.

What this script does NOT do (and neither does any other way that works by unbinding the usbhid module) is re-claim the device on resume from S3 suspend. After the resume, the usbhid driver grabs it again! Overall, this has to be submitted as a bug so that a patch can be made against the usbhid module to blacklist these devices in quirks...

-- Also, just for kicks the tree command is nice, but you can also just nicely ls the location to see the driver bindings:

xbmc@XBMCLive:~$ ls -lR /sys/bus/usb/drivers/lirc_imon/
/sys/bus/usb/drivers/lirc_imon/:
total 0
lrwxrwxrwx 1 root root    0 2009-11-16 20:33 4-1:1.0 -> ../../../../devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0
lrwxrwxrwx 1 root root    0 2009-11-16 20:33 4-1:1.1 -> ../../../../devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.1
--w------- 1 root root 4096 2009-11-16 20:33 bind
lrwxrwxrwx 1 root root    0 2009-11-16 20:33 module -> ../../../../module/lirc_imon
--w------- 1 root root 4096 2009-11-16 20:33 new_id
--w------- 1 root root 4096 2009-11-16 20:33 uevent
--w------- 1 root root 4096 2009-11-16 20:33 unbind

Verify device location and binding (don't forget to escape the ':'):

xbmc@XBMCLive:~$ dmesg | grep 4-1\:1.0
[    2.591153] input: HID 15c2:0042 as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input6
[    8.998610] input: iMON PAD IR Mouse (15c2:0042) as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input8


All done :)

I haven't tried this yet, as I am moving to a new APT. But if this works this would be exactly what I was trying to figure out.

---

### Post by jfacemyer on 2009-11-23
The udev solution worked fine, except that I had to create a symlink - no /dev/lirc node was created.  I symlinked to /dev/lirc0.  (Is there a better way to manage that?)

Also, I'm having trouble with my Sony RM-VL600 and other remotes.  The only remote that will seem to work is the one that came with the Basic.  irrecord doesn't recognize that I am sending it ir signals, but the blue light on the Basic blinks no matter what ir signal I send it.

I've tried a regular tv remote, doesn't work either.

However, programming the Sony with the included remote from the Basic works...but that only gives me one set of controls, and a very limited one at that!

Any ideas or recommendations?

---

### Post by shabazzk on 2009-11-23
```
SYSFS{idVendor}=="15c2", SYSFS{idProduct}=="0042", MODE="0666", PROGRAM="/bin/sh -c 'echo -n $id:1.0 >/sys/bus/usb/drivers/usbhid/unbind;\
echo -n $id:1.1 >/sys/bus/usb/drivers/usbhid/unbind[COLOR="SeaGreen"];\
mknod /dev/lirc0 c 61 0[/COLOR]'"
```

Try the green code at the end for a temp fix, not sure if it will  work as I haven't tested it. There is a better way with more UDEV parameters, but I'm not sure how to set the major and minor that way yet. So if this works it is only temporary. 

As for other remotes, you may have to put ur lirc device into MCE mode, and the only way I know how to do that is through windows.

And yes, the IR device will blink at any IR signal it catches.

---

### Post by atom boom on 2009-11-28
so i am kinda new to ubuntu and such but yea 
so i did all the stuff it says on herebut my lirc still cant find the receiver and  this is the usb that i have my "antec veris multimedia station ez" pluged into i am runing 9.10 and im trying to get this to work with xbmc so any help would be very appreciated 

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0042 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

---

### Post by shabazzk on 2009-11-28
> **atom boom said:**
> so i am kinda new to ubuntu and such but yea 
so i did all the stuff it says on herebut my lirc still cant find the receiver and  this is the usb that i have my "antec veris multimedia station ez" pluged into i am runing 9.10 and im trying to get this to work with xbmc so any help would be very appreciated 

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0042 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

Uhh...Dude, lirc clearly sees your IR, as the lirc driver is loaded for your IR.

1. What version of Ubuntu are you running?
2. What remote do you have?

NOTE: some ppl have reported that the steps in this thread only work for the IR 100 remote and not their MCE remote.

Type this in a console:
```
ls /dev | grep lirc
```

If you see lircd and lirc0 listed in the output, then you can move on to the next step, otherwise, you'll need to manually make the one with this command:
```
sudo mknod /dev/lirc0 c 61 0
```

Next, try to test your remote using this command:
```
irw
```
After typing this press buttons on the remote, if you see output, then all you have to do is setup XBMC, if you do not, then there is problem.

I will try to get this to work with my MCE remote tonight.

---

### Post by atom boom on 2009-11-28
scratch that last one i screwd something up along the way it works perfectly now i just re did everything and i want to thank every one that posted couse of u i got a fully working remote :)

---

### Post by shabazzk on 2009-12-16
I just reinstalled Karmic 9.10 and the first thing I did after updating the system was to install lirc and run the following:

sudo gedit /etc/udev/rules.d/90-lirc.rules

Copy and paste this in the file, then reboot (note: this only works for my device on my system):
```
#Attach lirc driver to Antec Verid device.
SYSFS{idVendor}=="15c2", SYSFS{idProduct}=="0043", MODE="0666", PROGRAM="/bin/sh -c 'echo -n $id:1.0 >/sys/bus/usb/drivers/usbhid/unbind;\
echo -n $id:1.1 >/sys/bus/usb/drivers/usbhid/unbind'"

```

Worked as expected, and lirc0 was there as it should have been. I waited a whole year for this simple solution. Thanks to the Ubuntu community I got it, albeit a little late. :guitar:

Now to test my Harmony 550 remote with it. :lolflag:

---

### Post by jaykumar_2001 on 2010-01-06
Thanks a lot..shabazzk

Works like a charm.

Thanks,
Jay Kumar

---

### Post by MrIcka on 2010-01-14
Hi, I can't get my remote to work properly.

It's working... sometimes =) if i run irw i get output on lets say up and it works but if I then press down i get nothing and if I after that press up again  I have to press it like 10 times before it works again... whats wrong.

Running 9.10 and i have selected the IMON Antec Veris in Lirc and created the file /etc/udev/rules.d/90-lirc.rules[B]

And changed it to my id 15c2:0038

Please help me =)
[/B]

---

### Post by shabazzk on 2010-01-14
What remote are you using? Check your /etc/lirc/lircd.conf file to make sure it points to the correct imon remote file. You may need to make your own with irrecrd. 

Also, do you have the Antec Veris Basic or something elst?

---

### Post by MrIcka on 2010-01-15
I'm using the rm100 that came with my Antec Fusion Micro, yeah not Antec Basic... maybe thats whats wrong?

Yes the lircd.conf file is correct and I get output whit mode2 --raw.

Another strange thing is that the play, FF, Rew and the green button is not reconised at all by the mode2 but al other buttons work there

Some more info:

xbmc@XBMCLive:~$ ls -lR /sys/bus/usb/drivers/lirc_imon/
/sys/bus/usb/drivers/lirc_imon/:
total 0
lrwxrwxrwx 1 root root    0 2010-01-15 09:24 3-4:1.0 -> ../../../../devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0
lrwxrwxrwx 1 root root    0 2010-01-15 09:24 3-4:1.1 -> ../../../../devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.1
--w------- 1 root root 4096 2010-01-15 09:24 bind
lrwxrwxrwx 1 root root    0 2010-01-15 09:24 module -> ../../../../module/lirc_imon
--w------- 1 root root 4096 2010-01-15 09:24 new_id
--w------- 1 root root 4096 2010-01-15 09:24 uevent
--w------- 1 root root 4096 2010-01-15 09:24 unbind


xbmc@XBMCLive:~$ dmesg | grep 3-4\:1.0
[    9.272643] input: iMON PAD IR Mouse (15c2:0038) as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input5
[   65.457989] input: iMON PAD IR Mouse (15c2:0038) as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input7

Two iMON?!? Strange or?

---

### Post by Plaguester on 2010-01-19
Does anyone know if the Antec Veris Basic receiver will work with any remote? I'm trying to get it to work with my Universal Remote (using presets for Apple/Microsoft remotes). I ran irrecord and keep getting no gap found despite the little blue LED blinking like crazy (irrecord works if I use the little RM-100 remote that it came with).

I also tried having the universal remote learn the signals from the RM-100 and that failed miserably.

---

