---
title: "Slow network performance belived problem."
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by Profusion on 2006-06-27
Ok guys I believe I know the reason for the slow internet / network performance some people ahve be finding.

But before I continue I will just bring up what was thought to be the problems before.

- IPv6
- Firefox not disabling IPv6
- Ubuntu design
- all other thoughts from people


I have noticed at home I had no issues with my network, but when I went to work I had the slow lagging issues some where experiencing on this forum.

My conclusion of the problem!!

Duplexing! 

At work after trying to fix other issues not regarding to this problem I noticed when I had changed my private MPLS speed to Full duplexing, my web administration to my page was instand with no lag on ubunu! then I confirmed it by puting it back to 100 Half duplex and instatly it lagged and was slow bringing up the page!


I believe that somewhere down the network chain to your isp if all there routers are not set on the same full duplex this causes some problem. 

It seems Half duplex messes with the packets.

Can anyone confirm this and is there a possible fix that can be done in ubuntu to confirm this?

---

### Post by Hufi on 2006-06-28
How have You turned off Halfduplex and turn on Fullduplex?

---

