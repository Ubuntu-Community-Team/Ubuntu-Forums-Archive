---
title: "Configure static IP?"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by g0nz0uk on 2013-01-18
Hello,

I want to give my wireless card a static IP for a while, but can't see how I do this as I am new to this, any ideas on how to set this?

Thanks

---

### Post by ahallubuntu on 2013-01-18
Click on the Network Manager Notifier Icon (the one that shows wireless networks, etc.)

Click "Edit Connections."

Click on the Wireless tab.

Click on the Wireless connection you are interested in.

Click Edit.

IPv4 Settings

Change the "Method" from "Automatic (DHCP)" to "Manual."

Click "Add" to add the static IP, etc.

---

### Post by g0nz0uk on 2013-01-18
Hi,

I tried that but 'ifconfig' shows the DHCP IP still, even after a reboot.

---

### Post by steeldriver on 2013-01-18
What version of Ubuntu are you running?

Do you have anything other than the loopback (lo) interface defined in your /etc/network/interfaces file?

---

### Post by dpurgert on 2013-01-18
put something like this in /etc/network/interfaces

```

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4

```

then restart the computer, and the interface will have a static IP (granted, if you're using a wireless card or your wired network card isn't eth0, you'll have to change that to suit your setup)

---

### Post by ahallubuntu on 2013-01-18
If you use Network Manager (like most people do) for network connections in Ubuntu, the /etc/network/interfaces file may be ignored completely.  Either use Network Manager to do it or uninstall Network Manager completely and do all of your networking manually via the terminal.

---

