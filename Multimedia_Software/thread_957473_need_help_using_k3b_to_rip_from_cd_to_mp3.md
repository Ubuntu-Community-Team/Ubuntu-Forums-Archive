---
title: "need help using k3b to rip from cd to mp3"
date: 2008-10-24
forum: Multimedia Software
---

### Post by tinylasers on 2008-10-24
Hey everyone, I need a little help using k3b to rip cd to mp3. I don't like the clutter of applications piling up on my computer so I'm trying to find ONE good all around program to rip/copy/burn disks. K3B has done great on the last two counts but has been a total dud on the first. 

Right now if I want a music CD on my computer I'm using k3b to copy, soundkonverter to encode, and then finally editing tags in amarok. I know k3b should be fully capable of doing all of these (right?), but as of now, when I click on "Rip Audio CD" NOTHING happens. No error message, no strange behavior, no crash...just nothing. 

I already tried adjusting my settings according to [this thread]("http://ubuntuforums.org/showthread.php?t=446326"), but still nada.

:confused:

Any ideas? (Ones that don't involve using another program, I'm trying to do this **IN K3B**) 

thanks in advance....

---

### Post by cariboo on 2008-10-24
I understand what you're going through. I gave up on using k3b for ripping cds a long time ago. Grip is what you are looking for, you set quality and output file type, it automagically sets tags and is fully configurable. Sometimes the one app fits all just doesn't work the way the author expected in the real world.

Jim

---

### Post by jetpeach on 2008-11-08
it used to work fine for me, until intrepid. now it's erroring out... they are fully focused on the kde4 version of k3b right now, so i'm not sure when this will get fixed.

does anybody have a workaround? i know i have lame installed, it responds at the command line, but k3b errors saying, "Command failed: lame -h -tt ......[whole bunch of stuff for the mp3tags naming here]...." I can't 

All the log has is:
[System] K3b Version: 1.0.5
[System] KDE Version: 3.5.10
[System] QT Version:  3.3.8b
[System] Kernel:      2.6.27-7-generic
[Devices] ASUS DRW-1814BLT 1.04 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

I suppose if we ever want this working in Intrepid, we'd better make sure a bug is filed in launchpad. Would be nice to see some posts from others with this problem as well though...

---

