---
title: "2 sound cards and a jack"
date: 2017-06-29
forum: Multimedia Software
---

### Post by michaelairving1812 on 2017-06-29
Hello everyone. I've been banging my head against a wall on this one. There are posts on my issue, but dating back to Jaunty days.

I want to install Kodi on a mini pc through alsa or jack, but its important that I can use a second sound card! I have 2 usb sound devices from Behringer. One will be the main out put, and the other, I want to dsp through Jack-Rack and qjackctl. I can get jack and jack-rack running, but jack only uses one card. I've tried various ways, and lastly tried "alsa_in", with jack running and a terminal open, I get

```
alsa_in
Capture open error: No such file or directory
```

It must work, because info on the www goes back to Jaunty, Ubuntu 8? Has Zesty changed? People have been listening on laptop speakers whilst using earphones at the same time etc

Please, help Thanks

---

### Post by CatKiller on 2017-06-29
If the information that you've been reading is old, you possibly have a jaundiced view of PulseAudio since it had a bumpy introduction. It lets you route audio streams about and will give you a monitor stream for each of your cards which may prove useful for what you're trying to achieve. Or it might not. It does integrate well with both ALSA and JACK, though.

It's a long time since I played around with JACK, though, so I can't give you more specific guidance.

---

### Post by michaelairving1812 on 2017-06-29
Thanks, so  how can I get this to work? I was trying with two raspberry Pi's, but the one doing Jack, keeps crashing ! Still early days for Arm :-(

---

### Post by CatKiller on 2017-06-29
> **michaelairving1812 said:**
> Thanks, so  how can I get this to work? 

I don't know.

I don't know what it is that you're trying to achieve, and I haven't used JACK in a loooong time, and even when I did it was multi-channel on a single card.

You've got one card that handles audio output from Kodi, yes? So that's connected to some kind of output device.

Then you've got another card that's doing... what, exactly? Are you manipulating the output from Kodi in some way? You can do that just by copying the stream on the same card. You wouldn't need a second card at all.

If you're generating a different audio source as well that's going to a different audio output, I don't really see the problem. One card spits out the audio from Kodi to wherever it's going, and the other one spits out the audio from whatever else it is that you're doing at the same time to wherever *that* is going.

Without more details of what you're trying to do, no one can help you do it.

---

### Post by michaelairving1812 on 2017-06-29
Hi CatKiller, I currently use a Raspberry Pi for kodi. It has a Hifi Berry DAC for its main audio out. I then take a feed off of the speakers, to another PI. I use Jack-Rack on this Pi solely to DSP my subwoofer, using Steve Harris plug ins. I use the Triple band parametric with shelves to control my subwoofer. This second Pi is up to date, but keeps crashing after a couple of hours. Because ARM is buggy, and I have a mini PC, and 2 sound cards, I thought it might be better to install Kodi on it, one sound card does main Left Right out, and the other card Jack and Jack-Rack! 

Sorry, hope its not too confusing?
Thanks

i.e. kodi stereo out through one card
      Kodi to jack & Jack-Rack second card 

similar to a crossover 1 signal 2 outputs High frequency and low frequency

---

### Post by CatKiller on 2017-06-29
> **michaelairving1812 said:**
> Hi CatKiller, I currently use a Raspberry Pi for kodi. It has a Hifi Berry DAC for its main audio out. I then take a feed off of the speakers, to another PI. I use Jack-Rack on this Pi solely to DSP my subwoofer, using Steve Harris plug ins. I use the Triple band parametric with shelves to control my subwoofer. This second Pi is up to date, but keeps crashing after a couple of hours.

So this is what you're doing now?

> Because ARM is buggy, and I have a mini PC, and 2 sound cards, I thought it might be better to install Kodi on it, one sound card does main Left Right out, and the other card Jack and Jack-Rack! 

And this is what you want to do instead?

What outputs do you have on the cards and the computer? And what inputs/outputs do you have on the subwoofer? My sub has its own crossover, so I pass left/right to that, and then take left/right from there to each of my mains. I'm guessing that you wouldn't be doing this if you could just do that, though. Have you considered just getting a hardware mixer for your crossover?

So if I understand correctly, you're taking one stereo stream, copying it, and sending one copy through a high-pass filter and the other through a low-pass filter, and you're trying to then route the high-pass to one set of outputs and the low-pass to another set of outputs? If you have an LFE output to any of your sound devices, that's exactly what happens there. And you're using two cards so that you have enough outputs? I think that would be beyond what you could easily do with bare ALSA or PulseAudio without a hardware LFE channel, but should certainly be doable with JACK. I think when I was messing around with JACK previously, there was a virtual patch bay that made signal routing much easier to understand. It was probably Patchage. Just follow the signal path and remember what you're trying to achieve.

[This page]("http://www.jackaudio.org/faq/multiple_devices.html") details ways that you can use multiple cards with JACK. The sensible way, according to that page, is to not let JACK use either of the cards directly. Instead you use ALSA mapping to make a pretend device that has the combined outputs of all your sound cards. Then you use JACK as outlined above to route your signal to the appropriate outputs of the pretend device, which ALSA will then translate back to the hardware outputs.

---

### Post by mashaffer on 2018-02-21
I have this same issue. I want to try the merged device approcch at the link above but am unsure of how to name my second slave device. It is a CM108 USB device. aplay -l gives...

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

CARD 4 is the usb device.

---

