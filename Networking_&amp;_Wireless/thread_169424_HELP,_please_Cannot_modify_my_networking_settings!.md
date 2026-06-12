---
title: "HELP, please: Cannot modify my networking settings!"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by ptsapralis on 2006-05-02
Ubuntu Breezy Badger with GNOME Desktop on an IBM Thinkpad R40 laptop.

When I select System -> Administration -> Networking, the "Network settings" dialog is displayed on the desktop but an error messaging pops up immediately, stating "Could not run su", "Check that you have permissions to run this command". I get this error message even when I log in as root or when I directly execute the command "network-admin" within a terminal.

The result is that I cannot modify my network settings, so, I am tied to my ADSL connection at home and I cannot connect my system to the corporate data network at my workplace (I have temporarily bypassed the dead-lock by using a SuSE Linux Enterprise Server 9 virtual system within VMWARE Player, but this cannot be a permanent solution by any means).

What is happening here? Have I done something wrong? How can I unlock my network settings?

Any help would be greatly appreciated...

Thanks,

---

### Post by ptsapralis on 2006-05-03
I have not yet been able to find any solution to this problem (and I do not see anybody providing any help, which means that this is a rather rare situation - although I found out today that yet another colleague of mine is encountering exactly the same ill behavior on his laptop system). It seems like UBUNTU has yet some distance to travel until it reaches the level of reliability that other Linux distributions offer.

Anyway, I decided to bypass this dys-functional "network-admin" applet and proceed to configure the network settings directly into the relevant files. I understand that there are two files to modify, namely "/etc/network/interfaces" & "/etc/resolv.conf". I have tested my new configuration and it seems to work properly - however, I would like somebody to verify that I have the correct understanding or, otherwise, tell me what more needs to be done.

BTW, can I un-install and re-install this thing (or it will kill my network connection alltogether)?

Thanks,

---

### Post by mips on 2006-05-03
Until you find a solution you can always manually edit the /etc/network/interfaces file.

---

