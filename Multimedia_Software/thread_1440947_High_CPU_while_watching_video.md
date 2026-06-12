---
title: "High CPU while watching video"
date: 2010-03-28
forum: Multimedia Software
---

### Post by nampat on 2010-03-28
Hi,

I am using Ubuntu 9.10 (64-bit) and VLC player. When I watch a movie I see a really high CPU usage. I have used windows on this same machine and haven't seen anything like that. If I am watching video full screen, it consumes about 85% of CPU. I can't watch 720p and 1080p at all, although I watched 1080p on windows with absolutely no problems.

I have also tried mplayer without success. 

So do you have any ideas why it is like that? It is quite annoying.

I have:
Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
4 GB memory
ATI Technologies Inc RV710 [Radeon HD 4550]

Thanks a lot!

---

### Post by no2498 on 2010-03-28
for me on a dell 6400 with 910 karmic 
i had to set the plugin in gstreamer-properties
open a terminal type, gstreamer-properties click enter
click video set the plugin to, x window system (no xv)
restart the computer
this come from cheese help faq's


now i see smplayer says to set it to, x11

hope this helps

---

### Post by nampat on 2010-03-28
Thank you for the response. I changed the settings, but it is still the same. High CPU. Any other ideas?

---

### Post by no2498 on 2010-03-28
did you restart the computer 

and look for updates

---

### Post by nampat on 2010-03-31
Yes I did the restart, but the problem is the same. Is it possible, that the problem is somehow connected with the ATI card? I have read some articles, saying that ATI drivers doesn't support some functions needed for streaming the video for the GPU to be decoded?

---

### Post by cottfcfan on 2010-03-31
I'm also using the propriety ATI Driver.
But the issue is the same even with the open source drivers.
I think its a flash issue.
I'm hoping its fixed in the next release.

---

### Post by cchhrriiss121212 on 2010-03-31
> Yes I did the restart, but the problem is the same. Is it possible, that the problem is somehow connected with the ATI card? I have read some articles, saying that ATI drivers doesn't support some functions needed for streaming the video for the GPU to be decoded?

This is correct. Nvidia cards can use hardware acceleration (vdpau output) which is not available for ATI cards. You can however compile mplayer to use multithreading as you have a dual core cpu:
[http://ubuntuforums.org/showthread.php?t=1049449](http://ubuntuforums.org/showthread.php?t=1049449)

---

### Post by cottfcfan on 2010-03-31
No2498 your a star.
Ive just set my gstreamer-properties to:
"x window system (x11/xshm/Xv" and my problem is solved.
CPU Usage has dropped from 80% to 20%.
Ive been wrestling with this for months.
Thanx again.

---

