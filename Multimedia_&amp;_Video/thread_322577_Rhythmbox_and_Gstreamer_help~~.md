---
title: "Rhythmbox and Gstreamer help~~"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by zhlmmc on 2006-12-20
Hi all,

I want to use Rhythmbox to play ape and I have installed gstreamer0.80(including gst-monkeysaudio-0.8.0). But Edgy uses gstreamer0.10, how to set the gstreamer0.80 as default? Or any other ways to let Rhythmbox play ape? 
Thanks in advance. 

//I copied "libgstmonkeysaudio.so" to /usr/lib/gstreamer0.10/, but Rhythmbox still can not //play ape file.

Regards,
Hailong Zhang

---

### Post by zhlmmc on 2006-12-21
Does any body know this problem?

---

### Post by olejorgen on 2007-06-23
bump?

---

### Post by doclivingston on 2007-06-23
Recent versions of Rhythmbox don't support GStreamer 0.8. Basically, someone needs to do the work to port the APE plugin from GStreamer 0.8 to 0.10.

---

### Post by olejorgen on 2007-06-26
Thanks for clearing that up, I troed to build 0.8 and it was a pain, so no I don't have to suffer anymore.

Anyone no if this is a lot of work? Only small interface changes?

---

