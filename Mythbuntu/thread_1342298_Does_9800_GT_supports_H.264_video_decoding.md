---
title: "Does 9800 GT supports H.264 video decoding ?"
date: 2009-11-30
forum: Mythbuntu
---

### Post by mars76 on 2009-11-30
HI All,

 I am wondering whether the 9800 GT supports the H.264 video decoding ?

Or am i better off getting the GS 250 Series ??

Currently i have 8600 GT and when i tried to view the recorded movie (in 1080i using my hd-pvr) it froze couple of times and the machine got rebooted automatically.

I am not sure whether it is because of the VPDAU issues or because my graphics card .

I have a quad core cpu so processing shouldn't be an issue.

mars

---

### Post by hackmeister on 2009-11-30
> **mars76 said:**
> 
Currently i have 8600 GT and when i tried to view the recorded movie (in 1080i using my hd-pvr) it froze couple of times and the machine got rebooted automatically.

I am not sure whether it is because of the VPDAU issues or because my graphics card .

I'm using an 8600GT card in my main Myth system and it works great with VDPAU. Getting < 5% CPU load when watching 1080i h264 recordings. Make sure you setup VDPAU in your playback profiles:
[http://www.mythtv.org/wiki/Vdpau#Display_Profiles](http://www.mythtv.org/wiki/Vdpau#Display_Profiles)

Try the different de-interlacers as well. I wound up using bob 2x (w/VDPAU normal) for my main box and my Ion box.

---

### Post by ian dobson on 2009-12-01
Hi,

I'm running a 9600 in my frontend and am not having any problems with MPEG2/H264 in VDPAU.

If the recordings aren't 100% OK (corruption from a weak signal) then you could see picture corruption but never a crash.

Whats the temperature of your graphic card like? use nvclock to read out the temps. On my passive cooled 9600 the temperature jumps up 15°c when I start playing a H264 recording.

Regards
Ian Dobson

---

