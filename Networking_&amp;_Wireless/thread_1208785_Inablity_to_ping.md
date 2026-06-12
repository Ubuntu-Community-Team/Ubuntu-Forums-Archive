---
title: "Inablity to ping"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by Philo1 on 2009-07-09
I'll use Microsoft for my example. I realize that may be a bad word but bare with me. I am unable to send packets via TCP/IP (manually) to this address. Why? The only resort I can arrive at is that their going from public to private. What do you think? As well it seems that if you sit on their page for x amount of time, the ip will change. I know this may sound crazy but I can't arrive at a logical point. 

For example:

I hit 207.46.19.254 - Host: [www.baytest2.microsoft.com](www.baytest2.microsoft.com)
I hit 65.55.21.250  - Host: Unknown

I'll not continue on as I have many other examples. My intentions are true as I just can't figure this one out. I've ran into other websites in the past but this is the most recent. I have the same result whether using Linux based or Win based OS. They all utilize TCP/IP so it's just kind of strange.

---

### Post by amingv on 2009-07-09
I'm not sure I understand what you want to achieve, but if memory serves, I believe microsoft's network does not allow to be pinged (to prevent DoS attacks, I have heard).

```
$ ping www.microsoft.com -c3
PING lb1.www.ms.akadns.net (207.46.192.254) 56(84) bytes of data.

--- lb1.www.ms.akadns.net ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2005ms
```

Considering the possibility I misunderstood you, please explain what it is that is not working.

---

### Post by Philo1 on 2009-07-09
Thanks for the reply. I was originally messing with this at work. You idea concerning DoS attacks is very plausible. However, I am now at home and have reproduced the issue.

Not working: the ability to ping/send packets via cmd/terminal/network manager

Win:

>>ping [www.microsoft.com](www.microsoft.com)
Pinging lb1.[www.ms.akadns.net](www.ms.akadns.net) [65.55.21.250] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out. 

Ubuntu:

$ ping [www.microsoft.com](www.microsoft.com)
PING lb1.[www.ms.akadns.net](www.ms.akadns.net) (65.55.12.249) 56(84) bytes of data.
From xx.xx.8.62 icmp_seq=161 Packet filtered
From xx.xx.8.62 icmp_seq=200 Packet filtered
From xx.xx.8.62 icmp_seq=230 Packet filtered

I'm simply perplexed and was attempting to find out why it's so. (Pure Curiosity) Flat out, why can I not ping them, that's the simplicity of the issue. Cisco is the same way, however I wanted to find out exactly why it works as it does.

Thanks,
Philo1

---

### Post by Dr Small on 2009-07-09
Their firewall does not respond to ping requests, maybe?

---

