---
title: "Is there a way that I can see all devices on my local network and their local ip addr"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by josephellengar on 2010-05-16
Yeah- I'd like a way to see all of the devices on my local network and what their local IP address is.  I recall that I used wireshark to troubleshoot a similar problem a while back, but it doesn't seem to have a way to see all of the devices- only the traffic.  Any ideas?  Thank you.  
(I'd like to do this without having to physically interface with my router if possible, and I am in an encrypted network if that matters)

---

### Post by iponeverything on 2010-05-16
```

sudo apt-get install nmap
suso nmap -sP 10.0.0.1/24

```

Where 10.0.0.1/24 is your local network.

Do a "man nmap" for much more detailed options.

---

### Post by josephellengar on 2010-05-17
> **iponeverything said:**
> ```

sudo apt-get install nmap
suso nmap -sP 10.0.0.1/24

```

Where 10.0.0.1/24 is your local network.

Do a "man nmap" for much more detailed options.

I see, just read the nmap man.  So if I want to scan everything on my local network an nmap [options] 192.168.1.0/X (my local ip right now, for example is 192.168.1.5) that will scan the first X objects on the network?  But I also would to know what they are, connected to the network.  Would the option -O be best for that?  Or is there something that I missed that can also give you the name of the device?  That's what I'm really looking for.

And, unrelated, if I use the option -p 22, that would tell me everything that has the ssh port open, correct?  Sorry about all of the naggy questions.  I'm relatively new at this.

---

### Post by 8Kuula on 2010-05-17
> **rossholley said:**
> I see, just read the nmap man.  So if I want to scan everything on my local network an nmap [options] 192.168.1.0/X (my local ip right now, for example is 192.168.1.5) that will scan the first X objects on the network?
[http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)
As quick help, 192.168.1.0/24 means all IPs between 192.168.1.0 - 192.168.1.255. 192.168.0.0/16 == 192.168.0.0 - 192.168.255.255

> **rossholley said:**
> 
And, unrelated, if I use the option -p 22, that would tell me everything that has the ssh port open, correct?
Yes, you can give port range (-p 20-30) or individual ports (-p 22,80,443).

---

### Post by teh_drizzle on 2010-05-17
Hey there,

Why are you trying to find all the devices on the local network? The reason I ask is because there are a few options you may have. The first being the local network router. If you own the router you should be able to log in via the web (using the local default gateway). Typical home routers have a nice GUI displaying all the connected hosts (their NetBIOS, computer name in Windows, name and IP).

nmap is certainly a great option too! Using the -O switch, nmap will try to the best of it's ability to determine the Operating System of the host. (nmap explains a bit how it tries this, but it's not a certain approach.) 

If your end game is to be able to connect to your local hosts via their "computer name" then you might need to jump through a few more hoops. ([http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)) :)

---

### Post by josephellengar on 2010-05-17
> **teh_drizzle said:**
> Hey there,

Why are you trying to find all the devices on the local network? The reason I ask is because there are a few options you may have. The first being the local network router. If you own the router you should be able to log in via the web (using the local default gateway). Typical home routers have a nice GUI displaying all the connected hosts (their NetBIOS, computer name in Windows, name and IP).

nmap is certainly a great option too! Using the -O switch, nmap will try to the best of it's ability to determine the Operating System of the host. (nmap explains a bit how it tries this, but it's not a certain approach.) 

If your end game is to be able to connect to your local hosts via their "computer name" then you might need to jump through a few more hoops. ([http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)) :)

It's a little experiment that I'm running.  It'll sound incredibly stupid but anyway, I came into the possession a couple of itouches, and jailbroke them in different ways, leaving one with the default root/alpine ssh password.  I'm interested in tracking how quickly it gets hacked and if it gets infected with a virus relative to the jailbroken one with different passwords and the non-jailbroken one with a few other weaknesses that I put in it compared to the regular firewall.  Which is why I need device name if possible- because there are three machines with the same OS.  And my router regularly changes the local ip address, so when I use my packet sniffer I'd like to be able to know exactly which machine I'm looking at.  Yeah, stupid- but I'm a college student on break :)

---

### Post by iponeverything on 2010-05-18
Might want to try this, just the standard stealth scan with OS detection. 

This is the scan of my local network..

```

root@mac:~# nmap -O -sS 10.111.111.1/24

Starting Nmap 4.62 ( http://nmap.org ) at 2010-05-18 16:52 TJT
Interesting ports on 10.111.111.1:
Not shown: 1712 closed ports
PORT   STATE SERVICE
23/tcp open  telnet
53/tcp open  domain
80/tcp open  http
MAC Address: 00:23:69:xx:xx:xx (Unknown)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.11 - 2.6.20
Uptime: 0.049 days (since Tue May 18 15:41:22 2010)
Network Distance: 1 hop

Interesting ports on 10.111.111.11:
Not shown: 1708 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
3306/tcp open  mysql
5900/tcp open  vnc
6543/tcp open  mythtv
6544/tcp open  mythtv
MAC Address: 00:00:6C:xx:xx:xx (Private)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.21
Uptime: 1.321 days (since Mon May 17 09:10:30 2010)
Network Distance: 1 hop

Interesting ports on mac (10.111.111.100):
Not shown: 1714 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.23
Uptime: 0.047 days (since Tue May 18 15:44:55 2010)
Network Distance: 0 hops

Interesting ports on 10.111.111.102:
Not shown: 1714 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: 00:09:6B:xx:xx:xx (IBM)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.22 - 2.6.23
Uptime: 6.177 days (since Wed May 12 12:38:32 2010)
Network Distance: 1 hop

Interesting ports on 10.111.111.254:
Not shown: 1713 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: 00:00:39:xx:xx:xx (Toshiba)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.23
Uptime: 6.292 days (since Wed May 12 09:51:52 2010)
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at http://nmap.org/s
ubmit/ .
Nmap done: 256 IP addresses (5 hosts up) scanned in 20.274 seconds
```

---

