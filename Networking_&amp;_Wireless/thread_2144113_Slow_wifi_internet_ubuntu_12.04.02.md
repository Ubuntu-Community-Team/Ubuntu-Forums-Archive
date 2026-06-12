---
title: "Slow wifi internet ubuntu 12.04.02"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by parantonis on 2013-05-11
Hello everybody

Im a new linux user and the first time I use ubuntu in my laptop I face this problem.
 When I connect to my home wireless network my internet connection speed is like a PSTN.
 I try to give interrnet to my computer via ethernet and it works very fast. Please be more
 analytic if you can because as I mention before i'm a new Linux user. ;)

```
Laptop : Acer Aspire 5738
[COLOR=#000000] Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232][/COLOR]
[COLOR=#000000]Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201][/COLOR]
[COLOR=#000000]Kernel driver in use: iwlwifi[/COLOR]

```
Thank u in advance.

---

### Post by praseodym on 2013-05-11
Hi,

deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by parantonis on 2013-05-11
> **praseodym said:**
> Hi,

deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Thank you very much my wireless is FAST again :)

---

