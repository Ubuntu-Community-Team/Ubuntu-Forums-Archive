---
title: "Problem with scanner ACER 640BU and Ubuntu 10.04 64bit"
date: 2010-10-08
forum: Multimedia Software
---

### Post by oskiiiiii on 2010-10-08
I work with Ubuntu 10.04. After searching the forums, I have unsuccessfuly followed this proceure to make my scanner work:

1.-I have copied my scanner firmware to /usr/share/sane/snapscan/. According to the page [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/), my firmware should be u126v043.bin.

2.-I have edited the file /etc/sane.d/snapscan.conf and modified the line "firmware /usr/share/sane/snapscan/u126v043.bin", the place where my firmware file is located

Both xsane and simple scanning software detect the scanner as "FlatbedScanner16", but they cannot communicate with it.

The webpage I mentioned before says that it should be detected as "FlatbedScanner13".

As "FlatbedScanner16" is the way Acer 620UT is detected, I -unsuccessfuly again- tried to use u64v120.bin firmware.

¿Any suggestion?

To continue investigating, anybody can tell me where to find documentation related to firmware upload process? is the file uploaded to scanner? when?

Any help is welcome
Thanks a lot

---

