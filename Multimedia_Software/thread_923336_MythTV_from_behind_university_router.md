---
title: "MythTV from behind university router"
date: 2008-09-18
forum: Multimedia Software
---

### Post by LinuxPS2 on 2008-09-18
So after what seems like an eternity of setting up my MythTV rig I finally got it working. However, I can only access my mythweb from computers on my router, I have the port-fowarding on the router set up and everything and I can get to it from other people's computers in my dorm, but cannot get access from elsewhere on campus or off... its a large university so i would assume each building has a good number of seperate switches and routers so is there a way that I can access it from either on or off campus without going and trying to get the university to forward some random port to me.

---

### Post by paulg on 2008-09-18
See [Hamachi]("www.hamachi.cc"). It's a low-config VPN server/client software that does secure tunnelling. Works through some firewalls (depending on how strict) and most routers. Best to checkout the [forums]("https://forums.hamachi.cc/") for help/questions. The forums seem pretty barren but if you search you can probably find what you need. 

Negatives:
-Binary only, closed source
-Linux software hasn't been updated in two years

Positives:
-Easy to setup (relative to other options)
-Works on Linux, Mac and Windows

An alternative would be OpenVPN but that would still require a public IP (e.g. proxy).

---

### Post by LinuxPS2 on 2008-09-18
Thanks, but I am looking for something a little more open, and free, and with lots of community support (I know its alot to ask for)... And Hamachi doesn't seem to like my computer and from the word on their forums alot of other people's too and no real answer as to how to get it to work.

Anyone know of another way, and if OpenVPN is there a guide or something to tell me how to configure it for a situation like mine?... thanks

---

### Post by paulg on 2008-09-18
See if this [thread]("https://forums.hamachi.cc/viewtopic.php?t=16039&highlight=gutsy") helps. The binary stopped working for me after gutsy upgrade but has been working since after doing the described steps. The linux install has definitely been neglected since Hamachi was purchased by LogMeIn. The forum support for Linux/OSX appears to have really dwindled considerably under the new ownership.

I hear you on the free vs. open thing. I had looked into OpenVPN at one point but configuration is a lot more involved, requires open ports and at a public IP (could use dynDNS). If you have a firewall (or router or NAT) between your residence network and wherever else you are trying to connect then you'll need a third party to negotiate the connection - which is exactly where Hamachi helps. I haven't checked in over two years though so maybe it's changed? There are howto's out there if you look (not necessarily in these forums) but you might find something in the community docs at help.ubuntu.com.

---

