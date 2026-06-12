---
title: "No internet on wireless connection, but access through Ethernet"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by Veteropinguis on 2010-07-20
I'm troubleshooting a network problem for an acquaintance. He's running Lucid Netbook Edition on a Thinkpad X41.

A few days ago, according to him, he suddenly couldn't get online. He was at someone else's house and using their connection with no problems, then got back to his home network and couldn't connect.

He can connect to his network, and if the Ethernet cable is plugged in he can get online. Two other computers running the same OS are having no problems with the wifi- I'm using it right now, actually. My computer and the Thinkpad both had the OS installed from the same flash drive, yet my computer has no problems with the network.

I suppose it's possible that the wireless card randomly half-killed itself, but that seems unlikely.

I don't really know anything about networking; does anyone have any suggestions?

EDIT: I've been working through the wireless troubleshooting section of the Ubuntu Wiki. I can ping google by IP and by common name. His drivers are fine. He just can't get online through wifi.

---

### Post by irv on 2010-07-20
Have him plug the cable in get online, then go to System> Administration> Hardware Drivers. If he has a 3rd party driver loaded, selected and remove it. Then try to re-install it again. Disconnect the cable and see if it finds the network on the wireless. Something to try.
I don't know if this will help seeing it find a wireless at another location. And it doesn't sound like a router problem because you can get on via wireless. This seems strange.

---

### Post by Veteropinguis on 2010-07-20
Irv: He doesn't have any third-party drivers installed. I followed all the steps on the Wireless Troubleshooting page and determined that his drivers are fine.

(I forgot to mention, everything has already been power-cycled and reset in various orders.)

Well, this just seemed to have worked itself out. A  breaker flipped right after I'd messed around with a bunch of stuff (disabled IPv6 in Firefox and a few other things) so I'm not sure what fixed the problem.

Thanks to everyone who read this. I guess the Ubuntu Fairies fixed this problem for me :rolleyes:

---

