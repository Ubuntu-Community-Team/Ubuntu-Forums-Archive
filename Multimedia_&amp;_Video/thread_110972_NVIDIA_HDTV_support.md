---
title: "NVIDIA HDTV support"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by polt on 2006-01-01
**Summary**

The Ubuntu 5.10 "Breezy Badger" drivers, including those available in universe and multiverse, do not support HDTV output available on newer nVidia graphics cards.

**What is HDTV?** 

HDTV is essentially an analog television specification that is used to produce a newer, high-definition=high-resolution output on your newer TV. It is different from the old NTSC standard because it has wide screen (16x9) rather than the usual (4x3) aspect ratio. HDTV is also known as 1080i.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=5001&stc=1&d=1136123636[/IMG]

**Your computer and HDTV**

If you want your computer to output on an HDTV using the wide screen so you can play video games and do other cool stuff, there are two basic approaches:

**Approach 1 (HDTV output)**

Get a powerful, high-speed video card that has HDTV output. nVidia GeForce 4 cards from about 6600 up have this capability. Then attach the output from the card to your HDTV. You can use the 3 component video lines (RGB) similar to the connection to many DVD players.

Approach 1 does not work with Ubuntu but does work with Windows XP. I tried both. After 2 weeks of Ubuntu, 5 minutes of XP solved the problem. The reason is that nVidia provides excellent Windows XP/XP64 driver software for video cards with their newer chips. It works and it is easy to use. With XP we get 1600x900 resolution immediately.

The combination of the nVidia Linux driver and the X11 package supplied with Ubuntu only supports 4x3 video resolution. Experiment with xorg.conf and you will get a very nice 1024x768 window on your 1920x1080 background, but nothing else. 1280x1024 will probably overscan your screen and it will be hard to see the menu.

The two supported video modes in /etc/X11/xorg.conf are TV and Monitor; HDTV is not mentioned in the x.org documentation. That is probably a hint that Approach 1 is going to be difficult.
    
**Approach 2 (digital output)**

Output digital video data from any video card with a DVI connector to an HDTV with a matching connector. Then your computer is sending digital data to the TV just like it is a flat screen monitor. The conversion into the analog 1080i signal is then done inside the TV. If your TV functions as a monitor, you may be ok. But check to see if your video card, TV and output resolution are supported in Ubuntu.

**Conclusion**

If your HDTV is also a computer monitor, then you have some chance of getting Ubuntu 5.10 working in 16x9 mode. Under Ubuntu there is currently no way to get these wide screen modes from the analog HDTV outputs supplied with many nVidia cards. If you want to work on this, you should begin with the latest distributions from nVidia and x.org. It appears that a kernel rebuild is required.

---

### Post by MetalMusicAddict on 2006-01-01
> **polt]**Summary**

The Ubuntu 5.10 "Breezy Badger" drivers, including those available in universe and multiverse, do not support HDTV output available on newer nVidia graphics cards.

**What is HDTV?** 

HDTV is essentially an analog television specification that is used to produce a newer, high-definition=high-resolution output on your newer TV. It is different from the old NTSC standard because it has wide screen (16x9) rather than the usual (4x3) aspect ratio. **HDTV is also known as 1080i**.[/quote]

This isnt exactly true. HDTV has many resolutions avaialable. 480p, 720p, and 1080i. I think there is a 1080p format now.

[quote]**Your computer and HDTV**

If you want your computer to output on an HDTV using the wide screen so you can play video games and do other cool stuff, there are two basic approaches:

**Approach 1 (HDTV output)**

Get a powerful, high-speed video card that has HDTV output. nVidia GeForce 4 cards from about 6600 up have this capability. Then attach the output from the card to your HDTV. You can use the 3 component video lines (RGB) similar to the connection to many DVD players.

Approach 1 does not work with Ubuntu but does work with Windows XP. I tried both. After 2 weeks of Ubuntu, 5 minutes of XP solved the problem. The reason is that nVidia provides excellent Windows XP/XP64 driver software for video cards with their newer chips. It works and it is easy to use. With XP we get 1600x900 resolution immediately.

The combination of the nVidia Linux driver and the X11 package supplied with Ubuntu only supports 4x3 video resolution. Experiment with xorg.conf and you will get a very nice 1024x768 window on your 1920x1080 background, but nothing else. 1280x1024 will probably overscan your screen and it will be hard to see the menu.

The two supported video modes in /etc/X11/xorg.conf are TV and Monitor said:**
> 

If your running through a DVI or HDMI the connection stays digital. 

[quote]**Conclusion**

If your HDTV is also a computer monitor, then you have some chance of getting Ubuntu 5.10 working in 16x9 mode. Under Ubuntu there is currently no way to get these wide screen modes from the analog HDTV outputs supplied with many nVidia cards. If you want to work on this, you should begin with the latest distributions from nVidia and x.org. It appears that a kernel rebuild is required.

[HERES]("http://www.ce.org/shared_files/resources/HDTV_Brochure_Final.pdf") a PDF on HDTV.

I guess Ive been lucky here I have a 5700 Ultra doing 1280x720 through the DVI under Breezy. I am going to post a thread about my HDTV experience when I work out some other things.

---

