---
title: "Really tricky VPN/PPTP problem - maybe you can help?"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by meowsqueak on 2010-08-18
Hello,

I've searched this sub-forum and although I see a fair number of VPN-related posts, most of which involve setting 'refuse-eap' and using MSCHAPv2 only. I've tried all these things but I am still unable to get a VPN connection from my laptop running Ubuntu 10.04 to my work VPN.

I've written about this here:
[http://superuser.com/questions/176055/unable-to-connect-to-pptp-vpn-with-ubuntu-10-04](http://superuser.com/questions/176055/unable-to-connect-to-pptp-vpn-with-ubuntu-10-04)

This might be the first time after 10 years with Linux that I've actually hit a complete and total brick wall.

To summarise, I have tried every combination of username, domain, authentication setting, the lot. None of them work. I have tried manually creating a pppd config and running it via 'pon' with debugging, only to see LCP Request timeouts.

But the oddest thing is that, on the exact same LAN, I am able to connect to the VPN flawlessly (and with default config) from:

 - Windows 7
 - Mac OSX
 - Apple iPhone
 - and even more oddly, a WinXP VM running inside Ubuntu
 - but not from Ubuntu itself.

I can only conclude that PPTP support in Ubuntu 10.04 is somehow broken and frankly I have no idea how to resolve this now. I am at a complete dead end.

I am hoping that someone out there may read this and suddenly think of a good explanation, to give me something to go on.

I have a slight hunch that this might be a two-factor problem - something about Ubuntu's PPTP implementation and something slightly odd about my LAN are combining to produce this problem. Maybe.

---

