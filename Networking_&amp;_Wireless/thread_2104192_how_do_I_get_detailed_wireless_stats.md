---
title: "how do I get detailed wireless stats?"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2013-01-12
I have a bcm43xx chipset and would like to get some detailed stats like connection sig/noise, AP association info, and if I am connecting at wireless b,g, or n.

iwconfig gives me a s/n ratio, but how do I tell if i am connecting at b/g/ or n?

I'm fine with command line, but is there a gui that can give me these sort of stats in real time?

I guess I am looking for a wifi analyzer of sorts that can tell me if I am connected to b/g/n, but I don't want to have to use promisc mode.
-J

---

### Post by Cheesehead on 2013-01-12
Take a look at the 'iwlist' command. It provides that information.

Some hardware simply does not report the information.
And sometimes the system does not keep the information in the format you seek.

For example, the command [FONT="Courier New"]iwlist wlan0 rate[/FONT] will tell you the actual connection rate, which is much more useful to the system than the b/g/n protocol in use.

---

