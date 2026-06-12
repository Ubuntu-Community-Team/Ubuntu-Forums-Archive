---
title: "Cannot resolve web addresses"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by Dhekke on 2010-02-24
I have a Dell Inspiron 1545 with Ubuntu Karmic that was working like a charm until last week.

When I'm using my college's wireless I can browse just fine, but when I'm in my home's network the web addresses cannot be resolved.

I was suspecting of DNS error, but it's the same DNS address in all the other computers, and the whole network is working just fine...

The thing is that if I use the IPs, for instance 64.233.163.104 for Google, it works fine, both pinging and browsing. So the problem is in resolving the addresses... anyone can help?

Thanks.

---

### Post by bruno9779 on 2010-02-24
Set up openDNS and configure you computer to use it. This way you'll have the same DNS resolver everywhere you go.

here is the link for openDNS: [http://www.opendns.com/](http://www.opendns.com/)

when you have your DNS addresses you can simply:

> Generally speaking your router/gateway should get an IP address from your ISP. With that it should get the DNS servers addresses. Most then run DHCP to the internal network and tell the clients (your pc) the DNS servers to use, and to use the router as the default gateway. If this isn't working properly then you can set the DNS servers in the file /etc/resolv.conf. Edit this using the following:-

$ sudo gedit /etc/resolv.conf

Then make sure there is an entry for each nameserver in the format below

nameserver <ip address of nameserver 1>
nameserver <ip address of nameserver 2>

---

### Post by Dhekke on 2010-02-24
I did that but got the same problem, I can use the IP's, but not if I use domain addresses

---

### Post by Iowan on 2010-02-24
> **Dhekke said:**
> When I'm using my college's wireless I can browse just fine, but when I'm in my home's network the web addresses cannot be resolved. When in home network, what is in */etc/resolv.conf*? I remember a thread about stale information, but don't remember if it was **resolvconf** or something else.

---

### Post by Dhekke on 2010-02-24
```
nameserver 187.36.192.15
nameserver 187.36.192.15
```

This is the same DNS used by the other 2 PCs and Xbox, working in all 3.

I can ping the ip from my notebook just fine, so it's up, running and responding...

---

### Post by Dhekke on 2010-02-24
I used a Ubuntu live cd and managed to connect and browse just fine... so it's not my DNS server... there's a messed up config somewhere...

Anyone? :confused:

---

### Post by Dhekke on 2010-02-25
Bumping...

---

### Post by Iowan on 2010-02-25
Hmmm... most of my ideas are already shot down - **route** would have the same problem with IP addresses as names. DNS in hosts.deny probably wouldn't respond to ping. Firewall rules *probably* wouldn't differentiate (is firewall active?). MTU wouldn't care name vs. IP.

---

### Post by Dhekke on 2010-02-25
I just tried a wired connection to the router, and got the same problem, so it's not the wireless config...

And after it working on the live cd (with the standard network manager, not Wicd) I reinstalled Wicd in hopes that it had some configuration messed up, but that also didn't work

I can still ping anything, but it won't resolve hostnames...

---

### Post by Sylslay on 2010-02-25
Delete all device from network manager  applet( if use gnome),
and add new for eth0 and wlan0.
Mark in left corner as "auto connect". and use Automatic DHCP addresses only  at TAB  IP4 (is on Auto  by deflaut).

---

### Post by Dhekke on 2010-02-25
I'm using Wicd, can I do this on it?

---

### Post by Dhekke on 2010-02-25
Okay, while googling it I came across [this]("http://www.linuxquestions.org/questions/linux-networking-3/cant-resolve-host-as-user-but-works-fine-as-root-494270/") (can't resolve hostname as user, but works as root) so I decided to ```
sudo ping www.google.com
``` just for the heck of it, and it worked!

So it's a permission problem... probably on /etc/resolv.conf

What's the default permission for it?

---

### Post by Iowan on 2010-02-25
> **Dhekke said:**
> Ok
So it's a permission problem... probably on /etc/resolv.conf

What's the default permission for it?root:root on my Hardy and Karmic machines...

---

### Post by Dhekke on 2010-02-25
> **Iowan said:**
> root:root on my Hardy and Karmic machines...

I set mine to -rw-r--r-- and now it's working :p

Thanks for the help!

---

