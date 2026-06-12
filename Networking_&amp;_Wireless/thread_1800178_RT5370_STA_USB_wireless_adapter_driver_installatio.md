---
title: "RT5370 STA USB wireless adapter driver installation"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by TubaDaddy8 on 2011-07-08
I am also trying to install a wireless driver, but mine is for the  Ralink 5370 USB wireless adapter.  Do you have some patches for that  driver, and could you show me how to install the driver?  Thanks!

Here are the results for terminal commands. I only included the device in question:

lsusb
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp.

uname -r
2.6.38-8-generic

---

### Post by chili555 on 2011-07-08
While I pour a cool one, please open Applications > Synaptic, get an ethernet connection and install build-essential and linux-headers-generic. I'll be right back.

---

### Post by TubaDaddy8 on 2011-07-08
My Synaptic Package Manager is under System > Administration, if that makes any difference, and I already have them installed.

---

### Post by chili555 on 2011-07-08
People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.

---

### Post by TubaDaddy8 on 2011-07-09
Ok, it worked fine until I got to the modprobe rt5370sta.  It says FATAL: Error inserting rt5370sta (/lib/modules/2.6.38-8-generic/kernal/drivers/net/wireless/rt5370sta.ko): Unkown symbol in module, or unknown parameter (see dmesg)

---

### Post by chili555 on 2011-07-09
> (see dmesg)Let's follow its advice and see dmesg. Please run and post:```
sudo modprobe rt5370sta
dmesg | grep rt53
```Thanks.

---

### Post by TubaDaddy8 on 2011-07-09
It says "module license 'unspecified' taints kernel."  And then a bunch of unknown symbol errors.

---

### Post by chili555 on 2011-07-09
The 'license taints kernel' is trivial (and fixable) but wouldn't stop the driver from working. The unknown symbol errors are what we need to fix, however. Can you run:```
sudo su
make clean
make
```Then copy all the text from the terminal and paste into a text document and copy that to a USB key or similar so we can see and, hopefully, fix them?

---

### Post by elrock on 2011-07-09
I had the same error message ("unknown symbol") when trying to load this module, and I was able to get rid of it by following these instructions-- 

[Build RT3070 kernel module]("http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/")

--particularly the comment by Matt Williams at the bottom.  Basically you have to edit a couple of files and replace all instances of usb_buffer_free and usb_buffer_alloc with usb_free_coherent and usb_alloc_coherent.  Then the module should load without any error messages.  (I recently upgraded to Natty, so I have the same linux kernel as you.)

As an aside, I think it is absolutely ridiculous that users have to make these kinds of edits before a module will load properly.  Most users would have no clue what to do. [/rant]

---

### Post by chili555 on 2011-07-09
> As an aside, I think it is absolutely ridiculous that users have to make these kinds of edits before a module will load properly. Most users would have no clue what to do.Ahhh, the joy of source code! It is written to try to work with kernels from 2.6.wayback to 2.6.4xx. It is written to try to work with Ubuntu, Debian, Mint, Fedora, PCLinuxOS, Suse, etc., etc. It works pretty well in most cases and not at all in a few cases. The developers put drivers in the mainline distribution as fast as they can and yet new chipsets come out daily. Typically, they come out with *NO* Linux support. When a Linux driver is eventually released, we module monkeys have to fiddle with it a bit to get it to work. It beats the answer you get on other forums and IRC: "Take it back and get a supported device." 

I wish there was a better answer.

As an aside, I walked into Big Box Store a few days ago and saw a Netgear wireless USB device on the shelf. I read the model number and immediately, the user on this forum who is struggling to get it to work came to my mind. I must get away once in a while!!

---

### Post by TubaDaddy8 on 2011-07-09
Nevermind.  This is gay.  I'm just gonna go out and buy a new version of Windows instead of messing around with this crap.  You get what you pay for.

---

### Post by Requist on 2011-12-05
They put new drivers on their side which work with the instructions given at the beginning of this topic, so only adept config.mk. Build with Ubuntu 12.04 alpha1 (kernel 3.2.0.2) :D

---

### Post by matthewh3 on 2011-12-28
> **chili555 said:**
> People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.

I have done HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'

When I do cd Desktop/2011 I get No such file or directory.  I have tried going to the folder with the command line as root

root@matt-ubuntu:/home/matt/sta/sta1/os/linux# 

and when I run the first command 'make' I get 

*** No targets specified and no makefile found. Stop.

Help I've just got my shiny new wireless N adapter and can't use it!

---

### Post by chili555 on 2011-12-28
> **matthewh3 said:**
> I have done HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'

When I do cd Desktop/2011 I get No such file or directory.  I have tried going to the folder with the command line as root

root@matt-ubuntu:/home/matt/sta/sta1/os/linux# 

and when I run the first command 'make' I get 

*** No targets specified and no makefile found. Stop.

Help I've just got my shiny new wireless N adapter and can't use it!Did you download the file to your desktop? Or where? Downloads? Where was it when you right-clicked it to 'Extract Here?'

My instructions included:> ```
cd Desktop/2011
```

***Press Tab and the remainder will fill in. Press Enter.***Did you do that?

---

### Post by matthewh3 on 2011-12-28
Sorted it but thanks.

---

### Post by chingNotCHing on 2012-01-27
It works for both my 11.10 64bit and 10.04 nbr! Thank you very much!

> **chili555 said:**
> People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

updated to [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) 
I've used v2.5.0.3 which was not available at the moment of your post. 

> **chili555 said:**
> 
RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

There is "()" in the default directory name extracted. After I've renamed the directory to remove "()", I can run make without syntax errors.

> **chili555 said:**
> 
Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.
It's my first time to make drivers. I 'm very happy. Thanks a lot!

---

### Post by chili555 on 2012-01-27
> It's my first time to make drivers. I 'm very happy. Thanks a lot!Happy to have helped. Don't forget, when a new linux-image; aka kernel is installed by Update Manager, after reboot, you'll need to build the driver against the new kernel:```
cd Desktop/RT5370  <--or wherever you extracted it
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```Glad it's working!

---

### Post by minamitek on 2012-02-13
This is the part where I'm probably forgetting something really obvious, but...

I've followed all the instructions here, make install and modprobe etc seemingly with no problems. But what happens next? I'm not seeing any settings or config for me to set up the device and enter the network password. Tried Network Connections but nothing was listed there.

---

### Post by matthewh3 on 2012-02-13
> **minamitek said:**
> This is the part where I'm probably forgetting something really obvious, but...

I've followed all the instructions here, make install and modprobe etc seemingly with no problems. But what happens next? I'm not seeing any settings or config for me to set up the device and enter the network password. Tried Network Connections but nothing was listed there.

I just entered my password as you would for any WiFi device and it worked.

---

### Post by minamitek on 2012-02-13
Where did you enter your password? After modprobe and exit it just returned me to the terminal prompt.

---

### Post by matthewh3 on 2012-02-13
> **minamitek said:**
> Where did you enter your password? After modprobe and exit it just returned me to the terminal prompt.

In the desktop network manager.

---

### Post by minamitek on 2012-02-13
Darn, something must have gone wrong after all then. Funny, I didn't get any error messages during the build process.

---

### Post by chili555 on 2012-02-13
> **minamitek said:**
> Darn, something must have gone wrong after all then. Funny, I didn't get any error messages during the build process.Let's troubleshoot. Please run and post:```
sudo modprobe rt5370sta
lsmod | grep rt5
sudo iwlist wlan0 scan
iwconfig
```Thanks.

---

### Post by minamitek on 2012-02-13
Many thanks, the help is much appreciated.
entering lsmod | grep rt5 got a result:

```
rt5370sta       801203  0
```But when I typed iwlist wlan0 scan, I got

```
wlan0   interface doesn't support scanning
```and iwconfig gave me

```
lo    no wireless extensions.
eth0  no wireless extensions.
```
Now... it's possible I'm way off track & trying to use the wrong device with this driver. lsusb lists it as a PLANEX GW-USMicroN which I'm sure is a Ralink chipset. I've been using it for years on an old Mac laptop with Ralink's OSX driver & it works fine. Just no joy this time around, unfortunately.

---

### Post by chili555 on 2012-02-13
> Now... it's possible I'm way off track & trying to use the wrong device with this driver. lsusb lists it as a PLANEX GW-USMicroN which I'm sure is a Ralink chipset. Entirely possible. Let's have a look at:```
lsusb
```We need to see details, please.

---

### Post by minamitek on 2012-02-13
Here we go:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0566:3107 Monterey International Corp. 
Bus 001 Device 004: ID 046d:c069 Logitech, Inc. 
Bus 001 Device 005: ID 2019:ed14 PLANEX GW-USMicroN


```

Device 005 being the dongle I'm trying to shoehorn into this system. Maybe time to get a newer device...

---

### Post by mindlessgr on 2012-02-14
Hello guys, i have searched very much about this device, i have written a howto on my blog, you can check if you want.
[http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/](http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/)

hope this helps someone

---

### Post by mindlessgr on 2012-02-14
Try: iwpriv ra0 get_site_survey


> **minamitek said:**
> Many thanks, the help is much appreciated.
entering lsmod | grep rt5 got a result:

```
rt5370sta       801203  0
```But when I typed iwlist wlan0 scan, I got

```
wlan0   interface doesn't support scanning
```and iwconfig gave me

```
lo    no wireless extensions.
eth0  no wireless extensions.
```
Now... it's possible I'm way off track & trying to use the wrong device with this driver. lsusb lists it as a PLANEX GW-USMicroN which I'm sure is a Ralink chipset. I've been using it for years on an old Mac laptop with Ralink's OSX driver & it works fine. Just no joy this time around, unfortunately.

---

### Post by chili555 on 2012-02-14
> **mindlessgr said:**
> Hello guys, i have searched very much about this device, i have written a howto on my blog, you can check if you want.
[http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/](http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/)

hope this helps someoneYour blog says you have:> Bus 001 Device 003: ID [COLOR="Red"]148f:5370[/COLOR] Ralink Technology, Corp. RT5370 Wireless Adapterminamitek has this:> ID [COLOR="Red"]2019:ed14[/COLOR] PLANEX GW-USMicroNrt5370sta does not claim this device. 

Googling your device suggests several (possibly conflicting) ways to get this going. Let's try rt5370sta first. Please go to the files you extracted as a part of compiling the driver. Open common/rtusb_dev_id.c with any text editor; gedit or nano, for example. Scroll down to the section below and add the highlighted text. Punctuation, brackets, spacing, etc. are crucial. Type carefully and proofread twice. After the changes are made, be sure to save and close the text editor.```
#ifdef RT5370
	{USB_DEVICE(0x148F,0x5370)}, /* Ralink 5370 */
        [COLOR="Red"]{USB_DEVICE(0x2019,0xED14)}, /* PLANEX */[/COLOR]	
	{USB_DEVICE(0x148F,0x5372)}, /* Ralink 5370 */	
	{USB_DEVICE(0x13D3,0x3365)}, /* Azurewave */
	{USB_DEVICE(0x13D3,0x3329)}, /* Azurewave */
#endif // RT5370 //
```Now we must recompile:```
cd Desktop/RT3070etc.  <--or wherever you extracted the files
sudo su
modprobe -r rt5370sta
make clean
make
make install
modprobe rt5370sta
exit
```Any improvement?

---

### Post by mindlessgr on 2012-02-14
You are right chili555, i didnt notice the device id, just posted here trying to help people with the same problem with me, and the subject says that this thread is for the same module as mine.

:)

HTH

---

### Post by minamitek on 2012-02-16
Well, how about that! Adding the magic line as you suggested:

```
 {USB_DEVICE(0x2019,0xED14)}, /* PLANEX */
```

has made all the difference and I'm now online wire-free. Many thanks once again (especially from my wife since I'll no longer be hauling the rig into the living room to plug into the wall):)

You guys are brilliant.

---

### Post by chili555 on 2012-02-17
Thanks for your kind comments. We now have a confirmed method to get the Planex 2019:ed14 working. Awesome!

---

### Post by mindlessgr on 2012-02-17
Oh, thanks minamitek, im glad that i have put a brick to your solution :)

---

### Post by extraweb1 on 2012-02-26
):P Chili and ALL

I had the same problem as the user in post 1 and my device id matches however i am using BT5R1 "Backtrack" and i have absolutley no linux experience "really only as much as a newb :lolflag: " so i tried your instructions and still nothing so as a pc dev of drivers i wanted to read the makefile and noticed it was not looking in the right directories for some reason and was missing Module.symvers in my /usr/src/linux when compiling the first time; i do know a few things unix so i used: 

```

locate Module.symvers
cp "dir without quotes where found" /usr/src/linux

```

I tried changing the following in the makefile with after using locate to locate some of the requirements of the makefile

```
LINUX_SRC =/lib/modules/$(shell uname -r)/build
to
LINUX_SRC =/usr/src/linux
```

and below it:

```
LINUX_SRC =/lib/modules/$(shell uname -r)/kernel/drivers/net/wireless
to
LINUX_SRC =/usr/src/linux/drivers/net/wireless
```

ran
```

make
make install
modprobe rt5370sta

```

and now it works in Wicd after changing the preferences for wlan0 to Ra0 I can connect and it works :guitar:

---

### Post by anymoose on 2012-03-20
HI! This is the definitive fix for Ubuntu 11.10 and TL-WN727N(V3)

Use this link (only) if kernel version is shown below; Ubuntu 11.10

ls /lib/modules

3.0.0-12-generic

Web Link;
[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)

Use user Chili555 post #2. Everything is done in post #2 ie no files to download
no compilation, no other changes. This fix must be entered carefully; all spelling,
spaces and capital/lc letters *must* be correct. Worked for me after reboot. Test
your adapter with MS-Win XP with Included utility on CD ahead of time, if possible.

Not sure if this will work in Ubuntu live filesystem on CD for obvious reasons. Works
when filesystem is on HD disk and USB stick.

This the particular fix is obviously for beginners who don't want to recompile and 
install a new device driver. It will get them running.

Signed; Anymoose

---

### Post by Krazi3 on 2012-03-24
Here are the results 

lsusb

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and lsmod | grep -e rt3 -e rt2

```
rt2870sta             410104  0 
crc_ccitt              12595  1 rt2870sta

```

---

### Post by chili555 on 2012-03-24
It won't let you use rt5370sta for a wireless driver because it's already using rt2870sta. Isn't rt2870sta working as expected? Why did you decide to compile rt5370sta? What are your symptoms? Why do I ask so many questions....Oops, sorry.

---

### Post by Krazi3 on 2012-03-24
NO it is not working and i have also blacklisted rt2870sta.

I decided to compile rt5370sta because it showed up when i do 'lsusb' .

And i are noob in linux .. dnt know much about it. :p

---

### Post by chili555 on 2012-03-24
It's evidently not blacklisted correctly if it still loads. Please show us:```
dmesg | grep rt2
modinfo rt2870sta | grep 5370
cat /etc/modprobe.d/blacklist.conf
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Krazi3 on 2012-03-25
The results are as:

dmesg | grep rt2

```
[   12.387769] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   12.392910] usbcore: registered new interface driver rt2870
[   12.466668] rtusb init rt2870 --->
[   12.466673] Error: Driver 'rt2870' is already registered, aborting...

```

modinfo rt2870sta | grep 5370

Nothing happened

cat /etc/modprobe.d/blacklist.conf
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
blacklist rt2870usb
```

---

### Post by chili555 on 2012-03-25
The mystery gets deeper! Let's have a look at:```
dmesg | grep ndis
cat /etc/modules
cat /etc/rc.local
```One wonders why rt2870sta is evidently loaded despite the fact it is blacklisted. Quite a little problem here!

---

### Post by Krazi3 on 2012-03-26
The results are as follows :

```
krazi3@krazi3-desktop:~$ dmesg | grep ndis
krazi3@krazi3-desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt2870sta
krazi3@krazi3-desktop:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

---

### Post by chili555 on 2012-03-26
Please do:```
sudo gedit /etc/modules
```Remove the rt2870sta line, proofread, save and close gedit. If you don't have gedit, use nano or any other text editor. As long as we have our text editor sharpened up, let's do some more work:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove the line 'blacklist rt2870usb'; there is no such module so it doesn't help to blacklist it. Proofread, save and close gedit.

Now reboot with the device inserted and do:```
sudo modprobe rt5370sta
```Does it error out? Does the wireless work? If not, please post:```
dmesg | grep -e rt5 -e rt2
```Thanks.

---

### Post by Krazi3 on 2012-03-26
I did as you mentioned above and now when i did modprobe rt5370sta. It succeeded. It did not give any previous errors but the wireless is still not working.

 ```
krazi3@krazi3-desktop:~$ dmesg | grep -e rt5 -e rt2
[   11.972310] rtusb init rt2870 --->
[   11.973824] usbcore: registered new interface driver rt2870
krazi3@krazi3-desktop:~$ iwconifg
No command 'iwconifg' found, did you mean:
 Command 'iwconfig' from package 'wireless-tools' (main)
iwconifg: command not found
krazi3@krazi3-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

---

### Post by chili555 on 2012-03-26
Did you make the changes to config.mk as outlined in the README before you compiled? > ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
If not, please do so and then recompile:```
cd Desktop/RT5370   <--or wherever you extracted the files
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe -r rt5370sta
modprobe rt5370sta
exit
```Any change?

---

### Post by Krazi3 on 2012-03-26
Thank you very very very much.

Finally i are connected wire free. :D

---

### Post by chili555 on 2012-03-26
Excellent! Glad it's working.

Would you please use Thread Tools at the top and Mark Solved?

---

### Post by Krazi3 on 2012-03-26
Actually i can't .. i was not the main creator that is why maybe. :(

---

### Post by cthlhu1987 on 2012-05-24
> **chili555 said:**
> People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.
Thx, went without a glitch under Xubuntu 12.04, currently using the adapther ;) :guitar:

---

### Post by Krazi3 on 2012-05-25
Yes this is greatest guide to this adapter ... :D

---

### Post by Rowley1721 on 2012-06-09
> **chili555 said:**
> People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.


I have just registered on here to say a massive thank you to Chili555.  I spent over 5 hours talking to the manufactures, reading emails, trying everything they said and comming up blank, I wrote probs in excess of 100 lines in terminal and had to install Ubuntu twice after messing up big style, then I found this post.  Awesome.

One thing I will say though is that I needed to install all updates through Update Manager before this would work but that's just a side note incase it does not work for others :)

Anyway thank you again a now very happy Dual booted Ubuntu+win7 user :D

---

### Post by entonjackson on 2012-07-13
I want to connect to a Draft-N router and I am able to. But the connection gets los after about 30 seconds. After another 30 seconds it connects again. What have I done wrong?
I installed and configured everything you described.

Thanks in advance, chilli

---

### Post by chili555 on 2012-07-13
The only things I can suggest are to set your router to WPA2 only, not WPA and WPA2 mixed mode. Also, you might look here to see if there are any interesting clues:```
sudo cat /var/log/syslog | grep -e wlan -e 5370 | tail -n20
```Reliable N speeds are kind of hit or miss, unfortunately.

---

### Post by entonjackson on 2012-07-14
Unfortunately my router only knows "no encryption", "WEP" and "WPA/WPA2". there are no advanced settings to switch to WPA2 only...

here is the output of syslog:
```
Jul 14 08:00:09 anton-bct kernel: [ 1236.509179] wlan0: RX ReassocResp from 34:08:04:d8:78:de (capab=0xc31 status=0 aid=3)
Jul 14 08:00:09 anton-bct kernel: [ 1236.509182] wlan0: associated
Jul 14 08:00:09 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 14 08:00:13 anton-bct kernel: [ 1239.566599] wlan0: deauthenticated from 34:08:04:d8:78:de (Reason: 2)
Jul 14 08:00:13 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associated -> disconnected
Jul 14 08:00:13 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 14 08:00:15 anton-bct kernel: [ 1242.287610] wlan0: authenticate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:15 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 14 08:00:15 anton-bct kernel: [ 1242.328545] wlan0: authenticated
Jul 14 08:00:15 anton-bct kernel: [ 1242.330486] wlan0: associate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:15 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 14 08:00:16 anton-bct kernel: [ 1242.528035] wlan0: associate with 34:08:04:d8:78:de (try 2)
Jul 14 08:00:16 anton-bct kernel: [ 1242.536461] wlan0: RX ReassocResp from 34:08:04:d8:78:de (capab=0xc31 status=0 aid=3)
Jul 14 08:00:16 anton-bct kernel: [ 1242.536466] wlan0: associated
Jul 14 08:00:16 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 14 08:00:17 anton-bct kernel: [ 1244.374861] wlan0: deauthenticated from 34:08:04:d8:78:de (Reason: 2)
Jul 14 08:00:17 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associated -> disconnected
Jul 14 08:00:17 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 14 08:00:20 anton-bct kernel: [ 1247.017123] wlan0: authenticate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:20 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 14 08:00:20 anton-bct kernel: [ 1247.155772] wlan0: authenticated
Jul 14 08:00:20 anton-bct kernel: [ 1247.157685] wlan0: associate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:20 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 14 08:00:20 anton-bct kernel: [ 1247.356106] wlan0: associate with 34:08:04:d8:78:de (try 2)
Jul 14 08:00:20 anton-bct kernel: [ 1247.362661] wlan0: RX ReassocResp from 34:08:04:d8:78:de (capab=0xc31 status=0 aid=3)
Jul 14 08:00:20 anton-bct kernel: [ 1247.362665] wlan0: associated
Jul 14 08:00:20 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 14 08:00:22 anton-bct kernel: [ 1249.209591] wlan0: deauthenticated from 34:08:04:d8:78:de (Reason: 2)
Jul 14 08:00:22 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associated -> disconnected
Jul 14 08:00:22 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 14 08:00:25 anton-bct kernel: [ 1251.825742] wlan0: authenticate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:25 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 14 08:00:25 anton-bct kernel: [ 1251.864884] wlan0: authenticated
Jul 14 08:00:25 anton-bct kernel: [ 1251.867668] wlan0: associate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:25 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 14 08:00:25 anton-bct kernel: [ 1252.064045] wlan0: associate with 34:08:04:d8:78:de (try 2)
Jul 14 08:00:25 anton-bct kernel: [ 1252.070020] wlan0: RX ReassocResp from 34:08:04:d8:78:de (capab=0xc31 status=0 aid=3)
Jul 14 08:00:25 anton-bct kernel: [ 1252.070024] wlan0: associated
Jul 14 08:00:25 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 14 08:00:27 anton-bct kernel: [ 1253.952557] wlan0: deauthenticated from 34:08:04:d8:78:de (Reason: 2)
Jul 14 08:00:27 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associated -> disconnected
Jul 14 08:00:27 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 14 08:00:30 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 14 08:00:30 anton-bct kernel: [ 1256.641533] wlan0: authenticate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:30 anton-bct kernel: [ 1256.732426] wlan0: authenticated
Jul 14 08:00:30 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 14 08:00:30 anton-bct kernel: [ 1256.736931] wlan0: associate with 34:08:04:d8:78:de (try 1)
Jul 14 08:00:30 anton-bct kernel: [ 1256.758889] wlan0: RX ReassocResp from 34:08:04:d8:78:de (capab=0xc31 status=0 aid=3)
Jul 14 08:00:30 anton-bct kernel: [ 1256.758892] wlan0: associated
Jul 14 08:00:30 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 14 08:00:33 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jul 14 08:00:33 anton-bct kernel: [ 1259.812550] wlan0: deauthenticated from 34:08:04:d8:78:de (Reason: 6)
Jul 14 08:00:33 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jul 14 08:00:33 anton-bct NetworkManager[918]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```

i have TKIP/AES activated, maybe i should turn this to AES only?
also i'm on 64bit precise, if this helps?

thank you.

EDIT1: Ok. i edited the html document, that has disabled configuration of WPA only and WPA2 only on my router. After testing it with WPA2 only, i couldn't get a connection no more.
So I switched back to WPA/WPA2 but all of the sudden, the driver is no more loaded properly. I cannot connect to the internet with the rt5370 no more. I must say, I played around with the .dat. Maybe that's the reason, but i repeated your installation steps but i can't get it to run no more... if i plug the dongle into my notebook, dmesg outputs this all the time:

```
RTUSB_VendorRequest failed(-71),TxFlags=0x0, ReqType=IN, Req=0x7, Idx=0x1718,pAd->Flags=0x2
```

EDIT2: Ok the driver loads somehow, but a connection is not possible so far, as I can tell. But it's not really clear, because NetworkManager behaves pretty strange, which is usually a very stable app. Anyway, if i connect the dongle with my notebook, the system seems to freeze globally, mouse moves, but nothing reacts. When i pull out the dongle again, all events seem to be processed immediately. It's like the driver is blocking the whole system... i don't know how to describe actually..

---

### Post by chili555 on 2012-07-14
> i have TKIP/AES activated, maybe i should turn this to AES only?That would be my suggestion.> also i'm on 64bit precise, if this helps?I suspect the built-in rt2800usb is interfering and needs to bo blacklisted. If it were me, I'd uninstall rt5370sta and troubleshoot rt2800usb. See if its loaded with:```
lsmod | grep rt2
```

---

### Post by entonjackson on 2012-07-14
i have uninstalled the rt5370 drivers and did a 
```
sudo modprobe rt2800usb
```
then:
```

anton@anton-bct:~$ lsmod | grep rt2
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              55301  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  4 rt2800lib,rt2x00usb,rt2x00lib,iwlwifi
cfg80211              205544  3 rt2x00lib,iwlwifi,mac80211

```

---

### Post by chili555 on 2012-07-14
> mac80211              506816  4 rt2800lib,rt2x00usb,rt2x00lib,iwlwifi
cfg80211              205544  3 rt2x00lib,[COLOR="Red"]iwlwifi[/COLOR],mac80211Hello!

Do you have an internal wireless device that's hogging Network Manager? Please tell me what your setup is.```
lspci -nn | grep 0280
iwconfig
lsusb
```

---

### Post by entonjackson on 2012-07-14
Yes, that's right. I'm trying to find out how to install this dongle, to do it on a pc, that has no internal wifi.

sorry, i should have mentioned this earlier.

---

### Post by chili555 on 2012-07-14
> **entonjackson said:**
> Yes, that's right. I'm trying to find out how to install this dongle, to do it on a pc, that has no internal wifi.

sorry, i should have mentioned this earlier.Please post:```
iwconfig
lsusb
```Thanks.

---

### Post by entonjackson on 2012-07-14
i think i have a different problem in the meanwhile. i don't know what i've done, but i think my dongle is broken now. because it's no more listed in the lsusb list. only sometimes, it's showing up the dongle again, i don't know why. if it's not listed in lsusb, dmesg is telling me this:

```

[ 802.296000] usb 2-4: new high speed USB device using uhci_hcd and address 17
[ 802.408000] usb 2-4: device descriptor read/64, error -71
[ 802.624000] usb 2-4: device descriptor read/64, error -71
[ 802.840000] usb 2-4: new high speed USB device using uhci_hcd and address 18
[ 803.248000] usb 2-4: device not accepting address 18, error -71
[ 803.360000] usb 2-4: new high speed USB device using uhci_hcd and address 19
[ 803.768000] usb 2-4: device not accepting address 19, error -71

```

sorry for bugging you with this crap...

---

### Post by chili555 on 2012-07-14
> but i think my dongle is broken now. I do, too. Is it improved in a different USB slot?

---

### Post by entonjackson on 2012-07-14
No it doesn't.

I don't know if it makes sense, to investigate further. but 5 minutes ago was one of the few moments, the dongle showed up in lsusb:
```

Bus 002 Device 019: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

```

inserting the dongle seems to block every activity that has to do with the internet connection. Chrome, Pidgin, NetworkManager, and even iwconfig seems to block. so the output here is nothing...
as i pull the dongle, all events that have to do with the internet connection seem to flush in at once. people come online/offline. clicked links in chrome are processed, and iwconfig shows wireless interfaces, but only the internal one, because at his time the dongle is off, as i said.
and if i plug it in again, doesn't show in lsusb... until the next time.

so what is your suggestion, doc? you also think that thing is broken, right? if yes, can you recommend another chip, that works ootb on precise 32bit?

thank you.

---

### Post by chili555 on 2012-07-14
This device ought to work with Precice OOTB perfectly well. I suspect the presence of the iwlwifi driver is at least part of the issue. Please try:```
sudo ifconfig wlan0 down
sudo modprobe -r iwlwifi
```Check for any leftovers:```
lsmod | grep 8021
```If cfg80211 or mac80211 are still there, remove it or them:```
sudo modprobe -r xxx80211 [COLOR="Red"]<--whichever you found[/COLOR]
```Now insert the USB. Is it working? Any symptoms to report?

---

### Post by entonjackson on 2012-07-14
I would like to tell you. But the dongle isn't shown in lsusb no more. Sorry.

---

### Post by fatboy07 on 2012-07-19
FATAL: Module rt5370sta not found.
 got this error. :(

---

### Post by fatboy07 on 2012-07-19
> drei@ubuntu:~$ sudo modprobe rt5370sta
[sudo] password for drei: 
FATAL: Module rt5370sta not found.
drei@ubuntu:~$ cdcd Desktop/RT5370
The program 'cdcd' is currently not installed.  You can install it by typing:
sudo apt-get install cdcd
drei@ubuntu:~$ cd Desktop/RT5370
bash: cd: Desktop/RT5370: No such file or directory
drei@ubuntu:~$ cd Desktop/RT5370
bash: cd: Desktop/RT5370: Not a directory
drei@ubuntu:~$ cd Desktop/zach
drei@ubuntu:~/Desktop/zach$ sudo du
28	./tools
532	./os/linux
536	./os
2100	./common
804	./sta
264	./chips
108	./include/os
168	./include/chip
12	./include/iface
1080	./include
4888	.
drei@ubuntu:~/Desktop/zach$ make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
rm -rf os/linux/Makefile
drei@ubuntu:~/Desktop/zach$ make
make -C tools
make[1]: Entering directory `/home/drei/Desktop/zach/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/drei/Desktop/zach/tools'
make: *** [build_tools] Error 2
drei@ubuntu:~/Desktop/zach$ make install
make -C /home/drei/Desktop/zach/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -rf /etc/Wireless/RT2870STA
rm: cannot remove `/etc/Wireless/RT2870STA/RT2870STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
make: *** [install] Error 2
drei@ubuntu:~/Desktop/zach$ sudo su
root@ubuntu:/home/drei/Desktop/zach# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
rm -rf os/linux/Makefile
root@ubuntu:/home/drei/Desktop/zach# make
make -C tools
make[1]: Entering directory `/home/drei/Desktop/zach/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/drei/Desktop/zach/tools'
make: *** [build_tools] Error 2
root@ubuntu:/home/drei/Desktop/zach# make install
make -C /home/drei/Desktop/zach/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/drei/Desktop/zach/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install: cannot stat `rt5370sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
make: *** [install] Error 2
root@ubuntu:/home/drei/Desktop/zach# modeprobe -r rt5370sta
No command 'modeprobe' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modeprobe: command not found
root@ubuntu:/home/drei/Desktop/zach# modeprobe rt5370sta
No command 'modeprobe' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modeprobe: command not found
root@ubuntu:/home/drei/Desktop/zach# 


got this error.. :(

---

### Post by chili555 on 2012-07-19
> make[1]: gcc: Command not foundPlease do:```
sudo apt-get install --reinstall build-essential
cd Desktop/zach
sudo su
make clean
make
make install
exit
```Any errors now?

When you see this:> [COLOR="Red"]make[1]: *** [install] Error 1[/COLOR]
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
make: *** [install] Error 2You should stop and sort out the error. All further steps will be errors, too.

---

### Post by fatboy07 on 2012-07-19
thanks chilli, feedback later. :)

---

### Post by fatboy07 on 2012-07-19
> cp /home/drei/Desktop/zach/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-26-generic
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/chips/map_rom.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/chips/cfi_util.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/maps/ts5500_flash.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-kensington.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-axff.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-keytouch.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/fcoe/fcoe.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/fcoe/libfcoe.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/mvsas/mvsas.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/video/vgastate.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/video/intelfb/intelfb.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/firewire/firewire-core.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/em28xx/em28xx-alsa.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/tm6000/tm6000.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/gspca/gspca_ov534.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_cif.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_sercos3.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_netx.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_pdrv_genirq.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/hardware/eicon/divas.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/gigaset/gigaset.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/mISDN/l1oip.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/mISDN/mISDN_dsp.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/mfd.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/mrst_max3110.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_accent.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/max3100.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_exar_st16c554.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_boca.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/altera_uart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/timbuart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_mca.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/pch_uart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_hub6.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_fourport.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/n_r3964.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/nozomi.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/atm/solos-pci.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/atm/horizon.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/option.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/usbserial.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/iuu_phoenix.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/visor.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/gadget/g_acm_ms.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/regulator/mc13892-regulator.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/regulator/max8925-regulator.ko: Exec format error
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
root@ubuntu:/home/drei/Desktop/zach# make
make -C tools
make[1]: Entering directory `/home/drei/Desktop/zach/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/drei/Desktop/zach/tools'
/home/drei/Desktop/zach/tools/bin2h
cp -f os/linux/Makefile.6 /home/drei/Desktop/zach/os/linux/Makefile
make -C /lib/modules/3.2.0-26-generic/build SUBDIRS=/home/drei/Desktop/zach/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
  CC [M]  /home/drei/Desktop/zach/os/linux/../../common/rtmp_mcu.o
/home/drei/Desktop/zach/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicLoadFirmware&#8217;:
/home/drei/Desktop/zach/os/linux/../../common/rtmp_mcu.c:383:11: warning: unused variable &#8216;MacReg1&#8217; [-Wunused-variable]
  LD [M]  /home/drei/Desktop/zach/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/drei/Desktop/zach/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
cp -f /home/drei/Desktop/zach/os/linux/rt5370sta.ko /tftpboot
root@ubuntu:/home/drei/Desktop/zach# make install
make -C /home/drei/Desktop/zach/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/drei/Desktop/zach/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-26-generic
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/chips/map_rom.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/chips/cfi_util.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/maps/ts5500_flash.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-kensington.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-axff.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-keytouch.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/fcoe/fcoe.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/fcoe/libfcoe.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/mvsas/mvsas.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/video/vgastate.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/video/intelfb/intelfb.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/firewire/firewire-core.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/em28xx/em28xx-alsa.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/tm6000/tm6000.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/gspca/gspca_ov534.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_cif.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_sercos3.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_netx.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_pdrv_genirq.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/hardware/eicon/divas.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/gigaset/gigaset.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/mISDN/l1oip.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/mISDN/mISDN_dsp.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/mfd.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/mrst_max3110.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_accent.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/max3100.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_exar_st16c554.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_boca.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/altera_uart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/timbuart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_mca.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/pch_uart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_hub6.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_fourport.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/n_r3964.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/nozomi.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/atm/solos-pci.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/atm/horizon.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/option.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/usbserial.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/iuu_phoenix.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/visor.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/gadget/g_acm_ms.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/regulator/mc13892-regulator.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/regulator/max8925-regulator.ko: Exec format error
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
root@ubuntu:/home/drei/Desktop/zach# 


this is what I got from make install.

---

### Post by chili555 on 2012-07-19
Man, oh man! This just gets weirder by the moment. Please do:```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall build-essential
```Then sudo su and make again. Those tickmarks are on the left side of my US keyboard on the same key with ~.

Fingers crossed...

---

### Post by fatboy07 on 2012-07-19
> root@ubuntu:/home/drei/Desktop/zach# make install
make -C /home/drei/Desktop/zach/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/drei/Desktop/zach/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-26-generic
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/chips/map_rom.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/chips/cfi_util.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/mtd/maps/ts5500_flash.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-kensington.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-axff.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/hid/hid-keytouch.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/fcoe/fcoe.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/fcoe/libfcoe.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/scsi/mvsas/mvsas.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/video/vgastate.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/video/intelfb/intelfb.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/firewire/firewire-core.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/em28xx/em28xx-alsa.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/tm6000/tm6000.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/gspca/gspca_ov534.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_cif.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_sercos3.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_netx.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/uio/uio_pdrv_genirq.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/hardware/eicon/divas.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/gigaset/gigaset.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/mISDN/l1oip.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/isdn/mISDN/mISDN_dsp.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/mfd.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/mrst_max3110.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_accent.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/max3100.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_exar_st16c554.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_boca.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/altera_uart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/timbuart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_mca.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/pch_uart.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_hub6.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/serial/8250_fourport.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/n_r3964.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/tty/nozomi.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/atm/solos-pci.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/atm/horizon.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/option.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/usbserial.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/iuu_phoenix.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/visor.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/usb/gadget/g_acm_ms.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/regulator/mc13892-regulator.ko: Exec format error
WARNING: Can't read module /lib/modules/3.2.0-26-generic/kernel/drivers/regulator/max8925-regulator.ko: Exec format error
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
root@ubuntu:/home/drei/Desktop/zach# 

Oh darn.. :( do I need to quit installing this one? :(

---

### Post by fatboy07 on 2012-07-19
tried the modeprobe com. line kaboom! wifi works perfectly! thanks chilli! 4 thumbs uP for you! cheers!!!!!!!

---

### Post by demonfire24 on 2012-07-21
Hello chili555,  cheers for the instruction on how to install.  The build went ok with no issues but i still have no access to wireless.  I did a sudo modprobe rt5370sta and got these results.

> mark@mark-Aspire-X3812 ~ $ lsmod | grep rt5
rt5370sta             805299  0 
mark@mark-Aspire-X3812 ~ $ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

mark@mark-Aspire-X3812 ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          
mark@mark-Aspire-X3812 ~ $ sudo iwlist ra0 scan
ra0       Interface doesn't support scanning : Network is down






Hope you can help.

Cheers

Mark

---

### Post by chili555 on 2012-07-21
> **demonfire24 said:**
> Hello chili555,  cheers for the instruction on how to install.  The build went ok with no issues but i still have no access to wireless.  
Hope you can help.

Cheers

MarkPlease post:```
lsb_release -d
lsmod | grep -e rt5 -e rt2
lsusb
```Thanks.

---

### Post by demonfire24 on 2012-07-21
Thanks for getting back to me.  I am being cheeky as i run Mint but i can't find any info on how to install anywhere but here.  Don't worry if you can help or if its non compatible.  Anyway my results are:

```
3812 ~ $ lsb_release -d
Description:	Linux Mint 12 Lisa
mark@mark-Aspire-X3812 ~ $ lsmod | grep -e rt5 -e rt2
rt5370sta             805299  1 
mark@mark-Aspire-X3812 ~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 004: ID 03f0:8811 Hewlett-Packard 
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 004 Device 002: ID 04f3:02f0 Elan Microelectronics Corp. 
Bus 007 Device 002: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder


```

---

### Post by chili555 on 2012-07-21
> i run Mint but i can't find any info on how to install anywhere but here.It's good to be the king. 

rt5370sta is correct for your device; however in later kernels, it is claimed by rt2800usb. Please post:```
modinfo rt2800usb | grep 5370
uname -r
dmesg | grep -i rt5
```Thanks.

---

### Post by demonfire24 on 2012-07-21
Thanks i entered your code and got:

```
mark@mark-Aspire-X3812 ~ $ modinfo rt2800usb | grep 5370
mark@mark-Aspire-X3812 ~ $ uname -r
3.0.0-16-generic
mark@mark-Aspire-X3812 ~ $ dmesg | grep -i rt5
mark@mark-Aspire-X3812 ~ $ 
```

---

### Post by chili555 on 2012-07-21
> mark@mark-Aspire-X3812 ~ $ dmesg | grep -i rt5
mark@mark-Aspire-X3812 ~ $Wow! We don't even see rt5370sta being loaded. Was it?```
lsmod | grep rt5
```If not, please do:```
sudo modprobe rt5370sta
dmesg | grep rt5
modinfo rt5370sta | head -n3
```Weird...

---

### Post by demonfire24 on 2012-07-21
Ok latest results, baffled myself.

```
mark@mark-Aspire-X3812 ~ $ lsmod | grep rt5
rt5370sta             805299  0 
mark@mark-Aspire-X3812 ~ $ sudo modprobe rt5370sta
[sudo] password for mark: 
mark@mark-Aspire-X3812 ~ $ dmesg | grep rt5
mark@mark-Aspire-X3812 ~ $ modinfo rt5370sta | head -n3
filename:       /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
mark@mark-Aspire-X3812 ~ $ 
```

---

### Post by demonfire24 on 2012-07-22
Well i just went over to Mint and my Wifi WAS working.  I logged in for a second time and it has gone back to the way it was .. wifi-unmanaged

Confused.. so close

---

### Post by demonfire24 on 2012-07-23
Ok an update,  i decided to do a fresh install of Mint 13 and try again.  Followed the step by step instructions to a t.. Still nothing :( in fact, worse than before.  I inputed some of the last instructions you gave and got these results..

```
mark@mark-Aspire-X3812 ~ $ sudo modprobe rt5370sta
[sudo] password for mark: 
mark@mark-Aspire-X3812 ~ $ lsb_release -d
Description:	Linux Mint 13 Maya
mark@mark-Aspire-X3812 ~ $ lsmod | grep -e rt5 -e rt2
rt5370sta             796868  0 
mark@mark-Aspire-X3812 ~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 004: ID 03f0:8811 Hewlett-Packard 
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 004 Device 002: ID 04f3:02f0 Elan Microelectronics Corp. 
Bus 008 Device 002: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder
mark@mark-Aspire-X3812 ~ $ modinfo rt2800usb | grep 5370
mark@mark-Aspire-X3812 ~ $ uname -r
3.2.0-23-generic
mark@mark-Aspire-X3812 ~ $ dmesg | -i rt5
-i: command not found
mark@mark-Aspire-X3812 ~ $ dmesg | -l rt5
-l: command not found
mark@mark-Aspire-X3812 ~ $ sudo modprobe rt5370sta
mark@mark-Aspire-X3812 ~ $ dmesg | grep rt5
mark@mark-Aspire-X3812 ~ $ modinfo rt5370sta | head -n3
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
mark@mark-Aspire-X3812 ~ $ 


```

Hope to hear from you soon :)

---

### Post by chili555 on 2012-07-24
Were there any warnings or errors when you compiled the driver? Can you please rebuild and let us see the outcome?```
cd Desktop/RT5370folder  [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
sudo su
make clean
make
make install
exit
```Copy and paste the terminal output to a text document in gedit, leafpad or whatever text editor Mint has. Save it as demon.txt. Locate it in your user directory, right-click it and select *Compress*, and select zip. Attach the resulting demon.txt.zip to your reply using the paperclip tool at the top of the reply box. 

> modinfo rt2800usb | grep 5370Comes up blank, eh? In Ubuntu, it is claimed in the Ubuntu-ized compat-wireless suite which is provided by linux-backports-modules-[COLOR="Red"]cw[/COLOR]-3.3-precise-generic. Do you have such a thing in Mint? We could also use a little udev trick to get rt2800usb to work, possibly.

---

### Post by demonfire24 on 2012-07-24
Ok, rebuilt and have the results in the attached zip file.  I wouldn't know if there was an error or not tbh but it looked ok to me.  I also don't have any knowledge of the modules i have.. i'm a bit of a noob so sorry about that.  Hope you can sort something

---

### Post by chili555 on 2012-07-24
There are a ton of warnings and then there are a ton more. This has more holes in it than swiss cheese. The easy way out is:> In Ubuntu, it is claimed in the Ubuntu-ized compat-wireless suite which is provided by linux-backports-modules-cw-3.3-precise-generic. Do you have such a thing in Mint?Please check and install it if you can find it. Then you'll need to uninstall the leaky rt5370sta:```
cd Desktop/RT5370folder  [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
sudo su
make uninstall
exit
```

---

### Post by demonfire24 on 2012-07-25
Ok i've uninstalled rt5370sta.  My Mint did not have linux-backports-modules-cw-3.3-precise-generic but i have now (after a lot of messing) managed to install it.  So what next :)

---

### Post by chili555 on 2012-07-25
Make sure that your device is driven by rt2800usb:```
modinfo rt2800usb | grep 5370
```Load it and see if there is an error or warning:```
sudo modprobe rt2800usb
```Did it create a wireless interface, ideally wlan0?```
iwconfig
```Does it see networks?```
sudo iwlist wlan0 scan
```Does it connect?

---

### Post by demonfire24 on 2012-07-25
Ok do i re install the driver first? noob i know

---

### Post by chili555 on 2012-07-25
> **demonfire24 said:**
> Ok do i re install the driver first? noob i knowNo. We are going to get the native driver rt2800usb to claim your device. Insert the device in the USB slot and do the steps just above.

---

### Post by demonfire24 on 2012-07-25
Wow i think you've cracked it straight away.. full working wireless.  I can't thank you enough :)  I will post the responses just in case there is errors within them.  What you think?

```
modinfo rt2800usb | grep 5370
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
mark@mark-Aspire-X3812 ~ $ sudo modprobe rt2800usb
[sudo] password for mark: 
mark@mark-Aspire-X3812 ~ $ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

mark@mark-Aspire-X3812 ~ $ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:D1:F8:1A
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Bertie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aafd16d69
                    Extra: Last beacon: 164ms ago
                    IE: Unknown: 0006426572746965
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340D070700000000000000000000000000000000000000
                    IE: Unknown: DDB70050F204104A0001101044000101103B00010310470010775B6680BFDE11D38D2F002275D1F81A1021001442656C6B696E20496E7465726E6174696F6E616C10230018456E68616E63656420576972656C65737320526F757465721024000C463644343233302D342076311042000E32303933383432333030343332321054000800060050F20400011011001F42656C6B696E20456E68616E63656420576972656C65737320526F75746572100800020084103C000101
          Cell 02 - Address: CC:B2:55:6A:E2:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-146"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000012668c161
                    Extra: Last beacon: 1084ms ago
                    IE: Unknown: 000C54414C4B54414C4B2D313436
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010004127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B0001031047001049A081A8F81B2D55D55BCCB2556AE2E010210006442D4C696E6B1023000844534C2D323738301024000844534C2D323738301042000830303030303030301054000800060050F20400011011000844534C2D32373830100800020086

```

---

### Post by chili555 on 2012-07-25
Looks awesome to me! If it can scan it can usually connect. If 'Bertie' is your network, you'd probably find it easier to connect with WPA2 only and not mixed mode WPA and WPA2 as it is now:> Cell 01 - Address: 00:22:75:D1:F8:1A
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Bertie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aafd16d69
                    Extra: Last beacon: 164ms ago
                    <snip>
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="Red"]IEEE 802.11i/WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKCan you click the Network Manager icon and connect?

---

### Post by demonfire24 on 2012-07-25
There doesn't seem to be an option for WPA2 only?  Just mixed or WEP alone.  Yes can access network and connect successfully.  So if and when i upgrade again do i just do the final steps you went through earlier and not worry about the driver install?

---

### Post by chili555 on 2012-07-25
>  So if and when i upgrade again do i just do the final steps you went through earlier and not worry about the driver install?When you update, presumably the kernel, the upgrade should also upgrade the corresponding linux-backports-modules-cw package. That's all you need.> Yes can access network and connect successfully.Awesome! Glad it's working.

---

### Post by demonfire24 on 2012-07-26
Many thanks for the help.  One thing i will say is the speed seems to be quite slow, is there a way to calibrate that?

---

### Post by chili555 on 2012-07-26
> the speed seems to be quite slow, How so? Please let us see:```
iwconfig
ping -c3 www.google.com
```What are your speedtest.net test results compared to other computers on the same network?

---

### Post by demonfire24 on 2012-07-26
Hmmmm, results seem ok in comparison to windows.  Just seems a lot slower, especially streaming.  Results

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Bertie"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:22:75:D1:F8:1A   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:40   Missed beacon:0

eth0      no wireless extensions.

mark@mark-Aspire-X3812 ~ $ ping -c3 www.google.com
PING www.l.google.com (74.125.132.99) 56(84) bytes of data.
64 bytes from wb-in-f99.1e100.net (74.125.132.99): icmp_req=1 ttl=46 time=31.8 ms
64 bytes from wb-in-f99.1e100.net (74.125.132.99): icmp_req=2 ttl=48 time=41.2 ms
64 bytes from wb-in-f99.1e100.net (74.125.132.99): icmp_req=3 ttl=48 time=41.1 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 31.849/38.085/41.242/4.409 ms
mark@mark-Aspire-X3812 ~ $ 

```

Speedtest.net    ping 29ms  Download 10.12  Upload 0.96

---

### Post by chili555 on 2012-07-26
Looks awesome to me. I see nothing wrong except:> wlan0     IEEE 802.11bgn  ESSID:"Bertie"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:22:75:D1:F8:1A   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          [COLOR="Red"]Link Quality=**29**/70[/COLOR]  Signal level=-81 dBm  Are you close to the router?

---

### Post by demonfire24 on 2012-07-27
Well its about 10 meters away so not sure why its only around 20-30%  It does keep disconnecting too.  I think the streaming could be graphic drivers and such but i've no idea how to set it up properly.

---

### Post by MaccyDG on 2012-08-11
Thank you, Chili - I have read so many posts on how to get this card to work, and even tried ndiswrapper as a last resort.  It turned out to be the second-to-last resort, because your way worked perfectly!

NB to others: the first time I tried this method, I had an ethernet cable plugged into the laptop and the wireless card was not plugged in.  I got no installation errors, but the card didn't work.  I unplugged the ethernet cable and plugged the wireless card in, and tried installing again, and this time it worked.

---

### Post by mcaureliojr on 2012-08-29
> **chili555 said:**
> People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.

I got this error after in the end:
ralink# modprobe rt5370sta
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-42-generic-pae/kernel/drivers/net/wireless/rt5370sta.ko): Device or resource busy
root@serpro-1528852:/home/xxx/Desktop/ralink#

What im doing wrong?

---

### Post by chili555 on 2012-08-29
> WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.Let's see what's in there and fix it up:```
cat /etc/modprobe.conf
```> FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-42-generic-pae/kernel/drivers/net/wireless/rt5370sta.ko): Device or resource busyIt usually means some other driver is already loaded. Let's check:```
lsmod | grep -e rt2 -e rt5
```

---

### Post by mcaureliojr on 2012-08-29
> **chili555 said:**
> Let's see what's in there and fix it up:```
cat /etc/modprobe.conf
```It usually means some other driver is already loaded. Let's check:```
lsmod | grep -e rt2 -e rt5
```

Great, just ON but what should I do now to make the device start?

# cat /etc/modprobe.conf
options parport_pc io=0x378 irq=7 dma=3
# lsmod | grep -e rt2 -e rt5
rt2870sta             461971  0

# lsusb
Bus 002 Device 004: ID 148f:5370 Ralink Technology, Corp.

---

### Post by chili555 on 2012-08-29
> # cat /etc/modprobe.conf
options parport_pc io=0x378 irq=7 dma=3Let's just move it to the right spot:```
sudo mv /etc/modprobe.conf /etc/modprobe.d/parport_pc.conf
```> # lsmod | grep -e rt2 -e rt5
rt2870sta 461971 0
It looks like rt2870sta is loaded already. I doubt it covers your 5370 device. Any idea how or why it got loaded? It's OK, you can tell Dr. Chili!

---

### Post by mcaureliojr on 2012-08-29
> **chili555 said:**
> Let's see what's in there and fix it up:```
cat /etc/modprobe.conf
```It usually means some other driver is already loaded. Let's check:```
lsmod | grep -e rt2 -e rt5
```

I made that las command and got this:
rt2870sta             461971  0

But how to do to start device and make it work?

---

### Post by chili555 on 2012-08-29
> **mcaureliojr said:**
> I made that las command and got this:
rt2870sta             461971  0

But how to do to start device and make it work?Please:>  Any idea how or why it got loaded?What have you tried previously involving rt2870sta. I highly doubt it just loaded itself. We need to figure that out and fix it first.

---

### Post by mcaureliojr on 2012-08-29
> **chili555 said:**
> Please:What have you tried previously involving rt2870sta. I highly doubt it just loaded itself. We need to figure that out and fix it first.

I have no idea, I just follow the command in the beginning of this post

---

### Post by chili555 on 2012-08-29
> **mcaureliojr said:**
> I have no idea, I just follow the command in the beginning of this postPlease let me see:```
history | grep rt28
cat /etc/modules
modinfo rt2870sta | grep 5370
```Thanks.

---

### Post by mcaureliojr on 2012-08-29
> **chili555 said:**
> Please let me see:```
history | grep rt28
cat /etc/modules
modinfo rt2870sta | grep 5370
```Thanks.

# history | grep rt28
  364   | 29/08/12 - 16:28:48 | modprobe rt2870sta
  368   | 29/08/12 - 16:28:48 | modprobe rt2870sta
  377   | 27/10/11 - 15:11:24 | /sbin/insmod rt2870sta.o
  378   | 27/10/11 - 15:12:41 | $/sbin/insmod rt2870sta.ko
  390   | 27/10/11 - 15:16:26 | ./insmod rt2870sta.ko
  396   | 27/10/11 - 15:26:10 | chmod 777 rt2860.bin 
  398   | 27/10/11 - 15:26:15 | ./rt2860.bin 
  399   | 27/10/11 - 15:26:25 | mv rt2860.bin /bin
  401   | 27/10/11 - 15:26:36 | ./rt2860.bin 
  424   | 29/08/12 - 16:28:48 | modprobe rt2870sta
 1049   | 29/08/12 - 16:29:24 | modprobe rt2870sta
 1050   | 29/08/12 - 16:29:42 | modprobe -r rt2870sta
 1054   | 29/08/12 - 16:30:43 | modprobe rt2870sta
 1055   | 29/08/12 - 16:31:10 | history | grep rt28
---------------------------------------------------------------
# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

RT2870STA
rt2870sta
loop
lp

rt5370sta
---------------------------------------------------------------
# modinfo rt2870sta | grep 2870
filename:       /lib/modules/2.6.32-42-generic-pae/kernel/drivers/staging/rt2870/rt2870sta.ko
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*

---

### Post by chili555 on 2012-08-29
> I have no idea,Ummm hmmm, I see. Please do:```
sudo gedit /etc/modules
```Remove the two lines I've highlighted.> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

[COLOR="Red"]RT2870STA
rt2870sta[/COLOR]
loop
lp
Proofread carefully, save and close gedit. Reboot. Now do:```
sudo modprobe rt5370sta
```Any improvement?

---

### Post by mcaureliojr on 2012-08-29
> **chili555 said:**
> Let's see what's in there and fix it up:```
cat /etc/modprobe.conf
```It usually means some other driver is already loaded. Let's check:```
lsmod | grep -e rt2 -e rt5
```

# modprobe rt5370sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-42-generic-pae/kernel/drivers/net/wireless/rt5370sta.ko): Device or resource busy
# lsmod | grep -e rt2 -e rt5
rt2870sta             461971  0

---

### Post by chili555 on 2012-08-30
Wow.

Did you try ndiswrapper for this device or some other? If for this device, you don't need it and we can remove it:```
sudo rm /etc/modprobe.d/ndiswrapper
```Let's see:```
modinfo rt2870sta | grep -e 5370 -e version
iwconfig
lsmod | grep ndis
```Thanks.

---

### Post by mcaureliojr on 2012-08-30
> **chili555 said:**
> Wow.

Did you try ndiswrapper for this device or some other? If for this device, you don't need it and we can remove it:```
sudo rm /etc/modprobe.d/ndiswrapper
```Let's see:```
modinfo rt2870sta | grep -e 5370 -e version
iwconfig
lsmod | grep ndis
```Thanks.

Got this:
# rm /etc/modprobe.d/ndiswrapper
--------------------------------
# modinfo rt2870sta | grep -e 5370 -e version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-42-generic-pae SMP mod_unload modversions 586TSC 
--------------------------------
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
--------------------------------
# lsmod | grep ndis
ndiswrapper           184867  0 
#

---

### Post by chili555 on 2012-08-30
Did you try ndiswrapper for this device or some other? I asked for a reason. I don't want to remove something you need for some other purpose.

---

### Post by Helladog on 2012-10-28
Thanks to the contributors of this thread for your help.  I got my device to work after a bit of work using the newer code and original instructions.

---

### Post by naelphin on 2012-10-28
> **chili555 said:**
> People are running Unity, Guh-nome. kubuntu, lxde and idontknowwhatabuntu. I sometimes accidentally get it right!

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

RANT: The automagic tools that extract files in Ubuntu work great until they don't and ole Chili has to tapdance. It is far easier than it once was and less easy than I hope it will someday be. END RANT.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If there are any errors, stop and ask; warnings are usually OK.
the manufacturer changed the filename and forgot to put in the .tar before the .bz2. I had trouble until I renamed the file, now it works perfectly.

[http://www.ralinktech.com/en/04_support/license.php?sn=5016](http://www.ralinktech.com/en/04_support/license.php?sn=5016)

(and yes you need to make as root or it fails!)

---

### Post by japollock on 2013-07-19
> **chili555 said:**
> Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:```
cd Desktop/2011
```Press Tab and the remainder will fill in. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working?

If I could upvote these instructions on the Internet, I would.  I've spent the last week searching and making various attempts to get my Ralink 5730 usb wireless adapter to work with Ubuntu.  I'm not that savvy apparently because nothing worked.  Tried these instructions with no tweaking required, and network manager just discovers my new wireless device.  Awesome.  Thank you Chili.

---

### Post by wayne4 on 2013-09-29
> **chili555 said:**
> The 'license taints kernel' is trivial (and fixable) but wouldn't stop the driver from working. The unknown symbol errors are what we need to fix, however. Can you run:```
sudo su
make clean
make
```Then copy all the text from the terminal and paste into a text document and copy that to a USB key or similar so we can see and, hopefully, fix them?

Hello all,

I have been dealing with Tubadaddy's same issue, and got to this point before everything got really frustrating. 

Here is a link to my terminal's display after running 
sudo su
make clean 
make

:arrow: [ATTACH]246585[/ATTACH]

I also read into adding in the module_license("GPL") line, but got hung up on adding in the symlink. This is my fifth day of working in Linux trying to get this adapter to work, sooooo... newbish? Yes, absolutely... but not a quitter.

any help or general direction is appreciated :)

---

### Post by chili555 on 2013-09-29
> **wayne4 said:**
>  This is my fifth day of working in Linux trying to get this adapter to work, sooooo... newbish? Yes, absolutely... but not a quitter.

any help or general direction is appreciated :)Actually, your build went without error, however, there are so many warnings that I'm quite sure the driver won't work well if at all!

You have certainly made a tough job for yourself:```
Entering directory `/usr/src/linux-headers-[COLOR="#FF0000"]2.6.31-14[/COLOR]-generic'
```That suggests that you installed Ubuntu 10.04 or maybe even earlier and it may not even be fully updated. That's like buying a Pentium II and 256Mb of RAM. Can you run it? Barely. Could you, with a bit more effort, have a smoothly running system and few or no troubles? Oh, yes!

I strongly suggest you install Ubuntu 12.04.3 LTS at least and even Ubuntu 13.04 where your device works out of the box!

---

### Post by wayne4 on 2013-09-29
> **chili555 said:**
> That suggests that you installed Ubuntu 10.04 or maybe even earlier and it may not even be fully updated. That's like buying a Pentium II and 256Mb of RAM. Can you run it? Barely. Could you, with a bit more effort, have a smoothly running system and few or no troubles? Oh, yes!

I strongly suggest you install Ubuntu 12.04.3 LTS at least and even Ubuntu 13.04 where your device works out of the box!

Actually, now that I'm checking it out, I'm running Karmic Koala, which I'm realizing is pretty ancient. Where can I go to download the new version?

---

### Post by chili555 on 2013-09-29
For 13.04, right here: [http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)

---

### Post by wayne4 on 2013-10-07
Just installed 13.04 and everything connected without any troubles at all! Thank you! :)

---

### Post by adkarfa on 2013-10-28
I really need help to install it, Actually I am using LeoxSys Usb Wifi Device, I get Driver CD. 

I install that on Windows OS it is working fine, where I see the using "RT2870 Wireless LAN Card" on Windows 

How to Install that same for Ubuntu 12.04?

Thank You

---

### Post by chili555 on 2013-10-28
> **adkarfa said:**
> I really need help to install it, Actually I am using LeoxSys Usb Wifi Device, I get Driver CD. 

I install that on Windows OS it is working fine, where I see the using "RT2870 Wireless LAN Card" on Windows 

How to Install that same for Ubuntu 12.04?

Thank YouPlease start your own new thread and include:```
lsusb
```I suspect you do not have an RT5370 device but something else.

---

### Post by tom14 on 2013-11-10
Hello Chilli,it's me again,Tom.I finally received my RT5370 usb wifi dongle after waiting a long time.I was trying hard to make it work,and not to bother you with this,but no success.I think that driver could be installed ok,but I don't know how to enable it.I have "build-essential" and "linux-headers-generic" installed,and have also changed "n" to "y" where needed in code.Here is lsmod.Please help me.
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48923  3 rt2800usb,rt2800lib,rt2x00usb
arc4                   12473  2 
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath5k                 145127  0 
radeon                733899  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
ath                    19387  1 ath5k
rtl8187                56323  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac80211              436493  5 rt2800lib,rt2x00usb,rt2x00lib,ath5k,rtl8187
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96744  0 
cfg80211              178877  5 rt2x00lib,ath5k,ath,rtl8187,mac80211
drm                   197641  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
smsc_ircc2             28358  0 
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
eeprom_93cx6           12687  1 rtl8187
yenta_socket           27428  0 
irda                  185517  1 smsc_ircc2
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
video                  19115  0 
crc_ccitt              12627  2 rt2800lib,irda
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
wmi                    18744  0 
mac_hid                13077  0 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
tg3                   141465  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by chili555 on 2013-11-10
Wow, Tom! I don't even know where to start looking for your particulars in a 13 page thread. Please start your own new thread and include:```
lsb_release -d
lsusb

```Send me a private message with the link if I don't catch it right away and I'll be glad to help.

---

### Post by jaffaizal on 2014-10-12
Chili555,


Thank you. The WiFi USB card now works.


Went here to download the driver: [http://www.mediatek.com/en/downloads/rt8070-rt3070-rt3370-rt3572-rt5370-rt5372-rt5572-usb-usb/](http://www.mediatek.com/en/downloads/rt8070-rt3070-rt3370-rt3572-rt5370-rt5372-rt5572-usb-usb/)


then,
make
make install
modprobe rt5370sta


only the last command give me an error message. But I ignored this. Saw that the USB Card now lighted up.
Changes done with 'Network Manager' does not work.

In fact i read somewhere else that to install wicd.


sudo apt-get install wicd


open wicd network manager
click on the 'properties' of the wifi network you want to connect
key in the correct IP, NETMASK, GATEWAY, DNS server and the Encryption method


It is now working.


Thank you very much.


Keep up the good work.


Jaf

---

### Post by Nico_Janow on 2015-01-12
I followed the instructions here, using driver 2.6.1.3, but get the following make error:

               ^
/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.c:1141:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.c:1142:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/nico/newrt5370/nrt5370/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-39-generic'
make: *** [LINUX] Error 2

I tried makefile, but got:

install: cannot stat ‘rt5572sta.ko’: No such file or directory





I'm running 14.04 64 bit.  Perhaps it's a problem with the changes with this version?

---

### Post by mörgæs on 2015-01-12
The majority of the thread is some years old, and much can happen in the Buntu world during that time. The advice here is not necessarily valid for 14.04 and 14.10.

Closing the thread but you are welcome to open a new one. If you do then please read the sticky notes first and post the relevant output.

---

