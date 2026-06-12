---
title: "NVidia forgets settings, only communicates with 5.1 receiver when it wants (HDMI)"
date: 2013-06-02
forum: Multimedia Software
---

### Post by The Bright Side on 2013-06-02
Hello fellow Ubuntu experts,

I recently bought a new receiver and switched from analogue 6-channel audio to my Nvidia card's HDMI for audio. So far, I have not figured out how to make my PC communicate with the receiver reliably.

**My setup:**

Graphics card: Nvidia Geforce GTX 460
Receiver: Yamaha RX-V661
VGA: adapter cable Geforce DVI out to SyncMaster VGA in
HDMI: cable from Geforce HDMI out to RX-V661, another HDMI cable from RX-V661 out to SyncMaster DVI in

To illustrate:

[IMG]http://www.knowingme.org/nvidia-issues/layout.jpg[/IMG]

**Problem 1 (annoying): Nvidia forgets everything**

This is what the Nvidia control panel usually looks like:

[IMG]http://www.knowingme.org/nvidia-issues/Nvidia-Standard.jpg[/IMG]

The CRT connection is the one I am using. The other one is the same screen, and I can see the image when I switch over to the digital input. I don't care about that, I just want the sound, so I set my Nvidia settings to this:

[IMG]http://www.knowingme.org/nvidia-issues/Nvidia-Clones.jpg[/IMG]

Reboot and Nvidia forgets it all. Which makes my mouse cursor disappear onto a screen I cannot see when I make the mistake of moving it to the right edge.

I tried saving to Xorg.conf (as an administrator) but the settings just aren't retained.

I've seen threads with this problem dating back to 2008. Really sad.

**Problem 2 (critical): no communication between receiver and Nvidia!**

In about 20% of all attempts, Nvidia will properly recognize the connected receiver and use it as a sound output device. On most other cases, it will recognize my Samsung SyncMaster screen twice, and no audio will arrive at the AVR. As seen above, the only thing the receiver does is pass all signals right through to the screen, it's as if it wasn't there. I have set the receiver's own options to not do that.

I don't know what to do to make them communicate reliably! It just works when it feels like it. I thought I had it figured out when it started working when I turned my receiver on **after** the PC; but now that doesn't work either. I will keep trying right now and once I get them back together, I'll post a screenshot of my Nvidia settings to show how it's set up when it works.

Until then, any input is appreciated. I'm at the end of my wits. I just can't see the pattern.

EDIT:
Ubuntu 13.04 64 bit
Nvidia drivers 304.88

EDIT 2: added drawing to illustrate my setup

---

### Post by The Bright Side on 2013-06-02
Here's what I want:

[IMG]http://www.knowingme.org/nvidia-issues/Nvidia-Correct.jpg[/IMG]

I just achieved this by unplugging the HDMI cable that goes from the receiver to the screen, thus physically taking away the option to pass the signal through. It now ends in the RX-V661. I would surmise this is a reliable way to get what I want, but it's pretty brute. I will keep it like this for the time being and see if it solves my problem reliably. I guess if getting sound from PC means plugging in the HDMI cable whenever I want to use the Blu Ray player, then so be it.

---

### Post by gordintoronto on 2013-06-02
Any time you use adapter cables, the setup can be flakey. I take it the Syncmaster has no HDMI input? If you get everything working, you might still find that video and audio are out of sync.

---

