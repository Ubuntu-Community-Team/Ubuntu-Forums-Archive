---
title: "How to tell if wireless N is being used?"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by tonyps on 2010-06-11
Morning,
Laptop- Toshiba Satellite A505D-S6958
OS- Ubuntu 10.04, 32bit
Wireless- Realtek rtl8192E 802.11bg+n

My question is:
If my laptop is connected to a wireless network that supports "g and n", how can I tell if the laptop is making use of the faster "n" protocol and not just the "g"?
I remember in Windows that I had to change the setting on the NIC specifically to use n...

Thanks,
Tony ...

---

### Post by Arsic on 2011-04-05
iwconfig will tell you the bit rate. 54 Mbps is wireless G speeds, anything above that should be wireless N, but theoretically it should be around 300 Mbps. I've never gotten above 108 because my router sucks with mixed mode with other Wireless G speed devices on my network, therefore reducing a potential 130-150 Mbps realistic speeds to around 108 Mbps.

If there's any trouble, it's likely to do with the driver you're using.

---

### Post by Sef on 2011-04-05
> iwconfig will tell you the bit rate. 54 Mbps is wireless G speeds, anything above that should be wireless N, but theoretically it should be around 300 Mbps. I've never gotten above 108 because my router sucks with mixed mode with other Wireless G speed devices on my network, therefore reducing a potential 130-150 Mbps realistic speeds to around 108 Mbps.

The router will run at the lowest speed, so if you have G devices, then it would run at the G speed. Once all of the devices on the network run N, then you should see the N speeds.

---

