---
title: "Jaunty sometimes breaks wireless upon switching networks"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by itkeepsrepeating on 2009-05-08
Running Jaunty, fresh dual-boot install with pre-existing Vista on an HP G50-109NR laptop. I've only seen this problem twice, but this time there may be something else causing my issues. I'll lay out each scenario.

First time:

Jaunty install was less than a week old, and working fine. I took my newly pimped laptop next door, and tried to change to the closer wireless network, although it would still see mine from where I was. Upon trying to change, it wouldn't pull an IP address. It just sat there, one green dot, one grey, swirling around, exchanging blank stares with me. "Fine, I'll just connect back to my router at home," I thought, although upon clicking the icon, NO wireless networks showed up. Interesting. Rebooted into Vista. No wireless networks detected. I fiddled a bit, then went back into Jaunty. Still no networks. I gave up, shut it down, and came back an hour later or so, and booted into Jaunty. Wireless came right up. I'm thinking wireless hardware issue.

This time:

Same install of Jaunty, although now out of beta and fully updated. I decided after much dropping of WAN IP from the Belkin router, to go back to my Linksys WRT54Gv5 with DD-WRT v24-sp1 (07/27/08) micro firmware. I reset it to defaults, and set it up initially with no security, just changed the name and upped the wireless strength to 90, all while WIRED into the LAN port of the router. All looked good, so I unplugged the cord and tried to connect wirelessly. Same as described during the first encounter of this problem, complete with the reboot into Vista and back. I shut it down and walked away for about 20 minutes this time, and can now connect to the Belkin, which is plugged into a LAN port of the Linksys, but not the Linksys. I also noticed the signal strengths in the list of networks to be a bit erratic, showing full signal sometimes, and next to none the next. This goes for most networks in the list, even showing some I haven't seen before at this location. Mind you, this is not an apartment complex, this is a neighborhood with 1/2 acre lots. I don't usually see too many networks here. 

As far as any recent changes, I installed Gyachi yesterday. All else has remained the same since conky install over two weeks ago. I don't see any of this making a difference, but I AM here asking for help ;).

Please let me know any additional info needed to troubleshoot this.

Thanks in advance....

[EDIT] For reference, the Belkin router is model F5D8233-4v3. 

Ok, now I'm noticing 'device not ready' greyed out where the networks list should be. No combination/order of hitting the wireless on/off button and unchecking/checking the "enable networking/wireless" options seem to fix this.

---

