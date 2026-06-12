---
title: "Networkmanager lists no networks"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2010-10-30
First of all, what was the name of the alternative for networkmanager? I will try to download that with windows for the time being. 

Networkmanager is listing no networks. How do I get it to search? 
If I disable & reenable networking via the netman icon there is not change...

There should really, really be a refresh button!

update:

ok, found cnetworkmanager. used that to refresh... found that even though it was working fine before, its not now (dont know why). found out the chipset is rtl8180 according to dmesg... so will have to use ndiswrapper...

---

### Post by MooPi on 2010-10-30
What sort of device is it ? USB ?  PCI ?
Open a terminal and give us ```
sudo lshw -C network
```
And for good measure ```
lspci
```

---

