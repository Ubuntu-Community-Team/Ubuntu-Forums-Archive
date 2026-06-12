---
title: "Is &quot;Pulse Audio Device Chooser&quot; What I Want?(long)"
date: 2009-05-18
forum: Multimedia Software
---

### Post by wbee on 2009-05-18
Hello,

My Soundblaster Audigy SE card is recognized as sound card zero.

The tuner portion of my MSI TV Anywhere Plus card(a Phillips saa7134 chip) is recognized as card number one.

In 8.10,I fed the output of from the TV card to the shared "line in/microphone" input on the Soundblaster card,but in 9.4,that does not work.

In Preferences>Sound,the tuner chip is recognized as saa7133[0] OSS PCM device(OSS). In the "sound capture" catagory,it is recognized as saa7133[0] 7134 PCM(alsa). In the device mixer menu,the capture function is saa7134-saa7134 PCM Pulse Audio Mixer (OSS Mixer).The Playback function is CAO106 Pulse Audio Mixer SAA 7134 (alsa Mixer)

Setting all the volume preferences in all the possible combinations(yes,it is unmuted and no,I'm not confusing it with digital input,no sound,no sound at all.)

I have been stymied trying to get these all to connect.

**So,is the "Pulse Audio Device Chooser" the missing link I've been looking for?

Yes,I know,I could spend a day messing with it,but if you know the answer,if I install the plug in,and set up Pulse as mentioned in Mark Buntus thread,should I be able to select either sound card from the Applications>Sound and Video menu and get both TV video and audio?

********

I do not yet have a handle on Pulse Audio and I say that with due deference and appreciation to those who developed it. The diagram on its document page looks like an analogy of a cardio/vascular system,with everything being "pumped" through a "heart". Perhaps that is my problem;I've always considered sound to be a nervous system. If I wanted to set up my computer as as recording studio heart,I'm sure it would do that expertly---once I figured it out.

I freely admit that pulse is over my head,so far,and if there was a way to use the alsa mixer to get either card's audio feed,I would go that way. (Hint):-)

But again,if I install this plug in,and take the time and trouble to learn pulse audio,should that work for what I describe or am I missing the point completely?

------------

Thank you.

---

### Post by wbee on 2009-05-21
Bump.

I'm trying to read Pulse Audio documentation as time allows.

---

