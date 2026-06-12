---
title: "Very dark webcam"
date: 2008-07-08
forum: Multimedia Software
---

### Post by Estesark on 2008-07-08
I'm having a frustrating problem with my webcam, a "Microdia Sweex Mini WebCam". Ubuntu recognises it, so it works, but the picture is incredibly dark. It is so dark that only direct sources of light can be seen.

Example - my hand in front of a standing lamp, in a well-lit room:

[IMG]http://i216.photobucket.com/albums/cc295/Mustahattu/hand.jpg[/IMG]

I've searched the forums and the web, and tried what I could (namely editing /etc/modprobe.d/options), but without success. I've also changed the brightness/contrast settings in programs like camorama, but they do not really do anything, and often the camera quickly re-adjusts itself after I make these changes.

The webcam works without problems in Windows.

Any help is greatly appreciated. Thanks.

---

### Post by accord on 2008-07-13
I also have this webcam, and ran into this problem today. Searching the forums revealed the solution:
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

Following the instructions and I ended up with an acceptable image. It should work perfectly for you.

---

### Post by Estesark on 2008-07-13
I tried that, and it did get a little brighter, but the colour went very strange. I had to restart my computer for the changes to take effect, and I really can't be bothered to do that a hundred times to fine tune every setting on the camera. I was hoping there would be a simple way to do it.

Thanks all the same.

---

### Post by accord on 2008-07-15
Yes, the colors do get a bit off. In the link there is a way to set the options in /etc/modprobe.d/options so that you won't have to reconfigure them every time.

---

