---
title: "Antec Multimedia Station Basic w/ LIRC"
date: 2009-05-15
forum: Multimedia Software
---

### Post by shabazzk on 2009-05-15
I am stuck trying to get LIRC to recognize my hardware plugged in. When I run the irrecord I get the following error:

```
$sudo irrecord -d /dev/input/by-id/usb-15c2_0043-event-mouse lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get hardware features
irrecord: this device driver does not support the new LIRC interface
irrecord: major number of /dev/input/by-id/usb-15c2_0043-event-mouse is 13
irrecord: LIRC major number is 61
irrecord: check if /dev/input/by-id/usb-15c2_0043-event-mouse is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

It's working fine in Windows7 even working with the Harmony 550 remote I programmed for it.

Background:
I bought the Antec Multimedia Station Basic IR from newegg.com which turned out to be just the Soundgraph IMON Inside. I have been trying to set it up for the last 2+ weeks, with very little success.

I am running Ubuntu 9.04 Jaunty 64bit
Kernel: 2.6.28-11-generic

I have tried instructions from these sites:
1. [http://www.lirc.org/html/index.html](http://www.lirc.org/html/index.html)
2. [https://help.ubuntu.com/community/InstallLirc/Hardy#Unlisted%20Remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Unlisted%20Remotes)
But no joy :mad:

I have also tried various tips from these very forums, and also from XBMC forums for Linux. I am tired of struggling with it myself so I decided to post.

Info about my device:
```
lsusb
Bus 005 Device 002: ID 15c2:0043 SoundGraph Inc. 

sudo cat /proc/bus/input/devices
I: Bus=0003 Vendor=15c2 Product=0043 Version=0101
N: Name="HID 15c2:0043"
P: Phys=usb-0000:00:13.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input5
U: Uniq=
H: Handlers=kbd mouse2 event5 
B: EV=100017
B: KEY=70000 1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=103
B: MSC=10

sudo gedit /etc/lirc/hardware.conf
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""
```

---

### Post by speed32219 on 2009-05-17
Did you use the latest lirc driver module.  It is lirc 0.8.5pre1 or pre2 for your device.

I have the same device and I'm stuck, It lloks like the usbhid driver is loaded, follow my steps in the post attached to get rid of those drivers.  It is recognizing your device as a mouse, which the usbhid drivers will do.

Here is my post with what I have done so far and the command to get the new driver is in the middle somewhere. (wget)

[http://ubuntuforums.org/showthread.php?t=1161574&highlight=soundgraph](http://ubuntuforums.org/showthread.php?t=1161574&highlight=soundgraph)

Let me know how it goes, I have been fighting with this for over 2 weeks off and on.

---

### Post by shabazzk on 2009-05-26
I reinstalled lirc0.8.4a on Jaunty 9.04. But I still get no output when I run irrecord when I press buttons on the remote. 
```
$ irrecord -H devinput -d /dev/input/event5 test

Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event5'
```
How do I find the correct event to use with my IR device?

---

### Post by klato on 2009-06-21
Has anyone had any luck with this remote? I've got the same one but I cannot get it working.

Installed jaunty, updated, installed lirc from synaptic. No remote. Now what?!

---

### Post by shabazzk on 2009-06-22
This remote does not work out of the box with lirc 0.8.4a, which is the version in Synaptic in Jaunty. I was able to get it partially working with lirc 0.8.5a. mode2 recognized every button press, but after running irrecord only numbers worked then it seemed to crash, and would NOT work until I rebooted. SO of course for no apparent reason, I wiped my machine to get a fresh start.

After wiping my machine, I accidentally installed the 32bit version of Jaunty :(. So I decided to experiment and I even tried to patch 0.8.4a so it recognized my IR. This sorta work, as lirc is loaded for my IR device, and even the lirc0 and lirc1 devices are present in /dev/. But I do NOT get any ouput with irw, mode2, or irrecord. Strange :confused:

And that is where I'm at currently. The driver is loaded, the devices are registered, but all testing fails.

It would be great if someone could provide insight. As there are more and more people getting this remote.

I should NOTE that I'm using an harmony 550 programmed as a Mulimedian remote as the RM100 I received is dead. Which I will be contacting Antec about.

---

### Post by klato on 2009-06-22
I tried installing lirc 0.8.5 from their site, but it still doesn't work with my antec veris basic.

Bummer, since this is the only piece missing for my HTPC. Lost my whole weekend trying to make it work. I might just change OS and call it a day. :(

---

### Post by shabazzk on 2009-06-23
> **klato said:**
> I tried installing lirc 0.8.5 from their site, but it still doesn't work with my antec veris basic.

Bummer, since this is the only piece missing for my HTPC. Lost my whole weekend trying to make it work. I might just change OS and call it a day. :(

Don't feel bad, I and others have lost many weekends. I alone have spent well over 100 hours trying to get this to work, as this is also the remaining piece to my system.

Also, installing 0.8.5 does NOT install completely, there are special things you have to do after you install it, all of which I do NOT comprehend, which is why I gave 0.8.4a another try, to see if I can spot the difference.

I can help you get to where I'm at and hopefully further, and a lot faster than I did. First there are a few things we need to do before we proceed:

1. Have your original Antec Veris Basic remote (RM100 that came in the box) with you and working. 
*Note: To check if it is working, point it at a digital camera, and press some buttons; while doing so, look at the digital camera screen to see if you see a light as you press buttons on the remote, the light means it's working (nice trick I learned in these forums. You could also simply point it at the computer and see if the blue light on the receiver blinks when you press button on the RM100.*

2. Uninstall 0.8.5 completely, it will be easier to backup your files and reinstall a fresh copy of Ubuntu, as this takes much less time.

3. Check the Vendor ID and Product ID for the imon device you have, it may the same as mine, which is 0x15c2:0x0043. You can get this easily by typing 'lsusb' in a console and searching for Soundgraph, our you can type:
```
lsusb | grep Soundgraph
```.

If you IDs are different, then post them here. These will be used to patch the imon driver to recognize you IR.

4. Make sure no drivers are loaded for the IR hardware.

Once all this is done, you are ready to install the patched version of lirc 0.8.4a. Which I will explain once you confirm you are good to go :)

---

### Post by klato on 2009-06-24
> **shabazzk said:**
> Don't feel bad, I and others have lost many weekends. I alone have spent well over 100 hours trying to get this to work, as this is also the remaining piece to my system.

Also, installing 0.8.5 does NOT install completely, there are special things you have to do after you install it, all of which I do NOT comprehend, which is why I gave 0.8.4a another try, to see if I can spot the difference.

I can help you get to where I'm at and hopefully further, and a lot faster than I did. First there are a few things we need to do before we proceed:

1. Have your original Antec Veris Basic remote (RM100 that came in the box) with you and working. 
*Note: To check if it is working, point it at a digital camera, and press some buttons; while doing so, look at the digital camera screen to see if you see a light as you press buttons on the remote, the light means it's working (nice trick I learned in these forums. You could also simply point it at the computer and see if the blue light on the receiver blinks when you press button on the RM100.*

2. Uninstall 0.8.5 completely, it will be easier to backup your files and reinstall a fresh copy of Ubuntu, as this takes much less time.

3. Check the Vendor ID and Product ID for the imon device you have, it may the same as mine, which is 0x15c2:0x0043. You can get this easily by typing 'lsusb' in a console and searching for Soundgraph, our you can type:
```
lsusb | grep Soundgraph
```.

If you IDs are different, then post them here. These will be used to patch the imon driver to recognize you IR.

4. Make sure no drivers are loaded for the IR hardware.

Once all this is done, you are ready to install the patched version of lirc 0.8.4a. Which I will explain once you confirm you are good to go :)

Sounds good to me!

1. Remote is indeed working, blue light blinks when I press buttons

2. Reinstalled Ubuntu 9.04 entirely, starting from scratch

3. lsusb lists the 0x15c2:0x0043 ID

4. No drivers loaded whatsoever. Just did a fresh install and only ran update manager to bring the system up to date.

Thanks :)

---

### Post by shabazzk on 2009-06-24
I was very busy yesterday, but I will explain how to patch the imon driver and provide the patched file when I get home around (5:30PM EST 06/24/09) today.

---

### Post by klato on 2009-06-24
Much appreciated shabazzk!

---

### Post by shabazzk on 2009-06-24
1a. Get needed packages:

```

sudo apt-get install build-essential checkinstall automake dialog

```
1b. Grab the header files for your kernel (mines is 2.6.28-13-generic), they may already be installed, which is OK too, just check /usr/src for a folder that matches your kernel, that means the headers are installed, if not, then run the command below, just make sure change the version numbers to match your kernel:

```

sudo apt-get install linux-headers-2.6.28-13-generic

```

1c. Install lirc
```
sudo apt-get install lirc
```

1d. Install lirc sources:
	
```

sudo apt-get install lirc-modules-source

```

2a. Switch into the lirc source directory.
	
```
cd /usr/src/lirc-0.8.4a/drivers/lirc_imon
```

2b. Make a backup of the original imon driver.

```
mv lirc_imon.c lirc_imon.c.backup0
```

3. Download the patched imon driver file I made, you can compare mine with the one in the sources to see what I changed.
	
```
sudo wget http://www/shabak.net/lirc_imon.c
```

4. Now it's time to remove the old driver from the dkms tree and build and install your new one.

```
sudo dkms remove -m lirc -v 0.8.4a --all
sudo dkms add -m lirc -v 0.8.4a
sudo dkms -m lirc -v 0.8.4a build
sudo dkms -m lirc -v 0.8.4a install
```

5. Removed the old driver currently in use, and load the new one
```
sudo rmmod lirc_imon
sudo modprobe lirc_imon
sudo /etc/init.d/lirc restart
```

6. Check to see if the devices are in dev
```
ls /dev | grep lirc
```
The above command should print:
lirc0
lirc1
lircd

If not, then reboot and try the command again.

7. Time to test the the remote, enter the command below and try pressing buttons.
```
sudo mode2 --device=/dev/lirc0 --raw --driver=devinput
```

This is as far as I've gotten. If you have problems with my directions, take a look at this for referecne, I'm off to see transformers the fallen. Will check the forum when I get back home.

[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes)

---

### Post by klato on 2009-06-25
Thanks shabazzk, I'll give this a shot tonight.

---

### Post by klato on 2009-06-29
I had to put on my old Windows XP disc guys, as I couldn't spend any more nights on this thing. (My gf probably would've left me!)

:-({|=

---

### Post by shabazzk on 2009-06-29
I hear you man, I have to work on it in secret when she's not here with me.:lolflag:

---

### Post by klato on 2009-06-29
LOL

I'll give this another shot maybe a few months down the line (9.10)

---

### Post by jackflap on 2009-10-06
```
sudo wget http://www/shabak.net/lirc_imon.c
```

Has anyone still got this file? The command above isn't working. Generally the URL [www.shabak.net](www.shabak.net) isn't working.

---

### Post by shabazzk on 2009-10-06
jackflap, don't use that file. LIRC has been updated to support the Antec Veris Basic, and I hear it works by default in 9.10 Beta, if you're brave enough to upgrade to it. 

Try this tut: [https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)

SIDE NOTE: I have struggled too hard in 9.04 and have decided to help the LIRC project and eventually convert it to C++ and push to a git repository. Right now I am deciphering the code and setting up my development environment on the very HTPC I built with the Veris Basic as my test subject.


ATM All I can recommend is that u try the IR on 9.10 somehow without wiping your system or upgrading (separate partition/usb stick install).

---

### Post by jackflap on 2009-10-06
Hey thanks Shabazzk,

You're right, works like a charm in 9.10 (with help from this thread [http://ubuntuforums.org/showthread.php?t=1161574&highlight=soundgraph&page=3](http://ubuntuforums.org/showthread.php?t=1161574&highlight=soundgraph&page=3)).

Jackflap

---

### Post by shabazzk on 2009-10-08
jackflacpp

Glad to see that you got this resolved. If you don't mind me asking, how long have you been struggling with this?

---

### Post by jackflap on 2009-10-11
> **shabazzk said:**
> jackflacpp

Glad to see that you got this resolved. If you don't mind me asking, how long have you been struggling with this?

To be honest, I had actually found this howto, plus the one here: [http://ubuntuforums.org/showthread.php?t=1161574&highlight=soundgraph&page=3](http://ubuntuforums.org/showthread.php?t=1161574&highlight=soundgraph&page=3) before deciding to buy the Antec Basic (internal).

So, I had a pretty good idea that with some fiddling, I'd be able to get it to work. It's still not completely solved yet, I can see the events in irw, but I'm still kinda lost with the whole .lircrc and irxevent thing.

All in all, the whole thing will probably end up having taken me 2 full days (spread out over 2 weeks).

Your persistent efforts and struggles with these drivers is very much appreciated, it really is a GREAT media centre receiver :)

---

### Post by shabazzk on 2009-10-11
Good to hear it did not take you as long as it did others of us, so progress is slowly, but surely being made. The problem is the lirc program itself, it's just not user friendly and there are too many components that you have to configure individually. It would really be nice if someone who knew the ins and outs of this were to give guidance. 

Plus, it does NOT help that I can't figure out how Ubuntu is changing from release to release without becoming an expert, by this I mean usbhid grabbing the device and not letting lirc load for it.

---

### Post by jackflap on 2009-10-16
So, I'm attaching a very basic .lircrc I built for the Antec remote for irxevent and irexec. 

irexevent and irexec are damons that translate the ir codes received into key-presses to be sent to the computer.

Place the .lircrc in your ~ and run irxevent and irexec with it. Note. This .lircrc will only work with irxevent and irexec and not mythtv.

---

### Post by jackflap on 2009-10-25
Just an update. Last night I installed all updates in Karmic and it updated the kernel and lirc. That caused /dev/lirc1 to disappear.

I then ran sudi dpkg-reconfigure lirc and chose the default 'Soundgraph iMon Antec Veris' remote set-up from the lirc conf app, which worked out-the-box with my remote.

So, had I waited for the Karmic release, I could have skipped all of the above, oh well.. :P

---

### Post by shabazzk on 2009-11-18
We finally found a solution to getting the Veris Basic working with lirc as it should, you can read the details of how to set it up here:
[http://ubuntuforums.org/showthread.php?t=1161574&page=6](http://ubuntuforums.org/showthread.php?t=1161574&page=6)

Enjoy :popcorn:

---

