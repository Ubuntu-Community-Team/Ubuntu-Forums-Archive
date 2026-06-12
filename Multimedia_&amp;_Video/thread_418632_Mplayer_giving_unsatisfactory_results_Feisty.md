---
title: "Mplayer giving unsatisfactory results Feisty"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by puneit on 2007-04-22
HI, 
I am a great fan of Mplayer. Used it in Dapper, then Edgy and now in Feisty. Till Edgy, I had not faced any problem per-se with configuring the Video preferences in Mplayer. Used to use the x11 (XImage/SHM) drivers. But in Feisty using this option displays a very small box of video when playing in Full Screen Mode.
I have tried gl (openGL)and gl2 (OpenGL Multiple Textures) drivers. The problem with gl driver is that screen blanks after sometime. Don't know how to disable it. And the problem with gl2 driver is that while a movie is being played the video flickers intermittently.
Can someone give me a workaround for this? 
The machine has 512 MB RAM, ATI Radeon Mobility M300 graphics card (restricted drivers are in use)

---

### Post by Dearhell on 2007-04-23
Same graphic card here, I use the xv driver in mplayer preferences

---

### Post by puneit on 2007-04-23
When I select the xv driver I get a Fatal error!
> Error opening/initializing the selected video_out (-vo) device.

---

### Post by Dearhell on 2007-04-24
Did you choose propietary drivers at administration tab?

I had to unselect them in order to work with xv in mplayer

---

