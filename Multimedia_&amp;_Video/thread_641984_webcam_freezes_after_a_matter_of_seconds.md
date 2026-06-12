---
title: "webcam freezes after a matter of seconds"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by gluonman on 2007-12-16
Aloha.

I just bought a Logitech Quickcam Express. I used module-assistant to build and install qc-usb, spca5xx, and gspca. After all of that, I installed camorama and it detected my cam just fine and there was movement and everything. I was just about to celebrate when it froze. I had to force quit the application and try to run it again. Same thing. Every time I attempt to open camorama to test my webcam it will run for a random number of seconds and then freeze. I figured it might just be camorama. So I ran it in kopete. Same thing, except it causes all of kopete to freeze and I have to force quit.

I don't know what's causing it to freeze. Is there anything else I need to install to stop this from happening? What can I do?

---

### Post by orzechowskid on 2007-12-23
This is happening for me too.  Camorama will run for a few minutes then freeze up completely, making me have to kill it.  I ran it from the terminal and saw that the message

```
Xlib: unexpected async reply sequence 0x43b44)!
```

was generated (with different sequence numbers) each time it froze.  Not sure how to solve this, but poking around the source code didn't seem to unearth any obvious problems.

---

