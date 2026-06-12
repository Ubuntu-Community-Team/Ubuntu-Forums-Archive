---
title: "3D does not work (ATI card problem)"
date: 2012-05-26
forum: Multimedia Software
---

### Post by rudolfl on 2012-05-26
Hi, all,

Hopefully someone can give me  hand here, because I am lost.
Ubuntu 12.04 running on HP laptop Pavilion dv6. Vide card is ATI HD5000 series.

I have enabled and activated ATI driver shipped with Ubuntu. 3D effects do not work. Doing some investigations:

fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Tried to install driver from ATI and X will not start at all.
I am quite familiar with Linux, but not with X (I am mainly involved with Linux on embedded systems).
Any help is greatly appreciated.

Thanks,
Rudolf

---

