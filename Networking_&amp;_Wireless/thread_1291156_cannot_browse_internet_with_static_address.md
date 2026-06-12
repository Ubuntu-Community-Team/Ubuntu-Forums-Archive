---
title: "cannot browse internet with static address"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by ffoeg on 2009-10-14
I have the ip entered as static. I can ping internal addresses as well as external addresses. But I cannot browse the internet. It's got to be a DNS issue. But I tried everything I can find on the internet to resolve the issue. Can someone help me?

Here's the output of some key things:

ï»¿/etc/network

auto lo
iface lo inet loopback

nameservers 68.94.156.1 68.94.157.1 192.168.0.1

auto eth0
iface eth0 inet static
address 192.168.0.200
network 192.168.0.0
netmask 255.255.255.0
gateway 192.168.0.1


/etc/resolve.conf

nameserver 192.168.0.1
nameserver 68.94.156.1
nameserver 68.94.157.1



user@SERVER:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by hal10000 on 2009-10-14
your network is configured correct as far as i can see, but 

> /etc/resolve.conf


must be named [COLOR="Red"]/etc/resolv.conf[/COLOR] without the "e". That's the only error i can see.

---

### Post by Fire_Chief on 2009-10-14
+1 on hal10000's suggestion.

Could always try other DNS servers as well.

OpenDNS servers
208.67.222.222
208.67.220.220

GTEI nameservers
4.2.2.1
4.2.2.2

Cheers!

---

### Post by ffoeg on 2009-10-14
Hello. I've set my Ubuntu 9.04 desktop up with a static address. Although I can ping an offsite server, as well as any local ip, I cannot browse the internet. I've checked my settings a countless amount of times. Can anyone help me? Here's the output of /etc/network/interfaces    /etc/resolve.conf    and  $ route

Thanks in advance.


/etc/network
auto lo
iface lo inet loopback

nameservers 68.94.156.1 68.94.157.1 192.168.0.1

auto eth0
iface eth0 inet static
address 192.168.0.200
network 192.168.0.0
netmask 255.255.255.0
gateway 192.168.0.1


/etc/resolve.conf

nameserver 192.168.0.1
nameserver 68.94.156.1
nameserver 68.94.157.1



user@SERVER:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by Iowan on 2009-10-14
Hmmm - everything looks kosher... Can you ping internet via IP address? 
I saw a thread where **acpi** was causing failure except a couple of sites.

---

### Post by cariboo on 2009-10-15
Please don't double post, I have merged your two threads.

---

### Post by ffoeg on 2009-10-15
Sorry Cariboo...I thought my original port was lost.

And, hal10000, on my system the resolve file is spelled correctly. I just forgot the "e" in my manually types post. But thanks.

I guess I'll have to try other DNS servers. But everything else looks good, right? Anything wrong with the route?

Is there any way to check to see if something is blocking regular internet traffic?

Thanks

---

### Post by Fire_Chief on 2009-10-15
If you can ping IP addresses on the Internet then the route is working fine.

Here are some test IPs to try just to see if you are reaching all of the Internet or not. Try by IP and by name (though you may get different IPs when using the name but should still ping ok).

216.34.181.60  (sourceforge.net)
209.191.93.53  (yahoo.com)
74.125.67.104  (google.com)
204.9.163.162  (skype.com)

If you can only ping these by IP then you definitely have a DNS problem. For giggles, you may try removing the 192.168.0.1 nameserver entry from /etc/resolv.conf so the system will use the external DNS servers only.

Note: You could also browse using these IP addresses to see if you can pull up the respective websites. This will confirm there is no blocking for http traffic happening.

Cheers!

---

### Post by ffoeg on 2009-10-15
Thanks Fire Chief. I will try out all of those ideas as soon as I can.

---

### Post by chili555 on 2009-10-15
> And, hal10000, on my system the resolve file is spelled correctly. I just forgot the "e" in my manually types post. But thanks.I am confused. On your system is it resolv[COLOR="Red"]e[/COLOR].conf or is it resolv.conf?

It is supposed to be, and will only work, as */etc/resolv.conf*.

I apologize in advance if I have misunderstood.

---

### Post by ffoeg on 2009-10-22
When I entered the IP for google in Firefox, the website did show up. So, it was indeed a DNS issue.
I ended up manually putting important ip's into the hosts file. I was then able to download updates, and the problem was then resolved. 
I thank everyone for their help.

---

