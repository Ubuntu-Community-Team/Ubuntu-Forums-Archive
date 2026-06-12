---
title: "[SOLVED] Pixelated slow DVD video playback"
date: 2008-05-29
forum: Multimedia Software
---

### Post by Beowulf.1000 on 2008-05-29
U405-S2830 Toshiba Satellite subnotebook. 
  [http://www.notebookreview.com/default.asp?newsID=4372](http://www.notebookreview.com/default.asp?newsID=4372)
Very pleased except for DVD video playback. (on a plus note, the N wifi and connection to my wireless Brother HL-2170w laser printer worked automagically with no extra steps needed; however the wired LAN is not detect, not a big problem since I use wifi everywhere now).

Ubuntu 8.04 DVD movie playback essentially useless, so poor, slow, blocky pixelations, I can only figure that has something to do with an poor driver for the Intel graphics chip 
  Intel Graphics Media Accelerator X3100

I tried all of the video driver options in mplayer (X11, openGL, etc), installed all the mplayer codecs to /usr/lib/bin, install Ubuntu extras/codecs, gxine codecs, etc.

Am I sort of out of luck regarding video playback due to the graphics chip, do I need to just wait for a future version of Ubuntu that will address compatibility with the graphics chip in this laptop? DVD video playback is fine in MS-Vista on this laptop, so I know the laptop is capable in theory of playing video. Any help appreciated.

---

### Post by Beowulf.1000 on 2008-05-29
Solved. I just needed to install libdvdcss .deb package (googled for 'libdvdcss download'), downloaded the .deb file, double clicked it on my laptop and ubuntu installed it, now the DVD movie plays just fine.

I still have excess color saturation issues playing videos but that is another issue I need to solve.

---

### Post by ms.shams on 2008-06-29
hi, can you please tell me that have you any problem with this laptop? i want to buy one of this. thank you.

---

