---
title: "Realplayer?"
date: 2008-11-20
forum: Multimedia Software
---

### Post by chrispche on 2008-11-20
I'm trying to play the first file here [http://trashotron.com/agony/indexes/audio_interview_index.htm](http://trashotron.com/agony/indexes/audio_interview_index.htm) the Alastair Reynolds one. However it refuses to play on Movie Player. Do I need to install Realplayer? Is the file corrupt? If I do need to install it how do you. I'm using Ubuntu 8.04.

Thanks in advance.

---

### Post by wolfen69 on 2008-11-20
go [here]("http://www.real.com/linux/") and download the realplayer (.deb towards the bottom of the page) for linux. however, the first couple of links on that page seem corrupt and won't work. most others do though.

---

### Post by Bablefish on 2008-11-20
I have a solution just download the bin and follow these directions

[https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInst](https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInst)

---

### Post by chrispche on 2008-11-20
It's OK, the file appears corrupt. I have emailed the site. I used the *.deb file to install Realplayer.

Thanks for the advice though.

---

### Post by pastalavista on 2008-11-20
Install [Mplayer]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html"). It can play anything. wmv, avi, rm, mov, mpeg(2-3-4), flv, you name it. one all-purpose player.

---

### Post by tgalati4 on 2008-11-20
I got it to work with mplayer (Linux Mint Darnya, Gutsy):

mplayer [http://trashotron.com/agony/audio/alastair_reynolds.rm](http://trashotron.com/agony/audio/alastair_reynolds.rm)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://trashotron.com/agony/audio/alastair_reynolds.rm](http://trashotron.com/agony/audio/alastair_reynolds.rm).
Resolving trashotron.com for AF_INET...
Connecting to server trashotron.com[207.111.193.19]: 80...
Cache size set to 320 KBytes
Cache fill: 15.00% (49152 bytes)   
REALAUDIO file format detected.
Clip info:
 Title: Agony_Column_Fine_Print-Alastair_Reynolds-Rick_Kleffel
 Author: Reynolds-Kleffel
 Copyright: Copyright 2002
==========================================================================
Forced audio codec: mad
Opening audio decoder: [realaud] RealAudio decoder
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
Selected audio codec: [rasipr] afm: realaud (RealAudio Sipro)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   7.4 (07.3) of 0.0 (unknown)  0.6% 91% 

------------------------------------------------


realplayer (version 10.0.9.809 Gold) dumped.  You have to love those proprietary formats.

Rather large dumpfile not shown for sanity purposes.

Move along folks.  Show's over.

---

