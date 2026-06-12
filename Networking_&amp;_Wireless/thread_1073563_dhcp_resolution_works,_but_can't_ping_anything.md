---
title: "dhcp resolution works, but can't ping anything"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Darkmatter5 on 2009-02-18
I can run sudo /etc/init.d/networking restart and get the following result.

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.5 from 192.168.1.11
DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.5 from 192.168.1.11
bound to 192.168.1.5 -- renewal in 313082 seconds.

So I got an IP address of 192.168.1.5 from my DHCP server at 192.168.1.11, but I can't ping anything.  I can't even ping 192.168.1.11 the freakin' DHCP server I just got an address from.  

This is an Ubuntu server fresh installation, whatever the most current version is.  Does Ubuntu come installed with a firewall turned on by default?

---

### Post by Iowan on 2009-02-18
> **Darkmatter5 said:**
>  Does Ubuntu come installed with a firewall turned on by default?I think my Hardy server came with **ufw** enabled - and I had to turn it off to make things work right.  I suppose I should eventually learn the "right" way to work *through* the firewall.

---

### Post by Darkmatter5 on 2009-02-18
okay ufw is now disabled, but still can't ping anything.

---

### Post by Iowan on 2009-02-18
You restarted the machine (or at least networking)?

---

### Post by Darkmatter5 on 2009-02-18
Yep it's restarted, I can't ping in our out to this machine.  Also it IS a VMWare machine, not a physical machine.

---

### Post by EvinK on 2009-02-18
Can you post the output of ifconfig eth0 and route?   And can you ping 127.0.0.1?

---

### Post by Darkmatter5 on 2009-02-18
It's freakin' AVG's firewall that's blocking.  I disabled AVG's firewall and viola.  Now to figure out how to get AVG to pass traffic through VMWare.

---

### Post by EvinK on 2009-02-18
Are you using NAT or Bridged mode in your VM for your network card?

I also found this if you are running in Bridged Mode from vmware forums.

I just got a response from AVG that this is a bug in their software and that I should download the latest AVG beta version to fix it. Here is the message from AVG:


"....We would like to inform you that your issue has been solved in the latest beta version that is available on our beta portal ( 8.0.214 ) [[http://beta.grisoft.com/beta/index.php?lang=2]](http://beta.grisoft.com/beta/index.php?lang=2]) Please install the beta version and do the following: - Start the AVG User Interface - Select Tools -> Firewall settings -> <Active profile> -> Enable Virtual Machines Bridged networking option. - Save changes......"

---

