---
title: "Connection bridging trouble"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Visti on 2009-02-12
Hi guys,
I just yesterday switched to an Ubuntu derivative and I have spent today bridging my connection from my wlan card to my xbox through a an ethernet cable. Now, I've done this easily before with Windows using Internet Connection Sharing with no trouble.

Anyway, I used this guide right here:
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

And it works fine. Sort of. The xbox comes up with a message that my NAT is set at "moderate" and not "open" security, which may be a problem if I want to play online. I looked it up and it seemed I had to open a few ports in the router, which I did, but that didn't help. 

But can that really be the problem when it worked fine under Windows without fooling with the router at all? Then it has to be the only changed component: the OS, right? 

Can anybody advice at something I could try looking at? Like at all, because I'm really at a loss. The router I use is a SMC WBR14-G2, if that matters at all.

---

### Post by mttman on 2009-02-12
Hello,

A possibility could be the firewall on the computer. I'm not sure but i think Ubuntu comes with a default setting of iptables (a kernel level firewall). I highly recommend you DO NOT try to edit iptables on your own. it is complex and you could serious screw up your networking under Linux. 

My suggestion is to try and find a graphical firewall managing program and open the ports on the computer your using as an intermediate between your xbox and the internet.

I believe your right in thinking that it is not a problem with the router which was working under windows, as long as nothing on the router was changed when you switched to linux.

I hope this helps.

<Mttman>

---

### Post by Visti on 2009-02-12
> **mttman said:**
> Hello,

A possibility could be the firewall on the computer. I'm not sure but i think Ubuntu comes with a default setting of iptables (a kernel level firewall). I highly recommend you DO NOT try to edit iptables on your own. it is complex and you could serious screw up your networking under Linux. 

My suggestion is to try and find a graphical firewall managing program and open the ports on the computer your using as an intermediate between your xbox and the internet.

I believe your right in thinking that it is not a problem with the router which was working under windows, as long as nothing on the router was changed when you switched to linux.

I hope this helps.

<Mttman>

Ah, I had no idea there was a kernel level basic firewall. That mightbe exactly what this is. I'll look for a frontend and report back! Thanks!

---

