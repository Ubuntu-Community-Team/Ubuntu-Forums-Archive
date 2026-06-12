---
title: "QuickCam Orbit AF?"
date: 2014-06-02
forum: Multimedia Software
---

### Post by juan_carlos4 on 2014-06-02
how install a Logitech QuickCam Orbit AF?

---

### Post by Bucky Ball on 2014-06-02
*Thread moved to **Multimedia & Video**.*

Welcome. You might have better luck here. People will see you are new and will be gentle. ;)

Plug it in. What happens? Open Cheese. Does it see the camera? Is it USB? If so, when you have it plugged in, open a terminal and run:

```
lsusb
```

Also, immediately after you plug it in and before doing anything else, run this command:

```
dmesg
```

Please post the lines at the end of the output which should say something about the USB device you just plugged in. You might also get some clues here:

[https://duckduckgo.com/?q=Logitech+QuickCam+Orbit+AF+ubuntu](https://duckduckgo.com/?q=Logitech+QuickCam+Orbit+AF+ubuntu)

---

### Post by MikeCyber on 2014-06-03
I had it running all fine in 12.04 but haven't tried in 14.40 so far. If I remember correctly, I was able to pan etc. with guvcview. (not sure anymore)

---

