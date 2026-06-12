---
title: "Two Routers, Slow Internet"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by Hank_The_Dog on 2011-11-02
Greetings.

I am getting really slow Internet on one of my Ubuntu 10.10 boxes... 
[U][B]
Dual router setup...[/B][/U]

-  Modem -> Cat6 -> 'Internet' port of router A

-  Router A then supplies wireless, as well as running two devices off of ports 1 and 2 

*(Using DHCP on router A and all wireless devices and both computers have chronological IPs  (Works great!)* )

-Changed router B from DHCP into StaticIP (192.168.1.200) .. *hopefully I will never have 200 devices :)*

-Plugged cat6 from router A into port '4' of router B (NOTHING is plugged into 'internet' jack)

-Used remaining 3 ports for:

[LIST=1]
[*]Server
[*]His
[*]Hers
[/LIST]
-Internet does works on _**[COLOR=Black]all[/COLOR]**_ of the attached devices of router B, and every device receives a local IP address, so basically I just switched router B into WAP and hub...

List of IPs 192.168.1.....

[LIST=1]
[*]Router
[*][COLOR=DarkOrange]Boxee (cat6)
[/COLOR]
[*][COLOR=DarkOrange]Her Laptop (cat6/[COLOR=Magenta]wifi[/COLOR])
[/COLOR]
[*][COLOR=LightBlue][COLOR=Magenta]Wii (wifi)[/COLOR]
[/COLOR]
[*][COLOR=Red]Samba Share Server (cat6)
[/COLOR]
[*][COLOR=Red]His Desktop (cat6)
[/COLOR]
[*][COLOR=Red]Her Desktop (cat6)[/COLOR]
[/LIST]

BUT 192.168.1.7 = SLOW
I connected "[COLOR=Red]Her Desktop (cat6)[/COLOR]" DIRECTLY to router A, and to modem (Works Great!):confused:


[LIST]
[*]**Could this have something to do with the fact that it is last in the IP list?**
[*][B]192.168.1.5 and .6 and .7 all come from router B.
[/B]
[*]**Is it a bad idea to have 3 solid devices coming off of router B this way?**
[/LIST]

---

