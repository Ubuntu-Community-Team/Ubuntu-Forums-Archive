---
title: "PPTP connection failing with LCP timeout"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by ORBAT on 2010-03-06
I'm using Kubuntu 9.10, my pppd version is 2.4.5 and pptp is 1.7.2

I'm trying to connect to the iPredator VPN service, but I keep running into problems with LCP. I've tried using knetworkmanager, nm-applet, kvpnc and plain old text-based configuration to no avail.

Here's a snippet of pppd's output:

```
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf7dccf4b> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf7dccf4b> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf7dccf4b> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf7dccf4b> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x9dc87535> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
```

To me, it looks like the ConfAcks aren't getting through.

Here's what the routing table looks like when it's trying to connect:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
93.182.132.2    192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

Does this look correct?

(I've got "defaultroute" in my /etc/ppp/peers/ipred config file.)

Any ideas what could be causing this? Could it even be my router? It claims to support PPTP, but considering it claims a lot of other things which aren't true, I wouldn't be surprised if it was the culprit.

---

### Post by ORBAT on 2010-03-08
Bump. Anybody?

---

### Post by ORBAT on 2010-03-08
I'd just like to note that I solved the problem. After some poking around I came to the conclusion that my WLAN box was most likely not handling GRE (protocol 47) correctly (despite claiming to support it...). I bought a new router and voilà: PPTP works like a charm even from the GUI.

The lesson of the day is: if you're having trouble with PPTP and you see pppd sending LCP ConfAcks and ConfReqs and receiving only ConfReqs, you probably have a problem with your router setup.

---

### Post by redcharlie on 2010-06-27
I thought I might share my similar experience.  Fortunately I only needed to change one setting on my router, not replace it!

So, my story begins when upgraded my router to an Asus RT-N16 running Tomato 1.27  (I wanted the a dd-wrt compatible wireless router with a Gigabit LAN, and the RT-N16 seemed like a good fit). 

My wife complained that the VPN no longer worked.

I realized that GRE replies from the server at her workplace were not making it thru to her machine, reference:
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_timeout](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_timeout)

I confirmed this by disconnecting the router from the cable-modem and connecting a computer directly to the cable modem, whereupon the VPN worked fine.

Googling around I found this post:
[http://www.dslreports.com/forum/r23752777-PPTP-VPN-Issue-Tomato-127-SBS-2008](http://www.dslreports.com/forum/r23752777-PPTP-VPN-Issue-Tomato-127-SBS-2008)

But no replies :'(

By enabling logging of all inbound events on the Tomato interface, I saw the same behavior (dropping of inbound GRE packets)

Finally I realized that I had checked the GRE/PPTP box under Tracking/NAT helpers (in Tomato WebGUI, go to Advanced->Conntrack/Netfilter, then scroll down to Tracking/NAT helpers) but the **default** state was **unchecked**.

So I unchecked it, and VPN started working again!

Since Tomato documentation is thin, and since it seems counter-intuitive to need to uncheck the GRE/PPTP helper option to actually get PPTP to work, I thought I might share this with others.

---

### Post by acidblue on 2010-11-07
So let me get this straight, You have to **uncheck** GREP/PPTP in order
to get tomato to pass the protocol?
That seems backwards to me

{EDIT}\Ok I tried uchecking and tomato still drops some GREP packets, actually most of them.
Could some one recommend some firmmware that will let GREP pass thru.
My router is a WRT54GL v1.1

---

