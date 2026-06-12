---
title: "Thinkpads drop WiFi connection: needs reboot"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by orbister on 2009-11-26
I have observed this problem with three different Thinkpads, one R40e and two X31. All have internal Cisco Aironet wifi cards. I am trying to connect them to two different Netgear DG834G routers. One has WEP security, the other has none. Here is what happens:

The Thinkpad connects fine and can use the network without problems for an apparently random time between an hour and a week.

Then it loses the connection and nothing with bring it back. Network manager circles the green balls for a couple of minutes and then gives up. Starting dhclient from the command line times out. Switching wifi off and on does not help. The only way of getting connected is to reboot the machine.

Meanwhile, other computers can connect to the router without problems. iwlist on the Thinkpad shows the router and network fine. Plugging a PCMCIA card in and using that works fine. Using 9.10, fully up to date. Same applied in 9.04.

Any bright ideas?

---

### Post by Mahngiel on 2009-11-26
Aironet cards are largely unsupported my friend. Check the wifi wiki in the sticky above for complete details

---

### Post by keithmur on 2009-12-21
Well, my Thinkpad SL300 has exactly the same problem, and it has an Intel card:

[   30.579558] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54

I think it's device-independent.  Something to do with the new kernel?

---

