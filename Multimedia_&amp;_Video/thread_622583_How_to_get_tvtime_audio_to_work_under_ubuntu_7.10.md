---
title: "How to get tvtime audio to work under ubuntu 7.10"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-11-24
Hi, 

I have WinTV HVR 950 installed on Ubuntu 7.10. 
With TVtime, I can see video, on a tv channel, but there is no audio.

Can you please tell me how can I get audio to work for WinTV HVR 950 under ubuntu 7.10?

Thank you.

---

### Post by orzechowskid on 2007-11-26
does xawtv give you audio?

---

### Post by ehiebert on 2007-11-26
The problem is that TvTime doesn't know to look for the DSP channel. You have to use a saparate command to read the audio stream.

I followed the advice from Lunapark-6 on the HVR-950 and created a bash sheel script to run TvTime. The script is shown below. Save this file as tv, then chmod +x tv, and then add this to the menu as TV.

**_Solution #1 - sox audio player_**
Warning: There is a 1-2 second audio delay due to buffering delay with this solution. I am trying to find a fix for this.

#!/bin/bash
/usr/bin/tvtime &
sleep 0.25
sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp


**_Solution #2 - Use MPlayer_**
mplayer tv:// -tv driver=v4l2:alsa:immediatemode=0:adevice=hw.2
,0:norm=ntsc:chanlist=us-cable:channels=4-radiocanada,5-tva,7-tqs,19-rdi,20-canalD

**_Solution #3 - Use MythTV_**
This solution also gives you PVR funtionality; however, I am currently have audio issues with MythTV with this card. More on this later.

Hope this helps.

---

