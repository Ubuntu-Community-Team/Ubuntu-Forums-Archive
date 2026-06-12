---
title: "Wifi dropout requires system reboot"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by larascal on 2012-03-25
Having a bit of trouble with wifi in Ubuntu 11.10. Wifi will be running perfectly for anywhere from minutes to hours before dropping out. It will then ask for the password to rejoin the network, but will not connect unless I perform a system reboot.

I've already tried network manager restart, and attempted to use wicd instead without any luck.

Any help would be greatly appreciated,

thanks!

---

### Post by garvinrick4 on 2012-03-25
Open a terminal and copy and paste this in and tell users what network card you 
are using. 

```
lspci -nn | grep 0280
```

---

### Post by larascal on 2012-03-25
I'm using an Edimax N300 PCIE wifi card. EW-7612PInV2

Here is the output of the command.
>  01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01) 

Thanks!

---

### Post by garvinrick4 on 2012-03-25
So you are not using the internal realtek card?

---

### Post by larascal on 2012-03-25
No not using a Realtek card, using the Edimax pcie card with RTL drivers.

Thanks!

---

### Post by garvinrick4 on 2012-03-25
Is this where you got your driver:

[http://www.asus.com/Networks/Wireless_Adapters/PCEN15/#download](http://www.asus.com/Networks/Wireless_Adapters/PCEN15/#download)

---

### Post by larascal on 2012-03-25
No I didn't, I downloaded them from the Realtek website. I will try from your link and see how I get on.

Many thanks for your help so far.

---

