---
title: "Set laptop external monitor as primary"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by Ragnarol on 2006-09-30
Hi,

I have a laptop with an integrated ATI x200.

Recently i bought an external 20"W monitor. After googling a bit I was able to enable the external monitor to work in his native resolution 1680x1050.

My current problem is that when I use mplayer to reproduce anything using xv output It reproduce it in the laptop screen not in my new one.

My current configuration is "clone" monitor. How can I say Xorg that the primary screen should be the external one?

I attach my xorg.conf.

thanks in advance

---

### Post by Ragnarol on 2006-10-01
Mario Vukelic answer this question in the ubuntu mailing list. 

To fix it you need to add the following line to your device section in xorg.conf:

# Xvideo on external screen
    Option "OverlayOnCRTC2"

Thanks to Mario!

---

