---
title: "Can you let me know if you can see http://mycomputername.local/ from Windows, iPad..."
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by desconocido on 2010-08-14
I wanted to make it easy for devices connected to whichever WiFi lan my laptop was part of, to view files on my laptop computer.

I did not want to get involved with Samba. 
I did not want explicit ip addresses as they are supplied by DHCP servers in routers and they change as I change router.
I did not want dynamic DNS services.

I am running apache2 on Ubuntu Karmic 9.10, so using web browsing seemed a good approach.

This idea looked good:
Browsing to "http://mycomputername.local/", where "mycomputername" is the name you give your computer when installing Ubuntu.

Using that url, I could see my web pages

(a) from my own computer itself
(b) from an Apple Macintosh running OS X 10.3.9

I would like to ask people if they could let me know if it works from other devices as well.
For example, different flavours of Windows; MacOS 9; iPhones; iPads; other portable devices that have WiFi.
And whether the browser made a difference (I was using Firefox).
And whether the Ubuntu version on the target computer mattered.
And whether the model or settings of the router made a difference.

My thanks if you can help.

---

### Post by Kerubu on 2010-08-15
Because you mentioned ".local" I think you're talking about zeroconf environment. This is where there is no DHCP server assigning addresses but devices on a network co-operate amongst each other to get an IP address.

In this scenario even though there is no DHCP server, you STILL need some program but on EACH device that wants to be on the network. In Linux it's called Avahi. I haven't had much use of it and I find the documentation for it poor but as I've no need for it (at the moment) I haven't pursued trying to understand its operation. I know the theory of a zeroconf environment but one other reason I haven't used it is that it uses a different range of reserved IP addresses than what I use and I can't be bothered faffing about changing to the zeroconf range especially when I don't need it.

You might ask 'can't I do away with having an IP?' to which the answer is 'no'. Even though in the zeroconf environment you use memorable names (ending in .local) the underlying IP is still there.

I'm not really answered your question but I've provided you with a little background to what you're hoping to achieve

---

### Post by desconocido on 2010-08-15
> **Kerubu said:**
> Because you mentioned ".local" I think you're talking about zeroconf environment. This is where there is no DHCP server assigning addresses but devices on a network co-operate amongst each other to get an IP address.

Thanks for this, I did not know about zeroconf. In fact in most cases my laptop will be in a WiFi environment where there is a DHCP server, but I can think of at least one place where there won't be. Either way, it seems I can just refer to mycomputername.local and something will resolve it to a usable ip address.

I googled zeroconf and found this page in particular to be of interest:
"HOWTO Ridiculously easy home file sharing with FTP and Zeroconf"
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

It dates from 2006 but has been kept up-to-date and has some helpful suggestions about access from MacOS X and Windows using *.local addresses with or without zeroconf.

By the way, is there a technical name for using this *.local style of address?

Would still welcome experiences of access from iPhone, iTouch, iPad etc.

---

### Post by desconocido on 2010-08-16
Just tried [http://mycomputername.local/](http://mycomputername.local/) from
Windows Vista Service Pack 2 (different router and with Internet Explorer)

It failed to find it.

---

### Post by desconocido on 2010-08-25
Just tried [http://mycomputername.local/](http://mycomputername.local/) in the WiFi zone of yet another router.

It worked fine on
(d) Windows Vista with Firefox
(e) MacOs X 10.6.4 with Safari

It failed on 
(f) a Samsung mobile phone (didn't get the model) with WiFi and Web capability

Can't see any pattern emerging yet.

Is there any way of forcing routers to notice the names of devices they give DHCP leases to?

---

