---
title: "unable to access network-manager for wireless connection"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by andrewkillandrew on 2009-02-03
Hi,

I'm very new to ubuntu and am trying to connect to my wireless router via network-manager, problem is I am unable to access this application as I seem to be missing the 'network' option in system>administration. I have tried reinstalled the network-manager but the problem persists. Is there anyway I can open network-manager through the terminal or is there another way around this problem where I do not need to use network-manager?

Thanks.

---

### Post by Carlosmarioagamez on 2009-02-03
*Wifi connection through Networ-Manager simply sucks, well, also LAN connection, try to install wicd, you can find it on synaptic; install wicd and uninstall network manager :)*

---

### Post by Zeedok on 2009-02-03
Check on your panel, top right hand corner, you should see an icon that will allow you to configure network manager (see my attached screenshot).  Just right click first and make sure "Enable Networking" and "Enable Wireless" are checked.  The click on the icon and you should see the available wireless networks close to you.  Connect to yours, enter the password and "Bob's your uncle".

Hope this helps.

---

### Post by tednumber8 on 2009-02-03
You have to use NETWORK CREEPY MANAGER

---

### Post by andrewkillandrew on 2009-02-03
ok i've tracked down the network-manager applet, which won't run (not installed properly?). besides this it seems my network card is not setup properly:

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:82:b5:f6:5c:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

any suggestions?

---

### Post by andrewkillandrew on 2009-02-03
> **Zeedok said:**
> Check on your panel, top right hand corner, you should see an icon that will allow you to configure network manager (see my attached screenshot).  Just right click first and make sure "Enable Networking" and "Enable Wireless" are checked.  The click on the icon and you should see the available wireless networks close to you.  Connect to yours, enter the password and "Bob's your uncle".

Hope this helps.
that icon is missing from my panel.

---

