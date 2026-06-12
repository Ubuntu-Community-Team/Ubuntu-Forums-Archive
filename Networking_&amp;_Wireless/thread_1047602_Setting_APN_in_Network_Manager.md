---
title: "Setting APN in Network Manager"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by hophead18 on 2009-01-22
I'm running Ubuntu 8.10 (Network Manager 0.7.0) and am trying to get my tethered AT&T Tilt (HTC Kaiser) phone working with Network Manager.

I have been using wvdial to connect for a while, and it works fine.  I'd like to get Network Manager working just because it SHOULD work fine, and it's a much easier thing for newbies to get up and running...

So I plug in my Tilt, and a new "Mobile Broadband" network appears in Network Manager.  I configure that network, and put in the following values:

Number:  *99***1#
Username: ISP.CINGULARGPRS.COM
Password: CINGULAR1

I try to connect, and it never connects.  The problem is, I know that for an AT&T GPRS connection, there should also be an APN setting of "isp.cingular" but I can't find anywhere appropriate to enter that in Network Manager.  Does anyone know where this should be entered?

Thanks!

---

### Post by hophead18 on 2009-01-26
Figured this one out myself, although it's a different way than I was trying to get it working.  I was trying to use the phone as a modem... instead, on the phone, I ran the Application "Internet Sharing."  (In Windows Mobile 6, it's under the Windows folder.) When I do that, then click on "Connect" on the phone, Network Manager automatically detects the network connection, and uses it.

It couldn't have been easier! :)

---

