---
title: "How can I automatize pppoeconf?"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by rodrigo3n on 2010-10-03
Hello everyone, I am a Ubuntu user (10.04 as of now), since I use it, over a year, I have to manually enter the command **$ sudo pppoeconf** everytime I turn on the computer and want to connect to the internet, the I click enter some times, enter my password of my internet provider, then I click enter some more times to have internet.

I have to do this boring work, 3 times a day, just now I am asking you if you know any way of automatizing this?

Thanks!

Rodrigo Alves Vieira,
[http://rodrigo3n.com](http://rodrigo3n.com)

---

### Post by dineshs on 2010-10-04
_Method-I_
Use Network manager for configuring the connection.Please try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2") If this doesnt work try
_Method-II Use pppoeconf command _
Run ```
sudo pppoeconf
```to configure the connection.Now edit 
[COLOR="Purple"]/etc/network/interfaces[/COLOR]using the command ```
 gksudo gedit /etc/network/interfaces
```so that it contain only ```
auto lo
iface lo inet loopback
```,then restart.
To connect use```
pon dsl-provider
```
and to disconnect ```
poff dsl-provider
```
(while configuring pppoeconf you can opt [COLOR="DarkOrange"]start connection at boot time[/COLOR])

---

