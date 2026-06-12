---
title: "Can't access the internet in my work place (Ubuntu 12.04)"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by tarzanman6 on 2012-11-13
I started an internship about a week ago and so far I have been unable to access their network. I can, however, access my wireless at home. Both of the networks are password protected.

Details:
PC: Asus N53SV
Ubuntu: 12.04

I've read a very large amount of other posts similar to this one and I know that I need to give more information in order to get better help, but I really don't know what that information is. On top of that, from what I've gathered, it seems the information varies according to each situation so...idk

All I can say for sure is: I need help:)

---

### Post by Bucky Ball on 2012-11-13
Welcome.

You need to firstly ask the sys admin people at your work for the details of their setup. Static IPs? Are you being served an IP from their LAN? Do you need to use a password or any specific setup on your end? What do you need to do to get on the LAN according to them?

It is hard to know what advice to give before you can give details of the LAN you are attempting to join. If you know your wireless is working fine elsewhere and you are good to go, talking to the IT staff at work is your next step or providing as much detail as you can about the work LAN here if you already have (omitting, of course, passwords and any sensitive information).

PS: Yes, the information required can vary depending on the setup they have at work and the information they give you, among other things ...

PPS: You never know your luck; one of the IT crew or another employee may have Ubuntu running already and can tell you in five minutes. Of course, that is reliant on if the stars are aligned correctly!

---

### Post by tarzanman6 on 2012-11-13
The company I'm working at is quite small, so I don't think they have anybody who takes care of the networking.

When I first attempted to join their network, the only thing they did was type in the password when it was asked for so I assume I only need a password (which ubuntu kindly saved for me to read :D). I also know it's the correct password because I switched to windows and I was able to get in the network with no problems.

Continuing on the first paragraph...Since I didn't find anybody to ask for help, I went ahead scavenged whatever information I could find:
- The networks security  is a WAP personal (Confirming, as far as I can tell, the single need for a password to get into the network)
- I know the ipv4, but I don't think that's relevant to the situation
- I know the router's ip
- and ipv6 doesn't seem to be explicitly set

I know this isn't much more than what I gave before, but I really don't know much about networking...I wish I did so I could figure out these problems myself. If there's some, more specific, information you need I'll try and get it. Otherwise I'll just try and figure something out.

EDIT: By the way, I read quite a few things on additional drivers while I was looking for a solution. I looked for it on my pc and when I opened the application it was completely empty; only said: No Proprietary drivers are in use on this system. I don't know if that has anything to do with my problem, but "I" never know...

---

### Post by Bucky Ball on 2012-11-13
Okay, set it up in you Network Manager then. Right click on the Network icon and Edit Connections.

Create a connection for wireless there setting IPv6 to ignore, the password and set to WAP in the appropriate sections, set to Automatic Configuration for DHCP (their router is serving an IP address if you only needed the pw. Tick 'Connect Automatically' and 'Available to all users'. Save all that and restart your machine. If that is the fix it should attempt to connect at boot and when you left click the Network icon you should see the name of that connection there (you are going to need name of the AP or access point, which could be their router, if it is not recognised or given automatically).

Think the most important thing is to get the security setting right, i.e. make sure you are using WAP and not WEP or anything else and make sure you have the name of the LAN you are trying to connect to in there.

Good luck.

---

