---
title: "Ethernet net card not detected in ubuntu 9.10"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by smenon2009 on 2011-08-02
Here is the  result to the command/
sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)

Ethernet card is not detecting .I tried the option on the similar prob, but nothing working fine for me.

Thank you for the help..

---

### Post by wildmanne39 on 2011-08-02
Hi, run this command please.
```
lspci -nn | grep 0200
```
and post the results here.
Thank you

---

### Post by Elfy on 2011-08-02
If you have only just installed it, do you know that you've installed an End of Life version that's no longer supported. 

If you did know then ignore me ;)

---

### Post by smenon2009 on 2011-08-04
lspci -nn | grep 0200
01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1083] (rev c0)

---

### Post by bkratz on 2011-08-04
> **smenon2009 said:**
> lspci -nn | grep 0200
01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1083] (rev c0)



Here is a whole thread about that device ID 1969:1083

[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

but check your kernel version to see if it applies

---

