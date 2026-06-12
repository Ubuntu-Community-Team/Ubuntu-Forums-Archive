---
title: "Notebook network card problem after reinstalling ubuntu 5.10"
date: 2006-05-13
forum: Networking &amp; Wireless
---

### Post by Edgy Eft on 2006-05-13
Hi,

I got a root file-system error this week and I had to reinstall ubuntu completely. Everything on my notebook is working good, but there is one thing:

Last week I was able to boot not wired to a LAN and i got the yellow triangle in the gnome LAN widget. If I wired it to my router, I got an IP and was able to start working on my LAN immediately. After reinstallation this doesn't work anymore. If I boot without a wired LAN cable, I got a red symbol in my widget and LAN doesn't work, if I wire my notebook to LAN.

The only solution is to reboot my notebook. But that ist not practical at all.


I can't even wake up my LAN card with "sudo ifup eth0" or sth else. What can I do, to declare my LAN card permanent enabled like last week?

dmesg:
```
[4294679.995000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294680.019000] e100: eth0: e100_probe: addr 0xfc020000, irq 9, MAC addr 00:E0:00:3F:6F:7F
[4294726.101000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
```

lspci:
```
0000:00:12.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
```

lsmod:
```
e100                   32768  0
mii                     5248  1 e100 
```

The modul is loaded, but I can not activate it with dhclient or ifup...

/etc/network/interfaces 
```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp
# auto eth0

# The secondary wifi interface
# iface eth1 inet dhcp
# auto eth1

```


Is there any chance? :)

---

### Post by slightly72 on 2006-05-14
It seems that the "auto eth0" line is connected. That means that, on boot, or when doing /etc/init.d/network restart, that card is not going to be activated (in my case, I don't have an eth0, and for eth1 -- the wireless card -- it means that no IP address is set). Try uncommenting that line and either reboot or restart the networking.

---

### Post by Edgy Eft on 2006-05-14
Hi,

auto eth0 ist already uncommented one line above. And I dont want do to restart. If I restart, I will have LAN. But I don't want to restart. This has to work without, like last week.

---

### Post by slightly72 on 2006-05-14
If you don't want to restart, maybe you should try "sudo /etc/init.d/networking restart" -- this disables all the networking, and restarts it (i.e. gives you a clean restart, as if you'd reboot the computer). Though, it might not do much, since I think this script calls ifup eth0.

---

### Post by Edgy Eft on 2006-05-14
As I mentioned above, this command is not successfull. Restarting the network gives an [ OK ], but my LAN card is not initialized!

If I want to bring it up with ifup or ifconfig up, I got an error: eth0 device not found.

The LAN card module is loaded, but eth0 is not reachable or initiateable. That is my problem.

---

### Post by Edgy Eft on 2006-05-14
I solved my problem:

I just installed the package 
```
ifplugd
```
and reconfigured it with
```
sudo dpkg-reconfigure ifplugd

```
It is important that ifplugd is _not_ allowed to look for eth0 at booting time. Its a little bit funny and doesn't make sense at all, but it is working perfect! :) 

After booting without LAN cable, the small yellow triangle appears in my LAN widget. Connecting my Notebook to my Router ... and the yellow triangle disappears and I can open my VPN connection to university...

I love ubuntu ;)

---

