---
title: "updated 10.4 &amp; it stopped detecting nvidia sound &quot;card&quot;"
date: 2010-10-17
forum: Multimedia Software
---

### Post by jtwdyp on 2010-10-17
Hello, I'm a multi-Linux/multi-boot guy currently running Xubuntu, PCLinuxOS, Arch & OpenSuSE. All of which needed me to use the proprietary Nvidia drivers (the versions available from each distro's repositories) Once that was done, only Xubuntu gave me any trouble with sound...

I acquired this used replacement desktop back in June 2010 It's an HP Pavilion a1410n with on-board Nividia GeForce 6150 LE.

In July I installed Xubuntu. (Though as with all my Linux, XFCE is only used as a backup to my preferred e17 desktop environment.) 

Back then I had some sound troubles that, once I ditched PulseAudio in favor of Alsa turned out to be just a permission issue.

Some nice person on the Xubuntu users mailing list suggested I check out the output of:

 $ ls -al /dev | grep audio

Which was:

```
crw-rw----+  1 root   audio    14,  12 2010-07-23 23:03 adsp
crw-rw----+  1 root   audio    14,   4 2010-07-23 23:03 audio
crw-rw----+  1 root   audio    14,   3 2010-07-23 23:03 dsp
crw-rw----+  1 root   audio    14,   0 2010-07-23 23:03 mixer
crw-rw----+  1 root   audio    14,   1 2010-07-23 23:03 sequencer
crw-rw----+  1 root   audio    14,   8 2010-07-23 23:03 sequencer2
```

And once I added user rw permissions to those devices the sound worked until I recently upgraded via synaptic. Including: vmlinuz-2.6.32-25-generic.  I didn't notice the new sound problem right away because I was busy debugging some other issues with my OpenSuSE installation, and was spending most of my limited 'puter time there... Last night however, I booted into Lucid and ran startx only to discover I couldn't play my music files anymore...

Here is some current snippage from a root shell:

```
UnderTree =-> 
UnderTree =-> ls -al /dev | grep audio
UnderTree =-> 
UnderTree =-> aplay -l
aplay: device_list:223: no soundcards found...
UnderTree =-> 
```

The audio devices were there before I let synaptic apply all upgrades...  Alsa USED to work. Would anyone have a clue what went wrong? Or more importantly how to resolve it? 

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by jtwdyp on 2010-10-21
And now I feel STUPID !!!

For assorted reasons I maintain a manualy edited classic grub boot partition.
I let each linux install their grub to their root partition and include chainloader entries for each of those. But where ever possible, I also include direct boot entries in _MY_ grub And since I used ext3 rather than ext4, that includes Xubuntu. This means that every time there is a kernel update I need to manually update my grub. And evidently I was interrupted in that process because I'd updated the title line, but failed to make the matching changes in my kernel & initrd lines... So when I got around to booting Xubuntu again, my grub menu said I was booting the newer kernel, but wasn't... My Bad!!!

The surprising thing is that the only thing that stopped working in the 2.6.32-24 kernel when the system was updated for 2.6.32-25 was the sound.

Anyway, I fixed my grub entries and the problem went away.

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

