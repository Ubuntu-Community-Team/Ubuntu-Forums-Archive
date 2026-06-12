---
title: "Ubuntu network bug?"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by jessede on 2012-11-20
I try to start my ubuntu machine as a dhcp server on a network with some computers and only a switch. When i start ubuntu connected to that hub (no other connections) it starts without full network capabilities and says the following at boot:

waiting for network configuration" and "waiting up to 60 more seconds"  and then "booting system without full network configuration"

How can i setup my ubuntu so that i don't need a router/inernet connection?
Becaus if i start my ubuntu server connected to my normal home network it boots just fine.

Is this a bug???

---

### Post by cwsnyder on 2012-11-20
If you have no other router on the system, I believe your server will essentially have to BE the router, either for the internal network or between networks, with a full IP stack and be configured with the required  server configuration files.

---

### Post by dmac1blah on 2012-11-23
With only a switch the config your using has nothing to route traffic the swich will work if its going from the modem to the swich to the computer but thats not really gonna to do much you could add a router to handle this task or use a computer as the router. I found this link [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) I have not tried it yet but it is on my list of to-do projects
 
> **jessede said:**
> I try to start my ubuntu machine as a dhcp server on a network with some computers and only a switch. When i start ubuntu connected to that hub (no other connections) it starts without full network capabilities and says the following at boot:
 
waiting for network configuration" and "waiting up to 60 more seconds" and then "booting system without full network configuration"
 
How can i setup my ubuntu so that i don't need a router/inernet connection?
Becaus if i start my ubuntu server connected to my normal home network it boots just fine.
 
Is this a bug???

---

