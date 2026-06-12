---
title: "Running SSH on Port 80"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by the pwner224 on 2012-10-31
I there any way to run SSH on port 80 without losing access to HTTP? I was planning to SSH into to home computer from school, but my ISP (clearwire) blocks every port except 53, 80, 9800, and 9801. I tried running SSH into those ports just to check if incoming connections were allowed. Port 53 dropped the connection  when i tried to connect to it but the others work.

Now I have a few options:
Use port 9800/01 for the SSH tunnel (unless those ports are actually used for something - google didnt give much info)
Use port 80 for SSH and HTTP at the same time
Use SSH to connect to port 80 on another computer that I dont use, which can forward it to my desktop's port 22 over the LAN
Or something else

What service would I lose by using port 9800 or 9801? and

How could I set up SSH and HTTP on port 80 at the same time?
or
How would I use the other computer to forward port 80 to port 22 on the desktop?
or
I read somewhere that if I buy a wireless card, the computer will have 2 IP addresses on the LAN (one for the wired connection, one for the wireless connection). Would I be able to set the router to forward HTTP connections on port 80 to the wired card and SSH connections on port 80 to the wireless card, and would the computer be able to correctly handle the 2 connections?

---

### Post by ahallubuntu on 2012-10-31
You can tell your SSH server to listen on port 22, and in your router/firewall (if it supports this feature), redirect 80 on your WAN IP to port 22 of your SSH server.  I am not sure if the router will be listening on 80 for anything.

Why not try a really high port like 15000?  Many firewalls only block the lower ports.

---

### Post by Lars Noodén on 2012-11-01
It is possible to multiplex SSH and HTTP/HTTPS according to sshttp: 

[http://blog.stalkr.net/2012/02/sshhttps-multiplexing-with-sshttp.html](http://blog.stalkr.net/2012/02/sshhttps-multiplexing-with-sshttp.html)

I haven't tried it but the design seems simple enough.  You really should get together with others and pressure them to open HTTPS (443) so that you are allowed at least secure web traffic.

---

### Post by Lars Noodén on 2012-11-01
If you have access to an external server, you could also get in via a reverse tunnel.  But if the tunnel goes down, you can't get back in.

---

### Post by the pwner224 on 2012-11-01
I can not forward port 80 on the router to port 22 on my computer, my router only supports forwarding the same port.
I used nmap on all ports, and it showed that the only unblocked ports are 53, 80, 9800, and 9801.
I tried Lars Nooden's solution, it did not work. Apparently they block incoming connections on port 80.

---

### Post by the pwner224 on 2012-11-01
They also block incoming connections on ports 9800 and 9801, and port 53 always closes the connection.

For some reason https works even though port 443 is blocked - I can connect to https websites.

---

### Post by Lars Noodén on 2012-11-01
If the connections are blocked the you have only two choices.  One is to negotiate an open port with them.  The other is to get an external machine with ssh and make a reverse tunnel.

It seems strange that additional ports cannot be opened on the router.

---

### Post by the pwner224 on 2012-11-01
I can not get an external machine with SSH.
I already tried to get port 22 open, they would not open it. They might open some other port and I could run the SSH server on that port.
If that doesn't work ill switch my ISP.

---

