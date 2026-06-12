---
title: "Gitso, DynDNS, DynamicDNS and port forwarding"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by B34N on 2009-07-02
I would like to use Gitso (or any other remote desktop solution) to be able to be able to remotely support my 70-year old father-in-law over the Internet.

Most of the time I'll be doing the support from my home.  I have dynamic IPs through Verizon DSL service using a Westel Versalink 327W.

I successfully installed Gitso and connected to the father-in-law's laptop over the local network.  

I believe that I successfully setup a hostname using DynDNS. I can ping that hostname and I see that my public IP address is assigned to that hostname.  How can I determine if the 327W supports DynamicDNS?

I am unable to connect to connect with Gitso using the DynDNS hostname.  I look at my 327W firewall settings and it is set for "No Security - All traffic allowed" (I believe that is the way it came from Verizon.  Isn't that unsafe?)  If I don't have a firewall setup, do I still need to setup port forwarding?  To setup port forwarding, what settings should I use for "Protocol" (TCP?) "Global PortStart" (5500?) "Global PortEnd" (5500?) "Base HostPort" (5500?)?

Am I missing anything else?

Thank you!

---

### Post by computer13137 on 2009-07-02
This page may be of assistance to you: 
[http://portforward.com/english/routers/port_forwarding/Westell/Versalink-327W/default.htm](http://portforward.com/english/routers/port_forwarding/Westell/Versalink-327W/default.htm)

-Kirk

---

### Post by superprash2003 on 2009-07-03
you just need 5500 i think ( im not sure if 5900 is required ) .. use this online port scanner to see if this port is open , thats the basic requirement first [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by B34N on 2009-07-03
Thank you for the replies.  I think that I'm making progress but I'm still not quite there.  I'm pretty sure that I'm overlooking something very simple.

I'll put aside the DynDNS and DynamicDNS for the moment so that I can focus on getting Gitso or VNC up and running using the public IP address.

I have two machines currently on the same LAN.  I can use Gitso and VNC with either computer as the host if I use the local hostnames.  The problem comes up when I  try to connect to my "office-desktop" (its local hostname) machine using the public IP address or the public hostname.

When I check the "Remote Desktop Preferences" of the machine that I want to be able to give the support from, it states that "Others can access your computer using the address XXX.XXX.XXX.XXX" (where the Xs are my public IP address).  Wouldn't this mean that I likely have the port forwarding properly setup because before I did the port forwarding it said that the machine could only be access from the local lan?  The error that I get with VNC using the public IP address of the machine that I eventually want to give support from is "Connection to host XXXX.XXX.XXX.XXX:5900 was closed"

I've attached some screen captures of the port forwarding settings I setup on my router.  I forwarded ports 5500, 5800 and 5900 because my understanding is that I need all three for VNC and just 5500 for gitso.

I tried the [http://www.t1shopper.com/tools/scan.php4](http://www.t1shopper.com/tools/scan.php4) for port scanning and I get a response on 5500 only when gitso is running, I never get a response on 5800 and I always get a response on 5900.

The full model number of my router/dsl modem is B90-327W15-06.  It's made by Westel exclusively for Verizon and only supported by Verizon.  Verizon's support site give no responses when I search for "port forwarding".

Thank you in advance for your help!

---

### Post by dmizer on 2009-07-03
If both machines are on the same lan, you will not be able to use the public IP to gain access as most retail routers are not able to loop back.

---

### Post by B34N on 2009-07-03
> **dmizer said:**
> If both machines are on the same lan, you will not be able to use the public IP to gain access as most retail routers are not able to loop back.

That is exactly what my best guess as to what I'm doing wrong was.  It will be a challenge to try to get this computer on another lan (other than tethering with my BlackBerry) and be able to test it with both machines in my presence.  Is there anything else I can do to verify that I'm doing everything else correctly?

Thank you!

---

### Post by dmizer on 2009-07-03
I don't know anything about gitso, but if you can configure it to work through a proxy, you could test your external IP that way.

---

### Post by superprash2003 on 2009-07-04
do you have firestarter , gufw or anything similar running?

---

### Post by B34N on 2009-07-04
> **superprash2003 said:**
> do you have firestarter , gufw or anything similar running?

 Not that I'm aware of.

---

### Post by superprash2003 on 2009-07-06
post output of **sudo iptables -L**

---

### Post by B34N on 2009-07-06
> **superprash2003 said:**
> post output of **sudo iptables -L**

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by superprash2003 on 2009-07-07
well it should work ,you just need port 5500 open and you dont need to setup system->pref->remote desktop.. alll you need to do is , turn on gitso on your pc and select Give support .. and go to your relative's machine and turn on gitso there and tell him to select Get help and tell him to enter the dyndns hostname or the ip address you get when you go to [www.whatismyip.com](www.whatismyip.com) ( on your machine ) . Once that is entered , it ideally should work!!

---

### Post by Diviati on 2010-08-07
I have port 5500 on my router forwarded via NAT to my computer (192.168.1.2).
I have used [http://www.dyndns.com/](http://www.dyndns.com/) to allocate a name to my ever changing IP address.

On my website I have a page with my allocated domain name. (myhome.dyndns.com)
I also have links to the Debian, Windows and Mac versions of the programs from
[http://code.google.com/p/gitso/downloads/list](http://code.google.com/p/gitso/downloads/list) so they can download and install the program.

Saves a lot of trouble.

---

