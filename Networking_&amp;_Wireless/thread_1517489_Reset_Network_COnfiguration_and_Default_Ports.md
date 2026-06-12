---
title: "Reset Network COnfiguration and Default Ports?"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by soasertsus on 2010-06-25
The other day I was using BitTornado and it was running so slow it was almost unholy. After some research I found out that if the yellow light was on it means I couldn't receive any incoming connections and had to open some ports on the firewall. 

That, my friends, is not the problem. I tried to manually open up the bittorrent port and did some other things that I can't quite remember but eventually I accidentally killed all bittorrent functionality on my laptop. 

Is there any way I can reset my network and ports back to the default settings or am I utterly screwed? I'd really prefer not to have to reinstall my whole OS just to fix my bittorrent or worse, have to download on Vista *shudders*. I'd rather go back to my uber-slow bittorrent than none at all.

I've tried everything I can think of, even the godlike might of Google couldn't get me out of this one. Now I am forced to bother you, all because I wanted to see a damn sci-fi film from Switzerland (Cargo[2009]).

As an afterthought, I'd really like to see Stargate Atlantis too :p

---

### Post by Iowan on 2010-06-25
Not really my forte, but your thread looked lonely...
Is the firewall on your laptop? 
You can check **iptables -L** to see what rules exist.
(That's not a "reset", but might help debug...)

---

### Post by soasertsus on 2010-06-25
Thanks, I ran

```
dylan@dylan-laptop:~$ iptables -L

```The return was:

```
iptables v1.4.4: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
```So I tried sudo

```
dylan@dylan-laptop:~$ sudo iptables -L

```And input my password. Now the return was this monster that I can't even begin to understand:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
INPUT_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
OUTPUT_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 

Chain ALLOW_MATCH (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain BLOCK_MATCH (2 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain INPUT_QUEUE (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 253

Chain OUTPUT_QUEUE (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
RETURN     udp  --  anywhere             anywhere            udp dpt:domain 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 254

```Any ideas?

---

