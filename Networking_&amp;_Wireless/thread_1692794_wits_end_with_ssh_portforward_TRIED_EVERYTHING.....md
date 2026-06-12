---
title: "wits end with ssh portforward TRIED EVERYTHING....last resort is here..."
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-02-21
Omg with this portforwarding already for my ssh server....what I want to do is beable to ssh into my desktop at home start my VNC server and remote my desktop gui onto her computer....this has been not going so well lol; within my home network np i use my laptop to check downloads on my desktop all the time....my problem is.....i cannot get port 22 public?????

Using nmap 204.112.131.224

```
adam@desktop:~$ nmap 204.112.131.224

Starting Nmap 5.36TEST4 ( http://nmap.org ) at 2011-02-21 22:00 CST
Nmap scan report for slkrmb01dc1-131-224.dynamic.mts.net (204.112.131.224)
Host is up (0.035s latency).
Not shown: 996 filtered ports
PORT      STATE SERVICE
23/tcp    open  telnet
80/tcp    open  http
8080/tcp  open  http-proxy
52869/tcp open  unknown

```

When I scan my ip...(also seems like alot of ports are open....but I guess that's another topic)

I have a D-Link  DIR-655 my internal ip for my computer is 192.168.0.100 external ip is 204.112.131.224

[http://portforward.com/english/routers/port_forwarding/Dlink/DIR-655/SSH.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DIR-655/SSH.htm)

1. So i've used both ip's to forward that port and cannot get nmap or [http://canyouseeme.org/](http://canyouseeme.org/) to see 22? 

2. Also created a virtual server for both ip's (22 and 22 so it's basically a forward) and still nothing....

I cannot understand for the life of me what i'm doing wrong?

3. when i try to access my ssh in LAN i use:

ssh adam@192.168.0.100

over the net i use

ssh adam@204.112.131.224 <-- is this wrong? and why?

---

### Post by adduds on 2011-02-24
shameless bump

---

### Post by adduds on 2011-02-26
can anyone help??

---

### Post by spiky001 on 2011-02-26
Have yo set the firewall to allow incoming connections?

---

### Post by 3177 on 2011-02-26
you forgot the password.
>name@IP# password<

---

### Post by asmoore82 on 2011-02-26
You need to set up the router to forward port 22 from the 204 address
to port 22 of the 192 address of your actual computer.

Home routers call this different things: Port Forwarding, Virtual Servers, or Port Triggering.

Personally, I just use static NAT so that all unsolicited traffic is forwarded to my real
computer. Routers call this: Static NAT, NAT Passthrough, or DMZ (De-Militarized Zone).

A free dns record is nice too: [http://www.dyndns.com/](http://www.dyndns.com/)

Also, make sure you test this from the outside &#8212; some routers are buggy about forwarding
ports from the inside back inside. My current DLink is fine with it.

---

### Post by CharlesA on 2011-02-26
If the port forwarding is set up correctly, it's possible yer ISP is blocking port 22.

---

### Post by adduds on 2011-03-17
bah i finally got it! i forgot the dsl modem had a webUI...  i had to set my dsl modem to transparent bridge then change my d-link router PPPoE instead of dhcp...i guess this is kinda like handing the work over from the modem to router?

---

### Post by CharlesA on 2011-03-17
Glad you got it working. It shouldn't really matter which device does what as long as it's working as expected. :)

---

### Post by adduds on 2011-03-17
> **CharlesA said:**
> Glad you got it working. It shouldn't really matter which device does what as long as it's working as expected. :)

cheers to that

---

### Post by adduds on 2011-03-18
quick question i opened a public port to 666 to forward to private port 22 do i have to use

ssh ad@myip differently now cause i'm using 666 instead of the standard 22

my sshd_config is still set to listen on 22 on my intternal ip box right?

192.168.0.100 listens 22 on TCP

external ip open on 666 TCP

EDIT: 

ah i figured it out :P

ssh -p 666 ad@myip

---

