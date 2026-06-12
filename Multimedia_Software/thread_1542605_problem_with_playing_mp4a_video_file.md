---
title: "problem with playing mp4a video file"
date: 2010-07-30
forum: Multimedia Software
---

### Post by chetanrocks on 2010-07-30
hi,, my mp4 file will play only  audio but not video,,,,, i tried to install h264 decoder but its not working,,
im gettin this error

Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


so please help to fix this problem

---

### Post by Earl_Maroon on 2010-07-30
This should be easy enough, though I couldn't say exactly what your problem is. Try installing ubuntu-restricted-extras, which should have what you need, if you don't have it:

Type, in a terminal (Applications>Accessories>Terminal)

```
sudo apt-get install ubuntu-restricted-extras
```

Hit enter and enter your password.

Restricted means that it's not necessarily on a free (as in libre) license; it's not GPL'd.

If that doesn't work try installing the Medibuntu repository, which has more codecs. Google it and you'll find step by step instructions. It is not free (libre) either, hence it is not included by default. The chances are you don't care about the software license, so that doesn't matter.

Make sure w32codecs is installed (and for DVD playback you should make sure libdvdcss2 is installed too - that wouldn't be related to your current issue, but it could be helpful at a later date).

Oh, and it's most likely that you don't really want to have your CD as an installation source - you can turn that off by unticking it in Synaptic's Settings>Repositories screen.


Hopefully somewhere in there is your solution.

---

### Post by chetanrocks on 2010-08-02
hey thanks ,i will check if its working or not

but unrestricted is for online videos, my video is not working in my system

---

