---
title: "Complicated Microslow Media Center to Mythbutu"
date: 2009-06-30
forum: Mythbuntu
---

### Post by dkhajavi on 2009-06-30
Guys I am new to Mythbuntu but am anxious to get rid of my dual boot MCE/Ubuntu 9.10 and go to a full Mythbunto 9.04.

My system is a dedicated Media Center:
P4 3.8
6gigs RAM
Primary IDE 80GB Raptor 10K RPM Drive
Sec 1 IDE 300GB Drive (All DVDs 90% full)
Sec 2 IDE 250GB Drive (DVDs, Music, Photos 80% full)
Water cooling with external radiator (100% inaudible)
Nvidia 7900GT Video
Haupage PVR 150 TV
6.1 surround with Digital Optical feed

I tried to install MythTV into Ubuntu but was not able to get all the drives working.  I am guessing MythTV likes one big drive?  Being unframiliar can you guys suggest how to properly make this system work with multiple drives and such?  

The 80GB Raptor is for the operating system and software only for speed reasons and size was not an issue for that reason but it seems MythTV is only able to allocate what is available on the same drive it is installed?  Is that right?

Thanks in advance!!

---

### Post by crez79 on 2009-06-30
The way windows handles drives and the way linux handles drives are very different. Windows assigns drive letter and name to each drive and does so automatically. Linux "mounts" hard drives in a folder, but it never assigns drive letters. There are some [good guides to mounting drives ]("http://www.psychocats.net/ubuntu/mountlinux")that are more accurate and understandable than I could be. Also, I am assuming they are NTFS format, which isn't necessarily a problem, but is not native to ubuntu. I would guess that they wern't automatically mounted because they are NTFS and I am not positive it is able to it by default. You may also have some luck with this [GUI]("http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14") until you get used to manually editing config files.

---

### Post by laffinet on 2009-06-30
> **dkhajavi said:**
> 
The 80GB Raptor is for the operating system and software only for speed reasons and size was not an issue for that reason but it seems MythTV is only able to allocate what is available on the same drive it is installed?  Is that right?

Thanks in advance!!

No, mythtv can work with multiple drives. 
Like crez79 said, you have to mount the drives first. Google for "ntsc and ubuntu" and "fstab" (excellent guide [here]("http://ubuntuforums.org/showthread.php?t=283131")) and "mounting drives".

Once you've done that and you can see the drives in Ubuntu you have to tell mythtv to use them for videos and recordings (bit of info in this [thread]("http://ubuntuforums.org/showthread.php?t=1046712").

---

