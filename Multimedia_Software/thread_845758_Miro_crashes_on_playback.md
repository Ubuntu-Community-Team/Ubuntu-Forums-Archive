---
title: "Miro crashes on playback"
date: 2008-06-30
forum: Multimedia Software
---

### Post by dbsoundman on 2008-06-30
I just installed Miro after looking for Democracy TV and finding that it has a new name...I was just looking for a general program where I could get web channels and keep up with news and such. Anyway, I successfully subscribed to several feeds and all that, but it seems that whenever I try to play one of my downloaded feeds, the program crashes; it just closes and disappears without a trace. Any ideas as to what is going on? I'm using Hardy Heron, AMD 64 dual core processor and ATI graphics.

Thanks,
Dan

---

### Post by fishtoprecords on 2008-07-01
I see this too. 8.04, dual Intel. ATI video.

Sometimes, Miro just disappears. Sometimes it crashes and takes all of X-Windows with it.

Miro is a cool idea, but its really unusable on my system

---

### Post by animaniac on 2008-07-17
> **dbsoundman said:**
> I just installed Miro after looking for Democracy TV and finding that it has a new name...I was just looking for a general program where I could get web channels and keep up with news and such. Anyway, I successfully subscribed to several feeds and all that, but it seems that whenever I try to play one of my downloaded feeds, the program crashes; it just closes and disappears without a trace. Any ideas as to what is going on? I'm using Hardy Heron, AMD 64 dual core processor and ATI graphics.

Thanks,
Dan

Same here, im on a thinkpad T42. So far the only thing i see in common that could be causing this is the fact that we all have ATI graphics, anyone know of a fix, or have more detailed info as to what might be causing this.

---

### Post by markbuntu on 2008-07-17
I had that problem until I switched Miro to gstreamer instead of xine for video playback. Now it works great, full screen HD, etc. I have an ATI Radeon HD 3650 card

---

### Post by animaniac on 2008-07-17
thanks, worked.

For anyone else having this problem, 

If you have 1.2 then Video --> Options --> Playback tab. Then select either gstreamer as the renderer to play videos. Then close and restart Miro for the changes to take effect. 

If you have pre 1.2 then just add this to software sources:
[deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/]("deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/")
and update your system, then you will have 1.2.

---

### Post by Karyyk on 2008-08-10
I'm having a similar issue. I have upgraded to 1.2 and changed the rendering to gstreamer. Now instead of closing, I get choppy playback and then Miro becomes unresponsive. Any ideas?

I am being forced to use proprietary drivers since I have an ATI video card installed. Could that be the source of the problem?

---

### Post by markbuntu on 2008-08-10
You can set the Desktop Visual Effects to None, and turn them back on when you are finished watching.

---

### Post by grahambr on 2008-08-12
Going over to gstreamer has cured this for me but I now have no audio on any of the videos.

My audio works ok in all other applications.

---

### Post by Bigbob22 on 2009-03-07
I switched to gstreamer but it still closes when I try to play the video.

---

### Post by Bigbob22 on 2009-03-07
please help

---

### Post by binbash on 2009-03-08
did you try changing video output at vlc or other players?

---

### Post by scragar on 2009-03-08
> **Bigbob22 said:**
> I switched to gstreamer but it still closes when I try to play the video.

I would make sure you are using an up to date version, I haven't followed miro development for quite some time, but last time I checked it wasn't working at all with gstreamer, so xine was required, it was high on the to do list back then though, so I expect it to be fixed in an up to date version.

---

### Post by markbuntu on 2009-03-09
In System/Properties/Multimedia System Selector try setting video to X Window System (No Xv).

To set xine preferences you need to use xine-ui. Try seting video to xshm.

This sort of depends on which video driver you are using so you may have to try different settings. Be careful when you change settings as some can crash the application or your system so do not have anything important going on when you do this.

---

