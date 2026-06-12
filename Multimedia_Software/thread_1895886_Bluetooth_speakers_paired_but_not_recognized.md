---
title: "Bluetooth speakers paired but not recognized"
date: 2011-12-15
forum: Multimedia Software
---

### Post by BlackWidower on 2011-12-15
So I have a set of Bluetooth speakers, (Creative D100, not that it matters), and I managed to pair it with my Ubuntu server which has a small bluetooth dongle.  

Here's the problem: That's all I got.  I open VLC and no sound comes out...from anywhere.  I assume it's getting to the main sound card, but there's no speakers plugged in there because I don't have any.

After a bit of tinkering I managed to determine that PulseAudio is receiving the audio, but it's not passing it onto the Bluetooth speakers.  In fact, as far as I can tell, it doesn't know I have Bluetooth speakers.

The only hardware sound device listed under Sound Preferences is "Internal Audio" which is obviously the main sound card.

Is there some step I'm missing?  How do I get PulseAudio to recognize the Bluetooth speakers?

As for what I'm using to pair the speakers...gnome-bluetooth.  I think it's just a front-end for bluez, but I'm not sure.

---

### Post by hansdown on 2011-12-15
Hi, BlackWidower.

In your sound preferences, click output.

Your speakers should show there.

---

### Post by BlackWidower on 2011-12-15
Okay, I probably wasn't clear enough.  I've already looked there and under the hardware tab.  All that's listed is the internal device.  Nothing about Bluetooth.  I just double checked, and there's still nothing.

Could I be missing a package?  Space is at a premium so I've been pretty paranoid about only installing packages I'm certain I need.

---

### Post by hansdown on 2011-12-15
Sorry, I wasn't paying enough attention.

Could you open a terminal, and paste the results of

```
lsusb
```

---

### Post by BlackWidower on 2011-12-15
I figured out the problem.  It didn't come to me until I wrote my last post.  I **was** missing a package.  

pulseaudio-module-bluetooth

Sorry if I wasted anyone's time.

---

### Post by hansdown on 2011-12-15
Glad you fixed it, BlackWidower.

It's never a waste of time.:D

---

