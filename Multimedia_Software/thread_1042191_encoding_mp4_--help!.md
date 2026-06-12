---
title: "encoding mp4 --help!"
date: 2009-01-17
forum: Multimedia Software
---

### Post by Quiane on 2009-01-17
OKay, i've been though every guide possible...i've posted a few times and followed directions.  
RIght now i'm running 8.04, and still no encoding joy.  I"ve tried handbreak, winff, and many others (including command line) to encode for my ipod.  It just doesn't want to work.  THinliquidfilm wont work due to not being linked with bash (i've followed their terminal lines to "fix" this, but it doesn't work, and i've had to boot in and replace my bash/dash and sh files from the disk.)  

anyway, i'm getting off topic...when i try to configure my x264 this is the output i get, and i think this may be the problem, but i dont know how to configure it properly.


[PHP]mark@mark-desktop:~/x264$ ./configure
Platform:   X86
System:     LINUX
asm:        yes
avis input: no
mp4 output: no
pthread:    yes
debug:      no
gprof:      no
PIC:        no
shared:     no
visualize:  no

You can run 'make' or 'make fprofiled' now.[/PHP]

So, is the fact that avis and mp4 output are set to no a problem, or am i barking up the wrong tree?

---

### Post by shirilover on 2009-01-17
You will not be able to use avis input as AviSynth does not run in linux.
Mp4 output requires libgpac-dev to be installed.
You may want to try using avidemux instead, it has an auto setting for ipods.

---

### Post by andrew.46 on 2009-01-18
Hi,

This might be an excellent time to head over to:

HOWTO: Compile the latest ffmpeg and x264 from source
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

as the newest ffmpeg now sports a couple of presets aimed specifically at iPods:

[http://svn.mplayerhq.hu/ffmpeg?view=rev&revision=16585](http://svn.mplayerhq.hu/ffmpeg?view=rev&revision=16585)

Commandline only though so if that is a problem perhaps shirilover's suggestion would be more useful to you?

Andrew

---

