---
title: "cannot install h.264 decoder: totem"
date: 2010-06-05
forum: Multimedia Software
---

### Post by zizzdude on 2010-06-05
I was able to watch videos that had h.264, but now I can't.

when I play the same video from before, it tells me I don't have the codec installed, but when I try to have it installed:

"No packages with the requested plugins found"

is it something I'm missing in the repository?


running ubuntu 10.04.

---

### Post by Ohrer on 2010-06-05
I have some problem like that.

does Nautilus show video thumbnails?

Try to launch totem as root user, if you can play videos tell me, please.

---

### Post by zizzdude on 2010-06-05
It doesn't show the thumbnails. I also ran totem in root, and it works. So for some reason I don't have permission to use the decoders needed?

---

### Post by Ohrer on 2010-06-05
Ok, I have the same problem, but I don't know to fix it. I going to wait somedays for an answer before reporting the bug.

---

### Post by eris23 on 2010-06-06
I had the same problem on Maverick.  Totem worked as root, not as user.  Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

---

### Post by zizzdude on 2010-06-06
that worked perfectly. thank you so much! :D

---

### Post by zizzdude on 2010-06-06
that worked perfectly. thank you so much! :D

---

### Post by Ohrer on 2010-06-06
Thank you, eris23

---

### Post by converted on 2010-08-10
> **eris23 said:**
> I had the same problem on Maverick.  Totem worked as root, not as user.  Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

Thanks so much!!

---

### Post by Nergar on 2010-08-20
> **eris23 said:**
> I had the same problem on Maverick.  Totem worked as root, not as user.  Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

worked like a charm!! (y)

---

### Post by Mnemic on 2010-09-01
> **eris23 said:**
> I had the same problem on Maverick.  Totem worked as root, not as user.  Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry
Cheers eris23! That worked like a charm! :)

---

### Post by higashi on 2010-09-09
Thanks a bunch, eris23!

---

### Post by klerik22 on 2010-09-10
I love you guys. THX :-)

---

### Post by Chilly_Willy on 2011-02-10
This should be in a wiki or beter yet, fixed. I just did a fresh install yesterday.

---

### Post by Rayaz on 2011-07-19
Thanks a bunch. Love the way a solution is just a google away with Ubuntu.

Cheers

---

### Post by Virus666 on 2012-02-17
> **eris23 said:**
> I had the same problem on Maverick.  Totem worked as root, not as user.  Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

That worked for me. Thank you!

---

### Post by vipseixas on 2012-06-28
> **eris23 said:**
> i had the same problem on maverick.  Totem worked as root, not as user.  Fix was, as user:
Rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

you rock!

---

