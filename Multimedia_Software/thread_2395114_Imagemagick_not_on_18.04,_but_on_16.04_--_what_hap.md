---
title: "Imagemagick not on 18.04, but on 16.04 -- what happened?"
date: 2018-06-26
forum: Multimedia Software
---

### Post by cigtoxdoc on 2018-06-26
I suddenly have need to use Imagemagick because of friends sending me email from iPhones in heic format.  I remember it being on my PCs before upgrades to 18.04.  I just checked an old PC that has 16.04 and imagemagick.  Synaptic says it is installed on my PC but cannot be found from software sources and it will not launch from command line.

Google search yields [https://linuxconfig.org/how-to-install-imagemagick-7-on-ubuntu-18-04-linux](https://linuxconfig.org/how-to-install-imagemagick-7-on-ubuntu-18-04-linux) .  Is that the only way to get Imagemagick back?

Thank you,

John

---

### Post by &amp;KyT$0P# on 2018-06-26
> **cigtoxdoc said:**
>  it will not launch from command line.
What was the exact command you ran?

---

### Post by Holger_Gehrke on 2018-06-27
ImageMagick 6.9.something is in the repositories. The article you link to is about installing ImageMagick 7. AFAIK neither of these will convert HEIF. There is a patch/fork to do it by using some library for h265 decoding, but the devs aren't sure about the legal situation since HEIF uses some techniques that are protected by software patents.

GiMP added support for HEIF in version 2.10.2, which is available from **ppa:otto-kesselgulasch/gimp**.

Holger

---

### Post by cigtoxdoc on 2018-07-05
Thank you very much.  JOhn

---

