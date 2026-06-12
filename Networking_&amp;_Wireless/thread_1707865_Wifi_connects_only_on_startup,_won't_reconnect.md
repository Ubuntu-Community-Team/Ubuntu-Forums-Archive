---
title: "Wifi connects only on startup, won't reconnect?"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by Popeluvsu on 2011-03-15
Newbie here having serious issues with the wifi. I can connect after start up but  after 5-10 minutes, the signal drops and I cannot reconnect (to mine or  any nearby network) unless I restart the machine.  

Just opened a brand new Lenovo Thinkpad Edge 14 and installed Ubuntu 10.10 wiping out windows. 

When I run 
lspci | grep Wireless 
I get this: 

```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)


```

Someone suggested I use the following: 

```
sudo rmmod r8192se_pci
sudo modprobe r8192se_pci hwwep=0
```

 this seems to offer a temporary  fix, letting the wireless reconnect for 5-10 minutes until it drops  again and I'm back to square one. 

Hoping to find a permanent fix, pretty frustrated at this point. Anyone have any ideas:confused:

If I'm missing some info please let me know, i'll be happy to find more in the terminal. Thanks!

---

