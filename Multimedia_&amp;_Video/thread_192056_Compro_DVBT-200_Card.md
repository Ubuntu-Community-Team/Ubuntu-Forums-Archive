---
title: "Compro DVBT-200 Card"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by chazzy on 2006-06-08
Hi all,

I installed Dapper with this card in the machine and during dmesg it shows it finds it and activates it etc but makes no mention of a tuner.

I have tried tvtime, mplayer etc and all I get it black space with nothing else.

[4294690.026000] saa7130[0]: subsystem: 185b:c901, board: Compro Videomate DVB-T 200 [card=71,autodetected]

I'm about to cry, and really hope someone can shed some light on the issue.

Many thanks.

---

### Post by chazzy on 2006-06-11
Hi there,

I have plodded on further with this problem and found that I need to complete the following:

> 
Compro VideoMate DVB-T200
Chipset: Philips SAA 7134
Support: Requires Kernel 2.6.12 or greater and the latest CVS from video4linux and linux-dvb
Installation:

    * Grab the CVS for video4Linux and linux-dvb, instructions can be found at LinuxTV.org ([http://www.linuxtv.org](http://www.linuxtv.org))
    * Goto the video4linux directory and run scripts/merge-trees.sh
    * Edit the Make.config file and make sure saa7134-dvb = n is changed to saa7134-dvb = m (builds the dvb part as a module)
    * Run make && make install
    * Then modprobe saa7134 oss=1 card=71
    * Then modprobe saa7134-dvb and you should be good to go.
    * For the DVB-T200, you will also need firmware. Please check the Documentation/dvb directory in the kernel source how to obtain and install it.
    * Remote Control:I don't have this card so I'm not sure if the patch for the T300 will work. If someone wants to try there's only a few lines to change in the saa7134-cards.c and saa7134-input.c files. Shoot me an email if interested. 

Thanks to MythTV's Wiki


I tried the cvs (v4l-dvb-d2f796f3590d.tar.gz) but it told me it needed 2.6.16 whereas on dapper its 2.6.15.. 

Can someone please shoot me or give me some dumbed down instructions on how to do this, then I'll bugger off and be as happy as a sand piper!

Thanks again.

Chaz

---

### Post by ultima on 2006-06-20
Hi chazzy,

I just got my Compro VideoMate DVB-T300 going.

I first compiled a new kernel (2.6.17) using this guide 
[http://www.ubuntuforums.org/showthread.php?t=157560&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=compile+kernel)
Then I rebooted into the new kernel

Then I downloaded this file v4l-dvb-676364f7622d.tar.bz2 from [http://www.linuxtv.org](http://www.linuxtv.org) and compiled it against the new kernel.

Then I used easyubuntu to install the multimedia codecs, mpeg-2 etc... to be able to play the dvb-t stream

For some reason I needed to shutdown the computer completely, then restart it for it to be detected, maybe because I'm on a dual boot system, I need to do the same thing everytime I boot into Windows.

Then I ran Kaffeine and it detected the card. I did a scan and it works.
I have not tried the remote yet.

The next step is MythTV

Edit: I forgot the most important thing you need to add saa7134-dvb to /etc/modules
Edit2: You may want to try just adding saa7134-dvb to /etc/modules first to see if that makes any difference

---

