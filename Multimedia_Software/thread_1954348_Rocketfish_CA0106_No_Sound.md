---
title: "Rocketfish CA0106 No Sound"
date: 2012-04-07
forum: Multimedia Software
---

### Post by maxietom on 2012-04-07
I previously had a problem with my on-board sound card, and eventually I found out that it came with a faulty sound card built in. Unfortunatly my warranty was up and I just decided to buy a sound card. Of course, my luck cased that one to not work in Ubuntu either. All it did at first was go fzzzzzzzzzzzzzzt in place of every noise.

After messing with some settings I managed to get no noise at all. I booted into my barely used Windows XP partition, and the sound worked flawlessly. Everything in alsamixer is cracked up to the max, and nothing is muted.

I attached my alsa-info below:
[http://www.alsa-project.org/db/?f=6ac5935f4e343b9f826ff927e76ce95ed4a9aaf1](http://www.alsa-project.org/db/?f=6ac5935f4e343b9f826ff927e76ce95ed4a9aaf1)

---

### Post by Rodney9 on 2012-04-07
Try Pavucontrol

```
sudo apt-get install pavucontrol
```

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

also 

these two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


Rodney

---

### Post by maxietom on 2012-04-10
Thanks for the reply. I tried the guides and the sound control, but no luck. Did you check my alsa-info log I attached?

---

### Post by BicyclerBoy on 2012-04-10
Your alsa info log reports 1 Jan 2008..

speaker-test -l 1 -c 2 -r 48000 -D hw:0,0
speaker-test -l 1 -c 2 -r 48000 -D hw:0,1
speaker-test -l 1 -c 2 -r 48000 -D hw:0,2
speaker-test -l 1 -c 2 -r 48000 -D hw:0,3
close & re-open terminal if you get errors..

Ugly reports here
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)
about white noise on playback.

---

### Post by Yellow Pasque on 2012-04-10
Make sure the iec958/digital output is unchecked in alsamixer (seems to be a common issue with this chipset).

> Your alsa info log reports 1 Jan 2008..
Ubuntu 11.10 didn't exist then, so it must be an issue with the script or server

---

### Post by BicyclerBoy on 2012-04-11
> Ubuntu 11.10 didn't exist then, so
you don't say..

---

### Post by Yellow Pasque on 2012-04-11
> **BicyclerBoy said:**
> you don't say..
Sigh.. I was just pointing out that the user didn't do anything incorrectly.

---

### Post by maxietom on 2012-04-11
> **BicyclerBoy said:**
> Your alsa info log reports 1 Jan 2008..

speaker-test -l 1 -c 2 -r 48000 -D hw:0,0
speaker-test -l 1 -c 2 -r 48000 -D hw:0,1
speaker-test -l 1 -c 2 -r 48000 -D hw:0,2
speaker-test -l 1 -c 2 -r 48000 -D hw:0,3
close & re-open terminal if you get errors..

Ugly reports here
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)
about white noise on playback.

Yeah, I got white noise on my first boot with the card in. The speaker test didn't give any errors though. But, on the page you suggested, it said that if I compiled in the soundblaster module from OSS into my kernel that the snd-ca0106 module would work. Is there a way to do this? I have compiled things before, but kernels have always been a mystery to me.

EDIT: I got white noise again! (It's getter than nothing)

---

### Post by maxietom on 2012-04-11
I figured out the problem:

To fix the problem of no noise, I went into alsamixer and pressed F5 and switched the analog source to AUX and digital to SRC out (Not sure if it did anything with the digital...) Then I got the white noise again. After that, I remebered a post I saw a while back that said setting it to 9 would six the problem. Lo and behold, set it to 9 and my sound was back! If you put other application's sound at full blast it's a bit crackly, so put it at <80% and the noise is clear.

Here's a pic of alsamixer:
[IMG]http://i569.photobucket.com/albums/ss135/mtinc2/fixed.png[/IMG]

I hope it works for you others. :)

---

