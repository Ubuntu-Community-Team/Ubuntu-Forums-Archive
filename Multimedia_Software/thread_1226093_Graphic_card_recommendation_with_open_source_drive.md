---
title: "Graphic card recommendation with open source drivers"
date: 2009-07-29
forum: Multimedia Software
---

### Post by pzico on 2009-07-29
I'm sure this has been asked many times. I would like to hear the latest opinions.

What are the recommended graphic cards for Ubuntu nowadays. I don't want to use proprietary drivers, because they seem to make many bugs with Compiz. So what is very well supported and efficient card that can run for example basic Tux Racer game without any problem?

---

### Post by themusicalduck on 2009-07-29
I use an Nvidia gtx260 card and used a 6600GT before that. They both seemed to work fine with the latest proprietary drivers from the Nvidia website with no real bugs from compiz or games that I've noticed. Only problems I had were with running out of video memory while playing high quality video on my 6600GT with compiz on. gtx260 has fixed that though.

I think there are open source Nvidia drivers but I haven't used them much so can't comment. ATI cards are supposed to be less well supported on linux.

Any low end nvidia card would probably work fine for tux racer, as long as it is actually a supported card, since I think some very old Nvidia cards are not supported anymore.

---

### Post by Sockerdrickan on 2009-07-29
nVidia, any card just 8-series or later. Use the binary driver it pwns irl.

---

### Post by Arup on 2009-07-29
The only card with true compiz compatible open source drivers is Intel, that too for G31 and above chips, sadly they are still not that stable. For compiz you need proprietary drivers and the best ones are from nvidia period.So any cheap nvidia card from 8400GS will give you compiz and full HD movies with VDPAU enabling load to GPU rather than CPU.

---

### Post by pzico on 2009-07-29
At the moment I have Nvidia 7200 LE with proprietary drivers. This definately can't run Tux Racer or anything 3D well.

---

### Post by darkazurka on 2011-04-27
The thing that Arup recommends "G31" is integrated on the motherboard. It's not like a card you can install on your AGP or PCI express slot.

You need to change the whole motherboard to get "G31", "G41,G43,G45" etc.

Because I bought a new computer, I carefully selected a motherboard with the graphics card X4500 (P5G41T-M LX). I wanted preferably a G45 but they were sold out, and the G43 supported only DDR2, while I wanted DDR 3.

The graphics card with G41 and G43 is called "X4500" while the G45 one is called "X4500HD".

Lots of games work: Nexuiz being one but I couldn't run it with too many effects. I think I can't add water reflection and make it run smoothly on my screen (1440x900), but some effects are possible. I've tried Supertuxkart 0.7(just mentioning). Compiz works and when I started working with this computer I played a lot around with the water effect, drowning the screen in water :)

Here's a video I made of me playing Supertuxkart 0.7 (you can view it in HTML5). I unlock another map after completion of a track: [http://www.youtube.com/watch?v=OPIb90BvYmQ](http://www.youtube.com/watch?v=OPIb90BvYmQ)

---

### Post by Yellow Pasque on 2011-04-27
The r300g/r600g is probably the best open-source driver in terms of 3D performance and stability. I use a RadeonHD 4550 and it always works well with Compiz/KWin. Its weakness is video playback, but that's currently being worked on: [http://www.phoronix.com/scan.php?page=news_item&px=OTM4MA](http://www.phoronix.com/scan.php?page=news_item&px=OTM4MA)

---

