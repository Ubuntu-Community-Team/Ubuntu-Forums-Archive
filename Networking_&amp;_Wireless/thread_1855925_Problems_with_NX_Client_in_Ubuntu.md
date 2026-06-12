---
title: "Problems with NX Client in Ubuntu"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by carystoms on 2011-10-07
hi,

I'm having problems using NX Client in Ubuntu, and I'm hoping someone can help!

We've set up a Ubuntu machine with NX Server, and if I am connected via  the LAN I can connect to this properly from my laptop running Ubuntu.  The problem comes in when I try to connect from home - I'm first  connecting to a VPN, then using NX client to connect to the server. This  works perfectly from my Windows machine, but when I try the same thing  in Ubuntu, it doesn't work. It goes through the process of connecting,  starts a new session, and then gets stuck on 'Established the display  connection'. This eventually terminates with an error message 'Session x  failed'. When I click on Detail I get the following log: 

NXPROXY - Version 3.5.0 

Copyright (C) 2001, 2011 NoMachine. 
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information. 

Info: Proxy running in client mode with pid '3327'. 
Session: Starting session at 'Fri Oct  7 11:27:09 2011'. 
Info: Connection with remote proxy completed. 
Info: Using ADSL link parameters 512/24/1/0. 
Info: Using cache parameters 4/4096KB/16384KB/16384KB. 
Info: Using pack method 'adaptive-7' with session 'gnome'. 
Info: Using product 'LFE/None/LFEN/None'. 
Info: Using ZLIB data compression 1/1/32. 
Info: Using ZLIB stream compression 4/4. 
Info: Using cache file  '/home/carys/.nx/cache-gnome/S-9BB465D195E2E3CF6C93D25D87F177BA'. 
Info: Forwarding X11 connections to display ':0'. 
Info: Listening to font server connections on port '11016'. 
Session: Session started at 'Fri Oct  7 11:27:10 2011'. 
Info: Established X server connection. 
Info: Using shared memory parameters 1/4096K. 
Session: Terminating session at 'Fri Oct  7 11:28:10 2011'. 

I'm a bit stuck and Googling has been unsuccessful - any help would be  much appreciated! (Sorry if I haven't provided enough info, I'm fairly  new to all this!) 

Carys [FONT=-moz-fixed]
[/FONT]

---

### Post by tarjxvf on 2012-02-03
I have the same problem. nxclient 3.5 works on Win7, but not in Ubuntu 11.10. Here is the log file:

NXPROXY - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '5138'.
Session: Starting session at 'Fri Feb  3 11:14:25 2012'.
Warning: Connected to remote version 3.4.0 with local version 3.5.0.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method 'adaptive-7' with session 'gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '12046'.
Session: Session started at 'Fri Feb  3 11:14:25 2012'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Fri Feb  3 11:15:25 2012'.

---

