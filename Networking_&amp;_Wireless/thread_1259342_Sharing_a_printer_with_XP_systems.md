---
title: "Sharing a printer with XP systems"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by PlancksCnst on 2009-09-06
I'm running Jaunty, and have a printer setup (it prints successfully). I'd like to share it with a couple of XP computers.

First, I opened "Printing" from the administration menu, right-clicked on the printer, and checked "Shared". On the XP machine, I right-clicked on the printer I shared and chose "Connect..." I installed the driver that came with Windows. I tried to print a test page; it didn't print. I opened the print queue, and the title says "[printer name] on [server name] Access denied, unable to connect".

I found lots of people having similar problems, but no good solutions. I tried [http://www.jonathanmoeller.com/screed/?p=901](http://www.jonathanmoeller.com/screed/?p=901) since the comments at the end were promising, but it didn't work. I also tried [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP), which just says to make sure the printers are published, and the options "enabled", "accepting jobs", and "shared" are checked for the printer I'm sharing.

---

### Post by dbalascak on 2009-09-06
Did you configure permissions for CUPS?  This is a bit old but the permissions are accurate.
[http://ubuntuforums.org/showthread.php?p=1831119](http://ubuntuforums.org/showthread.php?p=1831119)

The other thing may be firewall.  If there are NO rules/restrictions you should see the following and this is not the problem.
```


$ sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by PlancksCnst on 2009-09-06
Most of those instructions were about setting up remote administration, which I don't need, but went ahead and setup anyway for you. The parts I didn't do are:
install drivers (already there), install cups and open-sshserver (already there), add printer (already there), the client stuff, and ```
adduser cupsys shadow
```. There isn't a cupsys user. It looks like that changed with 8.10, but I'm not sure.

I have no firewall rules.

---

### Post by yeats on 2009-09-06
Do you have Samba installed?  I seem to remember needing that for the Windows machines to see my printer...

(I currently use an external print server with an IP on the network)

---

### Post by PlancksCnst on 2009-09-06
Samba is installed. Otherwise, I wouldn't have been able to browse to the printer to open the print queue.

---

### Post by yeats on 2009-09-07
I see this, but if this is the problem, we're suddenly doing MS support :-):

[http://support.microsoft.com/kb/312055](http://support.microsoft.com/kb/312055)

---

