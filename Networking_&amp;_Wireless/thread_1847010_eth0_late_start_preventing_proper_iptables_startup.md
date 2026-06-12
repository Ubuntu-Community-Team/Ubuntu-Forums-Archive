---
title: "eth0 late start preventing proper iptables startup"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2011-09-20
Hello,
I have a server that has 2 motherboard ethernet ports (eth1 and eth2 in this case) and 1 StarTech PEX1000MMSC fiber optic card (eth0). From time to time when I restart it, I can't log back in. All connections are blocked. Restoring the routing table from the keyboard fixes it. So I decided to start digging in the logs and when the iptables appear to not get loaded (/etc/network/if-pre-up.d/iptables script) is when

[   13.356089] r8169 0000:0d:00.0: eth0: link up
[   13.356997] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Is missing from the dmesg. Since all but once restoring the routing tables from the keyboard fixed the problem, then I presume that eth0 eventually comes up but after iptables-restore is called. I'm also presuming that if eth0 is not up when the restore is attempted that is simply leaves things locked down.

Once, only a reboot would fix the problem. This is a more serious problem obviously.

So what can I do? Would putting a script in if.up.d help? Or something like post-up /sbin/iptables-restore < /etc/iptables.up.rules in /etc/network/interfaces.

The other thought is some kind of crontab script that checks the state of iptables and restores the tables and after so many tries reboots (for when eth0 never comes up). Anyone have a script like that I could work from?

Thanks for your ideas /suggestions!

Deron

---

