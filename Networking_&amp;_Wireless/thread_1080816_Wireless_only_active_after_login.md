---
title: "Wireless only active after login"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by svanheulen on 2009-02-25
I have a Linksys WMP54G v4.1 (uses rt61 chipset) and it works fine in Ubuntu but it only connects to my access point after I login.

How do I set it up so that it connects on boot-up? I was thinking I could add it to /etc/network/interfaces but that didn't seem to work... or maybe I didn't do it right?

This is what I added...
```
auto wlan0
iface wlan0 inet dhcp
    wireless-essid linksys
```
Then I did...
```
sudo /etc/init.d/networking restart
```
And it gave me this...
```
 * Reconfiguring network interfaces...         
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:10:e4:8a:e1
Sending on   LPF/wlan0/00:1c:10:e4:8a:e1
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:10:e4:8a:e1
Sending on   LPF/wlan0/00:1c:10:e4:8a:e1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18

```

---

### Post by svanheulen on 2009-02-26
... No one? Not even a clue?

---

### Post by God Of Atheism on 2009-02-26
I had a similar problem, and though I did not manage to solve it, [this thread](http://ubuntuforums.org/showthread.php?t=1077661) might give you some ideas.

---

### Post by excbuntu on 2009-03-01
i have the same issue. when my laptop is woken up, i can't ssh or vnc into it cause it doesn't acquire a wireless connection unless someone logs in! if my wired desktop acquires an internet connection before login, why is it that a wireless laptop can't do the same? psh.

---

### Post by qbox on 2009-03-01
You can try 

sudo gedit /etc/rc.local

insert all commands that you write in a console to connect to the access point. This commands will be executed on system booot.
This will probably help you.
PLEASE post me the results.

Cheers:rolleyes:

---

### Post by excbuntu on 2009-03-06
^ what specific commands would you be talking about?

---

