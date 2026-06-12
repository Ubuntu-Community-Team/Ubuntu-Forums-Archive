---
title: "LAN-only web server"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by rplantz on 2009-03-12
I would like to set up a web server on my Ubuntu desktop machine that can only be accessed on my LAN. My other machines include Mac OS X, Ubuntu/Vista dual-boot laptop, XP desktop.

I have file sharing working.

All the machines access the WAN through my router, which gets dynamic IP address from my ISP and it provides dynamic IP addresses on my LAN.

The problems I'm having trouble understanding are:

1. How do I set my own private domain name for my LAN?

2. What settings should I look for on my router?

I have web serving working on my main (Ubuntu desktop) machine. That is, ```
http://localhost/~bob
``` brings up the page
```
~bob/public_html/index.html
``` in my browser just fine.

---

### Post by whoop on 2009-03-12
I am not sure what you want but if I understand you correctly it can be achieved via using your own dns server or editing the /etc/hosts file on client so that an url points to your local webserver

---

### Post by rplantz on 2009-03-12
> **whoop said:**
> I am not sure what you want but if I understand you correctly it can be achieved via using your own dns server or editing the /etc/hosts file on client so that an url points to your local webserver

My router (Trendnet TEW-452BRP) is set to be a DHCP server. As I understand it, this means it provides IP addresses to each device on my LAN as that device comes up. I have both my desktop and laptops on now, and when I log on to the router I see:
```

   Host Name          IP Address
bob-laptop          192.168.1.101
bob-desktop         192.168.1.100

```

My desktop computer (Ubuntu) is set up to do web serving. So if I go to my laptop and enter
```

http://192.168.1.100/~bob

```
in my browser, sure enough, I get my home page.

It would be nice if I didn't have to look up the local IP address each time and enter something like
```

http://bob-desktop/~bob

```
in my browser on the laptop.

My router clearly knows that "bob-desktop" is IP address 192.168.1.100 -- today. But when I shut everything down tonight and reboot tomorrow, it may be a different IP address.

So I'm trying to figure out how to tell my laptop to tell the router to translate the host name (bob-desktop) into the correct IP address.

My other question is what settings should I be looking for in my router that would cause it to honor this request?

I realize that if I use static LAN IP addresses I could then put the name/IP-address information in my hosts file. But it would be nice if I can figure out how to implement the dynamic solution. Which leads to the question: would bind be the best thing for this?

---

