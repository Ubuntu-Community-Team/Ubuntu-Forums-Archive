---
title: "cannot reenable wifi"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by katj12480 on 2009-06-21
I disabled my wifi connection and cannot re-enable it, even after a complete reinstall, including formatting of partitions.

ifconfig shows eth0 and lo but not wlan0

/etc/network/interfaces:
auto lo
iface lo inet loopback

I am running 9.0.4 64 bit dual boot with Vista (yes I know; it came with the computer)

Assistance would be greatly appreciated

---

### Post by sanemanmad on 2009-06-21
please post output from following log files:

```

/var/log/syslog
/var/log/dmesg

```

what does ```
lspci|grep -i "Network Controller"
``` shww?

---

### Post by katj12480 on 2009-06-21
it's not working under Windows either. This is a brand new computer and wireless has been fine for the 3 days I've been using it.

btw, it's a Toshiba L305-S5894

---

### Post by sanemanmad on 2009-06-21
Well in that case... it sounds like this is a hardware related issue. Try searching for a Wireless on/off switch on the laptop. Hope this helps

---

