---
title: "Which headset to get?"
date: 2009-01-22
forum: Multimedia Software
---

### Post by rfkrocktk on 2009-01-22
I need to get a headset for Ubuntu so I can listen to music through it and also so that I can record my voice in a screencast with it. I already installed recordMyDesktop which works great, but now I need to record my voice with it. I'd also like to be able to use it with Skype.

Does anyone have any recommendations for what to get? I'd like to get a USB headset/mic, but I'm open to other options.

---

### Post by markbuntu on 2009-01-22
I got a plantronics usb headset and it works pretty good. It is the one with the usb dongle that has separate jacks for the mic and headphones. Ubuntu/alsa sees it as a c-media headset so I guess that c-media makes the dongle at least. I was able to use it out of the box.

The headphones and mic work well and I can also plug in any other headphones or mic or use the headset with my sound card without the dongle. I use my high quality sony headphones all the time with this dongle, it produces quality sound.

It was definitely worth the extra $10 for all that versatility.

---

### Post by rfkrocktk on 2009-01-29
This one?
[http://www.amazon.com/gp/product/B000VVXO7E/sr=8-1/qid=1233269163/ref=olp_product_details?ie=UTF8&me=&qid=1233269163&sr=8-1&seller=](http://www.amazon.com/gp/product/B000VVXO7E/sr=8-1/qid=1233269163/ref=olp_product_details?ie=UTF8&me=&qid=1233269163&sr=8-1&seller=)

---

### Post by cariboo on 2009-01-29
I got a generic bran usb headset at Staples, you have to change the setup in System-->Preferences-->Sound to output the sound to your headset instead of the sound card and capture to your usb device. In my case it shows up in lsusb as:

```
Bus 001 Device 006: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
```

and in sound preferences  by it's usb id.

I'm  running Juanty and the sound preferences applet is totally different, or I'd show you a screenshot.

Jim

---

### Post by Denestria on 2009-01-29
I have a Sennheiser headset that I use for Skype, comes with both USB or regular jacks.  I think they are PC155s?  Between my husband and I, we have like 4 pairs of different Sennheisers and they all have the ID# on the outside of the cup... that is all except for my headset and I don't remember exactly which ones I bought.  So they might be a slightly different one like 151s or 161s.

---

### Post by placidoaps on 2009-02-09
I have a logitech usb headset ([http://www.staples.pt/Produto.aspx?id=57128&top=151]("http://www.staples.pt/Produto.aspx?id=57128&top=151")). I had a jack headset but it recorded a lot of noise (Sound card problem).
At first the usb headset recording made some Huuum noise. I found out that it was the laptop AC adapter in the top of the table where I was recording, so I put it as far as I could and no problem then. Personaly I have a beter experience with Usb Headset.

In my case, to use the USB headdet I had to change:
System - Preferences - Sound
Audacity :: Edit - Preferences - Audio I/O :: **OSS:/dev/dsp1** (Playback and Recording)
Recordmydesktop :: Advenced - Sound - Sound Device :: **plughw:1,0**

---

### Post by markbuntu on 2009-02-10
If you are using pulseaudio the usb headset will just show up in the pa volume control so you can switch streams to it. You can also make a virtual device that will use all you sound devices at once. 

There is some explanation how to do all that here that will work for Hardy, Intrepid and probably Jaunty also:


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by rfkrocktk on 2009-02-10
I got the aforementioned headset ([http://www.amazon.com/Plantronics-DSP400-Foldable-Multimedia-Headset/dp/B000VEMNRS/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1234302879&sr=8-1](http://www.amazon.com/Plantronics-DSP400-Foldable-Multimedia-Headset/dp/B000VEMNRS/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1234302879&sr=8-1)), and I've been having problems with it. 

Whenever I try recording with it, I will get garbled audio, as if it's not transcoding correctly. I've tried using it with recordMyDestkop and that's not working, so I just selected --no-sound from the options list and it records fine, without audio, but even when I try recording it with Audacity, it doesn't sound too hot. I'll get dropouts and crazy transcoding errors with Audacity, which doesn't really help as I'm trying to produce 1-2 hour screencasts. In Skype, it's the same story. It'll get my voice, but there will be garbled parts, dropouts, and sound repetition over 1-2 seconds. 

Any ideas? I recently noticed that I've got BIOS bug 81 on startup, but it doesn't seem to be affecting things, could it be the culprit?

---

