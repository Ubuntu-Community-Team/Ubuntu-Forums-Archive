---
title: "Why is Realtek 8188CE so horrible on 13.04 and what can I do?"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2013-08-09
Every other wifi device in my house (iPhones, MacBooks, etc) is totally fine, but my System76 laptop (Realtek 8188CE card) has trouble constantly. The connection doesn't appear to drop, but all net access fails. Any suggestions?? I'm so frustrated I feel like ditching this laptop and getting a ZaReason which uses Intel-based wifi.

---

### Post by SweetAurora on 2013-08-09
Yes, this is from a Arch Forum, but this should also work on Ubuntu. It tells you how to manually install the driver for the card. Just head over to post #5 for instructions. :)
[https://bbs.archlinux.org/viewtopic.php?id=134548](https://bbs.archlinux.org/viewtopic.php?id=134548)

---

### Post by CaptSaltyJack on 2013-08-09
Already tried installing the drivers. It won't compile (various compiler errors).

---

### Post by SweetAurora on 2013-08-09
What errors popped up? Do you remember?

---

### Post by CaptSaltyJack on 2013-08-09
```

make[1]: Entering directory `/usr/src/linux-headers-3.8.0-27-generic'
  CC [M]  /home/bzb/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/bzb/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/bzb/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
make[2]: *** [/home/bzb/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/bzb/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-27-generic'
make: *** [all] Error 2

```

---

