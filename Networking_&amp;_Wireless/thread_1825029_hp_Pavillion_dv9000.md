---
title: "hp Pavillion dv9000"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by basedgod on 2011-08-14
[SIZE=3][B]im new to ubuntu and i cant seem to get my wireless driver working i did install ndiswrapper and i downloaded my driver and i installed it with ndiswrapper but it is still not working

[/B][SIZE=2][I]*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff
[/I][SIZE=3]**Im a huge noob and could really use some help!!**[/SIZE]
[/SIZE][/SIZE]

---

### Post by chili555 on 2011-08-14
Do you have a temporary wired ethernet connection? If so, this should get you going easily. Of course, post back if we can help you further.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by bkratz on 2011-08-14
> **chili555 said:**
> Do you have a temporary wired ethernet connection? If so, this should get you going easily. Of course, post back if we can help you further.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)



That is a good one Mr. Contributor--I bookmarked it!

---

### Post by basedgod on 2011-08-14
[COLOR=Black][B]Ok im going to reboot now

[/B][/COLOR]

---

### Post by basedgod on 2011-08-14
**Ok i did as instructed in the link but im still unclaimed**

*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff

---

### Post by chili555 on 2011-08-14
Let's see:```
sudo modprobe b43
ls /lib/firmware/b43
dmesg | grep b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by chili555 on 2011-08-14
> **bkratz said:**
> That is a good one Mr. Contributor--I bookmarked it!Several of us are trying to write this stuff once and link it when the same device comes up.

---

