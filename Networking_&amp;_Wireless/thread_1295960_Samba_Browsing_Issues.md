---
title: "Samba Browsing Issues"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by gareththered on 2009-10-20
I've three servers and one client currently on my home network as follows:-
SERVER - Router to the internet with DNS, DHCP, Shorewall and a few other system services.
OFFICE - File and print server.
MEDIA - Music, videos etc.
LAPTOP - (I'll let you guess....)

SERVER and OFFICE are running Ubuntu Server 9.04.  MEDIA is running Mythbuntu 9.04 and LATOP is Ubuntu Desktop 9.10 (Karmic) with Kubuntu-Desktop added and Ubuntu-Desktop removed.  So, they are all pretty similar.   All are configured to be in a workgroup called 'HOME'.

SERVER, OFFICE and MEDIA are running Samba.  For some strange reason, when I browse the Samba network from LAPTOP all  I can see is SERVER and any Windows 'guest' clients that are connected to the network.

If I use 'nmblookup -M HOME' on LAPTOP I get the IP address of SERVER as the Domain Master Browser.
If I use the same command on SERVER, I also get SERVER's IP address.

However, if I carry out the command on OFFICE and MEDIA I get MEDIA's IP address!   That explains why I can only see SERVER when I browse workgroups in LAPTOP.

The question is WHY!??
I've created a generic smb.conf file and copied it to all computers for testing purposes but it still shows the same results as above for the 'nmblookup' command.

Originally, the generic conf file had both local_master and domain_master set to auto so that the server would work out who the masters is by election.  This didn't work, so I made SERVER the domain_master.   This didn't help.  I've also tried configuring SERVER as a WINS server,  but no luck there neither!!

Does anyone have any idea?

Thanks in advance.

---

### Post by gareththered on 2009-10-28
The problem was due to the fact that different servers had different subnet masks! Ooops!

---

