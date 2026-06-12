---
title: "Mythtv and PVR-150(ivtv) troubleshoot"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by basgoossen on 2007-03-18
Hello,
I've set up an entire mythtv setup and installed the ivtv drivers properly, they function on mplayer when i do mplayer /dev/video1. so from that point of view everything is going fine. i started the mythtv-setup and setup my pvr-150, this seems also ok, i can even search for channels with the device and it looks like it really finds some channels.
then starts the trouble, if i start the mythtv frontend, and klik watch tv, nothing happens?!, wel the screen goes to black for a while and then back to the menu. after  that even mplayer /dev/video1 does not work anymore.

The only line that states an error in the logs is:
2007-03-18 14:04:33.964 MPEGRec(/dev/video1) Error: select timeout - ivtv driver has stopped responding

i looked all over the Internet for some more options to continue troubleshooting but that brought me only so far as now. and i cant seem to get a clue about how to continue now.

Can someone help please?!

---

### Post by majoridiot on 2007-03-19
you didn't specify which ubuntu you are using or what method you followed to install it, but i
suggest taking a fresh run at it with this guide, if you havent already:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

otherwise, you need to provide more info for troubleshooting.

---

### Post by beattie on 2007-04-18
I just spent a week fighting this problem.  I finally found a clue and discovered I missed a step in mythtv-setup when setting the capture card.  

From [https://help.ubuntu.com/community/MythTV_Edgy_Backend]("https://help.ubuntu.com/community/MythTV_Edgy_Backend")
> A very common error is when choosing the Hauppauge PVR Cards. There is an option for MPEG-2 Encoder Card (PVR-X50, PVR-500) as well as for standard V4L card. Be sure to choose the MPEG-2 encoder option here if you use a Hauppauge card.

Selecting the MPEG-2 encoder option fixed the problem.

---

### Post by majoridiot on 2007-04-18
glad you got things sorted! :D

---

