---
title: "How do you save resolution in xserver"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by captgadget on 2007-03-31
I can get to xserver with sudo dpkg-reconfigure xserver-xorg. Then as I go through the various steps I eventually get to the window that asks for a monitor name. I type one in and come back and it's gone. How do I save that? Then I go on to the window that shows all the resolutions. I arrow  down to 1280x1024, but how do you save it? Then I get to horizontal and vertical rates and put those in but they don't stay so how do I save all this information?

---

### Post by Trab on 2007-03-31
you can do it by manually editing your /etc/X11/xorg.conf if you understand what you're doing.

if you are just trying to mess with resolution from now on i suggest using
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

cheers,
Trab

---

### Post by captgadget on 2007-03-31
While I was there I saw the window that shows all the resolutions but how do you save the one you want? That's what I need to know.

---

### Post by kellemes on 2007-04-02
To 'save'  it as you say, you have to press the spacebar.

---

