---
title: "Sound card problem"
date: 2009-12-26
forum: Multimedia Software
---

### Post by AshNZ on 2009-12-26
Hi,

I installed latest Ubuntu on my Dell Studio 15 few days ago and since then I've had more troubles than it is worth. Latest one is with my sound card. Until last night, sound was working fine and I could listen to music without much problem. Then I woke up today morning and now Ubuntu can't read my sound card! When I right click on the speaker button, I can't see anything under Hardware. My sound card was there last night!!

Anyway, I checked [this thread]("http://ubuntuforums.org/showthread.php?t=205449") and went through the procedure. Then sound came back and I could see my card. It didn't last long though. After I made few changes to get my 5.1 system working, my sound card disappeared again. I repeated the procedure again but without any luck this time. 

I also went through [this page]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") and ```
aplay -l
``` gives me..

aplay: device_list:223: no soundcards found...

And, ```
lspci -v | less
```gives me.. 

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 029f
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fc700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: oss_hdaudio
        Kernel modules: snd-hda-intel

```Another script down that page gave me..```


!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Sat Dec 26 05:10:15 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Studio 1537


!!Kernel Information
!!------------------

Kernel release:    2.6.31-16-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 1028:029f


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
bridge
stp
bnep
oss_usb
oss_hdaudio
osscore
btusb
joydev
snd_page_alloc
arc4
ecb
iwlagn
iwlcore
mac80211
dell_wmi
iptable_filter
sdhci_pci
sdhci
led_class
ip_tables
x_tables
dell_laptop
dcdbas
cfg80211
psmouse
serio_raw
lp
parport
uvcvideo
videodev
v4l1_compat
usbhid
fbcon
tileblit
font
bitblit
softcursor
ohci1394
ieee1394
tg3
i915
drm
i2c_algo_bit
intel_agp
agpgart
video
output


!!ALSA/HDA dmesg
!!------------------

[    1.887854] i2c-adapter i2c-2: unable to read EDID block.
[    1.887857] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    1.894645] [drm] fb0: inteldrmfb frame buffer device
--
[   16.018201] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.142041] snd: Unknown symbol unregister_sound_special
[   16.142270] snd: Unknown symbol register_sound_special_device
[   16.142881] snd: Unknown symbol sound_class
[   16.144756] snd_timer: Unknown symbol snd_verbose_printd
--
[   17.506393] i2c-adapter i2c-2: unable to read EDID block.
[   17.506397] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.510986] i2c-adapter i2c-2: unable to read EDID block.
[   17.510988] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.642089] i2c-adapter i2c-2: unable to read EDID block.
[   17.642091] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.646694] i2c-adapter i2c-2: unable to read EDID block.
[   17.646696] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.542957]   alloc irq_desc for 22 on node -1
--
[   18.542966] oss_hdaudio 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.548006] oss_hdaudio: HDA codec 0x111d7675 not known yet
[   18.557111] oss_hdaudio: HDA codec 0x80862802 not known yet
[   18.558208] oss_hdaudio: HDA codec 0x111d7675 not known yet
[   18.558605] oss_hdaudio: HDA codec 0x80862802 not known yet
[   18.606295] usbcore: registered new interface driver oss_usb
[   19.295191] i2c-adapter i2c-2: unable to read EDID block.
[   19.295194] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.299790] i2c-adapter i2c-2: unable to read EDID block.
[   19.299792] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.434149] i2c-adapter i2c-2: unable to read EDID block.
[   19.434151] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.438740] i2c-adapter i2c-2: unable to read EDID block.
[   19.438742] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.574147] i2c-adapter i2c-2: unable to read EDID block.
[   19.574149] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.578781] i2c-adapter i2c-2: unable to read EDID block.
[   19.578784] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.805791] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
--
[   29.820632] i2c-adapter i2c-2: unable to read EDID block.
[   29.820636] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.825119] i2c-adapter i2c-2: unable to read EDID block.
[   29.825121] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.963170] i2c-adapter i2c-2: unable to read EDID block.
[   29.963173] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.967660] i2c-adapter i2c-2: unable to read EDID block.
[   29.967662] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.099914] i2c-adapter i2c-2: unable to read EDID block.
[   30.099917] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.104416] i2c-adapter i2c-2: unable to read EDID block.
[   30.104426] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.643120] i2c-adapter i2c-2: unable to read EDID block.
[   30.643124] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.647752] i2c-adapter i2c-2: unable to read EDID block.
[   30.647754] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   39.308061] wlan0: no IPv6 routers present
```I'm not an expert but I was surprised to see nothing next to ALSA Driver version.. is that odd? Also, there are no ALSA Modules installed. I'm a total newbie so I don't know how to fix that. There are few other oddities there but again, not sure how to fix that. 

Thanks for your time!!

PS: Soundcard is working fine in Windows. I dual boot Win 7 with Ubuntu.

---

### Post by fibercode on 2009-12-26
The thread you posted has 101 pages... sorry if I don't go through it :)

What you need is the ALSA drivers for your card:

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Download the 1.0.22 ver:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.tar.bz2)

Uncompress then open a terminal and go to the directory that contains the uncompressed files.

First make sure that you have the "patch" utility installed:
```

sudo apt-get install patch
```

Then run:

```
sudo configure
sudo make
sudo make install
```

Reboot your computer.

Then run:

```
alsamixer
```

This will allow you to adjust the sound and microphone levels.

---

### Post by AshNZ on 2009-12-26
Thanks buddy. I've tried to install the drivers but seems like it didn't work. First time I've done this so I'm not sure how to install them properly. If you could give me instructions for absolute dummies, that'd be great. For now, when I run alsamixer, I get "alsamixer: function snd_ctl_open failed for default: No such file or directory"

Another thing, when I run this command,

sudo configure
sudo make
sudo make install

do I copy and paste all three lines to the terminal or run them one by one?

When I run sudo configure, I get "sudo: configure: command not found"

PS: When boot off the Live CD, I can see my sound card.

---

### Post by AshNZ on 2009-12-26
Bump.

I'd hate to uninstall Ubuntu on basis of just this problem.

---

### Post by fibercode on 2009-12-26
Ok...

1. Download the file from the link I gave you. The file name would be alsa-driver-1.0.22.tar.bz2

2. Unbizp and untar the file:

- Open up "Terminal" and make sure you are in the directory where you downloaded the file. By default firefox will save you files on your Desktop.

- Once you are in the directory containing the file:
```

tar -xvjpf alsa-driver-1.0.22.tar.bz2
```

- This will create a directory called alsa-driver-1.0.22. Go into that directory:

```
cd alsa-driver-1.0.22
```

3. Configure, and install the ALSA driver:

Run these commands one by one in this order. You will get output after each command:

```

sudo ./configure --with-cards=all
sudo make
sudo make install

```

4. Reboot your computer.

5. After it comes up run in ternimal:

alsamixer

The alsamixer will allow you to adjust the sound and the microphone volumes. Please note that the microphone (input) volume will be muted by default after the ALSA installation so make sure to increase the volume if you want to use your mike.

Let me know how it went..

---

### Post by AshNZ on 2009-12-27
Thanks, buddy! For the first command, I'm getting this error:<br />
<br />
tar: alsa-driver-1.0.22.tar.bz2: Cannot open: No such file or directory<br />
tar: Error is not recoverable: exiting now<br />
tar: Child returned status 2<br />
tar: Exiting with failure status due to previous errors<br />
<br />
Even though the file is on desktop.

But, I did this manually and ran the other commands. But after rebooting, when I run alsamixer, I get 

alsamixer: function snd_ctl_open failed for default: No such file or directory

And when I ran, 'make install', I got this error at the end.. 

cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

---

### Post by fibercode on 2009-12-27
The warning at the end of the make install is fine. It is there to let you know that you need to adjust your volumes with alsamixer.

What worries me is that the alsamixer command produces:

alsamixer: function snd_ctl_open failed for default: No such file or directory

In this case I would ask you to go through the Sound Troubleshooting page, but it seems that you had already done so with no success.

Is this a fresh install of Ubuntu? Do you have a previous version of the kernel? If you do, you can boot into the previous kernel version.

To find out if you have another kernel run:

```
ls -l /boot | grep img
```

If you get back more than one line, then you have more than one kernel image.

In this case I will let you know how to use the other kernel image. Hopefully it will be fine with the sound.

That is all can think of right now.

---

### Post by AshNZ on 2009-12-27
Thanks mate. When I run that command you gave, I get even though I've never had Ubuntu before on my machine: 

-rw-r--r-- 1 root root 7642087 2009-12-25 02:24 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root 8141169 2009-12-27 14:52 initrd.img-2.6.31-16-generic

I will now boot into the other image and check.

---

### Post by AshNZ on 2009-12-27
Yep, I can hear sound on this image (2.6.31-14-generic). . I hope it doesn't go away after a while like it did with the other image. Anyway, can I get rid of the other image? Or can I make this one default so this one logs in automatically instead of me having to select it? 

Thanks for all your help so far.

---

### Post by lenkiatleong on 2009-12-27
> **fibercode said:**
> The warning at the end of the make install is fine. It is there to let you know that you need to adjust your volumes with alsamixer.

What worries me is that the alsamixer command produces:

alsamixer: function snd_ctl_open failed for default: No such file or directory

In this case I would ask you to go through the Sound Troubleshooting page, but it seems that you had already done so with no success.

Is this a fresh install of Ubuntu? Do you have a previous version of the kernel? If you do, you can boot into the previous kernel version.

To find out if you have another kernel run:

```
ls -l /boot | grep img
```If you get back more than one line, then you have more than one kernel image.

In this case I will let you know how to use the other kernel image. Hopefully it will be fine with the sound.

That is all can think of right now.


Hi fibercode,

I hope you can help me solve 5.1 sound problem via optical cable. Please see this thread.
[http://ubuntuforums.org/showthread.php?t=1359999&page=2](http://ubuntuforums.org/showthread.php?t=1359999&page=2)

Thanks.
Len

---

### Post by fibercode on 2009-12-27
> **AshNZ said:**
> Yep, I can hear sound on this image (2.6.31-14-generic). . I hope it doesn't go away after a while like it did with the other image. Anyway, can I get rid of the other image? Or can I make this one default so this one logs in automatically instead of me having to select it? 

Thanks for all your help so far.

Yes, you can make this image load automatically and you can also lock this kernel version so it does not get upgraded along with the other updates.

1. You need to edit your /boot/grub/menu.lst file:

```
sudo gedit /boot/grub/menu.lst
```

Change the line that says "default         0" to "default         2" (from 0 to 2). In this paragraph:

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0
```


This will tell grub to load the third kernel image that is specified towards the end of the file. Note that the count starts from zero, that is why 2 corresponds to the 3rd entry. The first 2 entries should be 2.6.31-16-generic and 2.6.31-16-generic (recovery mode) and the 3rd should be the 2.6.31-14-generic image - hence the one you want.

Once you do this you can reboot and it should automatically load the 2.6.31-14 kernel.

Now you need to lock this version of the kernel so that you don't have any problems in the future and lose some other functionality.

Go to:

System -> Administration -> Synaptic Package Manager

Choose "Status" from the left bottom of your screen, then choose "Installed" from up top.

Now search for "linux-" (without the quotes) in the "Quick Search" box.

Then click on each line that starts with "linux-" and then do Package -> Lock Version.

Make sure to do this for each line starting with linux-. Once you do this you will see them turning red.

This will prevent you from accidentally updating your kernel. Once you have a kernel that works for you, you don't have to update it. Just enjoy Linux :) You can still do the other regular updates though.

---

### Post by fibercode on 2009-12-27
> **lenkiatleong said:**
> Hi fibercode,

I hope you can help me solve 5.1 sound problem via optical cable. Please see this thread.
[http://ubuntuforums.org/showthread.php?t=1359999&page=2](http://ubuntuforums.org/showthread.php?t=1359999&page=2)

Thanks.
Len

Lenkiatleong, 

Unfortunately I do not have much experience with surround sound on Linux. But from reading the other thread it becomes clear that you lost all sound in your attempts to do 5.1.

I know that ALSA can do surround sound, so you can follow my instructions to AshNZ in this thread to get your sound back.

Once you do that then you can refer to the ALSA documentation to get the surround sound enabled.

Good luck.

---

### Post by AshNZ on 2009-12-27
When I try to edit my menu.lst, it opens up completely blank and when I try to go to that folder manually, I can't find that file. I did some research and found out:

> **DO NOT EDIT THIS FILE** This is the main Grub 2 file. It "replaces" Grub Legacy's */boot/grub/menu.lst*.  This file contains the Grub menu instructions.  Unlike Grub Legacy's *menu.lst* file, ***grub.cfg* is NOT MEANT TO BE EDITED!!!**

[B]

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

and 
[/B]> Ubuntu 9.10 has moved on from Grub legacy to Grub2 (or grub-pc as the package is called).

Editing menu.lst is a thing of the past. Grub2 uses grub.cfg which is automatically generated from scripts, so if you edit it, it gets overwritten frequently.[http://ubuntuforums.org/showthread.php?t=1307775](http://ubuntuforums.org/showthread.php?t=1307775)

Is there any other way?

Meanwhile, I've managed to lock kernel versions but locking everything that started with linux- 

On another note, I got into this trouble while trying to get surround sound too, but I will start another thread on it once this is done.

---

### Post by fibercode on 2009-12-27
> **AshNZ said:**
> 
Is there any other way?


Yes, there is...

I still have grub (not grub 2) eventhough I upgraded to 9.10 as soon as it came out.

Anyway... In grub 2 instead of editing /etc/grub/menu.lst file you need to edit the /etc/default/grub file. So do:

```
sudo gedit /etc/default/grub
```

And change GRUB_DEFAULT=0 to GRUB_DEFAULT=2

Then do:

```
sudo update-grub
```

That should be it.

---

### Post by AshNZ on 2009-12-27
It worked like magic. Thanks a lot for your help. People like you are priceless in this forum!

---

### Post by lenkiatleong on 2009-12-28
> **fibercode said:**
> Lenkiatleong, 

Unfortunately I do not have much experience with surround sound on Linux. But from reading the other thread it becomes clear that you lost all sound in your attempts to do 5.1.

I know that ALSA can do surround sound, so you can follow my instructions to AshNZ in this thread to get your sound back.

Once you do that then you can refer to the ALSA documentation to get the surround sound enabled.

Good luck.

Not exactly, fibercode. I did not lose the sound. I could get only Stereo from the optical path. What i missed is the 5.1 from the optical cable. I am not sure if my Intel DP35DP mobo could support 5.1 or not. I reckon that i need 5.1 driver from Intel that supports Ubuntu 9.10.
Have you heard of anyone getting 5.1 using optical or hdmi cable?

---

### Post by fibercode on 2009-12-30
> **lenkiatleong said:**
> 
Have you heard of anyone getting 5.1 using optical or hdmi cable?

Unfortunately I am not an expert on surround sound in Ubuntu.

I am sure that are other people that would be more helpful on this subject.

---

### Post by lenkiatleong on 2009-12-30
> **fibercode said:**
> Unfortunately I am not an expert on surround sound in Ubuntu.

I am sure that are other people that would be more helpful on this subject.

Hi fibercode,
Thanks for replying. I had re-explored Ubuntu 9.04 and then 9.10 and i am very impressed by the technical advances Ubuntu had made. Very easy for layman to install and etc..

The last thing that i need to make it work is the audio bitstreaming from PC to AV via optical/hdmi path, i.e., for now, its 5.1 and for the future, high bit rate codecs, i.e., Dolby TrueHD and DTS HD MA. 

I managed (with the help of ubuntu forumers, of course) to configure most things i need for a HTPC and i was blown away. :-)

Nevertheless, if you come across any thread that managed to solve this problem, please post it in this thread too. I subscribed to this thread and will get email notification.

Happy New Year to you and all forumers and Cheers.

Len

---

