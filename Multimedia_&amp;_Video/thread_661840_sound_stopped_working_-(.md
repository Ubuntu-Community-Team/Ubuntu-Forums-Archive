---
title: "sound stopped working :-("
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Finch75 on 2008-01-08
Hi everybody,

I'm in the process of installing my new Ubuntu system and "suddenly", the sound stopped working.

It still worked this morning, it doesn't work now. I don't think I changed anything relevant, but I could be wrong of course *g*

What can I do to fix this?

Everything "looks" fine, the sound devices are still available, the programs don't seem to be aware of the problem (i.e. I can play files in Rhythmbox and Amarok and others), I just don't hear anything...

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I am "computer literate", but unfortunately, I am new to Linux and don't know where to start troubleshooting... I don't have any obvious error messages and don't know where to look for them...

All of this is Ubuntu 7.10 and an Asus M2NPV-VM mainboard...

Any help appreciated!

---

### Post by radi0j0hn on 2008-01-08
I hate to admit this, but after struggling with the same problem, I found that, somehow, the speaker icon was set to OFF.  On my display, the status is not really obvious.  I clicked on it and all was well.  Hope your solution is this simple.. john

---

### Post by Finch75 on 2008-01-08
No, I'd checked that several times *g* (and rebooted and all kinds of stuff)
(also I've checked if the cable is still properly connected and if my receiver is muted... as sad as it is: this is the most important thing you learn in 20 years of experience with computers *g*)

Any other ideas? :-(

---

### Post by mempman on 2008-01-08
print the output of cat /proc/asound/version, cat /proc/asound/cards  and make sure amixer shows that Master and PCM are fully functioning and not muted.

---

### Post by Finch75 on 2008-01-08
Hi mempman, 
thanks for your post, here's some additional information:

> **mempman said:**
> print the output of cat /proc/asound/version,

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
```

> **mempman said:**
>  cat /proc/asound/cards

```
 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 22
```

> **mempman said:**
>  and make sure amixer shows that Master and PCM are fully functioning and not muted.

```
 amixer
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
[COLOR="Blue"]  Front Left: Playback 29 [94%] [-3.00dB] [on]
  Front Right: Playback 29 [94%] [-3.00dB] [on][/COLOR]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  [COLOR="Blue"]Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on][/COLOR]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
 [COLOR="Blue"] Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on][/COLOR]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: [COLOR="Blue"]Playback [on][/COLOR]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 15 [100%] [0.00dB] [off]
  Front Right: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mono',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Stereo Downmix',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]

```

Hmm... I think everything is on that needs to be on, isn't it? Are there any files that could contain error messages? Where can I see if everything is recognized and initialized during boot?

---

### Post by mempman on 2008-01-08
Are you dual booting with Windows  Vista, if yes, then go to Vista and post the name of the sound driver you are using......

I suspect you may be using "Conexant" , if so, uninstall it and instead install "High Definition Audio Driver".

---

### Post by Finch75 on 2008-01-08
huh?

No, I'm not using Vista, but I'm dual booting XP...

How can the sound driver in Windows have an effect on the sound in Ubuntu? Am I missing something fundamental here?

---

### Post by mempman on 2008-01-08
Read my other post: 
[http://ubuntuforums.org/showthread.php?t=661433](http://ubuntuforums.org/showthread.php?t=661433)

---

### Post by Finch75 on 2008-01-09
[I]*haha* - you just got to love computers, don't you?
I mean... I believe your story, but it's still very close to something I would normally call "not possible". And by the way: I've heard that it is *strongly* discouraged to put one OS into Hibernate and then (dual-)boot into the other OS. Most definitely if you share some data.[/I]


Oh well... *sigh*... my sound still doesn't work, no matter what I do in/with my XP partition. I tried booting a different (older) Ubuntu installation, but it won't start any more.... (and I don't have time (and skill) to fix it). Oh, that gives me an idea right there... I'll try a Live-CD tonight when I get home...

In the mean time... any other ideas? Anyone?

---

### Post by deadgobby on 2008-01-09
It is a bug. Here try this and see if it works

1. Download the latest alsa package from here: [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)

2. Extract it where ever you like and use cd in a terminal to get there.

3. Do: ./configure --with-oss=yes --with-sequencer=yes --with-cards=hda-intel ; make

4. sudo make install

5. Restart you're system and it is done!

Good luck! ;)

---

### Post by Finch75 on 2008-01-09
> **deadgobby said:**
> It is a bug. Here try this and see if it works

I tried it but it didn't help :-(
If it's a bug, how come the sound worked until yesterday?

I've also tried booting from a Ubuntu 7.10 LiveCD and if I do that, the sound WORKS!

> **deadgobby said:**
> 
If it is not broke, fix it till it is.


Yeah, looks like I've done that :-(

What can I do to find the source of this problem?

---

### Post by mempman on 2008-01-09
> **Finch75 said:**
> [I]*haha* - you just got to love computers, don't you?
I mean... I believe your story, but it's still very close to something I would normally call "not possible". And by the way: I've heard that it is *strongly* discouraged to put one OS into Hibernate and then (dual-)boot into the other OS. Most definitely if you share some data.[/I]


Oh well... *sigh*... my sound still doesn't work, no matter what I do in/with my XP partition. I tried booting a different (older) Ubuntu installation, but it won't start any more.... (and I don't have time (and skill) to fix it). Oh, that gives me an idea right there... I'll try a Live-CD tonight when I get home...

In the mean time... any other ideas? Anyone?



Did you find out what windows sound driver you are using?

---

