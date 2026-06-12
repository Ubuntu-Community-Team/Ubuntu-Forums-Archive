---
title: "Sound is crackling badly."
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by ÜbR on 2006-10-24
Hi all,

I need help to get my studio work properly.

OK.. first, here's my hw setup:

CPU= 1GHz Via C3 133 MHz
Chipset =  VIA Apollo PLE133T (VT8601T + VT82C686B)
Memory = 1 Gb
Harddisc = 80 Gb
Sound = Hoontech ST Audio dsp 24 value

Problem is that sounds are crappy and crackling badly when using Ardour. MP3 are playing OK with VLC. What do u think? Sw or hw fault? 

Here's what ST audio say's about VIA chipsets:
[http://www.staudio.de/kb/english/conflicts/index.html#via](http://www.staudio.de/kb/english/conflicts/index.html#via)

I've allready disabled ACPI, but that hasn't fix my problem. I can't get soundcard to unshared IRQ. I've tried all PCI  -slots. This might cause problems I think..

All help is wellcome. 

-ÜbR

---

### Post by brummer on 2006-10-24
maybe this site´s can help you
[http://tapas.affenbande.org/?page_id=40]("http://tapas.affenbande.org/?page_id=40")
[http://tapas.affenbande.org/?page_id=6]("http://tapas.affenbande.org/?page_id=6")

brummer

---

### Post by zettberlin on 2006-10-24
> **ÜbR said:**
> 
I can't get soundcard to unshared IRQ. I've tried all PCI  -slots. This might cause problems I think..


Yeah, could be: did you try to configure a single PCI-slot to use a single (unused) IRQ in the BIOS? Disabeling COM/Parellel-Ports and of course onboard-sound/joystick could help also.

But as i hear you say "crackling and dropouts" i doubt, your kernel could be the evildoer. You need at least a kernel with DESKTOP_PREEMPT enabeled. Mine is such a beast: 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 - this one works very well on Dapper and allowed uninterrupted usage of Ardour on a mediocre Toshiba-Notebook (with PIII/1300 and 256 RAM) also.

What do you get by this command:

:~$ uname -a

??

---

### Post by ÜbR on 2006-10-24
OK, I think you should know, that this computer isn't basic system. I've 19" 2U rack IPC with CPU-card and butterfly backplane. I want to use this chassis cause it fit in 19" rack. Backplane has 3 PCI -slots and it's OK, but this CPU -card is from ***. It's hard (=expensive) to find another CPU-card so that's why I want to get this system work.

[IMG]http://img.shopping.com/cctool/PrdImg/images/pr/177X150/00/01/68/f3/0f/23655183.JPG[/IMG]

> **zettberlin said:**
> Yeah, could be: did you try to configure a single PCI-slot to use a single (unused) IRQ in the BIOS? 
Not possible at this award BIOS.. if I remember correctly.

> **zettberlin said:**
> 
Disabeling COM/Parellel-Ports and of course onboard-sound/joystick could help also.
I've disabled COM -ports, LPT -port and floppy drive controller. It won't share those IRQ's to PCI -devices. It is not possible to disable integrated VGA or ethernet. This isn't good thing. 

> **zettberlin said:**
> 
But as i hear you say "crackling and dropouts" i doubt, your kernel could be the evildoer. You need at least a kernel with DESKTOP_PREEMPT enabeled. Mine is such a beast: 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 - this one works very well on Dapper and allowed uninterrupted usage of Ardour on a mediocre Toshiba-Notebook (with PIII/1300 and 256 RAM) also.

What do you get by this command:

:~$ uname -a

??
"2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux" or "2.6.15.6-rt21-ubuntumusique #1 PREEMPT Tue Jul 25 03:31:23 CEST 2006 i686 GNU/Linux" depending which kernel I'm using.

I still need to read those links posted by brummer.. thanks.

---

### Post by zettberlin on 2006-10-25
Well - it looks, like we have a problem in common - questions, nobody has answers to ;-) :-|

---

### Post by Rush_898 on 2006-10-25
I am just figuring out this linux thing, but as a DAW system in general I can tell you what I would try.  Sounds silly but try turning all volumes down very, very low and record and playback.  Sometimes crackling/dropout is simply overwhelming an input while recording and even though the volume isn't spiking to red it can be.  There are usually a lot of volume controls from A -> Z.  Manual on mic, input on DAC, software on OS, software on program, etc.  If it still give you static at least you know you aren't overrunning the buffer.

Just my thought.

---

### Post by ÜbR on 2006-10-25
Any ideas why Alsamixer and Envy24control doesn't work? It seems that softmixers has no effect to sound level.

---

### Post by ZephyrXero on 2006-10-29
I have bad crackles and pops (sounds like the audio is peaking) whenever I turn my PCM volume above 50% on two different machines, although both use on-board sound chips. Is there any solution to this? I hate to go here, but under Windows, I never had any of these problems, so it has to be a software issue somewhere :(

---

### Post by helrumyc1 on 2006-10-29
getta new system

---

### Post by ZephyrXero on 2006-10-30
> **helrumyc1 said:**
> getta new system
Thanks for all your help! I'll go out and buy a new desktop and laptop right away ;)

---

### Post by DROWE859 on 2006-11-06
You may try looking into ALSA. I had the same problem about one year ago and it cured it for me. Unfortunately, I have forgotten how to go about it, if I happen to find out how I'll be sure to tell you.

---

### Post by Max_Might on 2006-11-06
if you want to "tune up" ALSA just open your terminal and type **alsamixer**
:)

---

### Post by stbub on 2006-11-11
I have a brand spankin' new Core 2 Duo with 2G of ram.  The builtin audio is a Realtek ALC882 (Intel HDA).

So you'd think it's an upgrade over an AMD Athlon XP 2000 with 512M of ram, but it ain't.  Worst xrun rate, and significantly more serious is the **constant crackling**.

It appears to be jack related because, for instance, if I use Hydrogen WITHOUT jack, the sound is fine.  If I use Hydrogen WITH jack, then I get crackling.  I also get crackling with xmms/jack as well, so I don't think it's hydrogen, and I don't think it's alsa.

Did some googling and found nothing helpful.  Been trying to tweak things in alsa and jack with no success.

Lowering the volume in alsa doesn't make the crackling go away, so jack somehow munges the audio.

The only positive thing is that when jackd goes balistic and uses all the cpu for no explained reason, I can easily kill it 'cause i've got a second cpu ... so, all in all, not much positive to hang on to... :-(

But if you can light up my day, by all means, do so.

---

### Post by lapsey on 2006-11-11
i had a similar problem and it turned out to be the power cables

---

### Post by Kimm on 2006-11-11
Open alsamixer (in terminal), find "Mic" and "Mic Boost", then disable both of them (by pressing 'm')

---

### Post by ÜbR on 2006-11-15
I think my Kingston memory modules are not good enough. (Sdram 256mb KVR133 CL3, one sided)

With one bulk memory module, system works almost without problems. (Infineon chip) With two I get problems, but not so much as with Kingston. 

If you have problems like this, test your memorys one by one. Then use best ones.

---

