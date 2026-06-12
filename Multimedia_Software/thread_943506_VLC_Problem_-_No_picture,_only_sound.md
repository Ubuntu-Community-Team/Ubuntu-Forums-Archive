---
title: "VLC Problem - No picture, only sound"
date: 2008-10-10
forum: Multimedia Software
---

### Post by goldiejones on 2008-10-10
Hi, I know there are a lot of threads touching on this subject but I am extremely frustrated as I cannot find any answers.

I am trying to play a .avi (divx) movie on VLC, I have installed it correctly, but when I try to play the file I just hear sound no picture.  It does the same with Totem Movie Player also

Is there something I have missed here or does someone have some advice regarding this issue?

Thanks in advance

Kind Regards
Martin

---

### Post by xc3RnbFO8P on 2008-10-10
Do you have mediubuntu installed?

---

### Post by goldiejones on 2008-10-10
no...what is it and what does it do?

Kind REgards
Martin

---

### Post by xc3RnbFO8P on 2008-10-10
Its a codec pack, you will be able to play more formats of audio and video.

---

### Post by goldiejones on 2008-10-10
Ok I'll try it, thanks!

---

### Post by xc3RnbFO8P on 2008-10-10
Here is the link:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by xc3RnbFO8P on 2008-10-10
Here is How to (Hardy Heron, just copy/paste into Terminal):

You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.
**Say yes.**

1. > sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
2. > sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
3. > wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
4. > sudo apt-get install w32codecs
5. > sudo apt-get install libdvdread3
6. > sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by meka4996 on 2009-05-23
Try this one...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

