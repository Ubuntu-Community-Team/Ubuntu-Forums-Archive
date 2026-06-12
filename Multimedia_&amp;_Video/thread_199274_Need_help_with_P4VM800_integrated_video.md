---
title: "Need help with P4VM800 integrated video"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by Swami2 on 2006-06-18
It seems like this might be a frequently asked question, but I have been unable to find a recent thread about it.

I am using Ubuntu 6.06 with an Asrock P4VM800 motherboard with integrated S3 Unichrome video.

The X configuration process doesn't recognize the video card and leaves me with the horrible looking vesa driver.

lspci says

0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)

What's the easiest way to get this working correctly?  Thanks!

---

### Post by kalinicm on 2006-06-18
I've installed Edubuntu, and am running thin clients using the same motherboard mentioned above. All works well by default, but the video driver is the worst (vesa slow).

I tried to configure the thin clients via lts.conf file, but I failed. 

I would appreciate if, when the driver problem is solved, to post a working lts.conf file for the mentioned motherboard.

Thank you Ubuntu People, I switched to Linux thanks to your product.

Milan


PS. I just changed X_COLOR_DEPTH to 16 and all works like a charm now!

---

### Post by Swami2 on 2006-06-19
Could you clarify?  What works like a charm now and how did you make it work?

---

### Post by kalinicm on 2006-06-19
I have thin clients using 1280x1024 resolution, when on 24-bit pallete it works slow, when I switch to 16-bit it works much better, ~2x faster.

---

### Post by Swami2 on 2006-06-20
Can anybody help?

I'm trying to use the regular X server, not a thin client.

I'm about to try Debian to see if that is better, but would prefer to stay with Ubuntu.

---

### Post by calinb on 2006-06-28
[QUOTE=Swami2]
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)
[/QUOTE]I get that same message from my FC5-64 box on my P4M800Pro.   (My Ubuntu machine has Nvidia video.)

It doesn't keep the drivers from working, however, so I suspect your problem lies elsewhere.  Search your /log/var/xorg.0.log for EE lines which may reveal the problem.

---

