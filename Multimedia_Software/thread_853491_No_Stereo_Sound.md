---
title: "No Stereo Sound"
date: 2008-07-08
forum: Multimedia Software
---

### Post by catalystduck on 2008-07-08
Using Ubuntu 8.04 I can only get the left channel on all sound output.  (right speaker plays nothing at all)  I'm new to linux and as yet have not had to mess with sound configuration, so let me know what you need to help answer my question.  I've googled like crazy, but haven't found anything addressing this specific problem.
Thanks

---

### Post by randomidea on 2008-07-09
I had the exact same problem (for Kubuntu Hardy). After I ran across this thread I found another one that dealt with a similar issue. Sometimes (and I have no clue why) the volume on our alsamixer is turned all the way down. For some people it happens to both speakers, and for others it happens to only one (ours seems to be a rarer case, which is why googling hasn't helped). Anyway, to the point. Try typing in a terminal:

```
alsamixer
```

You should see a colorful mixer in your terminal. Use the horizontal arrow keys to select FRONT (above it should be something like "100<>0"). Now use your up key to increase the volume (so that you see "100<>100").

I hope that fixes your problem. I haven't checked to see whether the right speaker still works after I restart the computer, but I'll let you know when I find out.

*Edit* Yeah, still works.

---

### Post by catalystduck on 2008-07-11
Unfortunately I have no "FRONT" slider. "MASTER" is (currently) 71<>71.  I have played around with alsamixer for quite some time (with very annoying test sound playing in background) to try to get just the right combination of settings, but still no sound from my right speaker.

---

### Post by randomidea on 2008-07-12
No FRONT? Well unfortunately I'm also rather new to linux, so I can't help much. It was chance that I stumbled upon the solution for my problem. If you haven't already found it, [here]("http://ubuntuforums.org/showthread.php?t=205449") is the page where I found that info about alsamixer (it has a bunch of tips for sound problems).

Are any of the channels in alsamixer muted? There should be a green box under the channel if it is unmuted, and a gray box if it is muted. You can mute and unmute with the letter "M."

If that doesn't work, maybe type "amixer" in a terminal and take a look at your various playback channels. Maybe that can help diagnose the problem further.

I wish I could help more, but I'll keep trying until someone more experienced finds this post.

---

### Post by catalystduck on 2008-07-21
Still no luck.  this is the output of amixer; (it says "mono" a lot, but what changes to make and how?)

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Master Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [7.50dB] [on]
  Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-16.50dB] [on]
  Front Right: Playback 20 [65%] [-16.50dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Independent'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [on]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [on]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 26 [84%] [4.50dB] [on] Capture [off]
  Front Right: Playback 26 [84%] [4.50dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'A/D Converter'
  Item0: 'AC-Link'
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Downmix',0
  Capabilities: enum
  Items: 'Off' '6 -> 4' '6 -> 2'
  Item0: '6 -> 2'
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'High Pass Filter Enable',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
  Capabilities: enum
  Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
  Item0: '0 V'

 It seems my volume control applet controls the "master mono" level in alsamixer.  It seems to actually be set up to output mono, but if that's the case, wouldn't the right channel usually be mixed in with the left?

---

### Post by catalystduck on 2008-07-27
Ok, Update;  My sound card is an analog devices AD1985 on board an ASUS motherboard.  Asus provides an ALSA driver for the device, which I have downloaded, unzipped, untarred, etc, and I'm now left with a single folder with lots and lots of files in it that I have no idea what to do with.  How do I install this driver into my system.  The driver is [here]("http://support.asus.com/download/download.aspx?SLanguage=en-us") if it will help to see the files I ended up with. (its under motherboard/Socket 478/P4C800-E Deluxe/Audio)

Alternatively, is there an easier way to set up this device?

---

