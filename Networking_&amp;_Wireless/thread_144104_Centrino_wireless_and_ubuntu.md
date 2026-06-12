---
title: "Centrino wireless and ubuntu?"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by Elvish Legion on 2006-03-13
I recently bought a linksys router (came with a wireless G card) 

I tried installing xubuntu (worked fine) at first the wireless connection was running fine...then it just died...how do I fix it? The centrino card was auto configured by ubuntu installing...where are errors logged for this type of thing so I can post em for help

---

### Post by Zelut on 2006-03-13
Well lets see what we can figure out..

Error messages would be in /var/log/.  Probably syslog or maybe the messages file.  Browse through some of those & see what you can find.

If you want to give me some information about your wireless card as well we can see if we can get that running again.

Do these commands (at the terminal) return anything?
[B]lspci | grep 802.11
dmesg | grep 802.11
[/B]

Also,
**lspci -n**

---

### Post by Elvish Legion on 2006-03-13
elvish@xubuntu:~$ lspci | grep 802.11
elvish@xubuntu:~$ dmesg | grep 802.11
[4294697.404000] ieee80211: 802.11 data/management/control stack, 1.0.3
elvish@xubuntu:~$ lspci -n
0000:00:00.0 0600: 8086:3340 (rev 03)
0000:00:01.0 0604: 8086:3341 (rev 03)
0000:00:1d.0 0c03: 8086:24c2 (rev 01)
0000:00:1d.1 0c03: 8086:24c4 (rev 01)
0000:00:1d.2 0c03: 8086:24c7 (rev 01)
0000:00:1d.7 0c03: 8086:24cd (rev 01)
0000:00:1e.0 0604: 8086:2448 (rev 81)
0000:00:1f.0 0601: 8086:24cc (rev 01)
0000:00:1f.1 0101: 8086:24ca (rev 01)
0000:00:1f.3 0c05: 8086:24c3 (rev 01)
0000:00:1f.5 0401: 8086:24c5 (rev 01)
0000:00:1f.6 0703: 8086:24c6 (rev 01)
0000:01:00.0 0300: 1002:4c57
0000:02:00.0 0607: 104c:ac55 (rev 01)
0000:02:00.1 0607: 104c:ac55 (rev 01)
0000:02:01.0 0200: 8086:101e (rev 03)
0000:02:02.0 0280: 8086:1043 (rev 04)
elvish@xubuntu:~$

---

### Post by Zelut on 2006-03-13
Looks like those first two didn't return what we needed.  Can you try these as well please?  Is it an onboard wireless card? usb? pcmcia?

lsusb | grep 802.11
lspci | grep Network controller

---

### Post by Elvish Legion on 2006-03-13
elvish@xubuntu:~$ lsusb | grep 802.11
elvish@xubuntu:~$ lspci | grep Network controller
grep: controller: No such file or directory


Its an onboard intel wireless b...I have a pcmia G card I can use if need be

---

