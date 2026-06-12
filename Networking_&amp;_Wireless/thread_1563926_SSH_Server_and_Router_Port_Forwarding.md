---
title: "SSH Server and Router Port Forwarding"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by ThatBum on 2010-08-29
Heya,

I'm trying to get my SSH server I set up on my home box  working from behind a router. A 2wire 2700HG-B gateway, in fact. Now, I  know my server is working fine, because I can get into it via loopback,  anywhere inside the LAN from another machine, OR if I go into the  router's config and enable DMZ for the machine. However, I don't like  having DMZ on all the time because of the kludge-ness of it, and the  security issue of the complete absence of a hardware firewall.

If  I try to port forward and access it from outside the LAN using the  external IP (or my DynDNS, because it's dynamic), it just times out. I  have a nonstandard port (45) for the listen port of the server, to keep  away hack attempts if I were using the standard 22. I used [this]("http://www.yougetsignal.com/tools/open-ports/")  to see if the port was open, and it said it was. But, I tried the trick  of telnetting the IP with that port, and it also timed out, instead of  printing stuff about OpenSSH.

Attached is a screenie of my  router's firewall page, so you all can look at it and see if I'm an  idiot and doing it wrong. You might notice uTorrent there, it's because  this machine is a dual-boot with 7, and the router doesn't differentiate  the OS's. Also the SSH @ 46 port is for the Windows side, with  freeSSHd. I changed the port on that one so the client I have can  distinguish them, so it can run a reachability test.

What am I doing wrong here?

---

### Post by dmizer on 2010-08-29
Have you tried connecting to it with a computer that is not on your LAN? Most retail routers are not capable of loopback, so if you are on your own LAN and attempt to ssh to your external IP, it will probably not work.

---

### Post by ThatBum on 2010-08-29
> **dmizer said:**
> Have you tried connecting to it with a computer that is not on your LAN? Most retail routers are not capable of loopback, so if you are on your own LAN and attempt to ssh to your external IP, it will probably not work.

Wow, that actually seems to have worked. I tried it from my phone's 3G network and it seems to be operating. Although, I would still like to be able to SSH from within my own network, because my 3G is slow and not unlimited (I like doing SSH-tunneled VNC). Is there any way around this without using DMZ?

---

### Post by dmizer on 2010-08-29
> **ThatBum said:**
> Wow, that actually seems to have worked. I tried it from my phone's 3G network and it seems to be operating. Although, I would still like to be able to SSH from within my own network, because my 3G is slow and not unlimited (I like doing SSH-tunneled VNC). Is there any way around this without using DMZ?

While you are within your own LAN, you can just ssh to the machine's LAN IP address instead. Or, you can give your SSH server's LAN hostname. Usually the hostname is the second half of your terminal prompt. Here's an example from my own network:

My SSH server's terminal prompt:
```
dmizer@[COLOR="Red"]tokkyu[/COLOR]:~$
```
This is how I connect to the SSH server:
```
dmizer@japan:~$ ssh [COLOR="Red"]tokkyu[/COLOR]
Last login: Sun Aug 22 19:58:16 2010 from 10.2.0.118
dmizer@tokkyu:~$
```

---

### Post by dmizer on 2010-08-29
> **ThatBum said:**
> I  have a nonstandard port (45) for the listen port of the server, to keep  away hack attempts if I were using the standard 22.
This will not keep the hackers away. You will still need to harden your SSH server. If you allow password access, you will probably get hacked unless you have a REALLY difficult password (even then you could get hacked). There are ways around this, but really the best way to secure your server is to completely disable password authentication and use encrypted shared keys instead.

Finally, you should not be using port 45 as many scanners scan all ports from 0 to 1023 because these are the most commonly used ports.

Here's a start for you:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by ThatBum on 2010-08-29
> **dmizer said:**
> While you are within your own LAN, you can just ssh to the machine's LAN IP address instead. Or, you can give your SSH server's LAN hostname. Usually the hostname is the second half of your terminal prompt.

Thank you! It's so obvious now! Although this means I have to make another profile in PuTTY/iSSH. Meh.

Thanks for putting up with my n00bness.

EDIT: Oh yes, I did disable password access, and only use a 2048-bit key with it. I'll remember to change the port though.

---

### Post by BkkBonanza on 2010-08-29
You can also map the domain name in your hosts file so that it resolves to the local IP instead. This intercepts the DNS lookup and forces it local. This way you can use the same name whether local or outside, which helps for profiles and scripting. 

The downside is that you would have to comment the line out when you are accessing from outside your LAN, eg. on a laptop when away from home. 

Another way is to add the name as a static name entry in your router if it supports that (such as in dnsmasq on Linksys routers). This way it is automatically overrided.

---

### Post by ThatBum on 2010-08-29
> **BkkBonaza said:**
> You can also map the domain name in your hosts file so that it resolves to the local IP instead. This intercepts the DNS lookup and forces it local. This way you can use the same name whether local or outside, which helps for profiles and scripting. 

The downside is that you would have to comment the line out when you are accessing from outside your LAN, eg. on a laptop when away from home. 

Another way is to add the name as a static name entry in your router if it supports that (such as in dnsmasq on Linksys routers). This way it is automatically overrided.

No thanks, I would never remember to comment the line out every time I left home. I have enough trouble remembering to unplug my fingerprint reader so my machine doesn't ask me to scan my finger...when the reader is miles away!

---

### Post by BkkBonanza on 2010-08-30
Unlike having your fingerprint reader miles away, the /etc/hosts file is always right there and easy to alter in a few seconds.

For your Putty profile it's no big deal having two, but if you ever set up scripts then having to maintain two versions is more hassle.

---

### Post by dmizer on 2010-08-30
> **BkkBonaza said:**
> Unlike having your fingerprint reader miles away, the /etc/hosts file is always right there and easy to alter in a few seconds.

For your Putty profile it's no big deal having two, but if you ever set up scripts then having to maintain two versions is more hassle.
If it becomes a problem, the real solution here is to have a local DNS server to handle the correct name forwarding on the LAN.

---

