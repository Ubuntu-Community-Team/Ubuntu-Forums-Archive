---
title: "SIS SI7012 only left channel?????"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by dannyboy79 on 2006-10-24
#1       September 3rd, 2006  
 dannyboy79  
Quad Shot of Ubuntu
   Join Date: May 2006
Location: Milwaukee,WI
Beans: 445
Ubuntu 6.06 User 

 
Sound out of right speaker broke???? 

--------------------------------------------------------------------------------

Please please whoever can help I would greatly appreciate it. I did a fresh install of Dapper and my sound worked fine out of both speakers and the subwoofer!! It's a 2.1 channel system. It's onboard sound, here is the output of aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
Subdevices: 0/1
Subdevice #0: subdevice #0
Well, I had buddies over for poker night and did a remotre desktop from my laptop into my ubuntu box because that's where 1200 songs are. I used xmms and basically have one of those cables where it basically turns a audio plug (like the one that's on the end of headphones) and on the other side is rca plugs, white and red. I have used this kind of thing before but this time insterad of having to run up into my room and add songs to the playlist, I did it remotely using my laptop. Basically the audio cable I was using went from my ubuntu box out into my receiver tape selection and it plays what would be coming out of my ubuntu box. Well all of a sudden the it started playing out of the left side only. I didn't think anything of it at the time and just figured it was a badly recorded .mp3. Well, sure enough, now my sound only comes out of the left speaker and that's it. I have 2 computer hooked up aan audio, keyboard, mouse kvm switch and when I select the other computer by hitting scroll lock twice on the keyboard the other computers (winxp) sound is fine and comes out of both speakers so obviously it's ubuntu or alsa or something like that. What do I do? What could have made it break by just playing songs thru xmms. That was the first time i used remote desktop to do that and the first time I played with xmms but that can't be it can it? This is my relevant (i removed usb, ide, sata, vga, nvidia card, and pvr-350) lspci output:
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX H ost (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media I O] (rev 36)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
the only important line in dmesg was this:
input: PC Speaker as /class/input/input1
Can anyone please help me troubleshoot this. 

Update: I tried using the brand new Edgy RC1 Live CD and the sound only came out of the left side speaker just like Dapper? I suppose I will check out any jumpers on my motherboard? Also, maybe update bios if I can. I know it's not the speakers as they work fine in WINXP. Thanks for any help!

---

### Post by dannyboy79 on 2006-11-15
please help, some1. can't anyone good with alsa or oss help me troubleshoot?

---

### Post by TheMatt on 2006-11-15
I had something like this, I went into the Kmix program and adjusted the balance. Use whatever mixer program is in GNOME.

---

### Post by dannyboy79 on 2006-11-16
you've already suggested that before. I have this problem posted like 3 different places since I can't get anyone to help me. I tried messing around with alsamixer, playing around with the gnome volume balance thingy and nothing will do it?

---

### Post by subspawn on 2006-11-21
I got a Sis si7012 issue solved in the following way:

Clean install Edgy

Added "options snd-intel8x0 ac97_quirk=3" to /etc/modprobe.d/alsa-base

Next, set your mixer right, like this (amixer output):
> 
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [on]
  Front Right: Playback 18 [58%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 22 [71%] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [on]
  Front Right: Playback 19 [61%] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [on]
  Front Right: Playback 23 [74%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 26 [84%] [on] Capture [off]
  Front Right: Playback 26 [84%] [on] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [on] Capture [off]
  Front Right: Playback 28 [90%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-ex
clusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 24 [77%] [off]
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
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-ex
clusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 26 [84%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 26 [84%] [off] Capture [off]
  Front Right: Playback 26 [84%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 12 [80%] [off]
  Front Right: Capture 12 [80%] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]



I have to say, the Si7012 is probably one of the worst chipsets I've ever come across.

---

### Post by dannyboy79 on 2006-11-22
i sent you a pm about this, if you could respond that would be great. to everyone else who have this issue, if this fixes it I will post back what all I have done so you can get yours fixed also! Hopefully this is it!! I have dealt with this for along time!

---

### Post by dannyboy79 on 2007-03-08
this is soooo funny! i totally forgot that I was playing around with the audio header jumpers when I tried getting the front audio jack to work, well I forgot to put a jumper on 2 of the pins to make both channels work again. the reason it must have worked in xp is because windows must have some default setting to just duplicate the left side audio and spit it out the right side. that's the only explaination as to why it was working in winxp and not ubuntu. so this was my fault, once I put the other jumper on the front audio header, sound worked again out of both speakers. YEAH!!!!

---

### Post by popeyeray on 2007-05-07
I am running ubuntu 7.04 I went to Multimedia, then clicked on something called QAMix. I ajusted the sound one just one of the sliders and the sound immediately came out of my preiviously muted right headphone. I don't know if QAMix is part of the generic instalation so if not just use whichever update program you use to get it.

---

