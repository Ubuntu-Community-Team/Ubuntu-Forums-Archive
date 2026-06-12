---
title: "firestarter &quot;device not ready&quot;"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by Jcdlvsrbld on 2009-06-13
having trouble connecting my 360 through the ethernet port on my laptop. i found this: [http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)  this seems to be a sufficient method but i'm still having some questions.  first, i dont know how i should configure the dhcp settings, do i keep the orginal or create a new one , and second,  the firewall isnt starting. i keep getting "the device eth0 is not ready". Help is very much appreciated (and please, be specific).

---

### Post by Jcdlvsrbld on 2009-06-13
Please HELP

---

### Post by Jcdlvsrbld on 2009-06-13
bump

---

### Post by Jcdlvsrbld on 2009-06-13
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet manual

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports wlan0 eth0
```will this work to bridge the connection?
i adapted it from this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1
```

---

### Post by Jcdlvsrbld on 2009-06-13
This does NOT work. do not try

---

### Post by notoriousmic24 on 2009-07-26
i have the same problem...any solutions?

---

### Post by matchstich on 2009-09-07
i am searching this site right to find a answer to this, as i have the same problem

---

### Post by prentiz on 2009-10-15
Hi all, 

I'm also suffering badly from this problem with me Apire One laptop.  Have spent the last 3 hours trying to get this to work and googling like mad, but to no avail!  I realise this is potentially a stupid linux newbie issue - but I have tried and would appreciate any help available to resolve this!

Prentiz

---

### Post by weirdtalk on 2009-10-16
I had this problem here is how I solved it.
[http://ubuntuforums.org/showthread.php?p=8117154#post8117154](http://ubuntuforums.org/showthread.php?p=8117154#post8117154)

---

