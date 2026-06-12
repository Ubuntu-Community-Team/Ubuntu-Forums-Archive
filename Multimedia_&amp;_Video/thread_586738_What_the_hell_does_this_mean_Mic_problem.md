---
title: "What the hell does this mean? Mic problem"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by ashinshanghai on 2007-10-22
My built-in webcam mic is not working after installing Gutsy. Yes, I checked that it was not muted and the volume was up.

After this, I went to System>>Pref>Sound and rant the test on ALSA sound capture. In addition to an awful noise, I got this message:

```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

Can anyone tell me what this means, or more importantly how to solve the problem? Also, it is not recognizing my external mic when plugged into line-in.

Thanks.

---

### Post by kennedyjch on 2007-10-24
Have same issue with my workstation (Asus M2N-MX SE). Sound and mic worked fine in Feisty Fawn version. But after upgrade to Gutsy Gibbon, sound works but microphone does not. Get same message as you.

---

### Post by chrisstankevitz on 2007-11-11
me too.  Mine works under windows so I know it's a problem with linux, not my hardware.

---

### Post by chrisstankevitz on 2007-11-11
fixed:

double-click speaker icon in upper right
File | Change Device | HDA Intel (Alsa Mixer)
Edit | Preferences | Check all boxes
Unmute everything, no red X allowed anywhere

Good luck,

Chris

---

### Post by Darganot on 2007-11-11
I have the same problem with a logitech ps2 usb headset.  The above solution doesn't seem to work.

I have a soundblaster audigy se.

---

