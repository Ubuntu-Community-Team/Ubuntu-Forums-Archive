---
title: "OpenVPN traffic oddity"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by Greyed on 2009-06-13
I am tunneling all of my traffic through an OpenVPN connection to a Debian machine.  For months it had been working fine.  However a few days ago the connection changed and I cannot figure out what happened.  The symptom is that the traffic, as measured by KDE 4.3 beta's system monitor applet is showing nearly identical outbound traffic for all inbound traffic.  Normally the outbound traffic is far smaller since most of the time all it is doing is ACKing what's coming in.  As a result my speeds have dropped from 50Kps to under half that.  I know I hadn't made any changes to my network setup nor to OpenVPN on either side of the connection so I am at a loss as to how to begin to track down why the outbound traffic spiked so horribly.

---

### Post by Greyed on 2009-06-13
Yeah, nevermind.  The panel applet is borked.  Opening up the full system monitor shows proper stats.  The mouse over on the applet shows proper stats.  Not sure why the sites I normally visit feel slower ever since the applet was borked but the outbound traffic on a recent download was 2k for a 50k inbound stream.  The applet showed it to be more like 48k out for 50k in.  :(

---

