---
title: "USB wireless adapter detected but not working?"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by TheOm3ga on 2010-06-28
Hi. I've got a Inves Wireless USB Adapter and Ubuntu 10.04 (fresh clean install). The adaptar has got a green led.

When I plug it in, the led stays on and the device does not seem to work.

The output from [FONT="Courier New"]lsusb[/FONT] says:
```
Bus 002 Device 002: ID 0ace:1215 ZyDAS WLA-54L 802.11bg
```

And [FONT="Courier New"]lshw -C network[/FONT] says:
```
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:1d:1a:06:60:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

If I try to scan for networks, [FONT="Courier New"]iwlist[/FONT] says:
```
wlan1     Interface doesn't support scanning : Network is down
```

But if I enable the device using [FONT="Courier New"]ifconfig wlan1 up[/FONT], I'm able to scan and detect all the wireless networks (ONLY using [FONT="Courier New"]iwlist[/FONT]). Once I enable it, the led starts blinking slowly.

Regardless of what I do in the command line, the Ubuntu's Network Manager always says that the device is disabled.

What can I do to make the Network Manager detect/scan wireless networks?
Is there a way of automatically enabling the device when I plug it in, the same as ifconfig up does ?

---

