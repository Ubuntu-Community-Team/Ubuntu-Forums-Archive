---
title: "Wired Internet Connected / Can not browse"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by BriceH. on 2009-08-28
Hello everyone!  Let me first start off by saying how much I have enjoyed Linux and Ubuntu up to this point.  It wasn't until just recently that I started becoming serious in my attempts to learn and master the usefulness of everything Ubuntu has to offer.

I have Ubuntu 9.04 Jaunty installed on an ASUS K8V MB with AMD Athalon 64 processor 3200+, NVIDIA GeForce FX 5200 Ultra Graphics card, and 1.5 Gb if RAM.  THe Ethernet card is a 3COM 1 GIG.

The router is LinKsys BEFW11S4 version 4 (piece of JUNK IMHO).

Here is my problem.

I installed Apache 2.2 yesterday with PHP5 and MySQL.  The installation went perfect and is working right now.  My web site is hosted there if anyone would like to vist: 

[http://brice.is-a-geek.com ]("http://brice.is-a-geek.com")

Well I tried to establish a static IP on my Ubuntu machine, which seemed to work.  But my problem is I can not browse the Internet anymore.  What I can do though, is ping the static IP of my Linux box, ping my Router, and ping another machine in my network.  As I stated above, my website is hosted on that server so outside attempts can access the machine with no problem.  

So how or why did I lose the ability to browse outside sites?  And how can I establish a static IP on my machine without losing the ability to browse?

The problem is the same with IE6 and FF.  The IE6 is for browser compatibility when I am developing websites.

Willing to post more information as needed.

Thanks for any help that you can shed on the matter.

---

### Post by denver on 2009-08-28
Sounds to me like you are missing your nameservers. Nameservers are the servers required to resolve a domain name (example.com) into an IP address (like the one you configured statically).

Your computer cannot understand example.com. It only understands 192.168.0.1 or 127.0.0.1. What you probably need to do now is right click on nm-applet and go to:

Edit Connections-->wired/wireless-->Edit-->IPv4 settings

and under DNS Servers add one of the following:

192.168.0.1 (if this is the IP address of your Lynksys)
208.67.222.222 (If you wish to use OpenDNS service)

You can find out more about OpenDNS at:

[http://www.opendns.com/](http://www.opendns.com/)

If you don't use NetworkManager to manage your internet connections, then you must add the following line:

```
nameserver 192.168.0.1
```

or

```
nameserver 208.67.222.222
```

to 

```
/etc/resolv.conf
```

Of course you can add both, and you must be root to do so. Be aware that if you DO use NetworkManager, your modiffications will be overwritten.

Also, make sure you have a valid gateway set for your connection (modt probably 192.168.0.1)

---

### Post by BriceH. on 2009-08-28
> **denver said:**
> Sounds to me like you are missing your nameservers. Nameservers are the servers required to resolve a domain name (example.com) into an IP address (like the one you configured statically).

Your computer cannot understand example.com. It only understands 192.168.0.1 or 127.0.0.1. What you probably need to do now is right click on nm-applet and go to:

Edit Connections-->wired/wireless-->Edit-->IPv4 settings

and under DNS Servers add one of the following:

192.168.0.1 (if this is the IP address of your Lynksys)
208.67.222.222 (If you wish to use OpenDNS service)

You can find out more about OpenDNS at:

[http://www.opendns.com/](http://www.opendns.com/)

If you don't use NetworkManager to manage your internet connections, then you must add the following line:

```
nameserver 192.168.0.1
```or

```
nameserver 208.67.222.222
```to 

```
/etc/resolv.conf
```Of course you can add both, and you must be root to do so. Be aware that if you DO use NetworkManager, your modiffications will be overwritten.

Also, make sure you have a valid gateway set for your connection (modt probably 192.168.0.1)


Most excellent!  I was leaning toward that last night but I couldn't think straight anymore.  Then this morn I lost my train of thought and hadn't actually gotten into it.  I will check that out and let you know in a little bit.  Thanks.

---

