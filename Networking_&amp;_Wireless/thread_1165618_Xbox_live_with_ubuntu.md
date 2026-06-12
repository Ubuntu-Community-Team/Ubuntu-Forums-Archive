---
title: "Xbox live with ubuntu"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by dr.pepper23 on 2009-05-20
Does anybody know how to get on xbox live with ubuntu? It works perfectly with vista, but it sucks having to boot into vista just to get on xbox live. I've got my xbox plugged into my laptop which is connected wirelessly to a router. Thanks.

---

### Post by RichardT on 2009-06-12
Yeah im having this problem as well. It's so easy in windows, just click on bridge connection. But in ubuntu (im using 8.10) i can't get it to work.

---

### Post by dr.pepper23 on 2009-06-12
I've actually got it to work twice now. I have no idea why it worked, I just left the xbox plugged into my computer and when I turned on my xbox one day it randomly connected. The connection was dropped about an hour later, and the same thing happened about two days later. Don't know why it connected; I didn't do anything different...

---

### Post by RichardT on 2009-06-13
That's weird. How is your xbox connected? I mean, have you set up any firewall rules or changed the ip options on the actual xbox?

EDIT: Okay I have managed to get my xbox to connect to the network with this script

```
ifconfig eth0 up
ifconfig eth0 192.168.2.1
echo "1" > /proc/sys/net/ipv4/ip_forward 
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
```

But it fails when connecting to the internet: "Your DNS server can't resolve the names of the Xbox LIVE servers or xbox.com"

---

### Post by RichardT on 2009-06-13
Okay ive connected to xbox live. I used the above script and I turned off my firewall. The only problem is that i get NAT type Strict. This isn't my router because when I do connection bridge on windows I get open NAT.
Still, it's better than nothing.

---

### Post by dr.pepper23 on 2009-06-13
No I don't have any firewall rules and everything on the xbox is set to automatic. I did try using Firestarter because apparently it allows you to easily configure firewall rules, but I never could get it to work. Now that you mention it I do remember running a similar script, but that was a while ago. I don't know if that's what caused it to connect or not. I'll try playing with it some more.

---

### Post by chacro10 on 2009-06-13
hey, ive been wondering the same thing, when you find out, please let me know.:p

---

### Post by Jcdlvsrbld on 2009-06-13
ive been having the same issue. i found this: [http://onlyubuntu.blogspot.com/2008/08/howto-share-internet-connections-in.html](http://onlyubuntu.blogspot.com/2008/08/howto-share-internet-connections-in.html)   i'm going to try this later on

---

### Post by Jcdlvsrbld on 2009-06-13
the link i just provided i doesnt work with wlan and ethernet, i tried to adapt the code, but it stopped my wireless

---

### Post by astropirit on 2009-06-13
yes, i tried the same thing, it stops you to connecting to your router.

---

### Post by Jcdlvsrbld on 2009-06-13
> **RichardT said:**
> Okay ive connected to xbox live. I used the above script and I turned off my firewall. The only problem is that i get NAT type Strict. This isn't my router because when I do connection bridge on windows I get open NAT.
Still, it's better than nothing.


[http://www.portforward.com/networking/staticip-xbox360.htm](http://www.portforward.com/networking/staticip-xbox360.htm)

this may help

---

### Post by Jcdlvsrbld on 2009-06-13
bump

---

### Post by Jcdlvsrbld on 2009-06-15
[http://ubuntuforums.org/showthread.php?t=82258](http://ubuntuforums.org/showthread.php?t=82258)
[http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)

i managed to get this running in firestarter, first i got the unable to connect message, but that was fixed with a simple dns config on the 360. unfortunately, this still doesnt help with the strict NAT:popcorn:

---

### Post by dr.pepper23 on 2009-06-25
I want to bump this back up to the top. I've got it connected as well, but I've also got strict NAT. Anybody figured this out yet?

---

