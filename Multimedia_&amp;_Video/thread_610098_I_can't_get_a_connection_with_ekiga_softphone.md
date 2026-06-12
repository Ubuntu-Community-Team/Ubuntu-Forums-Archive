---
title: "I can't get a connection with ekiga softphone"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by hazel on 2007-11-11
I have registered with ekiga.net and I can log on and view my account. But when I try to run the echo test on [email]500@ekiga.net[/email], I get first "Registration failed - timeout" and then "Could not connect to remote host". My set-up is as follows:

Release: Dapper (but following advice from someone on the ekiga mailing list, I have upgraded ekiga itself from 2.0.1 to 2.0.9 - which has not solved the problem)

Network protocol: pppoe via eth0

ADSL router: SMC Barricade. This has a built-in firewall, configurable via an html interface, but as far as I can see, it's not doing any packet filtering or NAT. Ekiga's NAT test reports "open NAT".

Iptables firewall: flushed clean for the duration.

I attach a level 4 debug report. As far as I can see, the problem is that all operations - register, subscribe and invite - are timing out but I have no idea why.

---

### Post by YannickDefais on 2007-11-14
Hi,

Ekiga is using a private IP address.

Check in prefs if ekiga is listening on the right interface and/or turn on the STUN system.

Regards,
Yannick

---

### Post by hazel on 2007-11-16
Merci, Yannick:). That's just what I needed. I have switched ekiga to the ppp0 interface, which is the one my public IP address is assigned to. With that and STUN enabled *and* the firewall switched off, I have at last got a connection. The audio doesn't work very well but I hope that is just a matter of testing different combinations of devices until I get the right one.

Do you know of an entry-level explanation of how ekiga works? I mean something that explains how the connection is set up, what the REGISTER and INVITE operations actually do, and things like that? I always feel happier using software if I have some idea what I am doing.

---

### Post by YannickDefais on 2007-11-17
Hi,

Ekiga can use 2 standards protocols: SIP and H323

You're using SIP which is the more common.

Sip is a signalling protocol defined by the IETF: [http://www.ietf.org/rfc/rfc3261.txt](http://www.ietf.org/rfc/rfc3261.txt)

Wikipedia give some informations about it: [http://en.wikipedia.org/wiki/Session_Initiation_Protocol](http://en.wikipedia.org/wiki/Session_Initiation_Protocol)

This website is also a good source of information: [http://www.voip-info.org/wiki/view/SIP](http://www.voip-info.org/wiki/view/SIP)

We also have a wiki for Ekiga:
[http://wiki.ekiga.org/](http://wiki.ekiga.org/)

About your audio problem this can be due to limited bandwidth , try audio codecs like Speex, iLBC, GSM.

Regards,
Yannick

---

### Post by muztaba on 2008-05-22
am having same problem registration failed to connect with muztaba what can i do man??

---

