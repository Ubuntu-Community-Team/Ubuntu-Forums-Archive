---
title: "Firefox works, Evolution doesn't"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by drfox on 2006-06-28
I have a Toshiba A105-S4014. I had some problems surfing yesterday (connections were slow or non-existent), and they were solved by changing my about:config setting in Firefox to network.dns.disableIPv6 to "True"

What I can't do is get my POP email through Evolution or Thunderbird. They keep timing out, and I assume there is some network setting that needs to be tweaked. 

I changed all of my wireless hosts from their strings of ip6 to ip4 (for example, I changed ff00::0 alias ip6-mcastprefix to ip4-mcastprefix) and rebooted, but that didn't help.

What's my next step?

Larry]

---

### Post by thuya on 2008-05-01
hello drfox,

I think, ur problem doesn't concerned with internet connection. Coz i'm also using toshiba satellite a104-s4014 with ubuntu hardy. In order get pop mails through evolution or thunderbird, needs to fix with ur account setting by changing secure connection to SSL encryption.And make sure ur mail sever is set to allow pop.

Thats it!

---

### Post by beaker15 on 2008-05-04
I had this problem initially aswell trying to get mail from my yahoo mail account but turned out it was coz i was putting pop.yahoo.co.uk as the pop server instead of pop.mail.yahoo.co.uk. I suppose what i'm getting at is to check and double check your settings

---

