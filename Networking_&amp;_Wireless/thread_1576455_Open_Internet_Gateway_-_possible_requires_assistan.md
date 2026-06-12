---
title: "Open Internet Gateway - possible? requires assistance."
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by oucii on 2010-09-17
Kind of untraditional task.

1. Is it possible to connect or hop through with say "client" machine, to a host machine through the internet and then use the host's machines internet connection. Much like a VPN connection BUT without using any kind of VPN or additional data encapsulation, encryption as to avoid any unnecessary millisecond delays. Have already tried OpenVPN and PPTPD and both are unsatisfactory, instead would like the host (Ubuntu server) to act somewhat as a internet hop gateway, like a relay so that traffic is mostly untethered. Security is not needed at all, probably only to deny all addresses, apart from exceptions (client machine).

So
```

client -ADSL ---->(internet)----> eth1--host
             <----         <---- &#708; |
                                 | |
                                 | &#709;
                              (internet)
```

In case it might help, there are 2 Internet connections available to the host machine, with 2 public IP addresses. (2 NIC's as-well) 

2. Also would it be possible to use a router for example on 1 of them? The outgoing interface eth2 for example?

Something like this?
```

client-ADSL---->(internet)---->eth1--host--eth2-*R*->(internet)
           <----          <----                  <---  
```

Is this a clear enough explanation? Again, tried OpenVPN and PPTPD and delays were unaccepted, with or without compression. It might also probably involve client side configuration or route table alteration.

Reason why ask here, is because not a networking expert or advanced user, perhaps it's impossible to use dual WAN's simultaneously (don't know) perhaps someone can help, or point towards a good iptables/ipchains/linux networking/TCP-IP guide.

---

### Post by BkkBonanza on 2010-09-17
What you describe is a "**proxy**". You can run a proxy on host for either just HTTP (web browser traffic), or by running a SOCKS proxy you can proxy any kind of traffic, eg. mail, torrents, skype etc.

SSH makes an excellent SOCKS proxy but you don't want encryption (though I find SSH to be very fast for normal browsing it may be a bottleneck on high bandwidth uses).

So there's lots of proxy servers to choose from. The most well known is "**squid**".

---

### Post by oucii on 2010-09-18
Ok thank you for the info, will now go read up on SOCKS proxies and squid.

---

### Post by oucii on 2010-09-18
After reading manual pages, how to's and articles on squid, I get the idea it was geared as a web (HTTP/FTP/etc) proxy / transparent proxy first, then perhaps evolved into more. Probably didn't explain clearly. The purpose of this proxy/gateway would be to redirect ALL traffic, UDP/TCP in its original unaltered form. Why? Client's ISP has uber delays when trying to work on Bloomberg for example, or play fps games (which require UDP), in both cases a delay of additional 50ms is critical. 

Typically "client" ping to "server x" would be 300ms, the hosts (gateway/proxy) ping to "server x" would be 30ms, and the client to host would be only 20ms. So by using the host as a gateway/tunnel for ALL types of traffic, we avoid the undesirable 300ms delay. (We avoid the laggy hops on the client's ISP) And we want to avoid encryption + encapsulation as not to add any additional lag. There is no alternative ISP available on client, their delays are considered normal as stated by their technical support.

So far have not found any info about squid being able to do that.

---

### Post by BkkBonanza on 2010-09-18
I already told you that in my first post. If you want "all traffic" you would need a SOCKS proxy. SOCKS 5 in particular since it supports UDP. Squid can do SOCKS5 but I believe it has to be custom compiled for that. Probably you would be better with one of the many other SOCKS5 specific proxies around. 

I don't think the proxy should add more than a few mS onto latency, on a fast machine anyway. I've never measured it when I use SSH for this. Even in the Ubuntu repos there are a few SOCKS proxies. To use a SOCKS proxy your program has to support it.

---

### Post by oucii on 2010-09-18
Ok thanks again, am reading and searching for a SOCKS5 proxy options.

---

