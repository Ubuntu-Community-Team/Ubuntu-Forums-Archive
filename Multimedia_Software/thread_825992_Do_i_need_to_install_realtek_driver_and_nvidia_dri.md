---
title: "Do i need to install realtek driver and nvidia driver?"
date: 2008-06-11
forum: Multimedia Software
---

### Post by Milardo on 2008-06-11
Hi, is it necessary to install realtek sound driver and nvidia display driver in hardy?

---

### Post by wolfen69 on 2008-06-11
if your sound works, then you are OK. as far as the video driver, it depends if you need 3D acceleration.

---

### Post by Milardo on 2008-06-11
Thanks for your reply. I got sound but when Im playing enemy territory no sound is available. Also have you tried to install latest nvidia driver from their website for linux?

---

### Post by FuturePilot on 2008-06-11
The problem with sound may be a conflict between PulseAudio.
As for the driver I would recommend use the Hardware Driver manager under System&#8594;Administration&#8594;Hardware Drivers. It's the same Nvidia driver than you can download from Nvidia's site, though it might be a slightly older version, but it's all nicely packaged up specifically for Ubuntu, so you don't have to worry about X breaking on kernel updates as you would if you installed it manually.

---

### Post by Milardo on 2008-06-11
How should i go about disabling pulseaudio?

---

