---
title: "[SOLVED] ath_pci not loading automatically??"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by rixtr66 on 2008-12-17
I just reinstalled ubuntu,and built and installed madwifi-hal-.0.10.5.6
now last time i built and installed this it started up automatically.
now i have to start a terminal and sudo modprobe ath_pci every time i start?
whats different?How can i fix it?
any help would be appreciated!
Rick  #-o

---

### Post by bgerlich on 2008-12-17
check "Hardware drivers" in System -> Administration - turn off atheros 5xxxx, turn on "atheros support" (or someting similar)

---

### Post by iponeverything on 2008-12-17
if that does not work..
doing this will make it load at boot:

```
sudo echo ath_pci >> /etc/modules 

```

---

### Post by rixtr66 on 2008-12-18
Thanks iponevrything,that did the trick!!
Rick

---

