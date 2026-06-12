---
title: "Bluish Video when I open it"
date: 2009-10-28
forum: Multimedia Software
---

### Post by uchari on 2009-10-28
I've been using UBUNTU for at least 3 years and I love it. But today I finally had my first problem unresolved that is that the videos are bluish... did I change something without noticing?

[IMG]http://www.ubuntu-pics.de/bild/28897/screenshot_021_MK0001.png[/IMG]

Please I hope that you can help me. :(

UPDATE: The video thumbnail in the right is the REAL COLOR of the video. I have Nvidia Driver verion 185. and using Ubuntu 9.10 RC KARMIC

UPDATE2: So far I detected that there was something to do with the nvidia drivers... I did downgrade it to version 173. But I hope there is something else to fix so I can use the latest driver (suppose to be recommended)

---

### Post by mrfelton on 2009-10-29
I too have this problem with the Nvidia 185 driver since upgrading to Karmic today.

---

### Post by mrfelton on 2009-10-29
see [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/424864](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/424864)

---

### Post by RedRat on 2009-10-29
I had this problem too! However, I was able to solve it by starting Totem movie player. When you have it started and playing a video, go to Edit>Preferences>and click the Display tab. Adjust the color or hue to get the correct rendition. 

BTW, this control seems to control the picture even for VLC and the other movie players. Don't know why. Strange connection.

---

### Post by irvingswiftj86 on 2009-10-30
I had the same prob. That seems to have fixed it for now.
I am a bit dissappointed by such a massive bug.

Thanks for ur help

---

### Post by RedRat on 2009-10-30
Video drivers are the biggest pain in the @ss in Ubuntu followed by the codec problems. I just downloaded 9.10 and ran the live CD to check it out. Off the disk, it can't do much compared to Linux Mint off the disk. 

I know that the developers have their panties in a twist over "proprietary" and "closed source" drivers. I understand that. But this seems to have hampered the development of providing a good graphical experience in Ubuntu. To tell the truth, if the LiveCD was all I had of Ubuntu 9.10, as a new user, I would run away from it. 

OK, on the plus side, it does appear far, far faster than my current version (8.04) particularly FireFox. Its networking capabilities are much smoother, no question about that. In the end, I will probably upgrade but I think it will be Linux Mint--just far less hassle in getting up and running.

---

### Post by uchari on 2009-11-01
> **RedRat said:**
> I had this problem too! However, I was able to solve it by starting Totem movie player. When you have it started and playing a video, go to Edit>Preferences>and click the Display tab. Adjust the color or hue to get the correct rendition. 

BTW, this control seems to control the picture even for VLC and the other movie players. Don't know why. Strange connection.

Thanks for answering to everybody. I'm glad that I was not the only one. I hope that Nvidia can correct this ASAP. Is really annoying.

Update: I did install the new Nvidia driver Beta version 190 Beta and still its not fixed the HUE settgin.

I did FIXED it manually as it is mentioned by RedRat.

---

### Post by RedRat on 2009-11-01
I really do not think this bluish cast or hue control error is due to Nvidia, I think it is something peculiar to the OS. I first noticed this way back when I update from 7.10 to 8.04. I had the same driver for both of these systems. Why the Totem movie player controls hue and color for other movie players, I don't quite understand. Perhaps there is a some shared library.

---

