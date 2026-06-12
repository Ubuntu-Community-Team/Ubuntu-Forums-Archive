---
title: "Ubuntu 11.04 WLAN does not connect automatically on reboot"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by naturewise on 2011-05-07
I have a problem on Ubuntu 11.04 64-bit. The wlan does not connect automatically on reboot, although "Connect automatically" is ticked in network manager. I always have to choose "Connect to hidden wlan", choose my config, enter my password, then connect. Once connected everything works fine. But it's kind of annoying to manually connect each time after a restart.
Config:
- hidden SSID from router
- mode -> infrastructure
- connect automatically -> ticked
- available to all users -> ticked
- Encryption -> WPA & WPA2 personal

This worked well on Ubuntu 10.10.
Any suggestions? Thanks!

---

### Post by Wim Feijen on 2011-05-08
I am experiencing the same symptoms.

Ubuntu does not connect to my wireless connection, though it is listed as "auto linksys" in the configuration menu.

I am using a 32 bits Fujitsu Siemens Amilo Li 1718.

Best regards,

Wim

---

### Post by Kryzzalid on 2011-05-09
Exact same problem here! I tried to figure out why it doesn't connect automatically but i haven't found anything...

---

### Post by naturewise on 2011-05-11
This seems to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760015](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760015)

I hope it will be fixed shortly...

---

### Post by anco on 2011-05-13
exact same problem for me too. 10.04 for my wife's laptop is fine. 10.10 on my older laptop is fine too. 11.04 does not connect automaticly... really annoying several times per day manually connecting. 

thank you already for the person who can fix this.

---

### Post by Kryzzalid on 2011-07-01
Hi.

I untick the option "available to all user". (Since I'm the only one who uses this computer) then I saved. When I tried to reconnect, it asked me the WEP key and the name of the network. After I re-entered them, it now seems to connect automatically to the wifi router without entering system password. I hope it helps.

---

### Post by naturewise on 2011-07-20
Recently, there was a kernel update to 2.6.38-10. Now, it's working fine...
Thanks to those who fixed it!
Cheers!

---

### Post by jjaakkol on 2011-08-06
> **naturewise said:**
> Recently, there was a kernel update to 2.6.38-10. Now, it's working fine...
Thanks to those who fixed it!
Cheers!

I have kernel 2.6.38-10 but problem exists still. Acer Aspire 3610 and atheros. 

 description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.

      configuration: broadcast=yes driver=ath5k driverversion=2.6.38-1

---

