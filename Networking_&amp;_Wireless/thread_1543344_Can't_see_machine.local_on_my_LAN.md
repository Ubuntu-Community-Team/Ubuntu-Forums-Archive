---
title: "Can't see machine.local on my LAN"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by triwave on 2010-07-31
Hey there,

I have a network with 4 machines on it - 1 XP , and 3 linux boxes.

One of the machines is a server and I've always been able to get to it easily by addressing it as machine1.local  instead of having to know it's IP address.

I have upgraded my router today to add N capability using a Belkin Play model #F7D4302 with latest FW 1.00.20 (May 8 2010) 

With new router I can no longer access any of my machines by using the name.local , I have to use the IP address (which does work). If i'm on machine1 and I ping machine1.local there is a response, but from any other machine it times out or host unknown error.

I'm quite certain this is an issue with the router but to debug I'm trying to understand how this local machine naming works. Is there some certain port the router may be blocking?

I'm not sure what the service is that "broadcasts" the machine name to do further research.

Any ideas why I can't see my machines? What tools control how/when/ports the machine name is broadcast on?

Note: the IP address of the machines all changed since the router assigned them differently if that provides any clues.

Also done the prerequisite re-boots and so on...

Ideas anybody??

---

### Post by triwave on 2010-08-01
update : I verifed this is a router issue; I swapped an old router in that I pre-setup to have the same SSID and password so all the PCs connected immediately and all got different IP addresses but when I tried to view/connect to them using machine.local format it was no issue. I didn't change a thing on the PCs.

Does anybody know how those .local machine names are broadcast so I can debug the router? Some port or packet type must be blocked somehow. What is the service in ubuntu called that broadcasts these names? If I call Belkin to discuss problem I'd like to be specific on the service being blocked but I don't know what it's called.

Thanks

---

