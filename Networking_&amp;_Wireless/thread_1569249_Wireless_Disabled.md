---
title: "Wireless Disabled?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2010-09-06
So, about a month ago I installed Ubuntu 10.04 (WUBI) on my mother's Dell Inspiron 1721 with a Broadcom Corporation BCM4311 802.11b/g WLAN card. Everything installed great, wireless worked fine, and life was good.

Today, for no apparent reason, whenever she loads Ubuntu, it reports wireless is disabled. All the relevant info (lscpi, lshw, iwconfig, ifconfig, etc.) report networking is disabled. 

The following method gets wireless up-and-running, but it needs to be done *every time* she logs-in:
[list]
[*]Turn off wireless adapter via physical switch on side of notebook.
[*]Run "rfkill unblock all".
[*]Physically turn wireless back on and wait about 30 seconds.
[/list]

Now, all this came-up with *no changes to the system whatsoever*. How does this make sense?

Thanks, in-advance, folks!

EDIT:
Well, disabling the physical switch in the BIOS changes things a bit. *Now*, wireless is disabled until you log-in to Ubuntu and then flick the switch--yeah, that one, the one that's turned-off--either to off or on. *Apparently, it doesn't matter.*

What am I missing?

---

### Post by moore.bryan on 2010-09-07
Really? 55 views and no thoughts?

---

### Post by bkratz on 2010-09-07
You might want to post the output of

rfkill list

in both switch positions.

---

### Post by moore.bryan on 2010-09-07
Thanks, bkratz... when I head over, I'll do just that!

---

### Post by segamaya on 2010-09-22
i have the same problem, in my dell inspiron 1525

here is my rfkill list, i hope somebody helps.
----
switch on (without wireless)
----
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
----
switch off
----
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

----
switch on (after rfkill unblock all)
----
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

