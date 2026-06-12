---
title: "No Sound with NeoMagic256AV"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by mosseguello on 2006-02-21
Hi

i'm writting u after reading many stuff about sound troubles but getting no answer at all.

i'm supposed to have a soundcard installed 'cuz i get sth like this when i write "lspci"

...
...
...
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200[MagicMedia 256AV Audio](code 20)

I've tried every step there u describe but the last one, as when i try to execute alsamixer i get the following message:

"function snd_ctl_open failed for dfault: No such file or directory"

Moreover when i go to SYSTEM-> PREFERNCES-> SOUND
where it puts Default Sound card there's no sound card to choose!!!!!

Should i change my Multimedia System Selector (System->Preferences), it's set to ESS but i'm not sure it's sth to do with this

I've already executed gst-register-0.8

What else? ummm... i can tell u that inside /proc/assound/OSS there r 2 archives, the one called devices it's empty, while the other one called SndStat u can read:

"Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux sort 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG"

The Modules archive inside /proc says sth like:

"snd_nm256 67680 0 - Live 0xcca5c000
snd_ac97_codec 72188 1 snd_nm256, Live 0xcca14000
snd_pcm_oss 46368 0 - Live 0xcca3c000
snd_mixer_oss 16128 1 snd_pcm_oss, Live 0xcca0f000
snd_pcm 78344 3 snd_nm256,snd_ac97_codec,snd_pcm_oss, Live 0xcca27000
snd_timer 21764 1 snd_pcm, Live 0xcc9fa000
snd_page_alloc 10120 1 snd_pcm, Live 0xcc9d6000
snd 48644 6 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xcca02000
soundcore 9184 1 snd, Live 0xcc9da000
"
among many others.

Any ideas so that i can listen to music with my laptop? Cheers

---

### Post by mosseguello on 2006-02-21
Sorry, it's not Neo Magic, it's Magic Media

---

### Post by mosseguello on 2006-02-23
Sb to help out there? I'd be so thankful. If none of u can help me it'd be great if anyone could tell me somewhere else 2 look it up. Cheers again

---

### Post by 11hjpphty76lkjj on 2006-03-13
Did you get this working?  I'n having the same problem on an Omnibook 900.

Bump.

---

### Post by FarEast on 2006-03-27
Hi,

I have googled and found interesting threads:

[http://www.linuxforums.org/forum/linux-laptops/28985-omnibook900-neomagic-nm2200-256av-alsa-problems.html](http://www.linuxforums.org/forum/linux-laptops/28985-omnibook900-neomagic-nm2200-256av-alsa-problems.html)
[http://ubuntuforums.org/showthread.php?p=41579#post41579](http://ubuntuforums.org/showthread.php?p=41579#post41579)

I hope they help!

---

### Post by mosseguello on 2006-08-14
cheers 4 the help, one of the links u wrote i'd already had a glance to. The other one is a little bit desolating. It says sth like with 2.6 kernel there's no longer support 4 that soundcard. I've read many stuff and have tried most of the possible solutions many people has been successful with but it seems this is not working with mine :( 4 the omnibook guy i can tell u it seems u'll be lucky. I'm sorry i haven't got the links here but if u have a look googling u'll find plenty of people who seem 2 have solved ur problem. I'll write the links at the end of september when i come back from holidays ;)

I've also read sb who's been successful with the last knoppix release, but i'm afraid i can't be that optimistic after having a try with the live-DVD

---

