---
title: "issues playing dvd with ubuntu"
date: 2012-05-07
forum: Multimedia Software
---

### Post by bjgar on 2012-05-07
i HAVE TRIED VLC MEDIA PLAYER, XINE, GXINE ANd, movie player none work at least for redbox. gxine said error reading nav file. the other ones said i dont have permissions or that a dvd decryption library was not installed . i dont know why this is happening. i recently upgraded to ubuntu version 12 his never happened with 10 any help would be much appreciated.

---

### Post by kelvin spratt on 2012-05-07
> **bjgar said:**
> i HAVE TRIED VLC MEDIA PLAYER, XINE, GXINE ANd, movie player none work at least for redbox. gxine said error reading nav file. the other ones said i dont have permissions or that a dvd decryption library was not installed . i dont know why this is happening. i recently upgraded to ubuntu version 12 his never happened with 10 any help would be much appreciated.
you need these 2 packages 
libdvdcss2 and the codecs are optional for strange formats 
[LIST]
[*]**i386**: 
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
[*]**amd64**: 
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb) sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
[/LIST]


[LIST]
[*]For **i386**, the package is called **w32codecs**: 
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb) sudo dpkg -i w32codecs_20071007-0medibuntu2.1_i386.deb
[*]For **amd64**, the package is called **w64codecs**: 
wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb) sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
[/LIST]

---

