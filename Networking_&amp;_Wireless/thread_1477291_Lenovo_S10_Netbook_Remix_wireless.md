---
title: "Lenovo S10 Netbook Remix wireless"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Raguvian on 2010-05-08
I just installed Netbook Remix 10.04 on my Lenovo S10 netbook and wireless is not working. I looked on google for some answers and saw that the Broadcom STA driver may be missing so when I tried to install it through Synaptic Package Manager it said that it was already installed. When I click on the wireless icon, it says under wireless that the device is not ready and I can't connect to any wireless networks, even if the SSID is not hidden.

I am confused as I already have the driver and all the system updates but it still won't work.

Thanks

---

### Post by sysdfg on 2010-05-08
> **Raguvian said:**
> I just installed Netbook Remix 10.04 on my Lenovo S10 netbook and wireless is not working. I looked on google for some answers and saw that the Broadcom STA driver may be missing so when I tried to install it through Synaptic Package Manager it said that it was already installed. When I click on the wireless icon, it says under wireless that the device is not ready and I can't connect to any wireless networks, even if the SSID is not hidden.

I am confused as I already have the driver and all the system updates but it still won't work.

Thanks

I don't know what the odds are but I put Ubuntu on today also and the wireless would not work either. I'll be waiting on an answer to this also.

---

### Post by Raguvian on 2010-05-08
OK, I got it working. I went to System -> Hardware Drivers and it let me install the STA driver (actually there are two Broadcom drivers and I just installed both). You don't have to download them but you do have to install them (I guess they weren't included in the 9.10 release but they are there now, just not installed).

By the way, the first time I went to Hardware Drivers nothing popped up. When I rechecked it later it gave me the option to install the drivers.

Hope this helps.

---

