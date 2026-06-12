---
title: "Lose wireless connection when downloading torrents"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by kevin82485 on 2012-03-23
I have this issue that only occurs when I try to download torrents. I lose my wireless connection within minutes of starting a torrent download.  Once connection is lost, I try to reconnect but it will not reconnect.  Over and over again I try to connect it to my router, but the only way to regain connection is to restart my computer.  But if I start downloading a torrent again, I inevitably will lose my wireless connection, and have to go through the whole process again.

I know that it is not necessarily an issue with my router, because I am able to connect wirelessly with another computer at the same time.  My router is a Belkin N600DB.  My computer is a custom build with an Asus P5B Deluxe/Wifi-AP motherboard.  In Windows the built in wireless card uses the Realtek RTL8187L driver.  I'm running Ubuntu 11.10 64 bit.

---

### Post by kevin82485 on 2012-03-29
After 5 days of nothing this needs a bump.

---

### Post by SeijiSensei on 2012-03-29
This is a common problem with consumer routers.  Torrents create a lot of connections between you and all the peers.  Many consumer routers don't have enough memory to keep track of all those connections.

The best solution is to *limit the number of connections* your torrent client makes.  Note that this has nothing to do with limiting bandwidth.  You're limiting the number of peers you can connect with at any time.

Start small with a figure like 10.  If your router doesn't fall over, you can try increasing the number.

---

