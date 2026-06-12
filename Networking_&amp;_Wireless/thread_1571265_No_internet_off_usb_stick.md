---
title: "No internet off usb stick"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by kencm on 2010-09-09
I installed 10.4 on a USB drive and all is well except that I cannot connect to the internet.  I am on Charter that uses automatic DHCP and manual DNS which I can configure but there is still no connection, either in wireless or wired. Running Windows 7 on the laptop and a Belkin wireless G router.  Any help?

---

### Post by peanut99 on 2010-09-09
run
```

sudo ifconfig -a
sudo lspci

```

This will let you know if your NIC is being recognized.  HTH.

-Peanut

---

### Post by kencm on 2010-09-09
Thanks.  Returns no errors and recognizes the hardware.  Sorry I cannot pots the readout for you but all was OK.

---

