---
title: "Ubuntu 13.04 - Little to no wireless connectivity"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by ultrapiggy on 2013-05-10
I would post this in the wireless/networking forum, but I'm really new to Ubuntu still and I was overwhelmed when I tried to find an answer there. All I know is that I'm on my Windows partition at the moment, and I have full wireless strength. When I switch to Ubuntu, I have literally no signal strength at all. It keeps connecting and then disconnecting over and over again, which shouldn't be happening because the connection is CLEARLY strong enough to reach the wireless adapter.

I want to be able to use Ubuntu as my primary OS on this laptop, but it just won't connect to about 75% of the connections my Windows side picks up flawlessly.

I'm not entirely sure what my wireless adapter's make is, but I know it's an "N" card (It says "Ralink Technology, Corp." in the info when I look at it in the device manager in Windows. Also on the list is "Realtek PCIe GBE Family Controller"... Is there a driver or something that I can install to fix the issues they're having in Ubuntu?

---

### Post by madjr on 2013-05-10
Hi , I think this could be of use:

[http://askubuntu.com/questions/236119/how-do-i-troubleshoot-problems-with-my-wireless-connection](http://askubuntu.com/questions/236119/how-do-i-troubleshoot-problems-with-my-wireless-connection)

or

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by QIII on 2013-05-10
[I]Moved to **&#8203;Netwo**[B]rking and Wireless


[/B][/I]Hello!

Even if you didn't find the answer you were looking for, this is still the best place to wait and let the answer come to you!  :)

Best wishes!

---

### Post by ultrapiggy on 2013-05-13
Alright, according to everything, my wireless card's brand and model were identified, and I believe it's running the correct kernel driver.

I checked nm-tool, and it says I have at least 45-56 strength for all connections, meaning for something as simple as Google Docs, this should not be an issue. However, it appears to never connect, or say it's connected and never load anything.

---

