---
title: "Network connections not showing up in nmapplet"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by jmull on 2012-10-30
My network connections are not showing up in the network manager applet in xubuntu. If I open the "Connect to a Hidden Wireless Network..." box I can select the network and connect or it will occasionally autoconnect when that box is loaded, but I'm unable to connect to any new networks. The problem is intermittent but more often than not that is the only way for me to connect.

I've searched googleubuntu, askubuntu, and regular google but none have any answers that are useful since it appears most of these posts were done with 10.10 and the solution was to simply upgrade.

Details:
Xubuntu 12.04.1 
recent clean install (not Wubi)
i686
Kernel 3.2.0-33 (3.5+ Kernels are not an option as they either don't work with my graphics card, my network adapter, or both)

Relevant section from lspci:

```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

I'm running the proprietary broadcom driver, the open source alternative does not work.

Output from pppoeconf (suggested for 10.10 users):

```
 Sorry, I scanned 2 interfaces, but the Access            &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason for  &#9474;          
          &#9474; the scan failure may also be another running pppoe       &#9474;          
          &#9474; process which controls the modem.
```

---

