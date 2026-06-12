---
title: "Is resolv.conf where to set dns?"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by vayu on 2005-12-31
My /etc/resolv.conf has my dns settings (which I want to change) but there is a comment line at the top which says do not manually change these entries.  Where do I set the dns entries?  Also where do I set the IP address (I'm not using DHCP)?

I know how to do it with the GUI in System/Administration/Networking but I want to know which files these settings go in.

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=vayu]My /etc/resolv.conf has my dns settings (which I want to change) but there is a comment line at the top which says do not manually change these entries.  Where do I set the dns entries?  Also where do I set the IP address (I'm not using DHCP)?

I know how to do it with the GUI in System/Administration/Networking but I want to know which files these settings go in.[/QUOTE]
/etc/resolv.conf is for DNS, as you suspected.
Your static IP address goes in /etc/network/interfaces.

---

### Post by mips on 2005-12-31
System->Administration->Networking is the place to go if you want to change settings via a GUI.

You can also manually edit the files involved even though you have a msg saying not to do so.

---

