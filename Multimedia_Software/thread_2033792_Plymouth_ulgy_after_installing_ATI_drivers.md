---
title: "Plymouth ulgy after installing ATI drivers"
date: 2012-07-26
forum: Multimedia Software
---

### Post by poision_heart on 2012-07-26
i have installed additional drivers of ATI HD readon 4300 in my newly Kubuntu 12.04.

before ATI drivers plymouth was looking very pretty while booting.

after ATI drivers it became very ugly, it looks like streched logo of kubuntu is stretched and looks bigger.

how to set resolution for plymouth? i ve dell inspiron laptop 14" screen with max resolution 1366x768.

please help me to solve this..

---

### Post by brainwash on 2012-07-27
Install **hwinfo** and run following command (it will create a list of all [VBE]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions") modes which are  supported your ATI GPU BIOS):
```
sudo hwinfo --framebuffer
```

---

