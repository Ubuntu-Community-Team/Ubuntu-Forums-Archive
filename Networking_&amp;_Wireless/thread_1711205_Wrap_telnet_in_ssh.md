---
title: "Wrap telnet in ssh"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by blackmath on 2011-03-21
If I have an application running on a server that I can telnet into, but I want to make it available only via ssh. Is it possible to configure an ssh tunnel on the server that would effectively convert the application's telnet interface into ssh ? I.e. all clients would ssh into the server, and everything they send would be forwarded onto the application's telnet interface on that server.

---

### Post by zwelch on 2012-03-15
/bump on this.
 
My situation is very similiar. We have an IBM universe application that only work via telnet. But telnet is horribly unsecure and we need this application available external to our network. We have an SSL VPN appliance solution but it takes about 10 steps to get in and up, and it tends to disconnect the session because of the bad stability of telnet.
 
I'd like to set up a "proxy" server where people outside our network can establish an SSH tunnel connection to it, then have telnet forwarded through that box to the universe server.
 
Ideally I would like to use putty on windows clients to connect the userland VT220 emulator throught he tunnel. (or something as simple).
 
Any ideas on where to begin with this?

---

### Post by Derek Karpinski on 2012-03-15
Set up an ssh server on the local network that can telnet to the server.
 
Then ssh into that box from the outside network. Once connected to that ssh server, telnet into the telnet only server.
 
**[SIZE=2]SSH client[/SIZE]**---(SSH over internet)--->**SSH box**----(telnet over LAN)---->**Telnet Server**
 
In this way, your insecure telnet communication only takes place in the safe confines of your LAN, and you SSH over the scary internet. :D

---

### Post by zwelch on 2012-03-19
Thanks for the reply, but I'm looking for a slightly more elegant solution. I have an Ubuntu SSH box accessible through the firewall. Becase the telnet application we have requires VT220 emulation for all the function keys and export features built in using just staight telnet CLI is unfavorable.
 
I'd like to use putty to create an SSH tunnel to my Ubuntu box, tunneling the windows based VT220 Emulator through. When the attempt to connect to telnet on port 23 comes through the tunnel I want my Ubuntu box to forward that traffic through to the AIX box and back through the tunnel.
 
Something like this:
 
[Random PC] Putty, VT220 Emulator 
<=Internet=> 
[Ubuntu SSH] SSH Tunnel, forwarding port 23
<=LAN=> 
[AIX] Telnet App
  
But I'm not exactly sure how to make this work. I know putty will need to be setup with a tunnel that I believe just forwards port 23 to port 23 on the Ubuntu. Establish connection, then open the VT220 application and it should connect.
 
On the ubuntu side I just need to get all the port 23 traffic to redirect to the AIX server and back through the tunnel all on port 23, but inside the SSH tunnel.
 
This seems possible, but somehow difficult in the details of configuring. I'm looking now at Proxychains on Ubuntu, but it doesn't seem to be the obvious decision and more for utilizing proxies than becoming one.

---

### Post by Derek Karpinski on 2012-03-19
Okay.......along the same lines I was going for.......
 
Can you enable X11 forwarding in PuTTY......then ssh -X to your ubuntu box......then start 'xterm' on the ubuntu box, and run xterm in VT220 mode to do your telnetting?
 
You might have to install Xmimg, or another X server for windows.....or drop PuTTY, and run cygwin instead.  I think the latest version of cygwin comes with an X server by default.

---

