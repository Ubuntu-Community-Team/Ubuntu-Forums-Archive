---
title: "VPN For Ubuntu 8.10 - What Is A Good Solution?"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-04-24
I'd like to setup a VPN between my home computer which runs Ubuntu 8.10 and my Windows XP computer at the office.  What is the best software/method/etc...of vpn in Linux?

Thanks!

---

### Post by SabreWolfy on 2009-04-24
In my experience, PPTP VPN is broken in Intrepid and Jaunty (Network Manager 0.7). It works perfectly for me in Hardy (Network Manager 0.6.6). Searches on these forums and on LaunchPad will give you plenty to read about this. I'd also like to know what else I can use for VPN access, because at the moment I'm forced to continue using Hardy just for VPN access.

For what it's worth, I found a solution to PPTP VPN in Jaunty (and presumably Intrepid too). Link [here]("http://ubuntuforums.org/showthread.php?t=1136020").

---

### Post by The Cog on 2009-04-24
I recommend OpenVPN. We have used it in a number of situations and it is rock solid. Performance and reliability are both excellent. And you only need ot arrange forwarding of one UDP port from the internet to the server, which is generally quite easy. It works through NAT of course.

---

