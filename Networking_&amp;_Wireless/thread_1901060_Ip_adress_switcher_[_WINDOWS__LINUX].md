---
title: "Ip adress switcher? [ WINDOWS / LINUX]"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by Dlambert on 2011-12-27
Does anyone know of a piece of software that will allow me to switch between multiple IP addresses all on the same network? For example, from one pc 173.15.93.XX to 173.15.XY without changing computers? I need to access multiple craigslist accounts and it would be alot easier to switch IP's using one computer.

---

### Post by Dlambert on 2011-12-30
Bump

---

### Post by Lars Noodén on 2011-12-30
You could use [ifconfig](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html) or [ip](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ip.8.html) with [sudo](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html).

---

### Post by Dlambert on 2011-12-31
The person I'm doing this for need a gui. :/

---

### Post by Lars Noodén on 2011-12-31
Ok.  Then if you are using Unity and not KDE or XFCE:

System Settings->Network->Wired->Configure->IPv4/IPv6

---

### Post by Dlambert on 2012-01-01
> **Lars Noodén said:**
> Ok.  Then if you are using Unity and not KDE or XFCE:

System Settings->Network->Wired->Configure->IPv4/IPv6

Thank you, but how would I explain to him how to add/ switch IPs?

---

### Post by syerges on 2012-01-01
make him icons to switch back and forth... write the terminal codes in for the switch...
gnome-desktop-item-edit --create-new ~/Desktop

---

### Post by fdrake on 2012-01-01
> 
Does anyone know of a piece of software that will allow me to switch between multiple IP addresses all on the same network? For example, from one pc 173.15.93.XX to 173.15.XY without changing computers? I need to access multiple craigslist accounts and it would be alot easier to switch IP's using one computer.

why there is a problem with craigslist if you use the same ip? I did not know that....that's new to me...
also are you trying to access those account at the same time? or not?
sorry if the question sounds dumb but i am a little confused..

---

### Post by Dlambert on 2012-01-01
The person in question has multiple accounts, and wants to switch between IPs without physically moving to another computer in the network.

---

### Post by Dlambert on 2012-01-03
Bump

---

### Post by lisati on 2012-01-03
> **Dlambert said:**
> The person in question has multiple accounts, and wants to switch between IPs without physically moving to another computer in the network.

I hope this doesn't mean that you're trying to circumvent their TOS.... :(


You might also want to take a look at [http://whatismyipaddress.com/change-ip](http://whatismyipaddress.com/change-ip)

---

### Post by Dlambert on 2012-01-13
> **Lars Noodén said:**
> Ok.  Then if you are using Unity and not KDE or XFCE:

System Settings->Network->Wired->Configure->IPv4/IPv6

Exactly what He needed! Thanks!

---

