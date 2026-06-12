---
title: "No sound with Nforce4/ALC850"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by adx on 2006-09-30
I have a machine that has a Gigabyte GA-K8N Pro-SLI and I can't get the onboard sound to work. It recognizes the onboard card and loads the snd_intel8x0 driver. I can also see the card with aplay -l, but I just get no sound. I've check the mixer and have unmuted everything.

I don't know what else to check. It just seems like it doesn't work.

---

### Post by Kateikyoushi on 2006-10-01
Try to mute the external amplifier in alsamixer, I have no sound if it is on.

---

### Post by adx on 2006-10-01
The external amplifier is muted. Still nothing.

---

### Post by Kateikyoushi on 2006-10-01
Is the user member of the audio group ?

Check it System >> Administration >> Users and Groups >> Properties

---

### Post by adx on 2006-10-01
They are in the audio group. There is one thing to note. This is a server install so there is no X. That shouldn't make a difference if the sound works or not though.

---

### Post by Kateikyoushi on 2006-10-01
What do you see when you check out your sound preferences ?
System >> Preferences >> Sound
Is ESD sound mixing enabled ? 
Is there a sound card under the Default Sound Card?

---

### Post by adx on 2006-10-01
I don't have X installed so there is no esd or other sound daemon. The worst part is that it doesn't work even if I force it to hw0,0 using aplay. I'm sure it has something to do with the mixer settings, but I can't find a list of what everything should be set at. 

My current settings are:

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 12 [39%] [on]
  Front Right: Playback 12 [39%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [off]
  Front Right: Playback 31 [100%] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [on] Capture [off]
  Front Right: Playback 23 [74%] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Front Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic2'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 29 [94%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 6 [40%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

---

### Post by fms on 2006-12-18
> **adx said:**
> I have a machine that has a Gigabyte GA-K8N Pro-SLI and I can't get the onboard sound to work. It recognizes the onboard card and loads the snd_intel8x0 driver. I can also see the card with aplay -l, but I just get no sound. I've check the mixer and have unmuted everything.

I don't know what else to check. It just seems like it doesn't work.Hi. I had a similar sounding problem (that is, no sound at all) with the same motherboard. I'm posting this in case it helps someone else:

[http://www.gigabyte.com.tw/Support/Motherboard/FAQ_Model.aspx?FAQID=369&ProductID=1883&ClassValue=Motherboard](http://www.gigabyte.com.tw/Support/Motherboard/FAQ_Model.aspx?FAQID=369&ProductID=1883&ClassValue=Motherboard)
[http://www.planetamd64.com/index.php?showtopic=21247](http://www.planetamd64.com/index.php?showtopic=21247)

I disconnected the front audio panel from the motherboard, replaced the jumpers, and rebooted it coupla times - looks like the sound problem is sorted. I now have startup sounds, DVD sound in MPlayer, and can play the example sound files. Hope this helps :KS

---

### Post by dannystaple on 2008-03-25
Hmm - I was stuck with this a couple of days after putting aboard from one machine, into another. The other machine (which normally takes my cast offs as upgrades), did not have front audio.. Until I saw your post fms, I thought it was a software issue. I had recompiled alsa, mucked around with alsa config and module config as well as mixers with no results.
Simply placing those two jumpers on the board made it all work!
Thanks fms!

---

