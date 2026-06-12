---
title: "Hamachi and Windows LAN Gaming"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by Sazex on 2013-01-03
Hi, I'm sorry if this is in the wrong section but I'm not too sure where else to put this.

Anyways, I'm using Ubuntu 12.10 and running Hamachi (the VPN client) version 2.1.0.86.

I've made a server on Hamachi to make it seem as if me and my friend (who is running windows 7) are on the same LAN. We are both playing a game called Age of Mythology (or at least trying to), but we cannot connect to each other's games. For some reason in the LAN room, he can see me hosting (but can't connect) but I can never see him hosting. 

Please note that I also recently switched to Ubuntu on my new computer, and before, I had windows 7, and I had the same problem, except before I could see him hosting a LAN game as well. Before in Windows 7, we both had to change the metrics of hamachi to 1, and use only IPv4 connectivity before we could even see each other's games (I could see his back then). 

Now I believe I've changed my hamachi metrics to 0, with using this command ...
sudo ifmetric ham0 0

After I used that command he was able to see my game (but couldn't connect to it) 

Also note that we've told the game (Age of Mythology) to connect with our hamachi IP address, by creating a .cfg file.
We've even tried other games, to see if it was just Age of Mythology. We tried Torchlight II, but we can't even see each other hosting in that game. This has led me to believe that there is probably something wrong with our connection, but I really can't pinpoint the problem. Can anyone help me?

Again, I apologize if this is in the wrong forum, or even on the wrong website, but I really don't know where else to post this at.

---

