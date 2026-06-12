---
title: "VirtualBox:  LAN and WLAN on Ubuntu guest machine"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by lred_tree on 2011-07-08
I'm posting this info because I solved this myself and wanted to share.  Preemptive apologies if it's a repeat, but it may be helpful to somebody.

Okay so, I had two Ubuntu machines running on VirtualBox- a Lubuntu install and an Ubuntu server install.  I work in IT and can be in several different offices a day so I wanted the virtual machines to connect to whatever network the host system was on (Windows 7 btw), whether LAN or WLAN, or both.  I had a lot of problems where the guest system could only connect to wired networks, or only to wireless, but never either or.  So here's how I fixed it:

First, shut down the virtual machine.  In the VirtualBox window select the machine and go Settings -> Network.  Enable Adapter1 and attach the Bridged Adapter, select the Realtek NIC.  Under Advanced set the adapter to the Intel Desktop version.  Write down the MAC address.

Then, enable Adapter2 and attach the Bridged Adapter with the Broadcom NIC.  Under Advanced select the Intel Desktop version and write down the MAC address.

Start the virtual machine and log in.  In the terminal do:
```
sudo gedit /etc/network/interfaces
```

Edit the file so that it has:

```
auto eth0
iface eth0 inet dhcp
        hwaddress ether (adapter1 mac address)

auto eth1
iface eth0 inet dhcp
        hwaddress ether (adapter2 mac address)
```

Save and exit

Next, do:
```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

Make sure the lines that end with eth0 and eth1 line up with the right MAC addresses (IE adapter1 for eth0 and adapter2 for eth1), if not change it so it matches up.

Save and exit.

Restart your virtual machine.  This is important because VirtualBox needs to connect the appropriate network to the appropriate device.  Once you get back to the terminal do:
```
sudo ifconfig -a
```
to make sure everything looks right (eth0 should be LAN and eth1 WLAN).

If you don't have gedit, just do ```
sudo vi
``` or abiword or whatever.

---

