---
title: "Sharing Internet &amp; connecting Ethernet and wireless"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by yellowstar on 2010-01-13
I tried to setup sharing to connect Ethernet and wireless. I want Ethernet connected to desktop A, and wireless connected to another laptop(B), with my laptop acting as an AP. I set the network settings in Firestarter: Internet for wireless, local network for Ethernet. I want to share Internet from laptop B over the network. Internet won't work from my laptop since it seems to use the wrong interface.(Since the desktop is sharing Internet, although not on Internet usually when connected via Ethernet. And of course DNS/Gateway IPs aren't set for wlan0 since it's acting as an AP.) SMB wouldn't work for desktop A and laptop B: laptop B could detect desktop, but reports error "Path not found".

---

### Post by Iowan on 2010-01-13
Have you seen [this]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") help page?

---

### Post by yellowstar on 2010-01-13
No, but I got terminal error "command not found" when stopping NetworkManager. I tried sudo ls /etc/dbus-1/event.d, and got nothing listed.

EDIT:
Running sudo service network-manager stop, then running sudo gedit /etc/network/interfaces doesn't help, my network interfaces aren't listed there...(Or do they need added manually?)

---

