---
title: "Headphone jack problem with Audigy LiveDrive"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by Chott on 2008-04-21
I've been trying to get a working recording setup going here on this new system for a week now. I previously had a great setup with Slackware on some older hardware, sporting an Audigy Platinum card with LiveDrive. Everything worked great with Jack and Ardour. 

I recently built a new system and went with Ubuntu. I love Ubuntu thus far, having used Linux for 8 years now I'm tired of manually dealing with updates. 

I moved my trusty Audigy card over, and after a few hiccups, finally got the Mic2/Line2 input on the LiveDrive working. However, I still have NO output at all from the LiveDrive headphone jack. This used to work in Slackware, and a quick reboot to XP confirmed the drive is working properly. I just cannot get this front panel to work right.

I've tried setting ALL outputs to max on, unmuted everything, toggled every switch in the mixer, still no output on the headphone. When I boot the system and listen with the headphones, I get the slight hiss indicating the phones and jack work, up until the kernel initializes the sound, which it then goes completely mute. 

Does anyone have any advice at all?

I've tried QAmix, Kmix, alsamixer. I've read the docs for alsa in the kernel source, and everything I can find in a google search. I just don't get what I might be missing here.

---

### Post by Chott on 2008-04-21
Okay, just following up here. Somehow it started working (don't know exactly how) but it appears that the "Front" volume control is essential for some crazy reason for that output. I know I had previously turned all of the outputs up, perhaps it was setting the module options in /etc/modprobe.d or something.

If anyone else is having problems with the LiveDrive, here is my /etc/modprobe.d/snd-emu10k1:

```
options snd-emu10k1 extin="0x3fc3" extout="0x1fc3"
```

Not positive what exactly fixed it, but it works now.

---

