---
title: "Bridge kernel module problems"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by jabber42 on 2005-12-09
Hi all,

since the last kernel update to 2.6.10-6, I can't use bridging anymore.
When starting the bridge, I'm getting the following error:

> 
Dec  8 22:11:18 localhost kernel: Universal TUN/TAP device driver 1.5 (C)1999-2002 Maxim Krasnyansky
Dec  8 22:11:18 localhost udev[19298]: configured rule in '/etc/udev/rules.d/udev.rules' at line 66 applied, 'tun' becomes 'net/%k'
Dec  8 22:11:18 localhost udev[19300]: configured rule in '/etc/udev/rules.d/udev.rules' at line 65 applied, 'tap0' becomes 'net/%k'
Dec  8 22:11:18 localhost udev[19298]: creating device node '/dev/net/tun'
**Dec  8 22:11:19 localhost modprobe: FATAL: Error inserting bridge (/lib/modules/2.6.10-6-386/kernel/net/bridge/bridge.ko): Unknown symbol in module, or unknown parameter (see dmesg) **
Dec  8 22:11:19 localhost kernel: bridge: Unknown symbol br_fdb_update
Dec  8 22:11:19 localhost kernel: bridge: Unknown symbol br_fdb_update
Dec  8 22:11:21 localhost kernel: device tap0 entered promiscuous mode
Dec  8 22:11:21 localhost kernel: eth1: Promiscuous mode enabled.
Dec  8 22:11:21 localhost kernel: device eth1 entered promiscuous mode
Dec  8 22:11:21 localhost kernel: eth1: Promiscuous mode enabled.


All this happens on a headless computer, and afterwards I can not connect to that computer anymore, so debugging is a bit tedious (I had to restart the box :???: ).

A search didn't bring up any results.

Anybody an idea?

TIA, jabber42

---

### Post by shadowcode on 2005-12-25
I have the same problem. Looks like this kernel broke something.
I just rolled back to 2.6.10-5 until we/I/someone fixed this.

---

