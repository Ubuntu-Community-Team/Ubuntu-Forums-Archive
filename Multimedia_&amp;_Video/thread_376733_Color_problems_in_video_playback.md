---
title: "Color problems in video playback"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by mverrilli on 2007-03-05
New Ubuntu install (and user).   I have an ATI Radeon x1600.  JPG files and my desktop look fine, but MPEG, MOV, WMV and AVI files look... purple.  I'm using Totem Movie Player.

I installed codecs from EasyUbuntu, and I had installed the ATI drivers using Envy prior to that.  Cedega games look fine too.

How do I correct this?  

Thanks

---

### Post by panch0 on 2007-03-05
What video output is being used? If it's not XVideo, try XVideo instead.

What happens if you try with another engine, like KPlayer/MPlayer?

---

### Post by mverrilli on 2007-03-08
Sorry I haven't had much time to work on this.

I did manage to fix it.  It was using gstreamer... so instead I installed xine and it seemed to fix it. (At least, that is how I understand it, I'm kinda noobish when it comes to X stuff).  

I actually was looking up something else, and ran across this and thought that since apparently it changes what totem uses to do video, that maybe it'll also fix my problem.

This is what I ran:

```
sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine
```


Not sure what side-effects this may cause, but everything seems like it is working properly, now.  Thanks for leading me in the right direction.

---

### Post by darkfame on 2007-04-30
> **mverrilli said:**
> Sorry I haven't had much time to work on this.

This is what I ran:

```
sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine
```
.

This fixed my color problems as well (ATI Radeon X1700), seems to be related to gstreamer as OP says.

---

### Post by prato on 2007-05-06
> **mverrilli said:**
> Sorry I haven't had much time to work on this.

I did manage to fix it.  It was using gstreamer... so instead I installed xine and it seemed to fix it. (At least, that is how I understand it, I'm kinda noobish when it comes to X stuff).  

I actually was looking up something else, and ran across this and thought that since apparently it changes what totem uses to do video, that maybe it'll also fix my problem.

This is what I ran:

```
sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine
```


Not sure what side-effects this may cause, but everything seems like it is working properly, now.  Thanks for leading me in the right direction.

This solution works for me, too (graphic card ATI mobility X1300)

thks to mverrilli!! :)

---

### Post by jbmech006 on 2007-05-07
> **darkfame said:**
> This fixed my color problems as well (ATI Radeon X1700), seems to be related to gstreamer as OP says.


Add to that this fixed my problem as well ATI X1400. This is a gstreamer bug

---

### Post by Hhkmac on 2007-10-07
Worked for me too ... ATI Radeon X1300.  Cheers for the post!!

---

