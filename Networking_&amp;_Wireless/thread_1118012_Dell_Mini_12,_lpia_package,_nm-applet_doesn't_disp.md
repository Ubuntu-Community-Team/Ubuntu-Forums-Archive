---
title: "Dell Mini 12, lpia package, nm-applet doesn't display wireless"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by JerkyChew on 2009-04-06
I have a Dell mini 12 that I installed Hardy on using the LPIA architecture. The laptop has a Broadcom BCM4312 wifi card that shows up via lspci. It is running nm-applet 0.6.6 on the software side of things. 

I am also running a Dell Mini 9 as well with a slightly newer version of NetworkManager (0.7.0). It is using Intrepid Ibex using the i386 packages. 

When I right click the NM icon on the mini 9, it displays available wireless networks. When I right click the icon on the mini 12 it does not. It shows "enable networking" and "enable wireless" which are both checked. If I go to connection information it only shows the Ethernet (eth1) connection. If I run iwconfig from a command line eth0 shows up as an IEEE 802.11 adapter. 

How can I get the wireless to show up via the icon in the taskbar?

---

### Post by JerkyChew on 2009-04-06
2 more things that might be helpful:

1) The wl proprietary drive is in use. This came with the default package. I do not have ndiswrapper running (as far as I know).

2) If I go to Network Settings the wireless connection does show up with "Roaming Mode Enabled".

---

### Post by snowpine on 2009-04-07
Are you using "vanilla" 8.04, or the Dell version? The Dell version includes the driver for the Broadcom, but it was not added to vanilla Ubuntu until 8.10 (which is why Intrepid works on your other computer).

I would recommend either installing the Dell version of Ubuntu, or following these instructions from Broadcom: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

ps Also double check that wireless is enabled in the bios... sometimes it is the simple things. :)

---

### Post by JerkyChew on 2009-04-07
I am using vanilla 8.04, but the lpia architecture. 8.10 lpia wasn't out when I installed a couple weeks ago, not sure if it's out now.

Wi-fi is enabled and shows up in lspci so I assume the driver is loaded correctly. I'll check out that Broadcom link.

---

