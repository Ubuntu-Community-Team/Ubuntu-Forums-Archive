---
title: "DHCP and DNS(probably) problem"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by doktormiod on 2009-10-04
Hi, today after moving i finally have an internet connection which unfortunately works only on windows :/
It's a LAN connection with DHCP. On windows it works flawlessly but on kubuntu it connects only to google and sometimes to some random pages. On both OSs it's getting same DNS adresses but still i think this is the problem. I changed resolv.conf and some dhcp file in /etc to give it some other DNSs (eg. 4.2.2.1) but it didn't help :/
Anyone got ideas?
As i said symptoms are not connecting to any other page than google.

---

### Post by Iowan on 2009-10-04
Probably unrelated, but check [this]("http://ubuntuforums.org/showthread.php?t=971064") one.

---

### Post by houstonbofh on 2009-10-04
There is a command line program called nslookup.  It can be handy for troubleshooting here...  You can change servers within the nslookup shell for testing as well.

---

### Post by doktormiod on 2009-10-04
Damn, now i think it's not DNS related after all 'cos when i completely disabled DNS in /etc/dhcp3/dhclient.conf i still could connect to google by typing in IP adress but not to any other site :/. And 1 more thing - with dns enabled i can ping every site but in browser it just says "waiting for "any website"....". apt-get doesn't work as well so it's not browser related.

It seems like there was some filter in the system that just blocks some pages :/

---

### Post by houstonbofh on 2009-10-04
I am betting a web proxy that Microsoft is detecting without telling you.  Call your provider.

---

### Post by doktormiod on 2009-10-04
> **houstonbofh said:**
> I am betting a web proxy that Microsoft is detecting without telling you.  Call your provider.

Can you explain? ;) I don't really understand :/

---

### Post by houstonbofh on 2009-10-04
Internet Explorer has an automatic proxy configuration.  That could be allowing you to use the proxy in Windows without knowing it.

---

### Post by lswb on 2009-10-04
What kind of ISP do you have? ( cable, DSL, ? ) Do you connect through a router or ??

Just as a guess, try this in a terminal

sudo ifconfig eth0 mtu 1450

and see if it makes a difference

---

### Post by doktormiod on 2009-10-05
"sudo ifconfig eth0 mtu 1450"

Don't know what it did but it worked :D
I owe you a big one, thanks :D

---

