---
title: "pppd gigawords radius support"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Muppet on 2010-01-28
Hi,

I'm trying to find a solution (patch) for pppd with will allow the use of gigawords to be sent to an AAA server (in this specific case, freeradius).

Currently i'm hitting the 4.2GB limit, which then resets to 0 because pppd cannot handle 64-bit ints. Developement seems a bit slow for pppd, so was wondering if anyone know of a patch or knows of a way to patch pppd to accomodate Acct-Input-Gigawords and Acct-Output-Gigawords support?

The only patch i have seen is a gentoo one: [http://bugs.gentoo.org/attachment.cgi?id=102981](http://bugs.gentoo.org/attachment.cgi?id=102981)

However, since this isn't an area I am familiar with, I have no idea of its efficacy with Ubuntu. If someone could have a look at that patch and tell me if it would work (or knows of a better one), I would be extremely grateful.

---

### Post by Muppet on 2010-01-29
Friendly bump to top.

---

### Post by Farton on 2011-11-02
Patch [http://www.nuclearcat.com/files/gigawords-v3.patch](http://www.nuclearcat.com/files/gigawords-v3.patch)
Works on ppp-2.4.5, Ubuntu 10.04.3 amd64. I have deb file if any need it, ask.

---

### Post by chrroessner on 2012-05-16
Hi,

even this thread is some days old; I also tried to patch pppd-2.4.5. I added the patch to debian/patches and rebuilt the package. The built-log shows that the patch applied perfectly.

I also added the Gigawords attributes to /etc/radiusclient/dictionary and restarted rp-pppoe (pppoe-server). Then I did DVD downloads and watched the SQL table radacct. Unfortunately the counters acctinputoctets and acctoutputoctets still reset to zero.

I also use freeradius 2.

Am I missing something? Can somebody give me a hint how to get the Gigawords-counters to work?

Thanks in advance

---

