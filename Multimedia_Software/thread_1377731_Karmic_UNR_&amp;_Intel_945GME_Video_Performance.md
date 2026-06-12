---
title: "Karmic UNR &amp; Intel 945GME Video Performance"
date: 2010-01-10
forum: Multimedia Software
---

### Post by scottburton11 on 2010-01-10
Having not experienced the issues with Jaunty and Intel display cards, I can't say whether this is a real problem or not. From what I can tell, MTRR is not a problem.

On my new Dell Mini 10v w/ Intel 945GME and a fresh install of Karmic UNR, video playback performance is only so-so. 

Most YouTube-style Flash video is decent. Local H.264 playback from .m4v and .mov containers is flawless. But streaming Flash video originating as H.264 is dismally choppy - this includes Vimeo and Hulu-quality streaming video. 

Is this about what I can expect from Karmic and a 945GME?

---

### Post by Badirca Dorian on 2010-03-17
Having the same problem here . there is an slight improvement witch can be done by adding to your /etc/X11/xorg.conf a line like : 
Option        "AccelMethod" "uxa" 
Slight improvement for youtube movies, but still 0 improvement for flash games or other applications.

---

### Post by Badirca Dorian on 2010-03-17
Another improvement for the flash application if u have Intel 945GME is to disaple Hardware Acceleration from flash player. Just play any flash application ( like an youtube video ) , right click => settings => disable hardware acceleration .
Also if u have personas , disable it. 
i did those things and i can watch youtube flawlessly and play flash games almost perfect :)

---

