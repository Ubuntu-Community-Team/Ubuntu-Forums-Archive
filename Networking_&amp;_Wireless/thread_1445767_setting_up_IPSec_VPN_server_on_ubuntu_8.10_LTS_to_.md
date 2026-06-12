---
title: "setting up IPSec VPN server on ubuntu 8.10 LTS to work with iPhone clients. NON-L2TP!"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by ryanrhee90 on 2010-04-03
Hi,

I've searched through google, and all I can find are instructions on how to set up a L2TP/IPSec VPN that works with macs and iPhones.

I'm NOT trying to set up an L2TP/IPSec VPN. I'm trying to set up a pure-ipsec vpn.

The iPhone IPSec client is a built-in cisco client, I believe.

I'm staying away from L2TP and PPTP because I need multicast packets to go through.

Thanks in advance!

-R

*edit: wow, i just noticed that the title says "8.10 LTS". Oops! I obviously mean "8.04 LTS". Gah, the lack of sleep got to me.

---

### Post by ryanrhee90 on 2010-04-06
bump.

---

### Post by 3rods on 2010-06-09
This is also relevant to my interests... 

Bump.

---

### Post by ryanrhee90 on 2010-06-10
I have since upgraded to 10.04 LTS from 8.04 LTS, but I still want to do this. bump! >.<

---

### Post by tacom6 on 2010-06-13
> **ryanrhee90 said:**
> I have since upgraded to 10.04 LTS from 8.04 LTS, but I still want to do this. bump! >.<

I could also use a howto in this area. Sorry I don't have the answers for ya. :confused:

Hey will OpenVPN by any chance satisfy your multicast needs?

---

### Post by ryanrhee90 on 2010-06-13
> **tacom6 said:**
> I could also use a howto in this area. Sorry I don't have the answers for ya. :confused:

Hey will OpenVPN by any chance satisfy your multicast needs?

Yes -- and no.

OpenVPN does infact let multicast go through, but the iPhone has a very glitchy implementation of it.

The iPhone's implementation of openVPN is only possible with a jailbroken iPhone. And on top of that, somebody had to write a TAP/TUN interface emulator. It's far from stable. :/

Since my main goal is to have the VPN work with with an iPhone client, openVPN isn't an option.

Thanks for the suggestion though!
-R

---

### Post by lcoltrane on 2010-08-09
This may be what you're looking for:

[INDENT][https://help.ubuntu.com/community/IPSecHowTo]("https://help.ubuntu.com/community/IPSecHowTo")[/INDENT]

---

