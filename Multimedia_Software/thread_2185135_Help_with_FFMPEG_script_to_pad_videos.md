---
title: "Help with FFMPEG script to pad videos"
date: 2013-11-01
forum: Multimedia Software
---

### Post by stevenjrees on 2013-11-01
I converted a bunch of DVD movies a long time ago to MKV and cropped the black bars to reduce the size. the AR was stored in the MKV and it always played back correctly on corresponding supported devices. 
I now need to remux these to m2ts as as can successfully stream to my PS3 as mkv but i can as m2ts. 

My problem is, i need to re-pad the movies to force the aspect ratio and i have to do it for a lot of videos. 
i.e. i have one video as 704x448 and should have a AR 2.35:1 @ 25fps

i need to pad this so that it will fit on 16:9 format and retain the correct aspect ratio.

i don't know anything about scripting and would be grateful if someone could help with a script that add the destination size i.e. 526, 720, 1080 and the AR format that should be retained i.e. 2.35, 2.21, etc. 
ffmpeg should calculate what black to add to achieve a final display of 16:9

be really cool if someone could help me. thx

---

### Post by leeper69 on 2013-11-02
Hi I dont know how to write skript for ffmpg but the guy's at kdenlive do have you tryed this program to convert your mkv files to m2ts?

---

