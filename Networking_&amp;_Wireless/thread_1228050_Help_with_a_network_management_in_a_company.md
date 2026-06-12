---
title: "Help with a network management in a company"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by rugal on 2009-07-31
Hi everybody, first of all i'm not a sys admin, but i'll have to setup all the network management in my company (i use linux/gentoo for 5-6 years).
This is the schema i've in mind of it will be:
[[IMG]http://img44.imageshack.us/img44/2648/networky.th.png[/IMG]]("http://img44.imageshack.us/i/networky.png/")
As you can see there is a first server connected directly to the internet, which will filter, and manage authentications of the users. Then it's connected to the router to share the connection to others.
I've some questions for you ;)
1) i've to filter bad stuff which users would try to access, like movies, mp3s, warez, and stuff like that. what do you suggest to use? iproute2 would be good? do you have any good guide to setup something similar?
2) i've also to filter bad sites (porno, movies streaming, etc), for this i could use dansguardian. what do you say? is it good or is there something better?
3) the user of a workstation use whatever want as os (mostly linux, but there will be some win/mac guests). how can i setup that they can use their pc without problems (develop, or just work), but to connect to the internet they have to login to the server which will gain them the access? to the local pc they login locally, they don't need to connect remotely, but just when they want to connect on internet, or to the shared folders
4) i've to log everything the users do on the internet, which site they visit, who, and when.. how can i do this?
5) the other server (the on connected to the router) will have shared folders where everyone in the network can access (only in the lan, not external people). as there will be guests with windows and mac and they should do too much configuration to connect (obviously they need to authenticate to the system) i think i can use ldap, but something else.. samba?
the authentication data (user/pwd) to connect to the internet and to the shared folders would be better to be the same
6) what if we want to setup an internal voip system? which would work like an software operator, they can call from an external number, and choose an internal number to redirect the call to the right user. what should we use? asterisk?
7) what if all should be available also externally using a vpn? what should we use to create that? hamachi or is there something else?
8) which software would do you suggest would be required and useful to have on servers and workstations? (as it's the first time i don't know exactly what both of the servers would need... just that the one connected to the internet will need 2 ethernet ports ;) but i don't know then how to move from there, like sharing the connection, but logging/filter)
9) i cannot rely completely from the workstation machines, as they're full managed by the users (=root access)

i hope it's everything, but i'm sure i've missed something :)
It's welcome any extra advice, name of software, or even direct urls to guides (i'm already using google, but without the experience to know what's needed it's hard to find something :) ) (eventually also something about security ;) )
Thank you

---

### Post by dmizer on 2009-07-31
Depending on the size of your LAN, I suggest putting the router on the WAN side of the server for a number of reasons, but most importantly ...

1) It will be easier to filter and track LAN traffic that way.
2) As a novice network admin, a router will provide a good first line of defense in case you make a rookie mistake.

Also as a novice network admin, I suggest a prepackaged gateway OS like [Clarkconnect](http://www.clarkconnect.com/), [untangle](www.untangle.com/), or any other of the myriad of FLOSS gateway OS options. These will be much easier for you to manage, maintain, and keep upgraded. They will also be much more user friendly (web interface) than trying to build your own gateway.

When I was asked to put my own server in place on a small business LAN, it took me about a month to get everything working correctly because I configured everything by hand. By comparison, it took me a matter of minutes to have an Untangle gateway up and running. Both Untangle and Clarkconnect (and others) have add on modules which will allow you to expand the function of your gateway into performing functions like web hosting, file sharing, VPN, traffic monitoring, and more.

All of the above functionality would work equally well no matter what OS the workstations have installed.

---

