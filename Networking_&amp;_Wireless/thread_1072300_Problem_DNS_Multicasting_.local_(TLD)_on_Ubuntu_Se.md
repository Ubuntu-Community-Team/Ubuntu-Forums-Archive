---
title: "Problem: DNS Multicasting .local (TLD) on Ubuntu Server / OSX Client"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by nbcmayhem on 2009-02-17
i got a weird behaviors with mDNS. as soon as i start avahi-daemon on my ubuntu server the afp  file server shows up in the finder. i can connect in the very first minutes but after i disconnect and try to reconnect via bonjour/zeroconf i get a timeout. 

it's really strange, so i used ipv4 to connect. today i wanted to setup cups on my ubuntu server, but to my misery it connects to IAN.local and therefor it somehow can't connect.

so how can i find out whats wrong with multicasting ? wether it's my poor d-link router (dir 635) or if it's a setup problem on my server/mac ?

---

### Post by nbcmayhem on 2009-02-19
bump

---

### Post by andrewcd on 2009-08-29
Resurrecting an old thread for a similar problem.  I am using Jaunty and in certain places I get an error message saying something about how Avahi doesn't like .local.  Could someone perhaps explain whats going on and how to fix it to work with these networks? 

Thanks

---

