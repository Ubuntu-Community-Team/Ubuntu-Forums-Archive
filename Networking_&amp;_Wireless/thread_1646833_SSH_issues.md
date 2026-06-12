---
title: "SSH issues"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by ewehrer on 2010-12-16
Okay guys, I have searched for days for an answer to this, but I cant find it. Here is my problem:

When I try to connect to my router through an external IP over ssh, I get "Connection timed out" when I do it from anywhere other than the same network. When I try and connect using my exernal IP from the same network, I get "connection refused." Here is my basic network setup:

Zoneedit.com DynDNS ---> Cable modem ---> apple airport ---> DD-WRT router in client mode 

It has worked for me for years, and only stopped working just recently. I can't connect using my actual IP, or my domain name.

I connect to ssh through port 23, if that helps at all, although that has worked for me for years.

---

### Post by Joeb454 on 2010-12-16
Have you enabled port forwarding through the Airport [Extreme|Express]? That could be why you can't connect externally

---

### Post by ewehrer on 2010-12-16
Yes, and like I said, this problem just came up recently. And its the extreme, wireless N version.

---

### Post by theluddite on 2010-12-16
I'd try portscanning the remote host.

Install nmap using "sudo apt-get install nmap"

Then I'd try sudo "nmap -p 23 -sV -sU -sT your.external.ip.address"

If the service is visible to the port scanner using the external IP address, it must be a problem with your ssh config file or the command you're using to connect.  If it's not, it must be a router problem (i.e. port forwarding improperly configured).

---

### Post by ewehrer on 2010-12-16
This is what I got: 


Nmap scan report for localhost.localdomain (127.0.0.1)
Host is up (0.00013s latency).
PORT   STATE  SERVICE VERSION
23/tcp closed telnet
23/udp closed telnet

Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.33 seconds

And this is what I use to connect: SSH -p 23 -D 6500 [email]root@mydomain.us[/email] (fails with my actual IP as well)

This is what I get when I scan my external IP (From school)


Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-12-16 12:01 CST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.13 seconds

EDIT: 
The school also doesn't block SSH. I have a friend that can connect to his server from school.

---

### Post by theluddite on 2010-12-16
Nmap isn't seeing the ssh server even on your localhost.  You said you have no issues connecting with "ssh -p 23 user@127.0.0.1"?

---

### Post by ewehrer on 2010-12-16
The SSH server is the DD-Wrt router at my house, not the computer I'm on now.

---

### Post by theluddite on 2010-12-16
Ok.  Just to clarify, in your original post, you had said that you were able to connect via ssh within your own network.  I had originally posted that you should run an nmap scan on the local host first (127.0.0.1) to confirm this.  Unless I misunderstood, you're running the nmap scan of ip 127.0.0.1 on a different computer than the one that's running ssh.  Obviously, the scan won't show a result.  When you get home, run this command **on the computer running the ssh server:**  "nmap -sV -p 23 -sT -sU 127.0.0.1".  That'll show you if the port that ssh is supposed to be running on is actually open.  Alternatively, if you're able to connect using the command "ssh -p 23 user@127.0.0.1" you know that ssh is running correctly on your LAN.

If this works at home, and the scan of the remote host doesn't:  "nmap -p 23 -sT -sU -sV your.remote.ip.address" then it's likely a problem with your router settings.  Does that make sense?

---

### Post by ewehrer on 2010-12-16
Well I can connect with the router's local IP from inside the network (10.0.1.19) but if I try the IP the world sees from inside the same network I could use to connect with the local IP, I get "connection refused" Now If I connect to someone elses internet, the connection just times out and nothing happens.

---

### Post by ewehrer on 2010-12-16
If It helps at all, I may have accidentally set my other DD-WRT router to connect to the airport with the same IP adress, so for a few minutes they were both 10.0.1.1

---

### Post by theluddite on 2010-12-16
It must be a router problem.  The nmap scan you ran indicates your host isn't even visible externally.  Have you tried simply pinging your external ip?  "ping your.external.ip.address" (press ctrl+C to stop).  You can try scanning all of your ports to see if any services are visible:  "nmap -sT -sU -sV your.external.ip.address"  Given what you've already posted, it's likely that you'll get no result which means the problem isn't with ssh.  I'd power cycle your router and check the port forwarding settings.

---

### Post by ewehrer on 2010-12-17
Okay, I reset the airport and I still have the problem. I know the ports are forwarded unless all of the settings changed for some reason. I don't have enough memory on the router to install nmap to it though.

---

