---
title: "[SOLVED] MythTV on Feisty with PVR-150, LIRC required for remote?"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by md2020 on 2007-06-29
I have been following the excellent documentation for installing MythTV on Feisty.
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)

Myth is up and working, can watch live TV. Have not attempted to record yet. But I am trying to get the remote for my Hauppauge PVR-150 (not MCE/USB) working. The hardware doc indicates that the PVR-150 is "supported out of the box" for Feisty. Does that include the remote?

Was following the doc here for LIRC, without success.
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)
But after reading other posts I have ideas on how the instructions may need to be tweaked to get it to work.

In the LIRC doc, it indicates that "Some i2c remotes are supported directly by the kernel." And that "For remotes like this, the kernel is deprecating the use (and requirement) of lirc."

Is the remote for the PVR-150 one of those remotes? I searched in vain for the answer. Do I need to install LIRC to get my remote to work? (IR-receive only) Is LIRC required only if you need to use the IR-blaster? Is LIRC required for either/both?

If the remote is supported directly by the kernel with I2C, how do I get it to work?

Any guidance would be greatly appreciated!!


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Edit on 08/18/2007, solution found:

For those who will happen upon this thread at some later point and do not want to read the entire saga, here is what I learned and how I solved my problem of not getting my Hauppauge PVR-150 to work with LIRC:

The LIRC install instructions for Feisty seem to indicate that you can specify both the "lirc_i2c" and "lirc_pvr150" modules in /etc/lirc/hardware.conf. I am pretty sure that you can only specify one or the other in /etc/lirc/hardware.conf. Anytime I specified both, I got an error. If you need to control another set top box with your remote, use lirc_pvr150, otherwise you can probably use lirc_i2c. I am using lirc_i2c since I do not need to control a STB and am using the tuner on the PVR-150 to change channels.

I also had a defective PVR-150:  My issue was definitely the PVR-150 card. I did not change any of the settings when going from the old one, which did not work, to the new one which does work. I decided to try a new PVR-150 when I put my old PVR-150 in a different PC with completely different hardware. It still did not work under Ubuntu there either. The other really interesting thing is that the remote for the old PVR-150 would work under WinXP on either machine. It simply would not work under Ubuntu on either PC. So to put my mind at ease that I did not have a faulty card, I got a new one. Thankfully I did.

---

### Post by tgm4883 on 2007-06-29
You need to install LIRC to get that remote to work.  The guide you were following is an excellent guide.  Where were you having trouble?

---

### Post by md2020 on 2007-06-29
Thanks for the reply. Everything seemed just fine until time to test the remote with:
```
$ sudo /etc/init.d/lirc start
irw
```
That would return to the prompt right away. Checking this:
```
ls /dev/lirc*
```
would only return  /dev/lircd.

So it appears that the process was not finding/setting something correctly to get /dev/lirc0 established.

In the /etc/lirc/hardware.conf I had these settings:
LIRCD_ARGS="--device=/dev/lirc0"
MODULES="lirc_i2c lirc_pvr150"

For the /etc/lirc/lircd.conf, I used the lircd.conf.hauppauge found on the LIRC install guide. That config file has several remotes in it. Do I leave them all in or just pull out the one I want to use?

---

### Post by tgm4883 on 2007-06-29
Did you read about 2 lines below that 

> If irw returns immediately, and gives you another command prompt some of your modules aren't loading correctly. Try rebooting your computer. If this doesn't work check dmesg for clues as to which module isn't loading.

---

### Post by md2020 on 2007-06-29
Yes, I did read that and try it. No go. I see something like what is posted in this thread:
[http://ubuntuforums.org/showthread.php?t=422309](http://ubuntuforums.org/showthread.php?t=422309)

"no version for "lirc_unregister_plugin" found: kernel tainted."

I am at work now and do not have access to that PC, but from what I read in the above thread, I have some ideas to try. Will post again if still stuck. Thanks for your assistance!

---

### Post by md2020 on 2007-06-30
Had more time to play with this. Here is where I am at. Using Myth Frontend/Backend/Desktop on Feisty. Logged on as the main user, not mythtv or root.

After startup if I grep for lirc processes I see this:
[INDENT]root      7916     1  0 11:37 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0[/INDENT]
Attempting to run "irw" or MythTV will shut that process down.

Here is what I see from "dmesg":
[INDENT][   51.300000] lirc_dev: IR Remote Control driver registered, at major 61 
[   51.316000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.[/INDENT]

Looking in /var/log/syslog I see this:
[INDENT]Jun 30 11:37:48 mdpvr lircd-0.8.2-CVS[7916]: lircd(userspace) ready
Jun 30 11:42:22 mdpvr lircd-0.8.2-CVS[7916]: accepted new client on /dev/lircd
Jun 30 11:42:22 mdpvr lircd-0.8.2-CVS[7916]: could not get file information for /dev/lirc0
Jun 30 11:42:22 mdpvr lircd-0.8.2-CVS[7916]: default_init(): No such file or directory 
Jun 30 11:42:22 mdpvr lircd-0.8.2-CVS[7916]: caught signal
[/INDENT]

And at anytime I do a:  ls /dev/lirc*
All I have ever seen is:   /dev/lircd
I have never seen  /dev/lirc  nor /dev/lirc0 nor /dev/lirc/0. Should I get one of those to appear, I have read enough threads by now that I think I can handle the rest no problem.

I have followed the Feisty LIRC install instructions to no avail.  This thread seems to be the exact problem I am having, but I do not see a resolution in there. [http://ubuntuforums.org/showthread.php?t=422309](http://ubuntuforums.org/showthread.php?t=422309)

Any additional help would be greatly appreciated. Should I figure this out, I will post the resolution.

---

### Post by DyDx on 2007-07-02
I have this exact problem.  I too will return if I find a solution.

---

### Post by tgm4883 on 2007-07-03
Did you receive any errors while following the guide?  You selected the correct modules for your receiver?

>  PVR-150 on-card blaster/receiver: you will want to build the i2c and pvr150 modules

PVR-150 USB blaster/receiver: you will want to build either the mceusb or mceusb2 module 

^ Which one do you have?

Did you 

> You may be given an option to replace with a new version. Be sure to choose to Install the package maintainer's version.
Even though the picture says to "Keep your currently installed version"

:EDIT:

Also, did you add the correct info to /etc/lirc/hardware.conf

Double check this as it is easy to put things in the wrong place (did it myself)

---

### Post by md2020 on 2007-07-03
Again, many thanks for the assistance. I have the PVR-150 on-card (PCI) blaster/receiver. 

> PVR-150 on-card blaster/receiver: you will want to build the i2c and pvr150 modules
PVR-150 USB blaster/receiver: you will want to build either the mceusb or mceusb2 module

I have tried it both ways with the modules. First I built both the i2c and pvr150 modules. That did not work, so I went back and reconfigured with just the i2c. I do not need the blaster, so I took it out.

> You may be given an option to replace with a new version. Be sure to choose to Install the package maintainer's version.
I caught that in the guide and chose "package maintainer's version".

I think I have everything correct in hardware.conf. Here is my /etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS="--device=/dev/lirc0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

Addtionally here is what I see when I grep lsmod for lirc
```
$ lsmod|grep lirc
lirc_i2c               11268  0 
lirc_dev               15988  1 lirc_i2c
i2c_core               22656  14 cx88xx,bttv,lirc_i2c,i2c_ec,i2c_viapro,wm8775,cx25840,tuner,nvidia,via686a,ivtv,i2c_algo_bit,tveeprom,i2c_isa

```
So it looks like it is loading the i2c module to me.

Here is my ivtv section from dmesg
```
[   25.928000] ivtv:  ==================== START INIT IVTV ====================
[   25.928000] ivtv:  version 0.10.1 (tagged release) loading
[   25.928000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   25.928000] ivtv:  In case of problems please include the debug info between
[   25.928000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   25.928000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   25.928000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   25.928000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   25.928000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   26.880000] input: PC Speaker as /class/input/input2
[   26.956000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   27.428000] nvidia: module license 'NVIDIA' taints kernel.
[   28.440000] usbcore: registered new interface driver cdc_ether
[   28.544000] usb 5-3: bad CDC descriptors
[   28.544000] usbcore: registered new interface driver rndis_host
[   28.968000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   29.184000] ivtv0: Encoder revision: 0x02050032
[   29.184000] ivtv0: Recommended firmware version is 0x02060039.
[   29.264000] tveeprom 0-0050: Hauppauge model 26152, rev E5B2, serial# 10295246
[   29.264000] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   29.264000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   29.264000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   29.264000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   29.264000] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   29.264000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   29.264000] ivtv0: reopen i2c bus for IR-blaster support
[   29.396000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.700000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   34.224000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   34.324000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   34.364000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   34.368000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   34.368000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   34.368000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   34.368000] tuner 0-0061: type set to 50 (TCL 2002N)
[   34.684000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   34.684000] ivtv:  ====================  END INIT IVTV  ====================

```

Any other ideas?

---

### Post by tgm4883 on 2007-07-03
When doing this if you receive any errors, stop and let us know.

Do the i2c and PVR 150 modules, package maintainers version

MODULES="lirc_i2c lirc_pvr150"

I'm assuming that you have already tried it this way, but this is how it's should be.  So getting it here is going in the right direction.

Then make sure you do all this again.

> Build Lirc Modules

The lirc modules will need to be rebuilt every time that you update your kernel. Just follow these build steps every time you boot into a newer kernel for the first time.

    *

      This step will grab the necessary headers to build the kernel modules:
          o

            $ sudo m-a update,prepare

    *

      This will clean out any old lirc module builds:
          o

            $ sudo rm /usr/src/lirc*deb
            $ sudo m-a clean lirc

    *

      This will build the kernel/install modules:
          o

            $ sudo m-a a-i lirc

    *

      Update the modules list
          o

            $ sudo depmod -a



Then grab the lircd.conf.hauppauge file for your remote and make sure to rename it to lircd.conf, then 

sudo cp <name of downloaded.conf> /etc/lirc

Once done with that we do this and hope for the best

> $ sudo /etc/init.d/lirc start
$ irw

---

### Post by md2020 on 2007-07-03
I was not given the "package maintainers version" screen this time when executing:
```
sudo dpkg-reconfigure lirc-modules-source
```
But I have both i2c and pvr150 selected. I also have both in "modules" section of hardware.conf.

I already had downloaded lirc.hauppage.conf and replaced /etc/lirc/lircd.conf with its complete contents. So all good there. (I hope.)

Received no errors that I saw during build. However, lirc_i2c exists here /lib/modules/2.6.20-16-generic/misc/lirc_i2c.ko
and here /sys/module/lirc_i2c.

But lirc_pvr150 does not exist in either of those places. The last time I had redid things, I didn't get the "package maintainers version" screen until I removed all the LIRC packages. After doing that, it did appear. Could this be why it didn't seem to buidl lirc_pvr150? I assume that I do need the lirc_pvr150.ko to be showing up.

It can't find lirc_pvr150, getting this when atempting to start lirc now:
```
$ sudo /etc/init.d/lirc start
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

```

---

### Post by steven_ellis on 2007-07-03
Ok can you take a look to see if the lirc_pvr150 module has been compiled and installed. Usually the following will work.

```
locate lirc_pvr150.ko
```

If it isn't installed you need to look at your build issues, and make sure it gets installed correctly.

Then I'd run
```
depmod -a
modprobe lirc_pvr150
```
and have a look at the kernel error messages to see if anything goes wrong.

If all is sweet then restart lircd and run irw.

---

### Post by md2020 on 2007-07-04
Thanks. I tried looking for it earlier as I confirmed existence of lirc_i2c. Used your:
```
locate lirc_pvr150.ko
```
And it didn't return anything either. (even ran with sudo just in case.) 

There is probably a setting somewhere to allow it to compile/build, heaven knows where.  I know for sure that when I previously did the apt-get remove on the installed pieces, it will allow that to happen and gave me the "package maintainer's version" screen again.

The last time I removed I used:
```
sudo apt-get autoremove lirc lirc-modules-source
```
I think there was one other piece I removed with the package manager as well since just doing the above did not allow me back into the "package maintainer's version" screen.

Assuming I need to remove and reinstall LIRC, any suggestions? Or is there something else I need to do?

Love the help....

---

### Post by bto on 2007-07-04
I've been working the last few hours on what seems an identical issue...

Ubuntu 7.0.4, latest Myth, PVR-150.

I reviewed the last message and saw executed the uninstallation via 
"apt-get autoremove lirc lirc-modules-source"

Afterwards, I followed the same instructions very carefully again at: 
[https://help.ubuntu.com/community/Install_Lirc_Feisty#head-661b91158a667cd25342be5b8b85c16ecc8491b3](https://help.ubuntu.com/community/Install_Lirc_Feisty#head-661b91158a667cd25342be5b8b85c16ecc8491b3)

I did set it to lirc_i2c only since I didn't need the blaster.

hardware.conf:
LIRCD_ARGS="--device=/dev/lirc0"
DEVICE=""
MODULES="lirc_i2c"

I run:
/etc/init.d/lirc start
ps -A | grep lirc

No process.

the syslog shows:
Jul  4 18:23:59 myth lircd-0.8.2-CVS[19219]: could not get file information for /dev/lirc0
Jul  4 18:23:59 myth lircd-0.8.2-CVS[19219]: default_init(): No such file or directory

And the /dev/ directory:

root@myth:/etc/lirc# ls -al /dev/lir*
crw-r--r-- 1 root root 61, 0 2007-07-04 17:20 /dev/lirc
srw-rw-rw- 1 root root     0 2007-07-04 18:23 /dev/lircd
prw-r--r-- 1 root root     0 2007-07-04 17:20 /dev/lircm


When I run:
root@myth:/etc/lirc# cat /proc/bus/input/devices

I don't see any references to IR devices.

I'm stumped...  Hours invested this afternoon and at least I know I'm not alone!

Anyone else figured this out yet???

Thanks for the help!

Bryce

---

### Post by md2020 on 2007-07-04
bto,
Too funny. Here I am helping out someone else in my own thread. At least you got the /dev/lirc, I have never seen that yet.
> I'm stumped... Hours invested this afternoon and at least I know I'm not alone!

Anyone else figured this out yet???

Thanks for the help!

To fix yours, from what I recall reading, you have several choices. First, if I was you I would shut off your PC (power down), turn it back on and make sure you get /dev/lirc again. (i.e. verify that you are not seeing /dev/lirc0)

Should you have /dev/lirc and not /dev/lirc0 you can change your entry here:
hardware.conf:
LIRCD_ARGS="--device=/dev/lirc0"

To this:
hardware.conf:
LIRCD_ARGS="--device=/dev/lirc"

And it should work. Your second alternative (if you want to leave the device in hardware.conf as /dev/lirc0) is to create a symbolic link for /dev/lirc0. However, you would have to do that at after each boot. So you would probably want to add it to a startup script. You can check out this thread if you are interested in doing that. [http://ubuntuforums.org/showthread.php?t=123249](http://ubuntuforums.org/showthread.php?t=123249)
Personally, I would just change the the entry in hardware.conf. And if it stops working, you know one thing to check.

---

### Post by md2020 on 2007-07-04
Well I have at least figured out how to get it to compile/build lirc_pvr150.ko. After I had added that option back in using:
```
sudo dpkg-reconfigure lirc-modules-source
```
The key was in using the "Rebuild Modules" section of the Feisty LIRC instructions. The key ingredient I did not do the previous attempts was the first line:
```
sudo dpkg -r lirc-modules-`uname -r`
```
Either that, or the order of the steps made some kind of difference. 

Anyway, I now have both a lirc_i2c.ko and a lirc_pvr150.ko. I modprobe'd both of them and restarted LIRC with:
```
sudo /etc/init.d/lirc restart
```
I see both of them when I do a:  lsmod | grep lirc
However, I still only have /dev/lircd.  No other lirc entities in /dev.

When I do irw it still shuts down lirc. And I still see the usual in /var/log/syslog:
```
Jul  4 20:56:43 mdpvr lircd-0.8.2-CVS[21079]: lircd(userspace) ready
Jul  4 20:57:30 mdpvr lircd-0.8.2-CVS[21079]: caught signal
Jul  4 21:25:36 mdpvr kernel: [36076.312000]  [<f16db0b8>] init_module+0x48/0x50 [lirc_pvr150]
Jul  4 21:25:46 mdpvr lircd-0.8.2-CVS[26803]: lircd(userspace) ready
Jul  4 21:36:32 mdpvr lircd-0.8.2-CVS[26803]: accepted new client on /dev/lircd
Jul  4 21:36:32 mdpvr lircd-0.8.2-CVS[26803]: could not get file information for /dev/lirc0
Jul  4 21:36:32 mdpvr lircd-0.8.2-CVS[26803]: default_init(): No such file or directory 
Jul  4 21:36:32 mdpvr lircd-0.8.2-CVS[26803]: caught signal

```

I will try powering off and rebooting to see if by magic any variant of /dev/lirc would appear. If it does, I will post again shortly. Otherwise, assume I am still in need of assistance.

---

### Post by williakj on 2007-07-04
I have a Hauppauge PVR-150 [PCI not MCE/USB, Model 1045, 44 button Remove w/ Silver front and Black backing). I have followed the [Install Lirc Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty?action=fullsearch&value=linkto%3A%22Install+Lirc+Feisty%22&context=180") instructions to a 'T'.

MythTV works fine, but I'm having the exact same issues as you guys with my lirc. So I feel everyone's collective pain in this thread.

I run

```
sudo /etc/init.d/lirc start
```

ps ax shows the process running:

```
ps ax
6784 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0
```

Then I run

```
irw
```

...which kills the process.

In any case its nice to know that I'm not he only one having this problem. But dogged persistence pays off, right?

I just want to use my remote to change channels in MythTV, so all I need is the IR Receiver, right? Do I have that right? If all you need is the IR Receiver, then the only module you need should be the i2c module. So does that mean you should have this in /etc/lirc/hardware.conf?

```
MODULES="lirc_i2c"
```

or this?

```
MODULES="lirc_i2c lirc_pvr150"
```

^this seems wrong because it should be either or and not both of these, correct?

```
locate lirc_i2c.ko
/lib/modules/2.6.20-16-generic/misc/lirc_i2c.ko
/usr/src/modules/lirc/drivers/lirc_i2c/.lirc_i2c.ko.cmd

```

finally, has anyone else noticed that the indicator light comes on when the IR cable is plugged in half way? Could this be the problem?

any help appreciated.

---

### Post by md2020 on 2007-07-05
williakj,
> **williakj said:**
> 
I just want to use my remote to change channels in MythTV, so all I need is the IR Receiver, right? Do I have that right? If all you need is the IR Receiver, then the only module you need should be the i2c module. So does that mean you should have this in /etc/lirc/hardware.conf?

```
MODULES="lirc_i2c"
```

You are correct. I have seen other posts where SuperM1 (who I believe wrote/contributed to the Feisty LIRC install instructions) has told those who do not need the blaster to only use lirc_i2c. And lirc_i2c is the IR receiver. tgm4883 was assisting earlier and he was having me redo everything from the beginning and include lirc_pvr150 (blaster). So maybe the receiver works as long as lirc_i2c is included.

> **williakj said:**
> 
finally, has anyone else noticed that the indicator light comes on when the IR cable is plugged in half way? Could this be the problem?

I also noticed someone talking about this in another thread. No one offered any advice on whether it mattered or not for it being only half way plugged in. I doubt that it is meant to be only part way in. Not that it matters yet to me, I can't get to that part!! Maybe someone who has the PVR-150 working will enlighten us.

It is slightly comforting to know that others are in the same boat. Hopefully someone will rescue us!!

---

### Post by tgm4883 on 2007-07-05
It's supposed to be off.  It only comes on when you press a button.

Actually now that I think about it.  I don't remember seeing an indicator light for button presses.  Only for when transmitting.

---

### Post by md2020 on 2007-07-05
tgm4883,

Thanks for the info. And now back to my continuing saga.

I have tried LIRC with both lirc_i2c and lirc_pvr150, and with just lirc_i2c. Either way does not seem to make any difference. The modules are loaded as far as I can tell. The lirc daemon is running and looks like this:
[INDENT]root 7916 1 0 11:37 ? 00:00:00 /usr/sbin/lircd --device=/dev/lirc0[/INDENT]

I check for /dev/lirc before and after running irw. (which always returns me back to the prompt)  I have a /dev/lircd with the chmod 666 permissions. I have never seen any variant of /dev/lirc (/dev/lirc0, /dev/lirc/0) before or after irw. 

I always get this after running irw: 
[INDENT]could not get file information for /dev/lirc0
default_init(): No such file or directory [/INDENT]

I have also tried changing the device from /dev/lirc0 to /dev/lirc. Same result.

Any other suggestions?

---

### Post by bto on 2007-07-05
No particular suggestion yet but I'm giving a reinstall a try after I noticed that the instructions at the link below now use the full Ubuntu desktop vs. the Alternate disk.  I had to redo for something else anyway.  No big deal.

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)

Will post an update after.

On another positive note, the mythtv list just received a note from one of the developers reporting positive action on the zap2it datadirect listings issue.  Reporting 50% > 75% > now 85% confidence today that there will be a good solution.  Makes me feel a bit better about things.

Too bad I'm still not getting datadirect listings at the moment.

Thanks,
Bryce

---

### Post by tgm4883 on 2007-07-05
> **bto said:**
> 
On another positive note, the mythtv list just received a note from one of the developers reporting positive action on the zap2it datadirect listings issue.  Reporting 50% > 75% > now 85% confidence today that there will be a good solution.  Makes me feel a bit better about things.


Link?

---

### Post by bto on 2007-07-05
See:
[http://www.gossamer-threads.com/lists/mythtv/users/277803](http://www.gossamer-threads.com/lists/mythtv/users/277803)

Look for posts by "rmeden" on 7/5 at 10:25 and 10:41.

Of course, I don't know who he is so take it with a grain of salt but I'm embracing the positive spin for the moment.

Bryce

---

### Post by bto on 2007-07-05
UPDATE:  Just followed instructions to the "T" after using Ubuntu Live CD Desktop installation (per the updated-since-yesterday link below) and my silver hauppauge PVR150 remote is working.

Wish I knew just what went wrong or changed but I'm just happy for a solution.

Hope reinstalling the OS works for everyone else...

Bryce

---

### Post by md2020 on 2007-07-05
> **bto said:**
> UPDATE:  Just followed instructions to the "T" after using Ubuntu Live CD Desktop installation (per the updated-since-yesterday link below) and my silver hauppauge PVR150 remote is working.

Wish I knew just what went wrong or changed but I'm just happy for a solution.

Hope reinstalling the OS works for everyone else...

Bryce
Crap. I was afraid you would come back with that. And after looking at a LOT of other posts and not seeing anything that can fix the issue, I am probably left with no other choice but to start from scratch again and pray. 

Those were the instructions I originally followed. I did not install via the alternate disk. I took a look at the instructions but didn't see anything that jumped out at me that changed.

---

### Post by md2020 on 2007-07-07
Did some debugging to see what else I could find. I did this to put lirc_i2c in debug mode:
```
sudo modprobe -r lirc_i2c
sudo modprobe -v lirc_i2c debug=1
```
I then restarted lirc with:
```
sudo /etc/init.d/lirc restart
```
I see this from dmesg:
> [ 1377.708000] lirc_dev: IR Remote Control driver registered, at major 61 
[ 1377.932000] lirc_i2c: probe 0x1a @ ivtv i2c driver #0: no
[ 1377.972000] lirc_i2c: probe 0x18 @ ivtv i2c driver #0: no
[ 1378.008000] lirc_i2c: probe 0x71 @ ivtv i2c driver #0: no
[ 1378.044000] lirc_i2c: probe 0x4b @ ivtv i2c driver #0: no
[ 1378.076000] lirc_i2c: probe 0x64 @ ivtv i2c driver #0: no
[ 1378.112000] lirc_i2c: probe 0x30 @ ivtv i2c driver #0: no
[ 1378.148000] lirc_i2c: probe 0x6b @ ivtv i2c driver #0: no

Looks like i2c/ivtv can't find a proper place to probe. I saw here ([http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft)) that I should be getting something like:
[INDENT]lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))[/INDENT]
But mine is finding nothing. After attempting to do irw, I get the usual:
> Jul  7 12:20:28 mdpvr lircd-0.8.2-CVS[6786]: lircd(userspace) ready
Jul  7 12:21:14 mdpvr lircd-0.8.2-CVS[6786]: accepted new client on /dev/lircd
Jul  7 12:21:14 mdpvr lircd-0.8.2-CVS[6786]: could not get file information for /dev/lirc0
Jul  7 12:21:14 mdpvr lircd-0.8.2-CVS[6786]: default_init(): No such file or directory 
Jul  7 12:21:14 mdpvr lircd-0.8.2-CVS[6786]: caught signal


I am starting to wonder if I have a newer version of the PVR-150 that is not fully recognized by i2c/ivtv.
Here is the info on my card:
[INDENT]WINTV-PVR-150
26152LF    Rev E5B2

(on Conexant MPEG encoder chip)
CX23416-22

(on different Conexant chip)
CX25843-24Z
[/INDENT]

Could anyone else confirm that they have this same card working? And/or can anyone else with a PVR-150 working on Feisty do the modprobe of lirc_i2c in debug mode and see where it connects?

I saw here ([http://dl.ivtvdriver.org/ivtv/stable/ChangeLog-0.10](http://dl.ivtvdriver.org/ivtv/stable/ChangeLog-0.10)) that for 0.10.2 release there is code for "Add autodetect for new PVR150 low-profile models" . While mine is not low profile, I wonder if it uses the same new chips??

Thanks in advance for any advice/help.

---

### Post by williakj on 2007-07-08
@md2020 i have got this far:

```
ls /dev/lir*
/dev/lirc0  /dev/lircd
```

```
 ls /lib/modules/2.6.20-16-generic/misc/ 

lirc_dev.ko  lirc_i2c.ko

```

```
locate lirc_i2c.ko

/lib/modules/2.6.20-16-generic/misc/lirc_i2c.ko
/usr/src/modules/lirc/drivers/lirc_i2c/.lirc_i2c.ko.cmd

```

```
dmesg | grep lirc
```

gives me this:

> [   90.107584] lirc_dev: IR Remote Control driver registered, at major 61 
[   90.400833] **lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.**
[   90.999310] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   90.999600] lirc_dev: lirc_register_plugin: sample_rate: 10
[150257.310459] lirc_dev: IR Remote Control driver registered, at major 61 
[150258.164610] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[150258.169279] lirc_dev: lirc_register_plugin: sample_rate: 10


^ kernel still tainted.

and:

```
dmesg | grep ivtv
```

gives me:

```

[   52.291673] ivtv:  ==================== START INIT IVTV ====================
[   52.291684] ivtv:  version 0.10.1 (tagged release) loading
[   52.291690] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   52.291696] ivtv:  In case of problems please include the debug info between
[   52.291703] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   52.291709] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   52.785676] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   55.294502] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   55.507532] ivtv0: Encoder revision: 0x02050032
[   55.507541] ivtv0: Recommended firmware version is 0x02060039.
[   55.593150] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   55.593156] ivtv0: reopen i2c bus for IR-blaster support
[   55.677268] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   55.840901] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   58.901354] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   58.944137] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   58.947934] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   58.949989] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   58.951593] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   59.268217] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   59.268260] ivtv:  ====================  END INIT IVTV  ====================

```

so its saying that my chip is found, however I'm not any further along than you are at this point because it still isn't working. i'm thinking its the kernel module not being loaded.

running 

```
sudo modprobe lirc_i2c
```

returns nothing on the terminal.

```
sudo lsmod | grep lirc
```

comes back with:

```
lirc_i2c               11268  0 
lirc_dev               15988  1 lirc_i2c
i2c_core               22656  11 lirc_i2c,cx88xx,bttv,wm8775,cx25840,tuner,nvidia,ivtv,i2c_piix4,i2c_algo_bit,tveeprom

```

what does yours say, md2020? (or anyone else)

here is my hardware,conf file

```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS="--device=/dev/lirc0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
~                                                                               
~                                                                               
"/etc/lirc/hardware.conf" 21 lines, 545 characters

```

also, can anyone tell me why are there two --device flags on the process? O_o

```
sudo /etc/init.d/lirc stop

```

```
sudo /etc/init.d/lirc start
```

```
 ps ax | grep lirc
28693 ?        S      0:00 [lirc_dev]
29736 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0 --device=/dev/lirc0
29740 pts/0    R+     0:00 grep lirc

```

is it possible that LIRCD_ARGS="--device=/dev/lirc0" is not needed in the hardware.conf file?

edit: just saw this

> **bto said:**
> UPDATE:  Just followed instructions to the "T" after using Ubuntu Live CD Desktop installation (per the updated-since-yesterday link below) and my silver hauppauge PVR150 remote is working.

Wish I knew just what went wrong or changed but I'm just happy for a solution.

Hope reinstalling the OS works for everyone else...

Bryce

say it ain't so =[

---

### Post by md2020 on 2007-07-08
williakj, I feel your pain. But I think I would gladly change places with you as you are farther than I.

I pretty much have the exact same things as you except where noted below.

Instead of doing this:
[INDENT]ls /dev/lir*[/INDENT]
Do this:
```
ls -l /dev/lir*
```
That will show you the rights/privileges granted to the directories.  They need to be rw-rw-rw-.

> **williakj said:**
> 
```
dmesg | grep lirc
```
[ 90.107584] lirc_dev: IR Remote Control driver registered, at major 61
[ 90.400833] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[ 90.999310] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 90.999600] lirc_dev: lirc_register_plugin: sample_rate: 10
[150257.310459] lirc_dev: IR Remote Control driver registered, at major 61
[150258.164610] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[150258.169279] lirc_dev: lirc_register_plugin: sample_rate: 10

Here is where you are getting farther than I and the reason you get a /dev/lirc0.
I never get the:
[INDENT]lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))[/INDENT]
That indicates that it found your IR chip.


> **williakj said:**
> 
```
dmesg | grep ivtv
```

Use this instead to see the whole section of your IVTV init. (everything between START and END)
```
dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac

```
Here is my complete IVTV init:
[INDENT][   27.304000] ivtv:  ==================== START INIT IVTV ====================
[   27.304000] ivtv:  version 0.10.1 (tagged release) loading
[   27.304000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   27.304000] ivtv:  In case of problems please include the debug info between
[   27.304000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   27.304000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   27.308000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   27.308000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   27.308000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   27.568000] nvidia: module license 'NVIDIA' taints kernel.
[   28.096000] usbcore: registered new interface driver cdc_ether
[   28.168000] usb 5-3: bad CDC descriptors
[   28.168000] usbcore: registered new interface driver rndis_host
[   28.664000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   28.880000] ivtv0: Encoder revision: 0x02050032
[   28.880000] ivtv0: Recommended firmware version is 0x02060039.
[   28.960000] tveeprom 1-0050: Hauppauge model 26152, rev E5B2, serial# 10295246
[   28.960000] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   28.960000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   28.960000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   28.960000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   28.960000] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   28.960000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   28.960000] ivtv0: reopen i2c bus for IR-blaster support
[   29.088000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.392000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   33.880000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   33.980000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   34.020000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   34.020000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   34.024000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   34.024000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   34.024000] tuner 1-0061: type set to 50 (TCL 2002N)
[   34.340000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   34.340000] ivtv:  ====================  END INIT IVTV  ====================[/INDENT]

> **williakj said:**
> 
so its saying that my chip is found, however I'm not any further along than you are at this point because it still isn't working. i'm thinking its the kernel module not being loaded.

running 

```
sudo modprobe lirc_i2c
```

returns nothing on the terminal.

```
sudo lsmod | grep lirc
```

comes back with:

```
lirc_i2c               11268  0 
lirc_dev               15988  1 lirc_i2c
i2c_core               22656  11 lirc_i2c,cx88xx,bttv,wm8775,cx25840,tuner,nvidia,ivtv,i2c_piix4,i2c_algo_bit,tveeprom

```

Your lirc_i2c module is loaded. That is what lsmod is telling you. Calling modprobe as you did will load it if it is not already loaded.

Here is mine:
```
sudo lsmod | grep lirc
lirc_i2c               11268  0 
lirc_dev               15988  1 lirc_i2c
i2c_core               22656  14 cx88xx,bttv,lirc_i2c,i2c_ec,wm8775,cx25840,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom,i2c_viapro,via686a,i2c_isa
```

My hardware,conf file is exactly the same as yours. No clue why you see two --device parms for lircd. Mine only has one. But you have a [lirc_dev] returned via "ps ax|grep lirc" where I do not. Here is what I see:
```
ps ax | grep lirc
 5041 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0
 6601 pts/0    R+     0:00 grep lirc
```

> **williakj said:**
> 
is it possible that LIRCD_ARGS="--device=/dev/lirc0" is not needed in the hardware.conf file?

I can't imagine that to be correct. But you do have an interesting situation seeing two of them. Again, no idea why.

> **williakj said:**
> 
say it ain't so =[

I have not done so myself yet. Holding out hope of finding out what is preventing it from working. I used the same install method bto used.

---

### Post by md2020 on 2007-07-16
For those of you following along, or even worse, playing along at home, here is where I am at and what I have been able to figure out.

I first removed the PVR-150 and placed it in a WinXP PC to verify that the IR receiver and the remote work. Both work perfectly.

My next task was to then find a drive to install XP on, and run it on the same PC where I have Feisty/MythTV/LIRC. Found a drive, installed XP, checked the remote. It works. 

So now I am confident that it is not strictly a hardware conflict and probably not a BIOS setting. Unless WinXP is somehow overcoming a BIOS setting that Ubuntu can not. 

I have also done some debugging with the LIRC_I2C module. From what I can see, LIRC is not to blame. The lirc_i2c module is calling the i2c_master_recv function that should return a successful return code when the IR Receiver is probed successfully. That function never returns a successful probe for any of the addresses it is checking.

I am in the process now of installing Edgy in a different partition to see if it has any better luck.

i2c_master_recv is a part of i2c-core.c from what I see. Maybe my IVTV or I2C bus code needs to be rebuilt. If anyone has further suggestions, let me know.

---

### Post by bla2000 on 2007-07-16
I have a working combined desktop/backend/frontend on Feisty with a pvr 150 grey remote that I installed 2 days ago.  I followed the same guide [https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty") .  Are there some commands that you'd like me to run so that I can display output for you to use as comparison?

---

### Post by charles909 on 2007-07-25
Hello, I was having this same issue, but I fixed it by going into /etc/lirc/hardware.conf and editing the MODULES line to only include lirc_pvr150 like this:

MODULES="lirc_pvr150"

Then, I did a reboot and everything worked!  I forgot where I saw this fix, but it took a lot of googling to find.

---

### Post by md2020 on 2007-08-18
> **charles909 said:**
> Hello, I was having this same issue, but I fixed it by going into /etc/lirc/hardware.conf and editing the MODULES line to only include lirc_pvr150 like this:

MODULES="lirc_pvr150"

You are quite correct. I have never been able successfully load both LIRC_I2C and LIRC_PVR150 modules at the same time. So I am pretty sure that you can only specify one or the other in /etc/lirc/hardware.conf. Even though the LIRC install instructions for Feisty seem to indicate otherwise.

And on a much happier note, I now have LIRC working for a PVR-150. Well I should say that the PVR-150 I started off with still does not work. I got a new PVR-150 and put it in, stared up Ubuntu, and boom, there is was just like it should be. It was a happy moment to see /dev/lirc0 looking back at me.

So my issue was definitely the PVR-150 card. I did not change any of the settings when going from the old one, which did not work, to the new one which does work. I decided to try a new PVR-150 when I put my old PVR-150 in a different PC with completely different hardware. It still did not work under Ubuntu there either. The other really interesting thing is that the remote for the old PVR-150 would work under WinXP on either machine. It simply would not work under Ubuntu on either PC. (I should further qualify that everything about the card worked in Ubuntu except for LIRC and the remote.) So to put my mind at ease that I did not have a faulty card, I got a new one. Thankfully I did.

I am now going to mark this thread as "Solved". Thanks to all who attempted to help me and provide advice/suggestions.

---

### Post by Depressed Man on 2007-08-26
Hmm I have MythTV on Ubuntu and it does see my PVR-150 card. I set it up as tuner but it can't seem to scan channels from it (it doesn't see it in the channel scanning).

---

