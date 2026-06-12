---
title: "[SOLVED] How do I check what connections get blocked/timed out to/from my machine?"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Ng Oon-Ee on 2008-12-31
Hi all,

A bit of background, the virtualization software Virtualbox allows me to run a copy of windows XP virtualized, with OpenGL 3D Acceleration. Which I want to use, in this case, for gaming, specifically Warcraft III: The Frozen Throne over a 'pseudo-lan' provided by this software called Garena. In case anyone is suggesting Wine, I have WC3 running there and use it when I'm in an actual LAN, unfortunately Garena does not yet work properly on that, hence my virtualized 3D-accelerated Windows XP for online gaming on Garena specifically.

So, I'm having what I believe are network-related problems. Specifically, it seems that the network connections being created by XP (I've just turned the firewall off initially, for testing) for the game are fine, as I can login to the game client, chat, etc., but once I start the game (where direct p2p connections are made to all 9 other players before starting the game), I can chat for a max of 3-5 seconds before the connection drops out.

I'm figuring this is a networking issue, either at the virtualization level or on my machine level (Ubuntu's networking). The virtualization level I'll try to find info about elsewhere, but in this forum I'd like to ask about Ubuntu's networking.

So, I'm running this ASUS laptop with Wireless connected to my home's router. Router is properly setup, I can play no problem from dual-booted Windows. Am using Network Manager, the default. I have firestarter, and have tried stopping it (does this open all ports?) as well as allowing all the forms of communication that are needed by the game (basically a few ports), as well as all miscellenous communication that seems to be blocked while the game is running (if its on my blocked list, I just enable it for testing, i can turn off the permissions later).

Anyway, does anyone have any idea how I can tell what packets or what type of communication is lagging/dropping/blocked? Some type of monitoring software where I can actually understand the output (etherape was nice and graphical. And totally gibberish to me).

Thanks in advance.

---

### Post by Schok on 2009-01-03
bump. need more dota/garena related solutions. if it works ill probably wont be dual booting anymore

---

### Post by Ng Oon-Ee on 2009-01-03
I solved this actually, without resorting to network sniffing.

After reading the wiki on bridging a LAN connection (and using parprouted to bridge a WIFI connection) I tried it out, but couldn't get it to work.

What DID work, however, was changing my Network connection in VirtualBox to 'Host Interface' and selecting my wireless card. I'm pretty sure you could do the same with a LAN card.

For further discussion, please bring to [this thread]("http://ubuntuforums.org/showthread.php?p=6484782"), to consolidate information. This is, for me, solved.

---

