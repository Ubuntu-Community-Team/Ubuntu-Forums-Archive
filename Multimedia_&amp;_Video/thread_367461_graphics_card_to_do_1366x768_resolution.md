---
title: "graphics card to do 1366x768 resolution"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by jethro10 on 2007-02-22
Right,
It looks like widescreen is hard work from the various posts in this forum.
I have a widescreen LCD tv at 1366x768 resolution.

So i'll turn this round. Which graphics card is the simplest to get to go widescreen at 1366x768 res and i'll go buy it.

Ta
J

---

### Post by ridgeone on 2007-02-26
I'm running a nVidia GeForce 6800GT with the new 9746 drivers on a 32" Viewsonic n3200w LCDTV @ 1280x768. Native res is 1366x768 but I haven't tried it yet since 1280 looks fine. Just add the resolution to your xorg.conf file, save and reboot.:guitar:

---

### Post by williammanda on 2007-02-27
I have a Westinghouse 42" lcd monitor (its native resolution is 1366 * 768) and I am running the 1.0-9746 driver. It sets my resolution at 1360 * 765 (I think, not at my computer) and stretchs it out to fill the screen. I have a EVGA Nvidia 7300 w/ 512 Mb. I let the Xorg.conf file read the edid of the monitor with very little changes.
Thanks

---

### Post by jethro10 on 2007-02-28
Right,
Used an ATI radeon 9600, put on binary drivers and its there. Dead easy.

used this howto, work correctly at 1360x768, size was autodetected after this :-
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

thanks
Jeff

---

### Post by gergtreble on 2007-03-08
Thank you immensely sir.

---

