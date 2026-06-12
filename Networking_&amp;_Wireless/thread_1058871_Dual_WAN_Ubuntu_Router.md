---
title: "Dual WAN Ubuntu Router"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by NoReflex on 2009-02-03
Hello!

I'm thinking of setting up a Ubuntu Server box as a router. 
I have about 10 machines on my LAN which host various things (http, ftp and other servers) and I'm connected to two different ISPs.
From what I've figured I need a machine with 3 NICs and a Gigabit Switch (I already have this one). Now on the Ubuntu box I would have one card for each ISP and one for my LAN.
The problem I'm afraid I will encounter is that the servers (http,ftp etc.) won't be accessible from both ISPs because the machines that host the servers have only one gateway. 
I would need to forward the same ports (80,21) to the same machine. I suppose that my Ubuntu box would simply forward the requests from both outside interfaces (from each ISP) to the correct machines inside but the responses from the machines would go out in the Internet through only one interface (which is the default gateway on the machine from the LAN). 
If I were to use SNAT...would the packets follow the right path (my guess is yes but I haven't used it before so I'm not sure) Would I need two local interfaces for this (one for each WAN connection)? . Anyway using SNAT would mean the servers would think that all the connections are coming from the same IP (the local IP of my Ubuntu Box which is also the default gateway) - so this would render useless any logs or "visits" page.
How do DualWan routers achieve this?

Thanks!

Best wishes,
NoReflex

---

### Post by jbarbieri on 2009-04-23
Hey there.

I am actually running a dual WAN ubuntu server right now. It is working awesome.

The reason why I went for a homebuilt solution over the others out there (pfsense, mono/smooth wall) was for the customization. Since it is a true linux box, and not someone else's hacked up version, I could do whatever I want with it.

Even though you are using SNAT, your client PCs won't see the connections coming from the ubuntu box, rather, it will see them as from the real internet. I proved this by doing a tcpdump on a box inside the LAN, and initiating a connection from the Internet, and watched the srcip, and it was the public IP of the host initiating the source.

If you want me to, I can try and share what I did to get this box up and running....I made scripts for everything, so it should be fairly simple. After I set it up the first time, I was able to get dual WAN working within 5 minutes after a fresh install.

Let me know!

--John

---

### Post by Xoldie on 2009-06-23
I have found this thread looking for help on setting up an ubuntu box as dual WAN router.
Dear jbarbieri, will you please tell how you accomplished said task.
Thanks in advance,

---

### Post by jbarbieri on 2009-10-19
Xoldie:


[http://ubuntuforums.org/showthread.php?p=8129464](http://ubuntuforums.org/showthread.php?p=8129464)

---

