---
title: "Cannot connect Ubuntu to Windows/Mac peer network"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by smikesmith on 2010-05-28
I have installed Ubuntu 10.04 on two different machines.  I have a private network of several machines, including OS X 10.4.11 with Samba 3.0.x, Windows XP, Win NT4, and now Ubuntu.  The machines that run Ubuntu are dual-boot machines that otherwise run WinXP.  The network has worked for several years with the WinXP/Mac10.4 combination, and I'm reasonably net-savvy.

I've added numerous features to my system, including public-key SSH, FTPES, so forth, and all works well among machines.  The one item I can't seem to crack is the SMB-Windows file sharing in Ubuntu 10.

On both U10 machines, I have spend a lot of time setting up the network and shares.  In both cases, the shares are visible and accessible from the WinXP and OS X machines.  However, the U10 machines cannot connect to either the Mac/Samba nor a Win XP machine, although they can see the shares.  The U10 machine also cannot connect to each other, neither through the Unix File System nor the Samba SMB system.  Shared printers are accessible everywhere.

While I'm not a network expert, I do know a bit about it, and have used WireShark on another machine to "snoop" the network packets when the problem occurs.  When I request a connection, for instance, to an XP machine, I see the U10 machine(s) launch a flurry of NBNS packets requesting the identity of the NetBIOS machine.  There will be several in rapid succession using various source ports to port 137 on subnet mask x.x.x.255.  No one responds.  The request looks slightly different from the usual packets for successful requests by the other machines, but here I'm not knowledgeable enough of the details.  The successful packets between XP and OS X machines are directed toward "Name query NB **hostname**<20>", while the failed requests are toward "Name query NB **hostname**<1d>".

A brief, partial example is here:

***
failed scenario, U10 to WinXP:
7    19.968038    192.168.1.101    192.168.1.255    NBNS    Name query NB SMS_DELL_510<1d>
***
10    20.172846    192.168.1.101    192.168.1.255    NBNS    Name query NB SMS_DELL_510<1b>
***
successful scenario, WinXP to WinXP:
246    342.427376    192.168.1.102    192.168.1.255    NBNS    Name query NB SMS<00>
247    342.427509    192.168.1.106    192.168.1.102    NBNS    Name query response NB 192.168.1.106
248    342.428599    192.168.1.102    192.168.1.255    NBNS    Name query NB SMS<20>
249    342.428622    192.168.1.106    192.168.1.102    NBNS    Name query response NB 192.168.1.106
***
The successful WinXP to Mac/Samba look similar.

I have a lot of detail on this problem, and would gather more, which I will not post here due to length, but would gladly share with anyone who might help me diagnose the problem.

Thanks,
Mike S.

---

