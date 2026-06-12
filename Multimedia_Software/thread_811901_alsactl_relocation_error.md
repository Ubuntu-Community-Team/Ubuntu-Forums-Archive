---
title: "alsactl relocation error"
date: 2008-05-29
forum: Multimedia Software
---

### Post by Vermind on 2008-05-29
Hello,
I had recently played with the most recent alsa sources from [alsa-project]("http://www.alsa-project.org/main/index.php/Main_Page"), and was wondering why my alsactl store was giving a weird error:
```
alsactl: relocation error: alsactl: symbol snd_tlv_parse_dB_info, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
```, and my gnome mixer settings did not seem to stick.
I googled a bit, found this old thread
[Intel HDA problems]("http://ubuntuforums.org/showthread.php?t=348248")
but nothing of use, really.
Someone had hinted somewhere, that they had two instances of alsactl:
one in /usr/sbin, and one in /sbin. a dpkg-query -S alsactl 
tells me that it should only be in /sbin in Ubuntu.
I therefore removed the (apparently left-over) alsactl from /usr/sbin,
and the error went away.

The right way to remove old alsactl and other alsa-utils, is to do it in a similar way you installed it. in my case, I should download the alsa-utils-0.16 source package and do:
```
./configure --prefix=/usr
sudo make uninstall
```, as I installed alsa-utils with ```
./configure --prefix=/usr
sudo make install
```. The important part here is that the prefix is the same as last time.

I posted this to help people, and possibly, me, when I mess up my alsa again.

---

### Post by geoffd123 on 2008-07-16
Thank you, it certainly helped me.  My sound card stopped working back in V7 and I had tried to get it working by downloading the sources and installing them.  Unknown to me I had 2 versions of alsactl, one on /sbin and one in /usr/sbin.

Cheers
Geoff

---

### Post by thripsi on 2009-03-26
Thanks too. Your hint solved a similar problem that I had after serveral trials to get sound working on server edition of ubuntu.

---

