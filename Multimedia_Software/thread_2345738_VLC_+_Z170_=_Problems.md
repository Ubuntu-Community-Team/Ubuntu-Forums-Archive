---
title: "VLC + Z170 = Problems"
date: 2016-12-07
forum: Multimedia Software
---

### Post by jackbn on 2016-12-07
I installed Ubuntu 16.04 on a new system:
ASRock Extreme 7 Z170, i7-6770k, Samsung 850 Pro SSD, Intel CPU graphics, 32GB RAM

VLC misbehaves big time on this system: 
Strange artifacts
Minimizing the frame leaves the frameless picture same size, on the screen
Time for the cursor along the bottom is hidden
Freezes frequently when changing VLC settings
Etc. etc.

I re-installed the entire OS on the Z170, SEVERAL times -- same result.
ALSO, I have two Z170 systems (identical Motherboard, CPU & RAM) -- same result in both of these.

THEN, I moved the SSD (with the software built on a Z170) to an older Z87 i7-4770k system,
also using Intel CPU graphics, where VLC behaves properly.

It seems that VLC has not been updated for Z170s.
Any insights?

---

### Post by gordintoronto on 2016-12-07
There's a good chance that it's not actually a VLC problem. With the latest hardware, it's usually best to use the latest OS, which would be 16.10.

---

### Post by Keith_Helms on 2016-12-08
I just built a Z170 based system and had the same problems with VLC.  The solution was to download the latest Intel firmware for a Skylake processor along with a config file change. 

See here:
[https://github.com/linuxenko/ubuntu-skylake-i915-video-fix](https://github.com/linuxenko/ubuntu-skylake-i915-video-fix)

The firmware was on a site called 01.org/linuxgraphics.  The file I downloaded was sklgucver61.tar_1.bz2.

---

### Post by oldfred on 2016-12-08
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

I think one of the two files was already current.
And now I get errors, but they are the kbl or kabylake versions which I ignore.
Updater must not know Skylake from Kabylake?

---

### Post by Keith_Helms on 2016-12-08
> **oldfred said:**
> [https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

I think one of the two files was already current.
And now I get errors, but they are the kbl or kabylake versions which I ignore.
Updater must not know Skylake from Kabylake?

I just untarred the sklgucver61.tar_1.bz2 file and ran the install.sh from the directory created.  Here was the output:

```
keith@linux-corei7:~/download/Intel Graphics/skl_guc_ver6_1$ sudo bash ./install.sh --install
[sudo] password for keith: 
Success: firmware /lib/firmware/i915/skl_guc_ver6_1.bin has been installed!
Forcing initrd/initramfs update...
Trying to backup /boot/initrd.img-4.4.0-53-generic
Created a bakcup of your current initramfs /boot/initrd.img-4.4.0-53-generic.i915-fw.backup
Trying to update /boot/initrd.img-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Success: Please reboot your machine!
```

---

### Post by jackbn on 2016-12-10
Per the suggestion of gordintoronto, I now have 16.10. 

Now VLC works, with a couple big annoyances:

1) in File Manager, when I right click on a mp4 file, VLC is not listed, and the search does not find it.
   So, I must first open an empty VLC, then drag an MP4 file into it -- nuisance.
2) VLC will NOT run more than one instance, despite Playlist and Instances being set (two boxes empty) for multiple instances.

DOES ANYONE KNOW how to get VLC on the right-click list to open an MP4? Or how to run multiple instances with Z170 and 16.10?

FWIW, Windows is NOT installed on this system.

---

### Post by oldfred on 2016-12-10
Probably best to start a new thread with that in title, so those who may know an answer will see it. They may not be looking at this thread.

---

### Post by cariboo on 2016-12-14
Thread closed, as there is a new thread [here]("https://ubuntuforums.org/showthread.php?t=2346124").

---

