---
title: "I can't connect to a Wi-Fi network?"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by DROIDAZ on 2013-06-07
I just recently installed Ubuntu 11.10 on my Gateway NE56R31U, and I realized that I can't get any connection. I have heard that I may need to update my driver but I can't seem to find it anywhere. It is the RTL8192CE by Realtek. And I also tried a few ping tests to my router's IP address and they were all successful.

---

### Post by lz1dsb on 2013-06-07
So... you can ping your router, but you can not exit from your inside network. Could we check the following:
iwconfig
ifconfig
lspci -nn

---

### Post by DROIDAZ on 2013-06-09
> **lz1dsb said:**
> So... you can ping your router, but you can not exit from your inside network. Could we check the following:
iwconfig
ifconfig
lspci -nn

I actually fixed it now by reinstalling the driver, but thank you anyways:)

---

