---
title: "Ubuntu 8.10 NetworkManager issues"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by sippyCUP on 2009-01-06
I upgraded to 8.10 from 8.04 and have been having serious networking problems. The wireless worked at my friend's house, but did not work at my home. The wired connection at my home did work, except for DNS (which I did specify in the network manager). My wireless driver is ipw2200.

So I used "sudo update-rc.d NetworkManager remove" (which I found recommended elsewhere). Honestly I'm not sure what this did, except that NetworkManager doesn't seem to start on boot now. I then added my router address to /etc/resolv.conf which made my wired connection start working (yay!).

However, I still want to use my wireless since I don't want to manually configure the wireless connection via config files every time I go somewhere. Can I reenable NetworkManager and still have my wired connection work? If so, should I use apt-get to remove/install NetworkManager?

Thanks for your time,
Eric

---

