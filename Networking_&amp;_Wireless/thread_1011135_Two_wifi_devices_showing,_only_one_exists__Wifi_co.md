---
title: "Two wifi devices showing, only one exists / Wifi constantly drops"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by Chemroydal Tissue on 2008-12-14
Since upgrading, my connection constantly drops. I've reviewed the forums and Google, but no fixes have worked for me. Attached are the results of:

```
lspci
ifconfig
iwconfig
lsmod
sudo lshw -C network
iwlist scan
sudo /etc/init.d/networking restart
```

as a .txt. Note:

```
sudo ifconfig ath0 down
sudo ifconfig ath0 up
``` results in a reset of the connection, as does ```
sudo ifconfig wifi0 down
sudo ifconfig wifi0 up
``` Despite not existing, wifi0 allowed to run alone seems to be more stable!?!

---

