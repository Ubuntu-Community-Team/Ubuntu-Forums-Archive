---
title: "Trouble with Streaming Audio"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by ghindo on 2007-09-07
I'm running 7.04 Feisty Fawn on a Dell Inspiron 1420n.

I am attempting to open up an audio stream in Totem, but I am having difficulties.  It's giving me the following error message:```
An error occured
Internal GStreamer error:  negotiation problem.
Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer
```Attached are screenshots to hopefully make the problem more clear.

---

### Post by kev000 on 2007-09-08
if its a quicktime link you may need an additional codec.  I would:

- try another player (mplayer maybe)
and/or:
-install the non-free codecs

---

### Post by ghindo on 2007-09-11
> **kev000 said:**
> if its a quicktime link you may need an additional codec.  I would:

- try another player (mplayer maybe)
and/or:
-install the non-free codecsI *think* I've installed the non-free codecs.  How do I check?

---

### Post by linuxwizard on 2007-09-11
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by andrew.46 on 2007-09-11
Hi,

 Do you have the URL of the stream?

           Andrew

---

### Post by ghindo on 2007-10-13
> **andrew.46 said:**
> Hi,

 Do you have the URL of the stream?

           Andrew[http://kdup.up.edu/sites/kdup.up.edu/themes/bluemarine_kdup/kdup_stream.qtl](http://kdup.up.edu/sites/kdup.up.edu/themes/bluemarine_kdup/kdup_stream.qtl)

---

### Post by andrew.46 on 2007-10-13
Hi,

 Very interesting:

QUOTE=ghindo;3524624][http://kdup.up.edu/sites/kdup.up.edu/themes/bluemarine_kdup/kdup_stream.qtl](http://kdup.up.edu/sites/kdup.up.edu/themes/bluemarine_kdup/kdup_stream.qtl)[/QUOTE]

Embedded in this file is:

rtsp://multimedia.up.edu/KDUPlow.sdp

 which claims to be unavilable at the moment. Try this a few times over the next little while.

                            Andrew

---

