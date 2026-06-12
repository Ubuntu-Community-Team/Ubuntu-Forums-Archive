---
title: "SLOW web in 12.10, flys in windows 7 :-("
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by rochford77 on 2013-01-03
so i was having this problem where i was pulling less then 2mbps in ubuntu, but over 14mbps (down) in windows 7 on my acer aspire timelineX. i tried several fixes, none worked. when i plugged directly into my router i would get the full 20mbps i pay for. so i took the security off my router and made the network open, and then just made the router not broadcast its name...not the best idea, but now i can pull 12mbps in ubuntu. 

whats strange, is it DOES NOT feel like 12mg. I am constantly getting "this web page can  not be displayed" and videos just sit there and buffer all day. ive tried both firefox and chrome, and both are dog slow. my ping is 75ms, down is around 12mbps, and up is about 3. i should be able to watch a video on youtube. i dont have this issue in windows. where should i start in diagnosing this problem? ive already check for additional drivers and none were found...

---

### Post by tgalati4 on 2013-01-03
Check your log files in /var/log and also ~/.xession-errors.  Post anything that might pertain to network speed.

Sounds like a wireless module problem.  What wireless card do you have?

---

