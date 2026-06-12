---
title: "Unable to connect to ADSL modem"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by arka.sharma on 2011-09-19
Hi,

 Sorry if I am spamming but I need an urgent solution for this.I am using ubuntu 8.10 and I'm having a broadband connection of airtel  which provides a wired ADSL modem.I connect my modem in windows 7 with  lan cable and dhcp.I tried to do the same in ubuntu by connecting the  lan cable to serial port and then tried to run dhclient.After a while it  shows "no working leases in persistent database sleeping".Then I  discovered that no light is blinking in the serial port where I connect  the lan cable.Please provide any solution apart from installing newer version. 

Thanks & Reards,
Arka

---

### Post by varunendra on 2011-09-19
> **arka.sharma said:**
> ....I  discovered that no light is blinking in the serial port where I connect  the lan cable.
Do you mean Ethernet port?

Please post outputs of:
```
ifconfig -a
```
and
```
sudo lshw -C network
```

Is there some particular reason why you don't want to try a newer version?

---

