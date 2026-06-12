---
title: "Logitech QuickCam Communicate STX won't start"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by osxdude on 2007-11-02
Hey, all. I have just gotten the driver for the Logitech QuickCam Communitate STX. Everything is loaded, and I see my camera in the camera list for Flash apps. However, the camera will not start!!!  A black, blank image appears where the video is supposed to be. How do I make the camera start automatically, or how can I make the camera start on request?

---

### Post by kyphi on 2007-11-03
Although I do not use the same webcam as you have, you may find the information at this link of some help:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

You also need to download 'camorama'.  You will find it in Synaptic.

---

### Post by osxdude on 2007-11-03
Hmmm...I have everything required installed, so I don't need any new software. The computer does not send a (comprehensible to the camera) signal...

---

### Post by kyphi on 2007-11-03
If the camera does not send a signal to the computer, you could try a different USB port - on some computers there are USB 1, 1.1 and 2.

Have you looked at the 'preferences' settings in Camorama?

---

### Post by Radon on 2007-11-03
My QuickCam STX works fine with the [Gspca/Spca5xx]("http://mxhaard.free.fr/spca5xx.html") driver.  Reinstall it or compile the latest version and try it out in Camstream.  I'm getting ~12FPS at VGA resolution, and the microphone is superb quality.

I'm using OpenWengo for my webcam because Skype sucks!  OSS FTW!

---

### Post by osxdude on 2007-11-03
Well, turns out all I needed to do was a reboot. Thanks, anyway.

I am streaming at [http://www.ustream.tv/channel/osxdudetv]("http://www.ustream.tv/channel/osxdudetv"), BTW. Whole reason why I wanted this to work.

---

### Post by Radon on 2007-11-06
> **osxdude said:**
> Well, turns out all I needed to do was a reboot. Thanks, anyway.
Hehe, I'll remember to ask this question the next time someone has a problem :)
Good to hear it's working alright for you!

---

