---
title: "wireless speed not as expected."
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by csh on 2010-12-28
Wireless NIC model: TP-LINK WN821NC (WN821N with USB cradle)
Driver: ar9170usb
Ubuntu version: 10.10 64 bit

Wireless router: TP-LINK W8960N (Wireless N 300 mbps)

In Windows, the connection speed can reach 300Mbps. But, in Ubuntu, the connection speed only reach maximum 54Mbps.

Why? How to solve?

---

### Post by Wayne_V on 2010-12-28
I would recommend you determine which chip set and driver the device is using (with lsusb/dmesg/lsmod) and then check if the driver fully supports your device yet (I think a lot of TP-Link devices use the Atheros chipset:  [http://linuxwireless.org/en/users/Drivers/Atheros](http://linuxwireless.org/en/users/Drivers/Atheros))

---

### Post by iponeverything on 2010-12-28
I think that the W8960N only has 10/100Mbps ports, so I am not sure how you reached 300Mbps. 

You should max out 100Mbps or about 11MB/sec in a best case.

---

### Post by csh on 2010-12-28
> **iponeverything said:**
> I think that the W8960N only has 10/100Mbps ports, so I am not sure how you reached 300Mbps. 

You should max out 100Mbps or about 11MB/sec in a best case.

That 300mbps is Wireless, not wired.

---

### Post by csh on 2010-12-28
> **Wayne_V said:**
> I would recommend you determine which chip set and driver the device is using (with lsusb/dmesg/lsmod) and then check if the driver fully supports your device yet (I think a lot of TP-Link devices use the Atheros chipset:  [http://linuxwireless.org/en/users/Drivers/Atheros](http://linuxwireless.org/en/users/Drivers/Atheros))

According to google, the chipset is Atheros AR9001U.

---

### Post by csh on 2010-12-28
Tried to blacklist the driver and use ndiswrapper with Windows XP 64 bit driver. It can go to 300Mbps.

But, I don't wish to use ndiswrapper. So, please, how to solve the problem?

---

### Post by iponeverything on 2010-12-28
> **csh said:**
> That 300mbps is Wireless, not wired.

Wireless to where? The wireless router and one of its 10/100 ports?

---

### Post by csh on 2010-12-28
> **iponeverything said:**
> Wireless to where? The wireless router and one of its 10/100 ports?

Of course the wireless router. Wireless N (or 802.11n) can reach 300Mbps. That mean if I use my wireless NIC to connect to my wireless router WIRELESSLY, of course it maximum can reach 300Mbps. If I connect through wired, then maximum can 100Mbps only.

---

### Post by Wayne_V on 2010-12-28
If it's an Atheros chip set you should look for support from the driver developer:  [http://linuxwireless.org/en/users/Support](http://linuxwireless.org/en/users/Support)

---

### Post by csh on 2010-12-28
I got another laptop which has built-in wireless NIC that use Atheros AR5B93 Chipset, that one can reach 300Mbps by just using ath9k driver that pre-installed with Ubuntu.

However, this one, the USB based one, must use Ndiswrapper with Windows driver to reach 300Mbps. Frustrated.

---

### Post by iponeverything on 2010-12-28
> **csh said:**
> Of course the wireless router. Wireless N (or 802.11n) can reach 300Mbps. That mean if I use my wireless NIC to connect to my wireless router WIRELESSLY, of course it maximum can reach 300Mbps. If I connect through wired, then maximum can 100Mbps only.

very useful, you can load up the router's configuration page in record time.

My point, the one that are choosing to miss is that 10/100 ports are a bottle neck.  How could you pull 300Mbit with your windows box when the traffic has to pass though 100Mbit port.

---

