---
title: "Does mplayer work with jaunty and capture card?"
date: 2009-09-22
forum: Mythbuntu
---

### Post by yzfr1 on 2009-09-22
I just put together my first myth box...  So excited.  I have been working on getting everything installed and up and running for about 2 weeks now.  

I have an Hauppauge 1250 Tuner Card, NVIDIA 7900 Graphics card, and decent hardware to support it.  

I can scan channels with scan and I can watch live tv. I have hit a few bumps to get this far but have made it without asking for too much help.  I do need some now though.

I can't get mplayer to recognize my card while doing a scan.  I am trying to run this script 

> mencoder  dvb://$1 -nosound -frames 10 -ovc lavc -o $1.avi &   
sleep 20                                                           
killall mencoder                                                    
sleep 1                                                           
killall -9 mencoder  

I found this on the mythtv wiki [here]("http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards") for scanning channels and trying 
to figure out what the channels are.

Every time I run this script I get this result

> MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz (Family: 6, Model: 23, 
Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
UNKNOWN TUNER TYPE
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://1.
Cannot open file/device.

Exiting...

So I tried running mplayer to view the video and I get the same error.

I tried mplayer with this command :

mplayer dvb://1 -r

I have setup my channels.conf file and it is in the ~/.mplayer directory.

I looked many places over the past few days and do not see that there 
is a good solution.

What do I need to do to get mplayer to work here?  I saw something about 
recompiling a while making changes to a file call dvbin.h but I can't find 
that file anywhere.

Please help.  Thanks in advance!

---

### Post by bruno9779 on 2009-09-22
It is a little more complicated that that, you need to install V4L-DVB

I did it following this link [linux.tv]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#First_Use:_Out_with_the_Old.2C_In_with_the_New")

Also, in this post _[here]("http://ubuntuforums.org/showthread.php?t=974366")_

And probably will want to have  a look at this too: [post]("http://ubuntuforums.org/showthread.php?t=1234274")

Googling "Ubuntu hauppauge 1250" hgave me 2870 results ...
googling "Hauppauge 1250 ubuntu forum" gave 2080 ...

---

### Post by yzfr1 on 2009-09-22
> **bruno9779 said:**
> It is a little more complicated that that, you need to install V4L-DVB

I did it following this link [linux.tv]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#First_Use:_Out_with_the_Old.2C_In_with_the_New")

Also, in this post _[here]("http://ubuntuforums.org/showthread.php?t=974366")_

And probably will want to have  a look at this too: [post]("http://ubuntuforums.org/showthread.php?t=1234274")

Googling "Ubuntu hauppauge 1250" hgave me 2870 results ...
googling "Hauppauge 1250 ubuntu forum" gave 2080 ...


Thanks for you quick reply bruno9779.  

I have already installed and updated the latest drivers.  I found those pages as well.  The card works...  I can watch live tv.  

Where I am running into a problem is that I can't use mplayer to scan the channels with mplayer and then use mencoder to output a snapshot of the video.

Everything seems to working the way it supposed to be other than this.  I was just trying to get my channels figured out.

Am I just looking at this wrong?

---

### Post by laceration on 2009-10-16
No.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/369349](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/369349)

Even though your dvb card has a different Conexant chip than reported in the bug, this bug seems to affect more dvb devices than referred to in the bug report.  The software defect in MPlayer is repaired in the version used in Karmic, so if you upgrade it should solve your problem.

---

