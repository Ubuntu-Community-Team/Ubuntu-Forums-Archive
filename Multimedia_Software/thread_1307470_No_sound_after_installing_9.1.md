---
title: "No sound after installing 9.1"
date: 2009-10-31
forum: Multimedia Software
---

### Post by spinfactor on 2009-10-31
Hi all, 

Just installed Ubuntu 9.1 via wubi. I have no sound. All else appears to be fine. I had 9.04 and it was fine. I have tried installing once again and the same thing happen, no sound. 

Also When I restart and go to Vista I will also have no sound unless I do a complete shutdown, then I will have sound in Vista but not Ubuntu.

Anyone have any ideas here?

Thanks in advance

---

### Post by spinfactor on 2009-10-31
Bump bump, no one has an idea eh

---

### Post by markackerman8@gmail.com on 2009-11-01
Hey Guys I am having real problems with sound too after a clean install of karmic and with grug2. ARghhhhhh I have looked everywhere and tried all the troubleshooting guides with no success double arghhhhh

Everything that points to an output device only shows the"dummy" (WITH PADEVICECHOOSER or system/preferences/sound_preferences),

but when I:

ack@Titan:~$ gnome-alsamixer ... it shows "Realtec ALC268"

or
ack@Titan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 0/1
Subdevice #0: subdevic

or
ack@Titan:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Hewlett-Packard Company Device 30cc
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

ANY SUGGESTIONS?????

---

### Post by lindsay7 on 2009-11-01
Try looking at System/preferences/sound. Then look at sound effects and input.  Make sure that the mute button is unclicked.

---

### Post by spinfactor on 2009-11-01
thanks for the reply, did all that, no luck. I also have been combing the planet with no bites or luck.

---

### Post by spinfactor on 2009-11-01
UPDATE:

Haven't been able to find a solution, this really sucks for sure. I can tell you that this time when I booted I did get some sound just before login screen, you know the little and quick drum tapping. But thats it, nothing more.

Hopefull I will stumble upon this soon.

---

### Post by kicksock on 2009-11-03
I had a similar issue which I fixed by right clicking on the audio icon in the upper panel and editing "Sound Preferences".  It seemed that on the second boot of 9.1, all the output volume and alert volume sliders were set to minimum.  Also the "Sound Theme" drop down showed null.  I had to reset the sliders to max and the Theme to Ubuntu.  My memory is dim but I think I had to repeat this a few times because the order seemed to make a difference.  After that, I had sound on boot up.

---

### Post by p110011 on 2009-11-03
Hello, I upgraded from 9.04-9.10 and it left me with a Jaunty Kernel-2.6.28. After removal and installing 2.6.31-14 my sound card is seen by Alsa. Or PulseAudeo rather.

It might be this for some.....:p

---

### Post by jcandali on 2009-11-03
I had this problem as well though not at first.  I didn't notice I lost audio output till the day after I installed 9.1.  As it turns out, the last thing I did before I shut my laptop down was to activate the proprietary driver for my internal modem.

Disabling the driver (System -> Hardware Drivers) brought my sound back from the dead.

Here's what I've got for audio in my laptop:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: TWINHEAD INTERNATIONAL Corp Device a00c
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I hope that helps.

EDIT:

I noticed this little tidbit in the description of the driver for the software modem:
> 
It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa supportand intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

Perhaps the interaction between the modem software and ALSA isn't quite right.

---

### Post by yyyoshiii on 2009-11-06
i installed 9.1 via wubi on an xp, and have no sound whatsoever.
its really pissing me off

i downloaded pulse audio with no luck. 

i believe i have a conexant high def audio soundcard

no, its not muted.
its just not working : (

---

### Post by spinfactor on 2009-11-07
This really blows

---

### Post by spinfactor on 2009-11-09
It's been 3 updates now and still no sound. Is it always like this with Linux? I mean if this happened in WIndows it would be World Wide head lines news, I have seens plenty of people here with the same issue. I just installed  Ubuntu 9.1 on another one of my machines with the same problem. No Sound!

---

### Post by ennoil on 2009-11-10
Funny thing is, I have a laptop (Dell Latitude D630) with 2 hard drives.  One drive had 9.04 running and I did a dist-upgrade with no sound problems. The other drive I did a fresh install of 9.10 and no sound. lshw, lspci, etc all show the sound card identically but I still get no sound on the freshly installed one.
I also did a fresh install on my son's laptop (Latitude D600) and he has no sound either. He is in the UK and I am in the US at the moment so I would hate to have to talk him through another Ubuntu install (downgrading to 9.04) just so he can get sound to work...
John

---

### Post by mjm1231 on 2009-11-12
Same problem here. Trying to breathe some life into an old Compaq EVO laptop with a dead CD drive, so installed xubuntu via wubi. Intel 82801CA/CAM AC'97 shows in lspci and lshw, no proprietary drivers loaded. The sound icon up in the system tray is covered with the blue sound wave bars, but no sound. Would love an answer or fix for this.

---

### Post by bobbiescap on 2009-11-13
What happened to me was that during the upgrade I was presented with several Grub options and I chose to keep the original menu.lst which meant that I was booting into the old kernel. Please remember that the numbers below may not necessarily reflect yours, also I am running 64 bit, which may affect things, but I doubt it.

To fix this I determined the running kernel:

```
uname -r
```

Output:

```
uname -r
2.6.28-16-generic

```

Then I checked the installed kernels:

```
dpkg --list | grep linux-image

```

Output:

```
 dpkg --list | grep linux-image
rc  linux-image-2.6.28-11-generic              2.6.28-11.42                               Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-13-generic              2.6.28-13.45                               Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-14-generic              2.6.28-14.47                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-15-generic              2.6.28-15.52                               Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-16-generic              2.6.28-16.55                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.31-14-generic              2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                        2.6.31.14.27                               Generic Linux kernel image

```

Then I backed up the menu.lst file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

```

Then edited it:

```
sudo gedit /boot/grub/menu.lst
```

When the editor opened I copied the first two paragraphs under "## ## End Default Options ##" and pasted them above the original, making sure that spacing was consistent; then replaced the kernel information in the first two sections so that the new kernel was listed, as in red below, if your kernel is a different version to mine then use your settings. 

Gedit has a replace option that will automate this process to a certain extent if you are careful with it.

Copying the first two paragraphs and modifying the copy, rather than the original listing leaves the Jaunty kernel as an option if problems are encountered. 


```
## ## End Default Options ##


title		Ubuntu [COLOR="Red"]9.10[/COLOR], kernel [COLOR="Red"]2.6.31-14[/COLOR]-generic
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.31-14[/COLOR]-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro quiet splash 
initrd		/boot/initrd.img-[COLOR="Red"]2.6.31-14[/COLOR]-generic
quiet

title		Ubuntu [COLOR="Red"]9.10[/COLOR], kernel [COLOR="Red"]2.6.31-14[/COLOR]-generic (recovery mode)
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.31-14[/COLOR]-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro  single
initrd		/boot/initrd.img-[COLOR="Red"]2.6.31-14[/COLOR]-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I rebooted and checked the running kernel with "uname -r" and found that I was now using the official Karmic kernel, full of optimism I tried an mp3, only to find that I had forgotten to turn the speakers down and was met by a musical roar! Moral is: "Turn the volume down first!"

Hope this helps somebody, I am no expert but it got me out of strife.

---

### Post by rtfm on 2009-11-14
I had the same issue on a clean install, no sound...

Like others my sound was returned by going to System/Administration/Hardware Drivers and removing the Software Modem Driver that I had "activated" a few days earlier.

Hope this helps.

---

### Post by rdogs on 2009-12-10
I had the same no sound problem with 9.1 after I upgraded using Ubuntu update. 

For me, the problem was solved using a 9.1 CD and doing a new install. As we all know, it's a PIA to start over, but it solved my problem.:p rdogs:

---

### Post by Zibodiz on 2009-12-19
> **bobbiescap said:**
> What happened to me was that during the upgrade I was presented with several Grub options and I chose to keep the original menu.lst which meant that I was booting into the old kernel. Please remember that the numbers below may not necessarily reflect yours, also I am running 64 bit, which may affect things, but I doubt it.

To fix this I determined the running kernel:

```
uname -r
```

Output:

```
uname -r
2.6.28-16-generic

```

Then I checked the installed kernels:

```
dpkg --list | grep linux-image

```

Output:

```
 dpkg --list | grep linux-image
rc  linux-image-2.6.28-11-generic              2.6.28-11.42                               Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-13-generic              2.6.28-13.45                               Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-14-generic              2.6.28-14.47                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-15-generic              2.6.28-15.52                               Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-16-generic              2.6.28-16.55                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.31-14-generic              2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                        2.6.31.14.27                               Generic Linux kernel image

```

Then I backed up the menu.lst file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

```

Then edited it:

```
sudo gedit /boot/grub/menu.lst
```

When the editor opened I copied the first two paragraphs under "## ## End Default Options ##" and pasted them above the original, making sure that spacing was consistent; then replaced the kernel information in the first two sections so that the new kernel was listed, as in red below, if your kernel is a different version to mine then use your settings. 

Gedit has a replace option that will automate this process to a certain extent if you are careful with it.

Copying the first two paragraphs and modifying the copy, rather than the original listing leaves the Jaunty kernel as an option if problems are encountered. 


```
## ## End Default Options ##


title		Ubuntu [COLOR="Red"]9.10[/COLOR], kernel [COLOR="Red"]2.6.31-14[/COLOR]-generic
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.31-14[/COLOR]-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro quiet splash 
initrd		/boot/initrd.img-[COLOR="Red"]2.6.31-14[/COLOR]-generic
quiet

title		Ubuntu [COLOR="Red"]9.10[/COLOR], kernel [COLOR="Red"]2.6.31-14[/COLOR]-generic (recovery mode)
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.31-14[/COLOR]-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro  single
initrd		/boot/initrd.img-[COLOR="Red"]2.6.31-14[/COLOR]-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		107c0df7-207a-4df9-9e8a-7d4d74632d2f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I rebooted and checked the running kernel with "uname -r" and found that I was now using the official Karmic kernel, full of optimism I tried an mp3, only to find that I had forgotten to turn the speakers down and was met by a musical roar! Moral is: "Turn the volume down first!"

Hope this helps somebody, I am no expert but it got me out of strife.

bobbiescap, you are a genius.  Just a note, you only have to change the lines:
```

kernel		/boot/vmlinuz-[COLOR="Red"]2.6.31-14[/COLOR]-generic root=UUID=107c0df7-207a-4df9-9e8a-7d4d74632d2f ro  single
initrd		/boot/initrd.img-[COLOR="Red"]2.6.31-14[/COLOR]-generic
```
Also, I just changed it on the main startup option -- that way if something goes horribly wrong, you can still startup using the old kernel with one of the other options.
But anyway, that was totally the same mistake I made -- fixing it resolved other issues, too.  Thanks! :KS

---

### Post by UbtuntuFan on 2010-01-19
Thanks jcandali !!!

I also lost audio on installation of a modem driver, but didn't realize that was the trigger until I saw your post.

Removed the modem driver and rebooted - got audio back with no further action required.

Your post saved me a lot of time and troubleshooting. Thanks again!



> **jcandali said:**
> I had this problem as well though not at first.  I didn't notice I lost audio output till the day after I installed 9.1.  As it turns out, the last thing I did before I shut my laptop down was to activate the proprietary driver for my internal modem.

Disabling the driver (System -> Hardware Drivers) brought my sound back from the dead.

Here's what I've got for audio in my laptop:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: TWINHEAD INTERNATIONAL Corp Device a00c
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I hope that helps.

EDIT:

I noticed this little tidbit in the description of the driver for the software modem:


Perhaps the interaction between the modem software and ALSA isn't quite right.

---

### Post by ramblinche81 on 2010-01-19
I had similar experiences and for what it is worth....try VLC media player....
 
my 9.10 system lacked sound until I applied fixes in Comprehensive Sound Problem solving. Then I had sound from CD device and files on hard drive, (music) and no sound from DVD play. I did have full video functionality. I have a CD/DVD combo player and the device is straightwired to onboard 7.1 sound. ASUS m2r32-mvp and AMD6000 which is ATI SBxOO chipset/drivers  sound module is snd-hda-intel
 
I tried ALL the various patches, fixes, sudo this and that, edit this and that etc etc etc. which eventually gave me music based sound, but no DVD sourced sound.
 
At one point I lost music sound until I re-installed all snd, device driver and ALSA related modules from scratch.
 
Then, on a whim, I just right clicked a DVD video file in the combo drive and chose open with (Movie Player) and there was sound. Also works if I open with (VLC).
 
If I go back to the Applications menu and open Movie Player and choose to play the disk and follow the on screen menu typical of DVD, no sound.
 
Applications - VLC media player does work with sound.
 
In summary, 
[INDENT]opening app MoviePlayer and playing DVD traditional method is no sound.
 
Right click video file and choose open with (MovPlay or VLC) and I have sound.
 
opening VLC media player and playing DVD traditional method with normal on screen menus I have sound.
 
[/INDENT]My otherwise limited knowledge tells me the problem is in MoviePlayer setup or application loading since VLC works and Movie Player works when front loading app is bypassed. The problem isn't sound, it is how MoviePlayer loads to play sound.
 
So many of the threads reference no sound in total which is different than no sound when loading app first before file.
 
I will use VLC to play DVD until something fails to work. hope the above helps somebody.

---

