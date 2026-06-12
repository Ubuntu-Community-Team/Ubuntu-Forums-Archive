---
title: "API mismatch after installing nVidia drivers"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by runesvend on 2007-05-04
I just got a new video card from a friend so I was eager to pop it in and give it a go. So that's what I did and then I searched on google and found the following guide to activating 3D acceleration in Ubuntu: [http://linux.about.com/od/ubuntu_doc/a/ubudg19t5.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg19t5.htm)

I skipped step 1 as my newer card wasn't in the list and did what it said from there on. After running the *sudo nvidia-glx-config enable* command I got an error saying something didn't work properly (I can't remember the specific output) and it said to either change the Driver string containing "nvidia" to "nv" under my video card in my **/etc/X11/xorg.conf** file or to run a command provided by the error message containing something about an MD5 checksum. I did both and ran the command again and it succeeded saying it had made a backup of the xorg.conf file in some directory.

When I restart my computer an error appears saying it wasn't possible to boot into X. I then look at the error reported which says that no device matched the driver for "NVIDIA" as far as I recall. I then booted into my Live CD and put the backed up xorg.conf file back in my **/etc/X11** folder thinking this should do the trick but when I start my computer again the error about not being able to start X appears again but this time the error is:

API mismatch: NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9631

How come reverting back to the backed up xorg.conf didn't solve my problems? Has the installation changed other files or how do I get back to my working configuration?

Thanks in advance!

---

### Post by Rictus on 2007-05-05
Hmmm, same problem here trying to install 8800 gts, following tutorial. Nvidia kernel is version 9755 but x module is version 9631.
 
Well now I know why. If you try to run desktop effects it will screw up your drivers fro some reason.
[http://ubuntuforums.org/showthread.php?t=431019&highlight=api+mismatch+nvidia+x](http://ubuntuforums.org/showthread.php?t=431019&highlight=api+mismatch+nvidia+x)

---

