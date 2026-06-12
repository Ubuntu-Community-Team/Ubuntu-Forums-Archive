---
title: "&quot;Connection Refused&quot; on certain connections after Hardy To Lucid upgrade"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by aie93 on 2010-06-27
Hi,

I'm having some serious issues after upgrading my server from Hardy to Lucid.  Currently all up to date and have 

Linux togo 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

I can connect to certain servers, and incoming connections work fine, however some (seemingly random) connections fail with "connection refused".  These are both internal (communicating with other computers in the network) local (connecting on the loopback) and external (connection through my router).  All sockets that I'm connecting to work perfectly on my other computers within the same network.

I have currently tried disabling ufw and ipv6 and combinations of both.  Example services which it will not connect to:

NUT (running on localhost)
wTorrent to rTorrent (running on localhost)
External mail server (IMAP) (running on a jaunty box on the internet)

There is not a problem with routes because it will connect to the SMTP server which is running on the same box as the IMAP.  However, it will not connect to the POP3 IMAP or IMAPS sockets.  I even reconfigured the external mail server to make the IMAP IPv4 and the IMAPS IPv6, no change.

This is really frustrating and I have no idea what to try next.  Hope someone knows how to read this seemingly random failures and provide something meaningful.  Thanks.

---

### Post by aie93 on 2010-06-28
I figured it out! There was a problem with my bind configuration:

Apparently using a CNAME for an NS is now illegal.

Also, moblock was causing no end of hurt, after playing with the config for 30 minutes I purged it and the box sprang back to life :)

---

### Post by jre on 2010-06-28
For these moblock problems you may find some tips here:
[https://help.ubuntu.com/community/MoBlock#Frequently%20Asked%20Questions%20%28FAQ%29](https://help.ubuntu.com/community/MoBlock#Frequently%20Asked%20Questions%20%28FAQ%29)

You may select less blocklists or whitelist some IPs or ports.

---

