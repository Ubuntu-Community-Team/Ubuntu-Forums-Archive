---
title: "A home server / router"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by Q-collective on 2013-06-17
Hey all,


Due to all the news around Prism an old idea of mine rekindled. I have a long running interest in Freenet, I2P, TOR and other privacy related technologies. However, I currently only have a laptop and running these services on that is doable but impractical.


So, I want to have a mini-server that, preferably, doubles as a router which can run the following services:
- Freenet
- I2P
- Tor
- YaCy
- OwnCloud
- Bitcoin

- ... Possibly more


I was looking into the HP Proliant series, but they're not really built with a lot of ethernet ports or wifi capability and, as such, don't double well as a router.


So, I'm opening this thread looking for some suggestions

---

### Post by Cheesehead on 2013-06-17
I have done something similar. There are a couple problems:
1) It eats a lot of power 24/7, even when doing essentially nothing.
2) It's a huge single-point-of-failure for your network. For example, if the OS crashes due to a problem with a complex service, network connectivity to all clients is lost (hard to look up a solution, then!) It is *much* harder to experiment and learn (and make mistakes) if a mistake kills your whole network.

My current setup has three machines: 
- A separate modem/router (and a spare on hand) for network reliability.
- A low-power always-on server for some tasks: Torrent server, media server, IRC monitor, Gameserver, etc.
- A high-power wake-on-LAN disk-intensive, RAID server for backups, media storage, etc.

---

### Post by Lars Noodén on 2013-06-18
I'd go with something lower power if it's going to be on most of the time.  Most of the tasks you list don't demand fancy hardware, except for the Bitcoin.  About the Bitcoin, it's way too late to be jumping on that one.  All the easily mined blocks have long since been taken.  You're starting to look at rooms full of servers to compete for the remaining blocks.  So a space heater will be a more efficient use of power, especially an infrared one. ;)

How many ethernet ports do you need on your home server/router?  Some hardware you might look at could be from Liantec or Soekris or MicroTik.  Look for comparisons and you should find other hardware.

---

### Post by Q-collective on 2013-06-18
> **Cheesehead said:**
> I have done something similar. There are a couple problems: 1) It eats a lot of power 24/7, even when doing essentially nothing. 2) It's a huge single-point-of-failure for your network. For example, if the OS crashes due to a problem with a complex service, network connectivity to all clients is lost (hard to look up a solution, then!) It is *much* harder to experiment and learn (and make mistakes) if a mistake kills your whole network. These are actually good points.   > My current setup has three machines:  - A separate modem/router (and a spare on hand) for network reliability. - A low-power always-on server for some tasks: Torrent server, media server, IRC monitor, Gameserver, etc. - A high-power wake-on-LAN disk-intensive, RAID server for backups, media storage, etc. I don't think that my current needs justify the third device, but yeah, pulling the router function out of that wishlist might be the best route.  > **Lars Noodén said:**
> I'd go with something lower power if it's going to be on most of the time.  Do you have any suggestions? As said, I was looking into the Proliant microserver, but there are probably better options.  > About the Bitcoin, it's way too late to be jumping on that one.  All the easily mined blocks have long since been taken.  You're starting to look at rooms full of servers to compete for the remaining blocks.  It's not for mining, just to keep in sync with the network really.  > Some hardware you might look at could be from Liantec or Soekris or MicroTik.  Look for comparisons and you should find other hardware. Thanks for the suggestions, but I think I'll go with the suggestion of leaving the router seperate.

---

