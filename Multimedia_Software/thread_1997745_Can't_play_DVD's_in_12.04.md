---
title: "Can't play DVD's in 12.04"
date: 2012-06-05
forum: Multimedia Software
---

### Post by Randy M on 2012-06-05
I get "Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed." I've tried: "sudo apt-get install libdvdread4" and "sudo /usr/share/doc/libdvdread4/install-css.sh" to no avail. This is in Movie Player and VLC, but VLC doesn't give an error. It just sits there.[/FONT]

---

### Post by VE6EFR on 2012-06-05
> **Randy M said:**
> [FONT=monospace]I get "Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed." I've tried: "sudo apt-get install libdvdread4" and "sudo /usr/share/doc/libdvdread4/install-css.sh" to no avail. This is in Movie Player and VLC, but VLC doesn't give an error. It just sits there.[/FONT]


I ended up doing the following in order to get DVD playback working on my system:

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

Depending on your computer this may or may not work in your case.

---

### Post by Randy M on 2012-06-05
Thanks, but I still get the same error.

---

### Post by Randy M on 2012-06-08
Looks like it was a region issue. I'd have thought that was automatic. Oh well, it plays, but it's really jerky. I'll post a separate question on that one.

---

### Post by Borunco on 2012-06-09
> **Randy M said:**
> Looks like it was a region issue. I'd have thought that was automatic. Oh well, it plays, but it's really jerky. I'll post a separate question on that one.

If you follow this tutorial everything will work.  [[all variants] Comprehensive Multimedia & Video Howto - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=766683").

enjoy
borunco

---

