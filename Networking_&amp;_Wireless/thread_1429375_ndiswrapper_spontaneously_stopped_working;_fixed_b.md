---
title: "ndiswrapper spontaneously stopped working; fixed by disabling wep?"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by knurledflanges on 2010-03-14
Greetings all,
I've got a couple different wireless cards that use the RT2500 chipset (I think - they both show up as RaLink RT2500). I recently started using wireless only in my desktop machine. I had issues with card 1 where it would connect and seem to function, but throughput was extremely limited for some reason (was not the "rate=1Mbps" issue). I installed ndiswrapper and set it up with rt2500.inf and it worked fine, full speed, but had the problem that after some hours of use it would stop working and nothing would get it to work again except restarting. Normally just restarting would work, but once it didn't, and I got it to work by deleting the entry for my wireless router in Network Connections and letting it detect it anew.

Today it stopped working and absolutely nothing I could think to do seemed to help. Numerous restarts, turning off networking and turning it back on, removing and re-adding the ndiswrapper driver, etc. It would see the network's ssid name and display a strong signal, but when I tried to connect it would take an abnormally long time to come up with the WEP prompt, and then it would display the "working" icon for about a minute, and then come back up with WEP prompt, over and over (which is the same thing it's done in the past when ndiswrapper seemed to stop working). I troubleshooted this for hours, which isn't saying much because I didn't have an internet connection to help me out :P. I tried removing ndiswrapper and going back to the original driver temporarily, but apparently I don't know how to do it - I took away the rt2500 entry, cleared the blacklist, re-ran "sudo update-initramfs -k all -u" (whose function I'm not entirely clear on) and restarted, and all I got was no wireless capability at all - lspci still showed the card, but no wireless options showed up in the network applet. At this point I tried physically switching cards, blacklisted the linux drivers and installed the ndiswrapper one again, and still had the same results - it saw the network but wouldn't connect. Getting frustrated, I tried turning off WEP on my router, and it works great all of a sudden. What's going on here and how should I fix it? (I don't really want to run without security long term, and yes I know WEP is pretty blah.)

If it matters, the router is an Actiontec dsl modem/router combo that I seem to have running in kind of a self-configuring wireless switch mode. It's connected to a master router on the property I live on that's connected to a cable connection. It's kind of a weird setup.

---

### Post by knurledflanges on 2010-03-15
Bump.
Also, I've discovered that disconnects also happen with no security settings on, only connecting again when the computer is restarted, and that it doesn't connect at all when WPA is on either.
Is there a command I can run that would do the same thing here as restarting completely? Like a command that restarts everything to do with networking?

---

