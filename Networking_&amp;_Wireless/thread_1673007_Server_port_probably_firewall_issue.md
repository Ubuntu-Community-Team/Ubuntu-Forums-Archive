---
title: "Server port probably firewall issue"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by MikeyDL on 2011-01-21
Been trying to setup to do remote connection for MySQL admin but I can't seem to access port 3306 on my ubuntu 10.04 server.  I've read that ubuntu comes with a firewall but it's off by default.  I take it, however that for a server distro it's on by default.  I'm not really knowledgeable yet at reviewing port and firewall settings, but was reading that while you can't ping a specific port you can telnet into that port to test if it's open or not.  

So I"ve been able to telnet into port 80, 22 ect. but I get a connection refused when I try to telnet into port 3306 (to test if open).  I did an:

```
sudo ufw allow 3306
```

to setup an access rule but that didn't seem to work.  I've also done a:

```
sudo ufw disable
```

to try and turn off the firewall but no luck yet.  Does anyone have ideas or can point me to the right place to work this type of issue.

---

### Post by gordintoronto on 2011-01-21
Where are you connecting from? If it's not from a computer on the same LAN, you need to set up port forwarding on your router.

---

### Post by MikeyDL on 2011-01-21
I"m connecting from a working laptop to the server.  Both the laptop and server are on the same subnet (192.168.1... internal addressing)  There is a firewall for external LAN access but I"m trying to connect via interal IP's.  I've also have a 3306 access rule setup for all incoming outgoing connections on the firewall just in case.  

I can ping and telnet to other ports on the server (port 80, 22) but not the 3306 one for some reason.

ADD:  I actually have two clean test ubuntu servers (just built).  Tested out the same process with the second one, and did a ```
sudo ufw allow 3306
``` but having the same problems.  Must be missing some key point.

---

### Post by MikeyDL on 2011-01-22
Actually still working on this.  After further research I finally edited the .cfg file and figured out that I needed to bind to something other then localhost in order to get mysql to respond.  After adding a bind-address line for my internal ip I was able to get a different error message when trying to connect with my db admin tool.  I'm looking into that right now.

With regards to using telnet to probe open port, maybe I was wrong on that assumption.  Tried connecting with other random ports and was getting connection refused messages.  It did seem to give me a connection with telnet for ports 80 and 22.  Are there any good tools for probing to see if a port is open behind a firewall?

---

### Post by ripat on 2011-01-22
Simply nmap.
```
$ nmap ip_server
```
Be patient as nmap will scan all ports. You can shorten the scan by specifying the port:
```
$ nmap -p 3306 ip_server
```

---

### Post by GeekUnder on 2011-01-23
Try this online test [http://mysql.icannotconnect.com](http://mysql.icannotconnect.com) to check if you can access the mysql port on an external server. If it is blocked, then at least you know that the problem is at the client side (ie. laptop or firewall in between is blocking outgoing connections to that port and not a server side firewalling issue.)

---

### Post by MikeyDL on 2011-01-23
Thanks for the suggestions those will both come in handy.

---

