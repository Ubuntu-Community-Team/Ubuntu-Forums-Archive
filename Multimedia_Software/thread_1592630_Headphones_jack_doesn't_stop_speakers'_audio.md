---
title: "Headphones jack doesn't stop speakers' audio"
date: 2010-10-10
forum: Multimedia Software
---

### Post by Vecktor on 2010-10-10
I'm having a little problem with an Acer Aspire 5536-5281 with Ubuntu 10.04 installed. In Windows, whenever I plug in a pair of headphones, the audio coming out of the integrated speakers stops and is switched to the headphones. In Ubuntu, sound comes out of both the speakers and the headphones. How can I fix this?

---

### Post by rette7mich on 2011-04-24
i experience this same problem on multiple machines and still have not found a fix.

experienced on:
asus laptop
archos 9 touchpad

if i find an answer i will post it here

---

### Post by KegHead on 2011-04-24
Hi!

Have you gone to;

System..preferences...sound?

KegHead

---

### Post by rette7mich on 2011-04-24
yup just did actually, and under the output tab if i changed it to analog output it would then only output through the speakers.

easy fix, must have been in a daze when i tried before.

---

### Post by KegHead on 2011-04-24
Hi!

Congrats!

Please mark you thread as "solved".

KegHead

---

### Post by felixbur on 2011-07-22
I have an Acer Aspire 8951G with Ubuntu Natty
and if i plug in the headphones the rear speakers stop but the front speakers still output sound (the headphones too).
 I tried all possible settings in alsamixer.

cheers, 
felix

---

### Post by Gbillou on 2011-07-22
Hi, I do have the same problem. I'm on natty and sound comes from both my internal speakers AND my headphones when i plug my headphones, and only internal speakers if nothing is plugged.
Here is my alsa information script output :
[http://www.alsa-project.org/db/?f=5d790a2ff7dd34cbc75cdd9da383af6965b52b91](http://www.alsa-project.org/db/?f=5d790a2ff7dd34cbc75cdd9da383af6965b52b91)
I already tried to force the snd_hda_intel module parameter "model" to "3stack" or "6stack", but nothing changed.
I updated to the latest alsa drivers from ubuntu-audio-dev ppa (as you can see my alsa driver version is 1.0.24).

I noticed strange log about alsa in dmesg ("ALSA hda_codec.c:487 hda_codec: Too many connections 32 for NID 0x23" etc..), see above link.

I tried many options and things from configuration utilities like alsamixer and gnome-volume-control.. In alsamixer there's a "headphones" column that is stuck to "00", i can mute it but can't raise it.

So.. i'm stuck :) heellpp mee pplleease ;) I'm pretty sure I may have missed something :-/

==== EDIT ====
I found this wiki page :
[https://wiki.ubuntu.com/ALSA/JackSense](https://wiki.ubuntu.com/ALSA/JackSense)
So now I have these 2 "debug" files. I may better open a launchpad bug about this issue, I'll let you know. BTW I can link those if someone is interested :)

---

### Post by felixbur on 2011-07-29
hi Gbillou
did you post the bug report?
can you link to it?
I attach the output of some versions at the bottom.

cheers,
felix


felix@felix-Aspire:~$ uname -a
Linux felix-Aspire 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

felix@felix-Aspire:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: PCH [HDA Intel PCH], Gerät 0: ALC670 Analog [ALC670 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 1: ALC670 Digital [ALC670 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0	

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

felix@felix-Aspire:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC670

==> /proc/asound/card0/codec#3 <==
Codec: Intel CougarPoint HDMI

---

### Post by tlambert on 2011-08-04
Hi, I've been half-way investigating similar stuff for Chrome OS.

The issue is going to be a combination of several things:

[LIST=1]
[*]the lack of a policy manager that can react to configuration changes for audio hardware by issuing mixer commands to enable and disable certain devices.
[*]the fact that devices are opened directly rather than being intermediated by a policy manager; the upshot of this will be that once opened by flash (for example), other devices won't be considered by the program.  I call this the "device/data rather than procedural interface problem".
[*]the wide variety of software that doesn't have a standardized expectations of a single common device interface
[*]the inability to represent everything about different devices in a uniform virtual device
[*]the wide variety of device hardware behaviours; for example, on some ARM systems, you're going to have a headphone jack which, when in use, is going to latch a value onto a particular GPIO to flag that you should change your mixer settings from internal speakers to headphones (or use both, or output different data to each, etc., depending on policy managed by the non-existant policy manager)
[/LIST]

The closest you are going to get in Ubuntu is going to be using PulseAudio, which still doesn't have policy management, but at least gives you GUI controls, and by virtue of providing a virtual device, as in #3 above; guaranteed this will conflict with #2 and #4.

Another drawback for PulseAudio is that it has popping and clicking and other noise artifacts, which you are supposed to deal with in your software, rather than their library, even though the solutions are well known and could be handled there.

Finally, it's going to introduce processing latency, which will cause action/audio synchronization issues for games, video playback, and event/result (e.g. a beep from bash for an ambiguous input).  The solution for these is tuning, although it could also be done automatically via back-propagation.

The drawbacks are why Chrome OS has ditched using PulseAudio, at least for current releases.

There's been some consideration of doing a policy management daemon of some kind for this; the current versions of libalsa has some incomplete configuration management support.  This is actually not really appropriate for policy management, and falls short there.  It seems to be intended primarily to support things like media-centric setups which select from a menu of specific configurations.  These would be more appropriate for equalizer rather than mixer settings from a remote control, e.g.: "Action, Rock, Classic, Concert, Drama, Lounge, Gaming, Sports".

I imagine patches/code to deal with all this would be welcome, but controversial.

Hope this helps explain the status quo somewhat.

-- Terry

---

