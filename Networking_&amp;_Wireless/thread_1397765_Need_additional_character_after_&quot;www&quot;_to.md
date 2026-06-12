---
title: "Need additional character after &quot;www&quot; to access website"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by AF1HS on 2010-02-03
I have not been able to access my server ([http://www.af1hs.com](http://www.af1hs.com)) from outside my LAN using the FQDN.  I could access it only if I use my ISP's IP address.  Today I was setting up another PC and checked the Internet by going to my website but accidentally typed in an "e" after the "www" and I was able to get to my website.  Other letters (such as a, b, d, and z) also succeeded - I didn't try any others.  The server can be accessed successfully with the www prefix from the internal LAN.  Anything entered after the www fails on the LAN (as it should).

Where could I begin to troubleshoot this?  Everything at GoDaddy and zoneedit look OK.

---

### Post by suseendran.rengabashyam on 2010-02-04
Hi,

The behavior that you see of www3, wwwh etc. resolving is because of a wild card entry in your DNS records. I have looked up all the 4 of your authoritative name servers listed below:

1) ns16.zoneedit.com
2) ns17.zoneedit.com
3) ns27.domaincontrol.com
4) ns28.domaincontrol.com

I found that, zoneedit.com name servers do not have the wild card entry, whereas domaincontrol.com name servers have this wild card entry. When you have a wild card entry like "*.af1hs.com A x.x.x.x" on your DNS server, it means any prefix before .af1hs.com would resolve to the same IP. So wwwe.af1hs.com will resolve the same way as foobar.af1hs.com and [www.af1hs.com](www.af1hs.com) will do.

The DNS clients are free to use one of the 4 servers and since there is a difference between the 2 sets of DNS servers, you may find that wwwe etc. resolve only intermittently on the strength of the wild card entry. If you want this to be fixed one way or the other, you would need to contact the administrators of the relevant name servers.

The reason for [www.af1hs.com](www.af1hs.com) not working for you initially might have been due to a simple non-availability issue with the DNS server

---

### Post by AF1HS on 2010-02-04
Thank you, suseendran, for that information and for taking the time to look into it.  I will contact my DNS provider.

AF1HS

---

