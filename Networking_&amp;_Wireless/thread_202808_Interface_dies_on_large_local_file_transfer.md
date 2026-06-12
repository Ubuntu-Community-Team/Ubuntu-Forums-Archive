---
title: "Interface dies on large local file transfer"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by dyssident on 2006-06-24
Im trying to transfer a 64MB file from a Dapper machine to another Dapper box via HTTP (apache2) on a wired local network. The transfer fails at 11MB and the interface on the recieving machine goes down. It comes back up automatically after 3 minutes, but it wont even fetch an address via DHCP. The only way to get it working again is to reboot.

The sending machine is unaffected; A WinXP machine plugged into the same switch copies it down fine.

Log files /var/log/syslog and /var/log/messages fill with the following output:

Jun 24 01:54:49 localhost kernel: [17180336.848000] NETDEV WATCHDOG: eth0: transmit timed out
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0: Transmit timeout, status 0c 0055 c07f media 10.
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0: Tx queue start entry 5189  dirty entry 5185.
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0:  Tx descriptor 0 is 0008a03c.
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0:  Tx descriptor 1 is 0008a03c. (queue head)
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0:  Tx descriptor 2 is 0008a03c.
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0:  Tx descriptor 3 is 0008a03c.
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 24 01:55:13 localhost kernel: [17180360.848000] NETDEV WATCHDOG: eth0: transmit timed out
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0: Tx queue start entry 4  dirty entry 0.
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0:  Tx descriptor 1 is 0008a03c.
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0:  Tx descriptor 2 is 0008a03c.
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0:  Tx descriptor 3 is 0008a03c.
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
<repeat every 12 seconds for 3 minutes; identical output in `dmesg`>

Jun 24 01:54:49 localhost kernel: [17180336.848000] NETDEV WATCHDOG: eth0: transmit timed out
Jun 24 01:54:49 localhost kernel: [17180336.848000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 24 01:55:13 localhost kernel: [17180360.848000] NETDEV WATCHDOG: eth0: transmit timed out
Jun 24 01:55:13 localhost kernel: [17180360.848000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
<repeat every 12 seconds for 3 minutes>

lspci says:
0000:04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

This one has got me truly puzzled. Any ideas? Many thanks in advance.

---

### Post by scxtt on 2006-06-24
why are you doing it via HTTP? (do you mean putting a link in an HTML file hosted on one of the ubuntu boxes?) ...

i'd use SSH or sFTP if you "own" the network & the boxes ...

---

### Post by dyssident on 2006-06-24
[QUOTE=scxtt]i'd use SSH or sFTP if you "own" the network & the boxes ...[/QUOTE]

If only it were so simple. Transfer via sftp dies in exactly the same way. So something is definiately wrong on a deeper level.

---

### Post by scxtt on 2006-06-24
what's up w/ those "NETDEV WATCHDOG" messages?

---

### Post by dyssident on 2006-06-24
[QUOTE=scxtt]what's up w/ those "NETDEV WATCHDOG" messages?[/QUOTE]

ive never seen them before. i did some googling and all i found was a bunch of forum posts with people saying "i have this problem" and "ive got this too" but basically nothing helpful. the only common element seems to be the 8139 ethernet driver and people fingering ACPI for one reason or another, although i have no idea why. im going to reboot with 'noacpi' just to see what happens.

---

### Post by dyssident on 2006-06-24
well i disabled acpi and eth0 wouldnt even come up. so at the very least there is some kind of connection between networking and acpi that i hadnt expected. 

now that i think about it, if you kill gnome networkmanager, the gnome power manager will occasionally crash. maybe the people blaming it on acpi have a point.

---

### Post by scxtt on 2006-06-24
maybe getting a cheap 10/100 card and popping it in would solve the problem? -- i have onboard LAN (and i'm not getting that message, seems to be a realtek issue?) otherwise i'd try putting in the old linksys card i have ...

---

### Post by dyssident on 2006-06-26
another good suggestion, but im doing this on a laptop. it is no doubt a realtek driver issue: ive found references to this problem going back to at least 2003.

in any event, ive gotten it working by dumping the default kernel driver (8139) in favor of ndiswrapper and the current WinXP driver. works like a charm now.

im about to throw up a howto and as soon as that is done ill link to it from this thread.

---

