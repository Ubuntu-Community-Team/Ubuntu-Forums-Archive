---
title: "SSH over VPN Tunnel"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by mail_e36 on 2010-04-30
Hello friends,

Let's assume I have established a** VPN tunnel using Vpnc from the an  Ubuntu 9.04 machine to a Cisco PIX** (a VPN endpoint/router/firewall).   Once I am on the VPN, my remote **Ubuntu box **is assigned an  internal IP address from the VPN pool.  Using this IP  address I have  full access to other machines on my LAN (ping, telnet,  ssh, etc.)  Everything seems normal.

The problem comes in when **I want to use another Linux machine (also ****Ubuntu)****  on my  internal LAN as my 'gateway' to the internet using "ssh -D" from  the  VPN'd host **(the remote Ubuntu machine, in this case).  I make  the "ssh -D" connection  from my VPN'd in remote Ubuntu machine to the  LAN linux machine, but any attempts to  browse the web from the remote  Ubuntu machine fail (I have set up the remote machine's Firefox  browser  to listen using SOCKS on localhost (127.0.0.1) on a specific  port).   (I have even tried the  "Links" text-only CLI browser, using the proper   SOCKS configuration with no luck, so I know it's not a browser issue). 

I have also tried this entire setup using the **Cisco native VPN client**   on a Windows XP machine with the **same results** (I can ping, ssh,   telnet, etc, but 'ssh -D' doesn't do anything), so I know the problem  is  not with the remote Ubuntu machine, per se.   

For background information, the "ssh -d" is supposed to specify a local   ''dynamic'' application-level port forwarding. This works by allocating  a  socket to listen to port on the local side, bound to a specified  bind  address. Whenever a connection is made to this port, the  connection is  forwarded over the secure channel, and the application  protocol is then  used to determine where to connect to from the remote  machine.  In  essence, I am trying to create a tunnel using SSH to my  linux box so I  can browse the web over the VPN.

Additionally, this entire **setup works perfectly when my remote Ubuntu  machine is  sitting locally on the LAN** (bypassing the VPN  altogether), so it  seems my "ssh -D" command is correct.  I am missing  one crucial piece,  but I am not sure what this piece is.    

Considering the caliber of IT knowledgeable individuals on this forum,**   I am hoping someone can share their ideas.   **

Thank you

---

