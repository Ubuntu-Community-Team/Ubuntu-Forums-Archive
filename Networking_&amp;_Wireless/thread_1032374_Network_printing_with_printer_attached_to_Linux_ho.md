---
title: "Network printing with printer attached to Linux host"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by akelsall on 2009-01-06
I've read several posts, including the Samba HowTo guide and the info found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605), but I still have problems. Here's what I have:

A Linux host with a locally attached HP printer. I **AM** able to print from the Linux host to the printer.

An XP box.

I can ping from the Linux box to the XP box, and vice versa (they're both hardwired to a router).

Both Samba and winbinds are installed. I've tried stopping and starting both services any time I made changes. 

Currently, when I click on Places | Network, I see "Windows Network" in the Network-File Browser. When I click Windows Network, nothing is displayed (i.e. I don't see the XP box and the Location box in the File Browser shows smb:///).

When I go to the XP box and click "My Network Places", then click "View Workgroup Computers", I don't see my Linux box. 

Attached are my cups and samba config files. Can someone provide some guidance so I can get this going? I just want to be able to print from my XP box to the printer attached to the Linux host.

Thanks,

Andy

---

### Post by superprash2003 on 2009-01-06
when you add a printer in xp.. and select network printer.. enter the address as \\x.x.x.x\printername where x.x.x.x is the ip address of ubntu machine and printername is the name of the printer on the network.. also in your smb.conf set browseable = yes

---

### Post by akelsall on 2009-01-06
superprash2003, I tried that, but since the two computers can't even see each other, I can't add the printer. Any other ideas? I'll modify that file as well.

Thanks,

Andy

---

### Post by superprash2003 on 2009-01-07
> I can ping from the Linux box to the XP box, and vice versa (they're both hardwired to a router).
this is good enough!!

---

### Post by akelsall on 2009-01-09
Unfortunately, none of the suggestions helped, so I'm going back to CUPS to see if I can get that working (I don't really need Samaba, since I'm not going to be doing any file sharing).

Thanks for the help anyway,

Andy

---

### Post by dmizer on 2009-01-09
While I understand that CUPS and SAMBA are two different things, they are both an attempt to solve the same problem (sharing a printer). In this case the thread title is not specific to either samba or cups, and should suffice to carry you through your solution be it cups or samba.

Please post the output of:
```
iptables -L
```
Cups should work with very little fuss if there are no firewalls, and windows is configured properly.

---

### Post by akelsall on 2009-01-09
I'm looking for a SIMPEL solution for printer sharing. I have an HP printer attached to my Linux host (prints fine from there). I want my XP box to be able to use this printer as well. I can ping my XP box from my Linux box (and vice versa).

When I go into my XP box and try to add a printer, I click "A network printer or a printer attached to another computer", then "Connetc to a printer on the Internet or on a home office network" and enter my printer as follows:

[http://192.168.2.16:631/printers/myprintername](http://192.168.2.16:631/printers/myprintername)

[COLOR="Blue"]**Note: I'm using the printer name as show in CUPS.**[/COLOR] 

I also tried it without port 631. Either way, I get an error message saying "Windows cannot connect to the printer. Either the printer name was typed incorrectly or the specified printer has lost its connection to the server."

---

### Post by dmizer on 2009-01-09
Did you enable printer sharing? In the cups interface, click on "server" > "settings" and check "publish shared printers connected to this system".

Then, right click on your printer and check "shared".

Edit, I've also merged your threads. It's much easier for us to follow your problem if you don't create so many threads.

Edit2, well, I've just tried to follow the directions and can't get my PDF printer to publish either. I'll dig some more as I'm unsure what the problem is.

---

### Post by dmizer on 2009-01-09
Did you enable printer sharing? In the cups interface, click on "server" > "settings" and check "publish shared printers connected to this system".

Then, right click on your printer and check "shared".

---

### Post by akelsall on 2009-01-09
Dmizer, thanks for sticking with this (and combining the posts). I checked the settings and it was already set to Share in both spots. Attached is the output of iptables. This is probably going to end up being something basic that I'm overlooking, but we'll see. 

Thanks,

Andy

---

### Post by dmizer on 2009-01-10
Looks like your firewall is interferring with your printer share.

My experience with IPtables is limited, so I won't be of much help. But you'll need to add a rule to allow two way communication over port 631 (and perhaps more). Are you using firestarter, UFW, or is it a hand configured script?

---

### Post by akelsall on 2009-01-10
Dmizer, you were correct. It was my FW. I flushed my FW, then just added rules to allow all TCP and UDP traffic, as well as allow all traffic originating from my subnet out (just as a test). After doing that, I was able to add my printer. I restored my old iptables and moved the line that allowed my subnet (192.168.2.0/24) to the beginning of the OUTPUT section, and that seems to have been the problem.

Now, I have another issue. When I try to print from Notepad, the application crashes. I tried this from both my virtual XP (running in VirtualBox) and my wife's XP desktop and both do the same thing. Doing a search on the error message suggested that I reload the printer drivers. So, I'll do that later on today and post the results here.

*******************************************************************************************************
Update - This is happening from any application, from both a "real" XP desktop, and an XP running inside VirtualBox. If I trying printing from Notepad, Word, or from Explorer, the application completely locks up, I get the hourglass, and have to end up killing the app. Any ideas why this is happening?
*******************************************************************************************************
Thanks for you help!

Andy

---

### Post by dmizer on 2009-01-12
How long do you wait before killing the app? I have heard reports that it takes minutes to send a print job over Cups. This has not been my experience, but people have mentioned that.

Does the experience continue if you clear your IPtables?

---

