---
title: "Mubuntu Poll #3 - What kernel are you using?"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-09-27
What kernel are you currently using **on the system that you use for music-making**?

---

### Post by maniacmusician on 2006-09-29
I don't currently have a system for music making...I dont have the hardware to make this possible. I could probably recompile or self-compile with the help of a tutorial. I want to explore making music in linux right now, though after reading a lot of posts i'm getting the feeling that it could be a pain. I dont mind fiddling a bit though.

---

### Post by ttoine on 2006-10-04
What about the possibility to have a real time patched kernell ? is it really "unmakable" ??

---

### Post by FrostFire on 2006-10-05
Actually I use an older dapper kernel for music (2.6.15.23).
This one doesn't complain about the system timer being to small.

---

### Post by dolson on 2006-10-05
ttoine, the poll isn't about what the possibilities of Mubuntu are, it is about what people are using right now. So if you are using a realtime patched kernel, then you would have selected the poll option "Self-compiled kernel."


FrostFire, that can be fixed.. Check the Ubuntu Studio wiki... Specifically here: [http://ubuntustudio.com/wiki/index.php/Studio_Preparation#Timer_Resolution](http://ubuntustudio.com/wiki/index.php/Studio_Preparation#Timer_Resolution)

---

### Post by xyz on 2006-10-10
Linux luser 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
It would not be honest to say I'm using this kernel to make music; I'm using it to learn how to make music with Linux.

---

### Post by christhemonkey on 2006-10-10
Im using a self compiled 2.6.17-686-rt kernel.


And the nvidia beta drivers.

Gives me very good manageable latencies. (although rarely get time atm to do anything useful with them)

---

### Post by nilux on 2006-11-08
Voted for the ubuntu default kernel.
I'm using edgy 32 on my amd64 (3700+), and it's not comfortable for working with ardour (0.99, from the ubuntu repository). When working on a 10 track project, the sound gets crap until i don't use 1024 samples latency, which is not suited for recording..

---

### Post by Sandsound on 2006-11-30
Real time patched kernel is a MUST !

Currently running Edgy and the kernel that came with it and everything but music-making is working.
Sadly enough I don't know enough about kernel-compilation to risk patching it myself.

Can hardly wait until Mubuntu is released :-)

---

### Post by lowracer on 2006-11-30
How are we defining music-making?  I'm using Azureus to download boatloads of legal music files, and Amarok to play those same files.  I use the standard kernel that ships with Ubuntu.

---

### Post by Rumpanzle on 2006-11-30
Music making is the use of Hardware/Software Synthesizer/Effectprozessor and Sampleplayer over a Protocol, mainly MIDI.

---

### Post by uga2 on 2006-12-07
Why is the kernel poll asking for the kernel I'm using instead of which kernel should be used? I'd be glad to switch to any kernel that better supports real-time recording.

As of now the default kernel is really bad. Recording the second track in Audacity with the first playing along is almost impossible (but works sometimes). The second track sounds like it was pitched down 4 octaves. Although this also happens in WinXP sometimes but much more rarely.

---

### Post by October on 2006-12-08
Which kernel?  That's easy :)

> overlord@biggun2:~$ ./infobash -v2
Host/Kernel/OS "biggun2" running Linux 2.6.19-7-generic i686 [ Ubuntu feisty (development branch) ]
CPU Info       AMD Athlon 64 3500+ clocked at [ 2211.357 MHz ]
Videocard      nVidia G70 [GeForce 7800 GT]  X.Org 7.1.1  [ 2560x1024 @100hz ]
Network cards  nVidia CK804 Ethernet Controller, at port: b000
Processes 110 | Uptime 1day | Memory 1852.15/2027.19MB | HDD ST380013A Size 80GB (3%used) | GLX Renderer GeForce 7800 GT/PCI/SSE2/3DNOW! | GLX Version 2.1.0 NVIDIA 96.29 | Client Shell | Infobash v2.51

Works suprising well too, out of the box!

> 14:42:30.330 JACK is starting...
14:42:30.330 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p128 -n2 -S
14:42:30.349 JACK was started with PID=23775 (0x5cdf).
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback

This is giving me a DSP load of 1.2% in Audacity and a latency of only 5.8ms running on an on-board sound chip (nforce4 AC97 Realtek ALC850).  I recorded a single 16bit 44100 Hz sample of Hydrogen playing and another one of the Audacious media player via it's Jack plugin at the same time with ZERO xruns. 

The only xruns I've had is when my opengl screensaver kicked in during a break for food ;)

> overlord@biggun2:/boot$ cat config*|grep PREEMPT
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set
CONFIG_PREEMPT_BKL=y
overlord@biggun2:/boot$ cat config*|grep HZ
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
# CONFIG_HZ_1000 is not set
CONFIG_HZ=250
CONFIG_MACHZ_WDT=m


So it looks like it could obviously use some improvement but still quite impressive for a "generic" kernel!

---

### Post by klss on 2007-01-04
I just installed 2.6.19.1-rt15.
I think RT-preemption is a must for serious mutimedia applications! 
Latencies of < 1,5ms should be the general goal.

Cheers

---

### Post by basslord on 2007-01-18
I'm using a 2.6.19-rt12 in Edgy. rt15 caused some trouble.
Like me there are many people I know who are kinda disappointed about the fact that Edgy doesn't ship with the Preemptible Kernel as Dapper did.

---

### Post by hilltop_yodeler on 2007-01-19
I am running the standard Edgy 2.6.17-10 kernel in Xubuntu on three different machines, and I'd have to say that audio recording does not work the same on all three machines.  On the machine that I specifically built up for recording, Audacity locks up once I add a second track.  I didn't do anything different during the build of this machine than on the other two.  Still can't seem to get midi to function even after obtaining the various libs.  Not sure that I can attribute any of this to the kernel or not --- it's most likely due to my own ignorance.
:D

---

### Post by unfnknblvbl on 2007-01-21
I use Windows if I want to record anything. Trying to record anything in Audacity under Dapper just makes me want to cry - everything just sounds sort of metallic, and lower in pitch than what I was playing. I'm a complete noob when it comes to Linux, so if there comes a decision to be made as to which kernel to use, I'm all in favour of using whichever one will rectify this issue. Hell, even one that gets automatically compiled specifically for your system during the install process would be nice.

---

### Post by mattl on 2007-01-21
As long as there's a choice for me to use a kernel without restricted modules and binary blobs, I'll be happy.

---

