---
title: "Wi-Fi only works when wired"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by ChrisNelson1022 on 2013-01-27
I upgraded from Ubuntu 10.04 to 12.04 a few weeks ago and have had problems with Wi-Fi most of that time.  The current symptom is that Wi-Fi only works when my laptop is docked at my desk and connected to a wired network.  If I suspend my computer, undock, and start it back up (that is, still on my desk, moved 6") I get no Wi-Fi.

rfkill sometimes shows a soft block but unblocking it doesn't help.

iwconfig says wlan0 has 0 dBm Tx-Power.

/etc/network/interfaces lists the loopback, eth0 (auto, dhcp) and eth1 (auto, static; this is a USB/Ethernet dongle connected to my dock).

/etc/udev/rules.d/70-persistent-net.rules lists eth0, wlan0, eth2 (an old name for the dongle), and eth1 (in that order).

I've tried adding wlan0 to interfaces with dhcp and that didn't help.

I tried reordering the udev .rules.  That didn't help.

Under 10.04, I sometimes had eth0 and eth1 labels reversed (that is, eth0 was the dongle and eth1 was the built-in NIC.  That didn't work well, either.

I'm using Xubuntu for the first time on 12.04 because I can't stand Unity but since the system doesn't see the Wi-Fi on boot, that seems irrelevant.

This is all on a Dell Latitude E5510.

Sorry that I can't post exact excerpts from my configuration files but I don't have a wired network where I am so the failing system is an island.

Any advice about why eth0 not being connected keeps wlan0 from working would be welcome.  Thanks.

---

### Post by praseodym on 2013-01-27
Change "false" to "true" in the /etc/NetworkManager/NetworkManager.conf. Otherwise the NM can not handle the settings in the interfaces. Reboot.

---

### Post by ChrisNelson1022 on 2013-01-27
> **praseodym said:**
> Change "false" to "true" in the /etc/NetworkManager/NetworkManager.conf. Otherwise the NM can not handle the settings in the interfaces. Reboot.

Thanks but that didn't help.  Or didn't help much.  On reboot the Wi-Fi was still unavailable.  If I open a terminal and do `ifconfig wlan0 up` the indicator comes on and `iwconfig` says I have a Tx signal but I don't get any connectivity.  Maybe I need to add wlan0 to interfaces?  But it used to Just Work (that is, boot or come out of suspension and Wi-Fi connected); that's where I want to get back to.

---

### Post by ChrisNelson1022 on 2013-01-27
I commented eth0 and eth1 out of /etc/network/interfaces and changed "managed" back to false in /etc/NetworkManager/NetworkManager.conf and rebooted.  The boot process didn't stall waiting for a network connection and Wi-Fi worked when I logged in.  I don't know how this will work at my desk tomorrow when I dock.  Will eth0 try to get an IP via DHCP from the company server?  I guess I'll find out.

---

### Post by ChrisNelson1022 on 2013-01-28
> **ChrisNelson1022 said:**
> I commented eth0 and eth1 out of /etc/network/interfaces and changed "managed" back to false in /etc/NetworkManager/NetworkManager.conf and rebooted.  The boot process didn't stall waiting for a network connection and Wi-Fi worked when I logged in.  I don't know how this will work at my desk tomorrow when I dock.  Will eth0 try to get an IP via DHCP from the company server?  I guess I'll find out.

Wired at my desk seems to be working.  I imagine I'm going to have to add back eth1 to get the statically assigned address I need there but this is progress.

---

