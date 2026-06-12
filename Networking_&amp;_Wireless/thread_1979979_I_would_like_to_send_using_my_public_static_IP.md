---
title: "I would like to send using my public static IP"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by shumifan50 on 2012-05-14
I have 5 public static IPs on BT Infinity fibre network.
I have a Cisco PIX501 firewall with V 6.3
I am running Ubuntu 11.10

I receive incoming traffic fine on my public IP 217.x.x.x and through my domain url  [www.xxx.com](www.xxx.com) through any of my public IPs, so incoming nat is correct.

However, when I go to a site that shows me my IP address(e.g. [http://www.whatismyip.com/](http://www.whatismyip.com/)) it shows an IP of 81.x.x.x, not 217.x.x.x as I would like it to be.

I suspect that I am missing some configuration somewhere, but I am a bit of a networking novice and I am not even sure where the misconfiguration would be, Cisco or Ubuntu, although I have a feeling that I need to tell Ubuntu which IP to use. My suspicion is based on the fact that I actually have 5 public static IPs, so the send has to be done to the correct IP.

Any help on this greatly appreciated.

---

### Post by shumifan50 on 2012-05-15
OK. I finally sussed it out.
First thing to note is that there is a difference between NAT and PAT. Read the Cisco docs tolearn about this.

The PIX firewalls can only support 1 Global PAT address as I understand it(proper IOS can support many). It can however support many global addresses, but all outgoing traffic will be patted to a specific global address or round robin assigned an address from the global pool defined.

So to get all outgoing traffic to use a specific:
global  (outside) 1 x.x.x.x
All messages originating from the inside (like an http request) will look like it originated from x.x.x.x
If you specify more than one IP in the above statement, PAT is disabled on the pix501.

If you specify
global (outside) 1 interface
All messages originating from inside will look like it came from an IP address allocatd from a pool of IP addresses owned by the ISP - none of which will match your static IP.

Please excuse terminology errors, I am a network newbie LOL.

---

