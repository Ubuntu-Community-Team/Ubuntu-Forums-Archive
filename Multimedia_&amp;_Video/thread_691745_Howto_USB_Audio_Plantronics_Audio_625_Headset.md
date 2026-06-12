---
title: "Howto: USB Audio Plantronics Audio 625 Headset"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by Sabot on 2008-02-08
I just purchased a new motherboard: abit NF-M2SV.  The problem is the Mic port does not function under Ubuntu 7.10.  My solution was to get a USB Headset: Plantronics Audio 625.  The nice thing about the 625 is it uses a USB adaptor to connect the headset.  This gives you a mic in and speaker out that you can use for anything you want:speakers or different headset.

Here is how I got it to work.  The first thing I did was go into my motherboard bios and turn off the sound card.  I wanted to just use the USB Headset only.  I connected my usb headset and started my computer.

I then opened a terminal and entered:

```
asoundconf list
```

This gave me the name of my sound card.  In my case it was default.  In the same terminal I entered:

```
asoundconf set-default-card default
```

Then restarted my computer.

This command is key because without it I was unable to hear startup sounds and flash in firefox would not play audio through my usb headset. This command also makes skype work correctly.

There does seem to be a glitch in alsamixer and the volume applet when using USB Audio.  When you try to adjust PCM playback the left channel does not want to stay linked with the right channel.  You have to keep playing around with it to get both channels at the same level.  Very annoying, but you can get them equal.

---

