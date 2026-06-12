---
title: "Video card in 3D games much slower on Ubuntu than Windows"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by Starlight on 2007-08-16
Hello!

I have a problem... it seems that my video card (ATI Radeon 9550) is much slower in Linux than it is in Windows. For example, the game Nexuiz is playable in quite good quality when I run it on Windows, but on Ubuntu even if I turn all effects off and decrease the quality of everything, the game slows down to around a few fps so often that it's impossible to play it (sometimes it gets so slow that the fps counter turns red and changes into spf!) I have the latest fglrx driver from the repository installed, and it seems to be working properly... for example, glxinfo says "Direct rendering: yes". So I have no idea what makes it so slow... How can I find out and fix it?

---

### Post by Starlight on 2007-08-17
bumping the thread...

And also just wanted to say that I played Nexuiz on Ubuntu a few months ago and it was well then.

---

### Post by eye208 on 2007-08-17
> **Starlight said:**
> it seems that my video card (ATI Radeon 9550) is much slower in Linux than it is in Windows.
This is a well-known issue with ATI's fglrx driver.

[http://www.phoronix.com/scan.php?page=article&item=731&num=1](http://www.phoronix.com/scan.php?page=article&item=731&num=1)

---

### Post by Starlight on 2007-08-17
> **eye208 said:**
> This is a well-known issue with ATI's fglrx driver.

[http://www.phoronix.com/scan.php?page=article&item=731&num=1](http://www.phoronix.com/scan.php?page=article&item=731&num=1)
ok, thanks!

The weird thing is that I remember playing Nexuiz on Linux a few months ago, and it was fast then...

---

### Post by raijinsetsu on 2007-08-17
Did you make sure that 3d acceleration was turned on? :)

---

### Post by RomeReactor on 2007-08-17
Hi. Make sure you have direct rendering enabled:
```
glxinfo | grep rendering
```

---

### Post by Starlight on 2007-08-17
> **raijinsetsu said:**
> Did you make sure that 3d acceleration was turned on? :)
hmm...how to do it? :)
> **RomeReactor said:**
> Hi. Make sure you have direct rendering enabled:
```
glxinfo | grep rendering
```

Yes, it's enabled. :)

---

