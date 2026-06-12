---
title: "Amilo l1300 wireless drivers"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
hi i just installed ubuntu on a [Fujitsu Siemens *Amilo L1300 and the wireless drivers are not working can anyone help me plz*]("http://www.diskusjon.no/index.php?showtopic=454531")


lcpci
```
01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
```

i dont have internet at it at all, writing this on a other computer with wireless working

---

### Post by chili555 on 2011-02-26
Please see post #4 here: [http://ubuntuforums.org/showthread.php?t=1694350](http://ubuntuforums.org/showthread.php?t=1694350)

The commands should be amended to:```
cd Desktop/lib/firmware
sudo cp isl3886pci /lib/firmware
```Post back if you need additional assistance.

---

