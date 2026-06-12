---
title: "Nvidia issue mx400"
date: 2009-11-02
forum: Mythbuntu
---

### Post by shocksafe on 2009-11-02
I upgraded from 9.04 to 9.10 and pretty much everything was perfect no graphics issues.

I then did a fresh install of 9.10 on the same machine (combined backend/frontend) and everytime I booted the xserver would crash and take me back to a terminal login with the screen flashing/stuttering.

I couldn't log in as input was stuttering as well so to type a letter in I had to hold it for a second or so. Fine for username but with password I had no idea if I held it long enough or too long (either no character typed or 2 characters typed)

Anyway I booted into recovery mode and changed my xorg.conf to "nv" driver.

I tried the 185 driver and then the 173 driver. Same issue.

Anyone have any ideas?

---

### Post by lightpriest on 2009-11-03
I don't like saying that but I have the same problem :)

I have MX400 as-well and I've upgraded from 9.04 to 9.10.
I'm not using any manually compiled X nor kernel/modules. Packages only.

I can load gdm with the proprietary nvidia drivers. I get to recovery console and type: ```
sudo gdm
```
It works.

This is the log when X crashes:
```
..
..
..
(II) resource ranges after preInit:
  [0] -1  0 0xffffffff - 0xffffffff (0x1) MX[B]
  [1] -1  0 0x000f0000 - 0x000fffff (0x10000) MX[B]
  [2] -1  0 0x000c0000 - 0x000effff (0x30000) MX[B]
  [3] -1  0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
  [4] -1  0 0xffffffff - 0xffffffff (0x1) MX[B]
  [5] -1  0 0x000f0000 - 0x000fffff (0x10000) MX[B]
  [6] -1  0 0x000c0000 - 0x000effff (0x30000) MX[B]
  [7] -1  0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
  [8] -1  0 0xffffffff - 0xffffffff (0x1) MX[B]
  [9] -1  0 0x000f0000 - 0x000fffff (0x10000) MX[B]
  [10] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
  [11] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
  [12] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
  [13] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
  [14] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
  [15] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
  [16] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
  [17] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
  [18] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
  [19] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
  [20] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
  [21] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
  [22] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
  [23] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
  [24] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
  [25] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
  [26] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
  [27] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
  [28] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
  [29] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xc87400]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
```

This is the log when everything is fine, I've included only the part that was supposed to be instead of the Backtrace.
```

  [27] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
  [28] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
  [29] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled

```

---

### Post by shocksafe on 2009-11-03
OK I have gotten this issue fixed on my machine. Please read all of this before trying anything.

I did some research based on your logs and found it was likely caused by an xorg/driver conflict or overlap.

[http://www.linuxquestions.org/questions/ubuntu-63/x-server-wont-load-after-8.10-upgrade.-680377/](http://www.linuxquestions.org/questions/ubuntu-63/x-server-wont-load-after-8.10-upgrade.-680377/)

So, as I'm kind of only testing atm and didn't have a lot to lose I started messing around.
I wouldn't go through all of what I did but at least it shows where the issue lies (or narrows it down at least).

Here's what I did (based on the above post, hearsay, and little actual knowledge)-

#sudo apt-get remove --purge nvidia*
#sudo apt-get remove --purge xorg*
(drastic - yes)

#sudo apt-get install xserver-xorg-video-nvidia
#sudo /etc/init.d/gdm restart
(I was hopeing this would install everything again through dependencies - wrong)

#sudo apt-get install xubuntu-desktop
#sudo /etc/init.d/gdm restart
(don't do this, I was trying to get xfce back up and didn't realise there was a mythbuntu-desktop)

#sudo apt-get remove xubuntu-desktop

#sudo apt-get install mythbuntu-desktop
#sudo /etc/init.d/gdm restart
(this didn't seem to affect my data ie all my recordings.videos, recording rules etc are still there)

then went to synaptic package manager and installed the nvidia-glx-173 driver.
then to Mythbuntu control center ->Graphics Drivers ->Launch Restricted Drivers Manager.

I had the install disk in at this point and had cdrom........ selected in synaptic repositories so not sure exactly what happened here but......

The Restricted Drivers manager searched and came up with nvidia-96 driver as recommended so I clicked ok, rebooted the machine, copied over my old working xorg.conf and BAM all good.

So I'm not sure now if it was just the new 96 driver. I would try this first - nvidia-96-kernel-source.
Nothing to lose there really just roll back or disable in xorg.conf if it fails.
If that doesn't work someone a bit more knowledgable than I will hopefully chime in and give you the correct way to reinstall xorg-xserver as I presume this is the issue if it's not just the nvidia driver.

Hope that wasn't too confusing.

Cheers

---

### Post by NickPrecision on 2009-11-04
I had a similar problem with my MX440. I did a clean install of 9.10 and X came up flashing and unable to take keystrokes like others have said. I logged in via SSH and used apt to remove nvidia-glx and rebooted, it came up then with the nonrestricted video drivers and "worked" except mythfrontend would segfault when playing a recorded show. I could play AVI's so I just did that for a few days. Tonight I reinstalled the latest restricted nvidia driver and it appears everything is working. I am not sure if they updated the nvidia restricted driver package in those few days or if something else changed (since I didn't have it installed I can't tell if it updated or just installed the old version again), but I can playback TV and AVIs without segfaults now.

---

### Post by 365nice on 2009-11-04
I think I had similar problems to you guys - I was installing on a new machine and during the installation I selected to use the NVidia drivers and then got the flashing screen with the "mythbuntu stopping ntp server" message and the login prompt.

This had all worked in previous release candidates and betas.

However I wend back and reinstalled but this time went with the open drivers (not nVidia) and it worked fine. Once I was logged in, I then went back and enabled the restricted driver and when I restarted it also worked fine.

Hopefully this helps with others following along.

Tim

---

### Post by lightpriest on 2009-11-04
I wouldn't take drastic measures like uninstalling with * and reinstalling since they are binary files and they'll work the same after you've re-installed.

According to what you all say (installing a different package then reinstalling 96) it sounds like there's something faulty with the post scripts of the 96 package (or related packages).
This problem probably doesn't exist in the open source drivers, which (probably) fixes it when you install the 96 package.

365nice, could you post you xorg.conf here?

Perhaps a directive in xorg.conf?

---

### Post by lightpriest on 2009-11-26
Well, if anyone is looking for a solution, here's one you can try.

I've noticed that I get a "conflicting memory types" error in the syslog (for every time Xorg tried to load, ofcourse).

I've cancelled PAT on the boot by adding "nopat" to the kernel boot line.
Now everything seems to be working fine.

If you do try this, first check that you have "conflicting memory types" error in the log.
Then change once with the boot, to see that it loads fine and that everything is working aswell.
After that, change the boot lines in grub's configuration (don't forget the update-grub script line: "# defoptions=..." so that future kernel upgrades won't break the system)

And just for reference: [http://cateee.net/lkddb/web-lkddb/X86_PAT.html](http://cateee.net/lkddb/web-lkddb/X86_PAT.html)
> Say N here if you see bootup problems (boot crash, boot hang, spontaneous reboots) or **a non-working video driver**.

---

