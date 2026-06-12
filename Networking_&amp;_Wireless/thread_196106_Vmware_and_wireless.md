---
title: "Vmware and wireless"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by buchalka on 2006-06-13
Hi,

I have dapper drake 6.06 running on my dell inspiron 9400 with wireless and that works fine.

Have installed VMWare and got that working using my wireless connection and NAT.  Problem is that whilst I can access the internet, etc from the windows xp install under VMWare, I cannot see the other Windows XP machine (not in VMWARE) on my network to attach to the printer connected to it.

I need to print from my VMWare windows xp install to this external printer.  I can print fine to it from within linux, just not from VMWare.  Within VmWare, I cannot connect to any machines on my network (e.g. can't see any machines or printers using a browse, and I get an error if I try and manually specify the computer name and printer share name).   Any tips or workarounds?

I tried setting up bridged mode for VMWARE without success, even using Firestarter, basically NAT and VMWare is the only way I can have connectivity to the internet.  I understand bridge mode does not work properly for wireless.

By the way with a wired connection this works fine, so it appears to be a wireless networking issue.

Any pointers would be appreciated.

Thanks

---

### Post by buchalka on 2006-06-15
[QUOTE=buchalka]Hi,

I have dapper drake 6.06 running on my dell inspiron 9400 with wireless and that works fine.

Have installed VMWare and got that working using my wireless connection and NAT.  Problem is that whilst I can access the internet, etc from the windows xp install under VMWare, I cannot see the other Windows XP machine (not in VMWARE) on my network to attach to the printer connected to it.

I need to print from my VMWare windows xp install to this external printer.  I can print fine to it from within linux, just not from VMWare.  Within VmWare, I cannot connect to any machines on my network (e.g. can't see any machines or printers using a browse, and I get an error if I try and manually specify the computer name and printer share name).   Any tips or workarounds?

I tried setting up bridged mode for VMWARE without success, even using Firestarter, basically NAT and VMWare is the only way I can have connectivity to the internet.  I understand bridge mode does not work properly for wireless.

By the way with a wired connection this works fine, so it appears to be a wireless networking issue.

Any pointers would be appreciated.

Thanks[/QUOTE]

I'm kicking myself because this was sooo simple to fix.  Put an entry in the windows xp's host file (c:\windows\system32\drivers\etc\hosts pointing to the win xp machine with the printer and you can then connect to the machine and install the printer, and all works fine!

Hope this helps someone.

Cheers

---

