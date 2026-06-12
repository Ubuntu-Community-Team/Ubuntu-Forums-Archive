---
title: "Problem"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by alter-- on 2011-06-27
Hello all im new on ubuntu and i have a problem but nobody canot help me.
 
The problem is like this?
 
Im using ubuntu as gateway, and i have clients that use public ip and i dont want they to nat with the linux ip address but i want they get out on internet with their ip address. Is there any way because when they check their ip they se the linux ip address they dont se their ip address so they become nated on linux i dont want them to be nated.. PLZ helppp..grazias

---

### Post by spiky001 on 2011-06-27
Are you saying that The Ubuntu box is connected to the internet and then the other machines connect to that machine via eth0 or wireless? If so the other client machines will have a local ip address not an internet address, as far as  I know it is not possible with this set up.

---

### Post by Dangertux on 2011-06-27
> **alter-- said:**
> Hello all im new on ubuntu and i have a problem but nobody canot help me.
 
The problem is like this?
 
Im using ubuntu as gateway, and i have clients that use public ip and i dont want they to nat with the linux ip address but i want they get out on internet with their ip address. Is there any way because when they check their ip they se the linux ip address they dont se their ip address so they become nated on linux i dont want them to be nated.. PLZ helppp..grazias

As the above poster already mentioned, unless your ISP gives you multiple IP addresses, OR if you have multiple ISP accounts you will only be able to NAT to the other machines.

If you want to forward specific ports to the NAT'ed machines this is possible with iptables.

---

### Post by alter-- on 2011-06-27
the problem is like this:
 
Internet---LINUX----router----clients
 
So i have multiple public ip's from my provider, and they work they give internet to the clients but when i check my ip in [http://whatismyipaddress.com](http://whatismyipaddress.com) i get the linux ip address not the clients ip address that is Public.
 
I get internet, and i share to the clients with eth0

---

### Post by alter-- on 2011-06-28
help plzzzzzzzzzzzzzz

---

