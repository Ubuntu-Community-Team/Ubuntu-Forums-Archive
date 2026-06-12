---
title: "Connection not Enabled on Startup"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2006-05-04
Hi guys,

I've been getting on great with my Linksys WPC11 v.4 wireless card since I installed it the other day. There's just one problem, I have to disable and then re-enable the device every time I start up my computer. It's clearly working in grub, as the link light goes on and it synchronises with the ntp.ubuntulinux.com server. Using Network-Manager I have got it to enable itself, but I have to enter a keychain every time, which is really no more convenient than the prior situation.

Is there any way to get the device to remain enabled?

My Network interfaces are as follows:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

auto wlan0

iface wlan0 inet dhcp
wireless-essid Big_Mutha
wireless-key XXXX
```

Thanks in advance,

mono.

---

### Post by monomaniacpat on 2006-05-05
Problem solved. I discovered that the link light went off when Network manager loaded in grub, so I uninstalled it. The ntp server is now loading successfully, too.

---

