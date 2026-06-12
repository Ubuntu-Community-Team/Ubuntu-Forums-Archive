---
title: "SSH fails over WAN"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by ctsdownloads on 2009-06-18
Been fighting with this for days now. I have a working SSH setup that allows me to connect easily from one pc to another, using SSH. Great.

Now I have made sure that my FiOS Actiontec router is set to forward port 22 and this has been confirmed. Yet despite this, all attempts to connect outside of the LAN to the computer from ANY remote location, fail and time out.

Again, SSH is working and the router has the server PC with a static IP and the right port is opened.

CanYouSeeMe gives me a report of connection refused on port 22?! So short of wishing there was better secure remote PC solutions for Linux as clearly, something is wrong here as Ubuntu 8.04 and before, never gave me a WAN problem with SSH like this.

"Lot's of help" over [at DSLForums]("http://www.dslreports.com/forum/r22569789-northwest-SSH-port-forwarding-with-FiOS-Actiontec-Router~reverse=1"), as no one even bothers to respond, much less help me to understand why Verizon is based on what I am seeing, blocking the damned port.

I mean,[ according to this]("https://www.grc.com/x/portprobe=22"), port 22 is showing up as stealth which again, has me thinking it's blocked somewhere before it even gets to the router.

Port scan of my LAN address for the server using Ubuntu tools shows the box as port 22 open. And being I can connect over the LAN, this makes sense.

Again, using Ubuntu tools to scan my WAN address...show that 22 is NOT EVEN LISTED. Yet, port 23 telnet is. Is it me, or Verizon messing with me here and blocking ports???

---

### Post by ctsdownloads on 2009-06-18
Justed tested this again, this time using port 23 - works in LAN, gives a new error over WAN. Connection closed by remote host.

So is this my router or the ISP?

---

### Post by regal_dunce on 2009-06-18
I find it highly suspect that Verison would block port 22.  In any case, you could setup your ssh server to listen on a port that's definitely not blocked by verison, (like port 80 for example) and give it another shot.  That will tell you pretty conclusively.  

To me, this sounds like a router problem.  I'm not familiar with your router, but I know that the port-forwarding section on most routers has the ability to forward packets from WAN/LAN or both.  Maybe check if the source is open to the world, rather than just the WAN?

---

### Post by ctsdownloads on 2009-06-18
> **regal_dunce said:**
> I find it highly suspect that Verison would block port 22.  In any case, you could setup your ssh server to listen on a port that's definitely not blocked by verison, (like port 80 for example) and give it another shot.  That will tell you pretty conclusively.  

To me, this sounds like a router problem.  I'm not familiar with your router, but I know that the port-forwarding section on most routers has the ability to forward packets from WAN/LAN or both.  Maybe check if the source is open to the world, rather than just the WAN?

Thanks for the response. Yeah, I want to lean with it being the router....except the ports are open and every tool out there tells me that the port is indeed, blocked by one or the other.

Tested port 23, it does not time out and gives me the ever helpful connection refused message. Both /etc/hosts.deny and /etc/hosts.allow are correct, too. The data is not looking good for Verizon or their products thus far. But being as that I am coax into the Verizon router for FiOS, I cannot simply switch routers out. 

So I have to assume that because the ports are open in all tested circumstances, something ISP related is happening....

Did I mention that merely a month ago...this worked fine? Only thing that changed...well, nothing actually. So no new firmware changes to the router....this leaves the ISP then.

---

### Post by ctsdownloads on 2009-06-18
Let's try it this way.

ssh -p 23 user@WAN-IP -v

OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to WAN-IP-Address [WAN-IP-Address] port 23.
debug1: Connection established.
debug1: identity file /home/uzer/.ssh/identity type -1
debug1: identity file /home/uzer/.ssh/id_rsa type -1
debug1: identity file /home/uzer/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host


Now with more details, can someone point me in the right direction?

For testing purposes, I am just using the password for entry, as I deleted everything from the ~./ssh folder(s).


Also, when I am successfully connecting to the same box over the LAN, I get the same as above, but with this right before asking for a password.

debug1: Next authentication method: password

So, it stops before asking for a password when accessing via the WAN??

---

### Post by regal_dunce on 2009-06-18
If you do a 'dmesg' on the server after you get a connection refused message, does it give you any useful information? 

This error:
```

ssh_exchange_identification: Connection closed by remote host

```

is most definitely something to do with your server-side configuration.

---

### Post by ctsdownloads on 2009-06-18
> **regal_dunce said:**
> If you do a 'dmesg' on the server after you get a connection refused message, does it give you any useful information? 

This error:
```

ssh_exchange_identification: Connection closed by remote host

```

is most definitely something to do with your server-side configuration.

I would agree, if I could figure out why this is happening... :)

DMESG results (shortened for readability...most recent at the bottom):


[  288.940841] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:13:d4:7e:fc:12:00:18:01:7e:1a:00:08:00 SRC=192.168.1.1 DST=192.168.1.16 LEN=438 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=59085 LEN=418 
[  319.090710] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:13:d4:7e:fc:12:00:18:01:7e:1a:00:08:00 SRC=69.54.39.87 DST=192.168.1.16 LEN=58 TOS=0x00 PREC=0x00 TTL=55 ID=10235 DF PROTO=TCP SPT=443 DPT=58576 WINDOW=62 RES=0x00 ACK PSH URGP=0 

Also, I have attached my sshd_config in hopes of finding out how or why, this is mis-configured. I have looked and I don't see anything.

---

### Post by regal_dunce on 2009-06-18
Looks like your firewall is blocking the connection on port 23.  (those are the UFW BLOCK INPUT messages) You can disable it temporarily with 

```

sudo ufw disable

```

or you could change the port in 

```

/etc/ufw/application.d/OpenSSH

```

---

### Post by ctsdownloads on 2009-06-18
> **regal_dunce said:**
> Looks like your firewall is blocking the connection on port 23.  (those are the UFW BLOCK INPUT messages) You can disable it temporarily with 

```

sudo ufw disable

```

or you could change the port in 

```

/etc/ufw/application.d/OpenSSH

```


Good find, but no go. Did both, actually. Changed the port, disabled UFW.

Also, the results in dmesg appear to be old, too. So whatever that was...is not updating when I try to connect yet again, only to get
ssh_exchange_identification: Connection closed by remote host

I'd be thrilled to go back to port 22, but that would just mean timing about again. And of course, the fact that I can SSH in on any port from within the LAN....now you see why this is so frustrating. Logic is right out the window. :(

[LIST=1]
[*]Router Ports, opened.
[*]config, set right.
[*]LAN connects - fine.
[*]UFW errors appears to be old.
[*] WAN @ port 22 times out while port 23 gives me what you've seen.
[*] Tested on three different clients, all give the same result for the server.
[/LIST]

---

### Post by ctsdownloads on 2009-06-18
So, just recreated the same thing on two completely new installs - same thing. Then I disabled port forwarding on the router - same results. Am I correct in assuming that this is clearly a router issue then?

Before changing things over to port 23, I tried port 22 once again on the same machine and sure enough, time out city.

OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to WAN-IP-Address [WAN-IP-Address] port 23.
debug1: Connection established.
debug1: identity file /home/uzer/.ssh/identity type -1
debug1: identity file /home/uzer/.ssh/id_rsa type -1
debug1: identity file /home/uzer/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

---

### Post by ctsdownloads on 2009-06-18
The only other thing I can think of is that I am using OpenDNS.com for DNS, with its default settings. Surely, this has nothing to do with anything?

---

### Post by iBurger on 2009-06-19
Have the same error with my VM debian machine. 

- I think it has something todo with the known hosts file in the .ssh directory.

---

### Post by ctsdownloads on 2009-06-19
This just in, I am blind. As I suspected, it was the router. And sure enough...

TCP Any -> port number

I had

TCP port number -> port number

Fixed. Most routers account for this, the FiOS Actiontec router however, gives you the option of either. I chose wrong. :)

---

### Post by ctsdownloads on 2009-06-19
> **iBurger said:**
> Have the same error with my VM debian machine. 

- I think it has something todo with the known hosts file in the .ssh directory.

I would agree with this. Also, sometimes dmesg right after it fails on the server can give some detail as well.

---

