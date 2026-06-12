---
title: "Configuring Wireless from the command line"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by malfist on 2009-02-17
So I installed ubuntu-server and it doesn't have a gui to use network-manager with and I need help configuring wireless (it didn't detect my ethernet for some reason (or ifconfig isn't seeing it)

say the ssid is hidden and is "dummy_network"
WPA Enterprise
WPA-LEAP
TKIP
username = blah
password = gobblygook (not real)
authentication type is MSCHAPV2

how can I configure my wireless?

Thanks,

---

### Post by malfist on 2009-02-17
Got ethernet working /etc/network/interfaces needed auto eth0
iface eth0 inet dhcp

Still would like to know how to configure wireless

---

### Post by Yellow Pasque on 2009-02-17
You can use the iwconfig command or you can enter the info in the interfaces file like so: [http://blog.dotkam.com/2008/06/03/connect-to-wireless-network-on-startup/](http://blog.dotkam.com/2008/06/03/connect-to-wireless-network-on-startup/)

---

### Post by malfist on 2009-02-17
I couldn't find anything about getting iwconfig to support wpa-enterprise. There's no way to specify a username.
I'm supposed to use wpa_supplicant.

---

