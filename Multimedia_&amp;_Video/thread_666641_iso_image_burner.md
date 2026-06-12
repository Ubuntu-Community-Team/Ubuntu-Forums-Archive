---
title: "iso image burner ?"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by id3379 on 2008-01-13
im trying to burn the powerpc version for my power book :) whats a good iso burning program for linux ?

---

### Post by lluisanunez on 2008-01-13
The CDburner into Nautilus works fine for me... there is also GnomeBaker

---

### Post by id3379 on 2008-01-13
will that burn it as a image file ? so it can boot from the disc ?

---

### Post by Steveway on 2008-01-13
Right click the .iso and choose Burn to disk (Or whatever it is called in your language.).
It will burn the .iso to the disk correctly.

---

### Post by steeleyuk on 2008-01-13
No, that'll take the image file and burn it as a "normal disc" which i'm sure is what you want to do. Unless I've completely misread your post.

Or you could try [Brasero]("apt://brasero") which is a very simple, easy to use burning app.

---

### Post by santiagoward2000 on 2008-01-13
Hi!
I haven't burnt many iso's, but **Brasero** worked really well for me.

---

### Post by lluisanunez on 2008-01-13
When you 'write to disk' from nautilus, it identifies the ISO and burns it OK. I've done it lots of times

---

### Post by Steveway on 2008-01-13
Yes Brasero is very good.
It even integrates into thunar and let's one burn to disk using it with a right-click.

---

### Post by id3379 on 2008-01-13
i already tried the right clicking, the my mac doesnt even detect that there is a CD in it, i can hear it spin up though

---

### Post by tsm1723 on 2008-01-13
It's not pretty, but I usually just use cdrecord from the command line. e.g.:

```
cdrecord dev=/dev/cdrw1 ubuntu.iso
```

(assuming your cd writer is at /dev/cdrw1 as opposed to /dev/cdrw)

I suppose it's better if you also specify a buffer size, but if your computer is reasonably fast this should do the job without a write buffer underrun (I've never had any trouble).

---

### Post by ubuntu27 on 2008-01-13
An ISO is a complete image designed to be burned onto a CD or DVD. They have the extension .iso.

Ubuntu (and other Linux distributions) ship as ISO images. Please see [GettingUbuntu]("https://help.ubuntu.com/community/GettingUbuntu") for how to get an ISO of Ubuntu. If have already downloaded the ISOs, see [BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") for complete instructions on how to burn this image onto a CD.

[How to get Ubuntu]("https://help.ubuntu.com/community/GettingUbuntu")

[How to burn iso]("https://help.ubuntu.com/community/BurningIsoHowto")

---

