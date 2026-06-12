---
title: "Video tear/flicker with fglrx driver"
date: 2008-04-25
forum: Multimedia Software
---

### Post by FLuA on 2008-04-25
I have tried both fglrx 8.3 and 8.4, and there is a horizontal tear in fast movements when i watch video with xv output. With x11 output it is even worse. When i start a movie player that uses the xvideo ouput, the whole screen goes black for 2-3 seconds, and then the video starts with the problems mentioned earlier. My video card is ATI HD2600XT.

---

### Post by FLuA on 2008-04-27
bump

---

### Post by harshil102 on 2008-04-27
unfortuenetly this is a fglrx problem and there isnt much anyone but AMD/ATi can do about it (or we can wait for DRI2 to come out and be supported). I know it sucks since i use fglrx on my X1600 but trust me it was much worse before there were at least 3 times as many if not more problems before.

---

### Post by chochem on 2008-10-07
For the record: I just switched to using the open source 'radeon' driver instead of fglrx and video renders far better and without artifacts. I have had some HD matroska videos taht I didn't think my laptop capable of playing until i ditched fglrx/catalyst. Of course the tradeoff is that with the radeon driver compositing and 3D rendering is off limits.

---

### Post by Onitake on 2011-03-27
Newer AMD drivers offer a setting for forcing vsync on in 2D mode. You can find it in Catalyst Control Center -> Display options -> Tear free
In my case, this helped greatly (gdm is now flicker free), though they warn you performance might be impacted.

---

