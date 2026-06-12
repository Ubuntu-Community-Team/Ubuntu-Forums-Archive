---
title: "D-Link DGE-528T problem"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by sco01 on 2006-01-13
Hello,

I just bought the card mentioned above and did a fresh "server" install of Breezy but the card wasn't detected during install. Lspci listed the card, so I googled around and found out that the card should work with the r8169 module, so i modprobed it without errors. lshw lists the NIC with the module, but lspci still lists it as "1186:4300 (D-Link System Inc: Unknown Device 4300 rev 10)". I added eth0 to /etc/network/interfaces and did an ifup eth0, but the dhclient doesn't get an address. I also tried restarting networking but with no results. I searched the forum and found only one other post regarding problems with this NIC in Hoary but no answers.

Is there anybody who got this NIC working? Any thoughts of what could be the problem?

Regards,
Stefan

Update: This thread (regarding Debian) indicates that this might be a kernel/module problem: [http://www.linuxquestions.org/questions/showthread.php?p=1790981#post1790981](http://www.linuxquestions.org/questions/showthread.php?p=1790981#post1790981)

Update: This is from the 2.6.9-ac16 kernel "release notes": *	"Add D-Link DGE-528T to the r8169 PCI idents	(Francois Romieu)". Uname -r on my system gives, me: 2.6.12-9-386, so i assume that the kernel supports it.

---

