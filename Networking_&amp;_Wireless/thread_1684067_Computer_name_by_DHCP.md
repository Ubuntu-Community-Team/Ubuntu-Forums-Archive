---
title: "Computer name by DHCP ?"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by kapetr on 2011-02-08
Hello,

I have a beginner question.

How to find IP address of computers in LAN served by simple DHCPd (in ADSL modem - without IP reservations/MAC address).

So is in Ubuntu something like on-fly name resolution in Windows ?
Without running DNS server with some kind of DynDNS ?

e.g.

My comp has hostname "GoGo" but I get random IP address from DHCP.

**??** How can other PC on same LAN resolve my changing IP address **??**

--kapetr

---

### Post by gordintoronto on 2011-02-08
Good question!

If I log onto my router, I can see what MAC addresses are used, and how much traffic they have had since the router was booted. Not too useful.

---

### Post by Iowan on 2011-02-08
On my system, I disabled the DSL modem's DHCP server and installed DNSMasq on another machine I use as a server. It allows me to ping (DHCP-addressed) machines by name... It also allows static leases (reserved addresses) for a web server and network printer.

... but DNSMasq kinda falls under the "running DNS server" description you mentioned...

---

### Post by Cheesehead on 2011-02-08
Using the router's device table to identify machines is preferable. It's fast and usually accurate. That's why I use a router I can SSH into.
Or if you have a machine with static IP, both DHCP machines can send current IP to it - thought that's a bit of a hack.
But if you have neither, then you are stuck...if you really need to know IPs (which is a bit strange).

Samba and Bonjour are designed to avoid this problem by broadcasting their machine identities, and listening for other broadcasts. Is there a reason you cannot use these tools that are designed for your apparent situation?

---

### Post by kapetr on 2011-02-09
Thanks for answers.

Running permanently some server on my mini LAN is no solution for me.

As *_Cheesehead_* wrote:

The "Bonjour" could solve my problem - I have forgotten this possibility because I newer try it before.  It is the "Link-local" choice in NM-applet, isn't it ?

But what do you mean with Samba solution? How to use it in this manner?

BTW - I have to say, that I don't know much about Windows -but is it not so, that in Windows is DHCP with random addresses working without problems together with "on-fly" name resolution ? Maybe is this that what you mean with "Samba solution". But could you tell me more, how to do it ?


thanks

--kapetr

---

### Post by kapetr on 2011-02-18
nobody knows or nobody needs ?

---

