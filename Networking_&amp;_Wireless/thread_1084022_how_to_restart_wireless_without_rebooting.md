---
title: "how to restart wireless without rebooting"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by axel_2078 on 2009-03-01
I noticed that whenever my laptop goes to sleep, the wireless connection is severed once it wakes up. Rebooting fixes the problem, but I want to know if there is a command I can type to restart just my wireless interface. After doing some searching in the forums, I found that people recommended using the following command: sudo /etc/init.d/networking restart

The problem is that when I issue this command, it seems to restart all the interfaces EXCEPT my wireless. My wireless interface is ath0 and when I run the command, I get this...

*Reconfiguring network interfaces
Ignoring unknown interface ath0=ath0

How can I restart just ath0? If rebooting fixes the problem, I would think there's a command I can issue that would do the same.

---

### Post by ddrichardson on 2009-03-02
This is very common and can be resolved by editing:
```
/etc/default/acpi-support
```Add a line that reads:
```
STOP_SERVICES=&#8220;networking&#8221;
```

If this doesn't work, type
```
dmesg
```
Look for messages about being unable to reset ath0 and error 11, if it's there let me know.

---

