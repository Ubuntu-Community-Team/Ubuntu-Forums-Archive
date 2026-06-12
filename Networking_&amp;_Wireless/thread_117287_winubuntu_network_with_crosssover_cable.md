---
title: "win/ubuntu network with crosssover cable"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by storm76 on 2006-01-14
I am new to Linux and am trying to network my laptop (linux) with desktop (windoze). Unfortunatly no broadband or DSL available. Windoze dial-up as an accesway to connet linux to internet. 

Thaxs.

---

### Post by Mr_Grieves on 2006-01-15
What is it that you wonder about? What cabletype you are to use?
Check out this cable type matrix: [http://cabletype.hacka.net](http://cabletype.hacka.net)

Between two computers you should not use cross over cable, but straight cable.

Else, just set you're Windows computer as default gateway in your Linux system. Make sure the computers reside on the same IP network aswell, for example:

Windows LAN interface: 192.168.0.1/255.255.255.0
Linux LAN interface: 192.168.0.2/255.255.255.0

---

### Post by storm76 on 2006-01-17
I am going from one computer to the other, no hub. Thus crossover required.

---

### Post by seakiwi on 2006-01-17
[QUOTE=storm76]I am new to Linux and am trying to network my laptop (linux) with desktop (windoze). Unfortunatly no broadband or DSL available. Windoze dial-up as an accesway to connet linux to internet. 

Thaxs.[/QUOTE]

I've just done this with a variation or two and had absolutely no problems. I have a Windows machine as the host machine - dial up - connected to my Linux machine and another Windows machine via a switch and straight cables (someone helped me set this up - I'm new at all this too, but I think they are straight cables) Without the switch you'd probably need the crossover.

As the previous poster said, you just need to go into Networking and set "static IP" with your host machine as 192.168.0.1 and your machine as 192.168.0.2  with the host machine as the gateway (under the ethernet properties)

Ubuntu detected my network settings during the install and once I'd done the above I was online - very very simple, and pleasantly surprising!  :)

Oh btw, don't forget to set up Internet Connection Sharing on the Windows machine and make sure you use the same IP addresses for the machines in both setups.

---

