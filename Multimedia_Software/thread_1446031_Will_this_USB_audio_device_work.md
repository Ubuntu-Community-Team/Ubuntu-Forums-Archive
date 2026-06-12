---
title: "Will this USB audio device work?"
date: 2010-04-03
forum: Multimedia Software
---

### Post by Edoardo_P on 2010-04-03
Hello, I was wondering if this USB audio device will work. It's an external USB soundcard, digital-to-analog and USB-to-SPDIF converter.
 
Unlike others USB external "no-driver-required" soundcards, which are limited to USB 1.1 to 16bit/48KHz, this one works with USB 2.0 (sampling the audio up to 24bit/96KHz)
 
[http://www.docethifi.com/UDAC.pdf](http://www.docethifi.com/UDAC.pdf)
 
The producer claims that it does not need any driver on Win or MacOSX because "the computer recognizes the interface automatically because the device goes directly to the processor core as a composite device".
 
I've sent them a mail, I've been aswered that they haven't tested it with linux yet but "there should not be problems"; by the way, I have been told that _it should be verified wheter the audio interface or the midi interface in Ubuntu limits the dialog between the device and the core._
 
WTF, can anyone help me please?
 
 
... Can anyone help me here?

---

### Post by Edoardo_P on 2010-04-03
bump:popcorn:

---

### Post by Edoardo_P on 2010-04-04
Happy Easter bump ):P

---

### Post by cchhrriiss121212 on 2010-04-05
Devices that do not need drivers should work without any configuration in linux. A few questions:
Have you tried plugging this in yet? If not, do so now and enter "aplay -l" into a terminal to see if it is recognised as an audio playback device.
What are you planning to do with it? and which programs will you be using?

 > _it should be verified wheter the audio interface or the midi interface in Ubuntu limits the dialog between the device and the core._

This just means: is the software (Ubuntu) designed to limit audio devices intentionally or otherwise? It should not, but you can have trouble with interference form other devices using other usb ports.

---

### Post by Edoardo_P on 2010-04-05
Hello, thanks for the answer
 
 
I do not have tried it yet. I don't have the possibility to plug it anywhere before buying it at the moment.
 
I will use it to connect it to an amplifier from its analog audio outputs or to another digital-to-analog converter from its SPDIF out... 
 
I will use it with programs such as Amarok, Audacity or Songbird, I don't know which one will be my favourite yet. I will play *.wav and FLAC files...
 
Thanks

---

### Post by cchhrriiss121212 on 2010-04-05
If you would like gapless playback (and who doesn't) then I'd recommend quod libet.

---

### Post by Edoardo_P on 2010-04-05
> **cchhrriiss121212 said:**
> If you would like gapless playback (and who doesn't) then I'd recommend quod libet.
 
 
Thanks, is it a player or what?  =P~

---

### Post by gordintoronto on 2010-04-05
> **Edoardo_P said:**
> The producer claims that it does not need any driver on Win or MacOSX because "the computer recognizes the interface automatically because the device goes directly to the processor core as a composite device".


This is obviously bafflegab.

I hope I'm not just prejudiced because of the poor English, but I would insist on trying it using a LiveCd before I would consider spending money on it.

---

### Post by cchhrriiss121212 on 2010-04-06
> Thanks, is it a player or what?  =P~
Yep, I've tried many different audio players, and this is by far the best. It handles large libraries easily and has a superb tagging system. You can find it in synaptic.

> This is obviously bafflegab.

I hope I'm not just prejudiced because of the poor English, but I would insist on trying it using a LiveCd before I would consider spending money on it.
Like I said there are usb devices that need no drivers (I own one). But +1 for trying this out if you can, especially if it is expensive.

You said you were going to maybe run this through another DAC, in which case you might want to look at a pci sound card like the alsa supported m-audio 24/96. PCI>USB, unless you are using a laptop of course.

---

