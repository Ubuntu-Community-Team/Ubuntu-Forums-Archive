---
title: "webcam logitech c500 not installing to /dev/video"
date: 2010-02-19
forum: Multimedia Software
---

### Post by DanBender on 2010-02-19
I'm trying to see if a webcam I have works well with my TV-box system running Mythbuntu 9.10. It's a Logitech Webcam C500 attached through a USB 1.1 hub.

When I attach it to my laptop running vanilla Ubuntu 9.10, it installs to /dev/video0 and works fine. However, on plugging into the tv-box nothing happens. It shows up under lsusb, but I don't get any new /dev/video* entries. I currently have three entries, video0, video24, and video32, but these are assigned to the three inputs of my TV tuner card (nstc tuner, QAM tuner, SVideo-in; not necessarily that order).

What's the best way to force the system to recognize it as a video device?

I'm sure I'm going to need to be wrangling around with the audio part of the webcam in a similar fashion (being the same device and all), and I *believe* I'm having a similar issue with my USB IR remote receiver (It also doesn't work, as if it's not being recognized). But I'm focusing on the webcam right now. If it is indeed a case of assigning a USB device to a proper /dev entry, I suspect that the process would be the same for fixing this other problem. Just a guess, though.

I've tried a couple of things I found so far from searching the forums and google, but nothing that's worked yet -- and it wasn't clear to me what some of those things actually do, so I'm somewhat gun-shy about haphazardly writing and changing files, especially in directories where I need root access.

Any good, simple pointers?

Thanks in advance,
-Dan

---

