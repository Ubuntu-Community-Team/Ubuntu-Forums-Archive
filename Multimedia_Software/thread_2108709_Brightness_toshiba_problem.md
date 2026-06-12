---
title: "Brightness toshiba problem"
date: 2013-01-25
forum: Multimedia Software
---

### Post by israa6000 on 2013-01-25
I just installed ubuntu 12.04 and i cant adjust the brightness
i have the nvidia_current installed and xblacklight but no xorgs file


when i try X -configure
the number of created screens does not match the current screens


please helpppp

---

### Post by tgalati4 on 2013-01-25
Open a terminal and post the output of:

```
lspci
```

Do the blue function keys for screen brightness not work?  Is there a setting in BIOS for controlling brightness?

There are some toshiba-specific controls that can be used:

```
apt-cache search toshiba
```

---

