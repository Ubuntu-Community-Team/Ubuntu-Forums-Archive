---
title: "[SOLVED] Codecs on Heron"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by ivansf92 on 2008-03-25
Does anyone know how to install libdvdcss2 and w32codecs on hardy heron?
While I used gutsy, there were two options available: automatix2 and medibuntu.
However, automatix2 announced that they will discontinue it as of yesterday and medibuntu does not support hardy heron yet.

Also, does anyone know what libdvdread3 does?

Any help would be greatly appreciated.

---

### Post by overdrank on 2008-03-25
> **ivansf92 said:**
> Does anyone know how to install libdvdcss2 and w32codecs on hardy heron?
While I used gutsy, there were two options available: automatix2 and medibuntu.
However, automatix2 announced that they will discontinue it as of yesterday and medibuntu does not support hardy heron yet.

Also, does anyone know what libdvdread3 does?

Any help would be greatly appreciated.

Hi and I just wen to 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and installed the deb manually and off I went
example
```


wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb
sudo dpkg -i w64codecs_20061203-0medibuntu2_amd64.deb


```[http://ubuntuforums.org/showthread.php?t=734518](http://ubuntuforums.org/showthread.php?t=734518)

---

