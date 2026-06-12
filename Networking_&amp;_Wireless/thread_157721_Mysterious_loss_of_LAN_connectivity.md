---
title: "Mysterious loss of LAN connectivity"
date: 2006-04-09
forum: Networking &amp; Wireless
---

### Post by grayhorse on 2006-04-09
Hi all

I lost LAN connectivity on my home PC yesterday. It had been working fine on Saturday. I'd been trying to compile a neat little routine that slowed down an MP3 file (yatm-0.4.2) and after seeming to download a new library everytime I turned around (thank goodness for Debian packages!!) I ended up with about 40Mb or so of upgrades I needed from the desktop automatic upgrade notifier. I just went and did it (foolish, I know) and when I started the machine the next day, eth0 couldn't connect to the ADSL modem. 

I can connect with the Hoary liveCD, and probably unsurprisingly I also had no trouble with the DeMuDi liveCD.

I've run through the steps in the sticky-noted troubleshooting guide, and the hardware is fine. It's an on-board sis900 setup. lspci & lsmod return the same codes and modules whether I boot from the HDD or a liveCD. 

In fact, I can't find any difference between the various settings between the liveCD session and my normal session, except two: 
[LIST]
[*]On the Network Tools menu, there is no provision to configure eth0; and 
[*]on starting, eth0 is down. This can be rectified with "sudo ifconfig eth0 up" but you still can't ping the ADSL modem
[/LIST]

Can anyone shed some light on what's going on here? Or at least, give me some guidance as to where else to look. I suspect I might have loaded a diferent kernel to what I was supposed to, but I didn't notice what was going on on Saturday. I'm afraid I was more interested in using yatm to slow down an astonishing, but **very** fast version of "the Ashplant" to hear what the flautist is doing....

I realise if you fiddle with or improve something often enough, it will break, but I don't understand how fiddling with Speex and wsWidget libraries will break the ethernet connection! Hopefully I can rectify this without having to re-install AGAIN ](*,)

---

### Post by waster on 2006-04-10
are you using dhcp? did you accidentally install resolvconf? (If so, just purge it)
does /etc/network interfaces have a line "auto eth0"?

---

### Post by grayhorse on 2006-04-18
[QUOTE=waster]are you using dhcp? did you accidentally install resolvconf? (If so, just purge it)
does /etc/network interfaces have a line "auto eth0"?[/QUOTE]

Yes - I am using DHCP. 
No - purging rexolvconf didn't help me. 
Yes - /etc/network/interfaces had a line "auto eth0"

I ended up re-installing in frustration, which turned out to be not too bad as it forced me to learn how to back-up %HOME and other significant areas.....

However, I've since discovered since then that it is not entirely unheard of for someone to suddenly have all sorts of problems due to an inadvertant kernel upgrade..... 

I guess the lesson here is "keep a firm eye on apt-get and don't try to do everything at once"

---

