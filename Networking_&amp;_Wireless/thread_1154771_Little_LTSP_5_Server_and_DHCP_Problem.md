---
title: "Little LTSP 5 Server and DHCP Problem"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by rcmysoft on 2009-05-10
[FONT=Arial][SIZE=2]Helo,[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]i set up a Edubuntu 8.10 LtspServer version 5.1.29  and I have 10 Clients DellGX110 with 3c905c Card (Earlier running on  Windows).[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Nothig works. When i boot the Clients most only one  will boot up to the Login Screen. The Other get a Error "nbd0: Attempted send on  closed socket" then i have to reboot hard.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]The first switched on client mostly boots to the  login screen.[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]I asked in the ltsp irc channel they told me i have  to flash the register on the clients network cards. No idea how to do this,  smile.[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]The second error is, that when i use the DHCP  Server on the LTSP Server only the first client gets the DHCPs IP Lease the next  clients dont get anything from the dhcp. For this arror i use another dhcp  Server in the Network its the Mirror of the LTSP Server, and its works  erverytime 100%.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]On The server i tested two different network card  with the same error.[/SIZE][/FONT]
 I think its a network card problem, perhaps i have to flash the nvram of the clients cards. 

 [FONT=Arial][SIZE=2]So if you can help, please feel free to answer.  Thanks

[/SIZE][/FONT]

---

