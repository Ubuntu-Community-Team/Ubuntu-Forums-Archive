---
title: "Everything seems to be in order, yet no Internet!"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by MystMan1102 on 2010-03-04
I recently downloaded Linux Ubuntu 9.10 (I think that was the number), and I hardwired dierctly into the modem in an attempt to get Internet. The log tells me that "eth0: link is ready," the ifconfig shows completely legit info, and the lspci tells me that the drivers are fine. Yet when I go to the Internet, it won't allow me to go anywhere whatsoever.
 
I am currently on Quest, and it's possibe I need to install the modem using a disc (which I have, but only for Windows XP-7), however I had the exact same problem when using a Time Warner modem. (we recently switched ISPs).
 
I have also connected my brother's computer (XP OS) to the modem with the exact same result, as far as I can tell. I tried the aforementioned disc in that computer, and it told me that the modem could not be found. Can anyone help me out?

---

### Post by t93ha07 on 2010-03-04
Do you have an ip address?  (ifconfig eth0)

Do you need to go through a proxy server?  

Can you ping anything including yourself?

---

### Post by Iowan on 2010-03-04
Is that the same machine you used before? Some modems need to be power-cycled before they will "talk to" a new client (MAC).

---

### Post by MystMan1102 on 2010-03-04
The modem is not the same, no.
 
Yes I have an IP address, I don't know about the proxy, and I don't even know what pinging is, honestly. I do know I'm sending and recieving packets currently, I don't know if that means anything. Also, the log tells me that I'm attaching to "resyslog.com" and "resyslog"ing the system.
 
How can I tell about the proxy?

---

### Post by MystMan1102 on 2010-03-06
> can you ping anything including yourself?

yes i can ping myself, but i cannot ping websites; however, i can ping the website's ip addresses

---

### Post by Iowan on 2010-03-07
I'm also on Qwest. What IP address do you have - hopefully not an **avahi** (ZeroConf) address (169.254.X.X). My modem has a configuration page - I don't remember the default IP address (192.168.1.1?). Which modem are you using?

---

### Post by MystMan1102 on 2010-03-07
First off, sorry about the above post. I had my mother write that because I didn't have Internet access at the time, but she did.
 
> **Iowan said:**
> I'm also on Qwest. What IP address do you have - hopefully not an **avahi** (ZeroConf) address (169.254.X.X). My modem has a configuration page - I don't remember the default IP address (192.168.1.1?). Which modem are you using?
 
I have a default IP (gateway?) of 192.168.0.1. I've already gone inside the modem and set it up, and it tells me I'm connected to the ISP. And when I look around and compare it to the ifconfig in the gnome terminal, they match up.

---

### Post by MystMan1102 on 2010-03-11
Ok, I've been screwing around some more and I found that if I input google's IP address into the URL bar I can get to google. However, I cannot do the same for any other sites (as far as I can tell) and I cannot follow any links.

---

### Post by sdpiowa on 2010-03-12
I found that manually adding DNS addresses fixed the problem for me after switching.

Try these (for OpenDNS):
208.67.222.222
208.67.220.220

---

### Post by MystMan1102 on 2010-03-14
Thank you very much for the help. The DNS server solved the problem.

---

### Post by Iowan on 2010-03-14
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :D
Glad you found success. *Ordinarily*, your machine should get nameserver addresses from DHCP - but use what works!

---

