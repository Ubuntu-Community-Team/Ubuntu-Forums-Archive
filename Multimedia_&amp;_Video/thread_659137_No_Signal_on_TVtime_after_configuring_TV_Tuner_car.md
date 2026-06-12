---
title: "No Signal on TVtime after configuring TV Tuner card"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by hnprashanth on 2008-01-05
I have successfully installed Tv Tuner card (which uses Philips Saa 7130).
But if i open TVtime it shows "No Signal". 
I have connected cable properly & works fine on windows.
I have selected PAL as TV system.
I also tried other TV standards also.
I don't understand why it shows "No Signal":confused:

---

### Post by Walc on 2008-01-05
scan for channels......

right mouse click>channel management>scan for channels

ud probably have to master sound standard as well....

---

### Post by hnprashanth on 2008-01-05
thanks for the reply,
nothing happens when i scanned for channels.
I also tried changing sound standard, but no result.
any idea?

---

### Post by wolfen69 on 2008-01-05
here [http://linux.bytesex.org/v4l2/saa7134.html](http://linux.bytesex.org/v4l2/saa7134.html) is the driver for it.see what happens.

---

### Post by wolfen69 on 2008-01-05
you will also need V4L checked off when you run:
```
sudo dpkg-reconfigure xserver-xorg
```
only concern yourself with the video modes.

---

### Post by hnprashanth on 2008-01-06
But drivers of SAA 7134 is alreadyincluded in my kernel. Should I need to install them again?

I am also able to select between inputs which my card provides like Television, Composite 1, composite2 & S-Video

---

