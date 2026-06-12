---
title: "Wireless signal but no internet from my Netgear"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by Zippidy on 2009-03-23
I am running Ibex on an Eee 901 using adamm's package, and my router is a Netgear WGT624 v3 (the white one). Everything was gravy before we moved, but now that I've got everything hooked back up I can't get online. My signal is 100%, but every website loads with a "Failed to Connect" error.
I know my wireless works because I have been able to log on at Starbucks.

---

### Post by roshanmohan on 2009-03-23
I am not sure, but could you please check you dns settings. Wrong/no entries could cause you problems.

---

### Post by Zippidy on 2009-03-23
I'm not sure how to do that. Is that something in Ubuntu that I do, or something with the router?

---

### Post by roshanmohan on 2009-03-23
Can you please give me your  ping [www.google.com](www.google.com) output.

On the terminal(Applications>Accessories>Terminal) run "ping www.google.com"

If i can see the output, i can tell you if its a dns issue. Otherwise we can try something else.

---

### Post by Zippidy on 2009-03-23
```
ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
```

---

### Post by roshanmohan on 2009-03-23
This seems to be a wrong dns server entry. 

If you know your router ip address, you can add it to the DNS server entry.
You can do that like this
System > Administration > Network > DNS.

---

### Post by Zippidy on 2009-03-23
I have
System > Administration > Network Tools
I can't find a DNS entry

---

### Post by jelle_ on 2009-03-23
i am not sure it is an dns-problem. can you try the following code and tell us the output

ping 74.125.79.103

---

### Post by Zippidy on 2009-03-23
(hen I'm doing the pings, I am of course removing my ethernet cable, then plugging it back in to post)

```
ping 74.125.79.103
PING 74.125.79.103 (74.125.79.103) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable
From 192.168.1.1 icmp_seq=5 Destination Host Unreachable
From 192.168.1.1 icmp_seq=6 Destination Host Unreachable
From 192.168.1.1 icmp_seq=7 Destination Host Unreachable
From 192.168.1.1 icmp_seq=8 Destination Host Unreachable
^C
--- 74.125.79.103 ping statistics ---
8 packets transmitted, 0 received, +8 errors, 100% packet loss, time 7031ms

```

---

### Post by clancymf on 2009-03-23
I think the problem is between the router and the internet.  This should have nothing to do with your pc, its wireless, ubuntu.

You should unplug the modem and router.  Let them reset and plug them back in and give it a try. If that doesnt work, try plugging your pc directly into the modem, test.. Basically we need to know the point at which the connection is broken.

Do you own your modem? I bought a modem and had Comcast cable.  To get the internet, I had to call and then give them the information about my modem and have them sync with me before getting on the internet.

---

### Post by Zippidy on 2009-03-23
+1 for being an idiot. When I went to unplug the modem and router, I saw that the router was never connected to the modem.

Things are working now. +1 for Ubuntu.

---

### Post by clancymf on 2009-03-23
> **Zippidy said:**
> +1 for being an idiot. When I went to unplug the modem and router, I saw that the router was never connected to the modem.

Things are working now. +1 for Ubuntu.

LOL... Well im glad things are working now.  :D

---

### Post by roshanmohan on 2009-03-24
Lol.:)

---

### Post by adventurejones on 2009-05-05
That is not good because I am having the same problem and everything is connected. I had wireless connection before with my DHCP and DNS settings automatic. Now I can see the network but cannot connect. If I manually enter my IP, Gateway, and DNS I can connect to other computers in my network but I can't get to the internet. The other computers can get to the internet. 

I'll try a few suggestions offered in here like restarting everything. Thanks for the help. 

Adventurejones

---

### Post by adventurejones on 2009-05-06
ok, I restarted my router and everything worked fine.

---

