---
title: "wi fi keep disconnecting regularly"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by viper_srt on 2011-04-28
i installed ubuntu 10.10 remix netbook edition on hp mini 110 last day.
my wifi is working fine its connecting every network only problem is it cant keep its connection constant, i mean it keep disconnecting frequently. once it disconnect i tried to connect again but it connects but i can not surf internet.
any one please provide me solution for this since i am first user for ubuntu so please explain me how to do this.


Thanks

---

### Post by uncaspi on 2011-04-28
Try power save mode on your wireless. Goto <Applications><Asses...> open a terminal and issue the following command:
sudo iwconfig wlan0 power off txpower 20

To determine if your card is named wlan0 issue the following command

sudo lshw -C network

---

