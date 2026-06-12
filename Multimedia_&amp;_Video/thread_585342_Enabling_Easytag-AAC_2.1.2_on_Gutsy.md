---
title: "Enabling Easytag-AAC 2.1.2 on Gutsy"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Ehtetur on 2007-10-21
There's a lot of great threads in the forums detailing how to compile easytag-aac from source... This ain't one of them... :twisted:

Instead of compiling from source, I used *deb files to get easytag-aac-2.1.2 working in Gutsy:

Get easytag-aac, libmp4v2, & libmpeg4ip from [ftp://ftp.gnome.org/mirror/debian-multimedia](ftp://ftp.gnome.org/mirror/debian-multimedia)
**Note:** Gutsy comes with a 3yr old version of libmp4v2 that needs updating.
```
wget ftp://ftp.gnome.org/mirror/debian-multimedia/pool/main/libm/libmpeg4ip/libmp4v2-0_1.5.0.1-0.3_i386.deb
wget ftp://ftp.gnome.org/mirror/debian-multimedia/pool/main/libm/libmpeg4ip/libmpeg4ip-0_1.5.0.1-0.3_i386.deb 
wget ftp://ftp.gnome.org/mirror/debian-multimedia/pool/main/e/easytag-aac/easytag-aac_2.1.2-0.0_i386.deb
```

Install the files

```
sudo dpkg -i libmp4v2-0_1.5.0.1-0.3_i386.deb  libmpeg4ip-0_1.5.0.1-0.3_i386.deb easytag-aac_2.1.2-0.0_i386.deb
```

Done! You can find EasyTAG in Applications --> Sound & Video.

---

### Post by twelve17 on 2007-11-05
Interestingly, easytag-aac_2.1.2-0.0_i386.deb is missing from there.

They have replaced it with easytag-aac_2.1.3-0.0_i386.deb, which, interestingly, depends on a newer version of libmpeg4ip than is available on the same repository.

Sigh.

---

### Post by artAlexion on 2008-03-09
try 
[http://debian.rab.co.id/multimedia/pool/main/e/easytag-aac/?C=N;O=D](http://debian.rab.co.id/multimedia/pool/main/e/easytag-aac/?C=N;O=D)

---

