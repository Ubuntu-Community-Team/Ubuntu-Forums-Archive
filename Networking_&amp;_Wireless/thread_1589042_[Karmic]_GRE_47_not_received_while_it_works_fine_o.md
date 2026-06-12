---
title: "[Karmic] GRE 47 not received while it works fine on xp?"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Remko on 2010-10-05
Dear all,

This has been bugging me for quite a long time. I need to have a pptp connection to my university. I have tried to locate the error, but this has been a real trouble.

A little bit of history:
My girlfriend had a laptop with M$ vista on it with a working PPTP connection. I had a laptop with Ubuntu, with which I couldn't get the PPTP working.

When my laptop crashed, I bought a new one on which I run a dual boot XP SP3 and Ubuntu. I also own a desktop (Dual M$ Win 7 / Ubuntu standard Karmic) and my girfriend also upgraded to Win 7.

Currently, the XP version is the only one on which I can get a connection. Both Ubuntu and the Win 7's give me a GRE proc 47 not received error. I know our router (a DAVOLINK DV2020) is notorious for not sending through GRE proc 47, but this either shouldn't be the case or it shouldn't matter, since I can make a perfect connection through the XP OS.

This is quite a handicap, since we both study at the university for which we require working VPN PPTP connections.

Settings:
Gateway: vpn-eur-pptp.eur.nl
Username: [EMAIL="123456ab@eur.nl"]123456ab@eur.nl[/EMAIL]
Password: password
Authentication: MSCHAP / MSCHAPv2
MPPE: Force 128 bit
No stateful encryption
No BSD data compression
No Deflate data compression
No TCP Header compression
No PPP Echo Packets

I would be very grateful when someone could help me tackle this problem.

Yours,


Remko

---

### Post by SeijiSensei on 2010-10-06
Post the results of the command "sudo iptables -L -nv".  If you've got a firewall up in Ubuntu, you'll need to add a rule for GRE traffic.  I would have thought Win7's firewall would be configured to support GRE and MS PPTP by default, though.

---

### Post by Remko on 2011-02-17
> **SeijiSensei said:**
> Post the results of the command "sudo iptables -L -nv".  If you've got a firewall up in Ubuntu, you'll need to add a rule for GRE traffic.  I would have thought Win7's firewall would be configured to support GRE and MS PPTP by default, though.

Whoops, I just went on using the xp machine.. here the results of my iptables:

```
sudo iptables -L -nv
[sudo] password for remko: 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
```

Would be great if you could figure this out!

---

### Post by Remko on 2011-02-19
I searched a bit on the internet; I added debug dump to /etc/ppp/ppp-options; it gave me the error in the attachment.

Shortly, it complains about a 'fatal decompression error'. Any thoughts about this?

---

