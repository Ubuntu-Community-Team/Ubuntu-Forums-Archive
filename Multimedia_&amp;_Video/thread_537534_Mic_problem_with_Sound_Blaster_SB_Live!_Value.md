---
title: "Mic problem with Sound Blaster SB Live! Value"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by cc6000 on 2007-08-29
Anyone using a "SB Live! Value" sound card? Did you have to change anything to get the mic to record under Sound Recorder?

I just installed the latest Ubuntu 7.04.  I can hear sound but cannot record sound.  I have two versions of the SB Live! Value cards: Model CT4780 and Model CT 4870.  On top of the volume control currently, it identified the card in my PC now as CT4871. One came from an old Gateway and one from an old Dell. I tried both and both with no recording.

I have tried all the different settings and still no recording. I have tried 4 different mics and it is not a defective mic. Under Volume Control and Playback section, if I unblock my mic,  I can hear myself talking on the speaker. However, the mic wil not record. I have done the alsamixer changes listed in some of the posts, mic to capture, capture to max, etc.  and still no recording. The SB Live! Value card is listed as a supported card on alsa's website.

My alsamixer is version 1.0.13, should I update the mixer?

I have spent many hours reading hundreds of post on ways to get the mic to work. Should I just give up?

---

### Post by cc6000 on 2007-09-03
Ok, I have a new request.

Can someone please recommend a PCI sound card that will definitely work with Ubuntu?  I do not need anything fancy like 5.1. I just have 2 analog speakers and a mic.

I have tried 2 separate SB Live! Value cards, one from Gateway and one from Dell, and both mic inputs do not work.

I would like to use the system for Skype.

A link to Newegg.com would be great, or something I can pick up at Fry's Electornics. The cheaper the better.

Thanks.

---

### Post by xtzc on 2007-09-04
i have a sb live value(the 4 channel model) and i dont know why sometimes the sb is switched of and the onboard sound card kicks in.even if in volume control the selected output card is SB live ...
btw in bios the onboard card is switchef of..
cant seeme to find a ficx to this..
btw its a genuine creative model

---

### Post by malrost on 2007-09-04
open a terminal

```
alsamixer
```

scroll through the mixer and make sure the mic is turned on. You may want to try the dB boost.

Here's a good run down on how to use alsamixer if the interface is throwing you: [http://en.wikipedia.org/wiki/Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")
(Take note: use the arrow keys or +/-, space, and m)

If that doesn't do it, here are some more detailed sound troubleshooting threads:

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

[https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

---

### Post by swan49 on 2007-10-16
I too have a SB live card: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]. And I too had trouble recording from microphone. I have finally found a solution. Set AC97 playback volume to zero. AC97 capture to max. microphone as capture device. "Capture" to a lower value. Now I can record in Audacity. If "Capture" volume is increased, Audacity shows that there is no input in left channel. Right channel is okay. And that explained why arecord would not record anything: it is recording mono by default and mono means left channel only.

I arrived at this resolution by installing 64Studio 32 bit version and comparing the out put from amixer command! Cheers to 64Studio team.

Hope this is useful. Below are some parts of the output from amixer. Wish someone could explain what those numbers mean!

[INDENT]Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 28 [90%] [7.50dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 3 [20%] [4.50dB] [on]
  Front Right: Capture 3 [20%] [4.50dB] [on]
Simple mixer control 'AC97',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 94 [94%] [-2.40dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 94 [94%] [-2.40dB]
[/INDENT]

---

