---
title: "jerky tv in myth tv"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by Colin Maguire on 2008-04-04
New build using ubunt 7.10 with Myth TV on top. TV is jerky, like 10 fps or so. System is Asus AM2-AVM.NDMI with Radeon 1250 graphics card on board, Athlon 64x2 (BE2400) 2GB Ram ,Hauppage 350 dvb-t Card.  Any help would be appreciated,
                                             Percy Vere

---

### Post by MrFSL on 2008-04-04
Check you MythTV settings. What are you using as a decoder. For he PVR-350 you probably want to use the onboard decoder right?

---

### Post by kah00na on 2008-04-04
Make sure your hard drive parameters are set correctly.  I had an issue with this with my mythTV box a while back.  Look through this page on how to check your settings and change them if necessary:

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html")

---

### Post by warp99 on 2008-04-04
There is a setting in the MythTV front end for this particular card. On the MythTV menu go to Utilites/Setup > Setup > TV Settings > Playback and on the first screen there is a box for "Extra audio buffering". Go ahead and tick that box. Then go through the rest of the screens until you reach the last one and tick the box marked "Use the PVR-350's TV-Out / Mpeg decoder".

---

