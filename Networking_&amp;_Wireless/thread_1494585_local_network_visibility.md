---
title: "local network visibility"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by pwaugh on 2010-05-27
I have install Ubuntu server on 192.168.1.20 with a fixed IP which is provided by my cable modem.  The hostname is "server" and it is on an ethernet to my wifi router.

My laptop also has a fixed IP, 192.168.1.10, and hostname "laptop"  (original I know), but connects to the wifi router via wifi.

Both systems have internet connectivity and I can ssh to the server from the laptop, but must do so by IP.  I am unable to refer to it with the ".local" like I am the laptop (ie laptop.local).

Why is this?  I would really like to ssh to the server by saying ssh server.local, vs. using the IP, and doing so without having to do so with brute force of editing hosts, or runnigg DNS.

Basically, I want to understand why the .local thing only works for the laptop.  I have a basic understanding of DNS, and routing etc, but have been out of the game awhile.

If you can point me in the right direction would be appreciated.

Patrick

---

### Post by iponeverything on 2010-05-27
unless you are running your own nameserver, you will have ip to name translations an /etc/hosts file on all the machines.

---

### Post by pwaugh on 2010-05-27
> **iponeverything said:**
> unless you are running your own nameserver, you will have ip to name translations an /etc/hosts file on all the machines.

I would have thought that too, but strangely, the laptop is recognized as laptop.local, while the server is not.

hostname -A on the laptop gives laptop.local, while on the server (with ubuntu server) gives nothing (ie null).

For the life of me, i can't figure out why.

Yes, I can put it in the host file, but I'm trying to understand why .local is recognized for the laptop and not the server.

patrick

---

### Post by Iowan on 2010-05-27
> **pwaugh said:**
> 
Yes, I can put it in the host file, but I'm trying to understand why .local is recognized for the laptop and not the server. **avahi** is likely the culprit - I doubt the server has it - whereas the laptop probably does. Probably because I don't really understand it, but **avahi** usually causes me more problems than it solves. It's supposed to be a sort of ZeroConf networking.

---

### Post by pwaugh on 2010-05-27
Yes, I have indeed solved the problem / figured it all out.

Basically, Avahi is a zeroconf mDNS resolver and it wasn't running on the server.

As I currently understand it, there are then 2 solutions to get this to work the way I wanted (beyond the simple direct edit of /etc/hosts).

1) patrick@server$ sudo apt-get install avahi-daemon

at which point the Avahi daemon will be installed and running on the server and things will now work, OR

2) On the laptop edit the Avahi hosts config file (similar to /etc/hosts) to specify the server host.

Option two then allows me to do my ssh from the laptop, without editing the /etc/hosts file, but does not allow a shell on the server to see the laptop (which might be just fine).  But, since the point of this exercise was to not have to "hard code" a hosts file, if I was going to do so, then it would seem I might as well just use the main hosts file to do so.

Anyway, I just wanted to understand this whole zeroconf thing.

Additional info can be found here:

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

[http://avahi.org](http://avahi.org)
[http://www.zeroconf.org/](http://www.zeroconf.org/)

patrick

---

