---
title: "Sending traffic through firewall over http port?"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by mikeym on 2009-04-13
Hi,

I'm wondering if it's possible to send all my traffic past my uni's firewall over a allowed port?

Specifically I'm wanting to listen to the radio using mplayer for listening to realmedia off the bbc, but I'm sure I'll come across other things that I'd like to do but can't because they seem to have blocked every port bar http.

I have at my disposal a linux laptop which I'd like to use in uni and a desktop at home which I can ssh into (although I've not tried this from in uni yet). 

Cheers.

---

### Post by mikeym on 2009-04-16
Hmmm. Seems that ssh doesn't want to work from uni either looks like the port I want to use is not allowed.


Any sugessions?

---

### Post by puppywhacker on 2009-04-16
you can try to run your ssh server on port 80 if it is only allowing port 80 by firewall rules. If they are using a proxy you can try to set it in the application your using to access the radiostation

---

### Post by superprash2003 on 2009-04-16
well it would be tough from a uni.. you wont have permission to open ports and stuff..(usually)

---

### Post by mikeym on 2009-04-18
Yes. I still don't - after years of mucking about with my home networks, firwalls and ports - really understand how they work. 

I view the ports as a slot on each computer which an application can monitor and that there's only suppost to be one application monitoring that slot. A firewall would then put a brick in each slot it wants to protect preventing monitoring or traffic on that slot.

My university seems to only have the slot for http traffic open (with one missing brick).

In my ideal situation I'd like to use something on my computer - setting or program such as a proxy - to take the ports that my application normally runs on and pipes them through the missing brick in my uni's firewall. It would then have to open up and access the required port on the server.

---

### Post by puppywhacker on 2009-04-18
your brick analogy sounds about right. The thing is on top of IP a few different transport layer protocols can run. UDP and TCP each have their own ports. HTTP default port TCP/80. SSH defaults to TCP/22. You can deviate and use port 80 for SSH as well. A pure firewall doesn't look at what it is actually transporting, so you can run any type of traffic. A proxy will look at the payload, so it has to be HTTP. You can still encapsulate SSH traffic inside HTTP. It's a trick to bypass obstacles, so don't expect this to be foolproof. But basically you're looking for something like this:

[http://www.mtu.net/~engstrom/ssh-proxy.php](http://www.mtu.net/~engstrom/ssh-proxy.php)

---

### Post by doas777 on 2009-04-18
most modern routers are capable of protocol analysis on port 80 and will notice that the data is not associated with a http connection. if the administrator checks for http compliance or cyphertext, then it won't work. 
this may be why your ssh is failing to establish a connection, or it may be a firewall problem on your home's ISP. 

on the homedesktop, if you go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and put in your ssh port, is it able to access the service? that test would eliminate problems on the receiving end.

---

### Post by lensman3 on 2009-04-18
Did they shutdown 443, the encrypted 80 port?    443 is used to check on bank statements, sending credit card info, etc.

I don't think a router can analyze packets if they are encrypted. BUT generally 80 port packets aren't encrypted.

For the amount of money you pay for school, go and tell them to turn everything back on.  (I'm speaking as a parent here)!

---

### Post by mikeym on 2009-04-19
Well I haven't been in over easter to try it out but I've set up my home computer to accept ssh connections on a commonly used port. I'm hoping that they don't have any sophisticated packet analysis. It's all abit overboard to listen to digital radio while I study but there you go.

What do you expect from a department that has set up some of the computers to check your password every time you open a new internet site!

---

