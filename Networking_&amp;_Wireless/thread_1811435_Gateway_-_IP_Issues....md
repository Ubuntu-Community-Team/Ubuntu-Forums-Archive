---
title: "Gateway - IP Issues..."
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by Zerocool Djx on 2011-07-24
I got a non-traditional network system going on and I need some help configuring it all. Here is what it is

                                                                                                       
Internet -- (Via USB)--> Computer -- (Via Ethernet)--> Wireless router ----- PS3


Anyway, the wireless router has a problem, and I am not even sure this is the proper terminology for anything I am speaking of and I am only guessing, but hopefully someone can help. I am assuming there is a problem with an IP address or Gateway issue, because every time I connect the wireless router to the Ethernet I get my internet from the USB hub disconnected. I was hoping someone could explain how ip's and gateways work, maybe a little picture  for visualization? That would help a lot in figuring this out.

---

### Post by jmoorse on 2011-07-26
What is the IP address of the router?

Please post the output of the following when internet access is working:

```

route -n
ifconfig -a

```

And please do the same for when the router is connected and internet access is broken

Thanks

---

### Post by newbie-user on 2011-07-27
I would suggest redoing your network: 
                            
Internet -- wireless router -- PC & PS3

Your PC prefers to be connected to the network via ethernet, not USB, so if your PC's network suddenly gets activity, it switches over.  I've seen modems that allow USB connections, although I don't really understand why.

If you want to keep your network setup, then you'd probably have to look into allowing forwarding through your PC.  Also, make sure that you plug your PC into the WAN port of the router.

---

