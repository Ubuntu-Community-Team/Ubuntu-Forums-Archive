---
title: "no wifi connection"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by jrev on 2009-10-09
I have configured the Wifi connection of my broadband Freebox modem.

My Asus netbook on windows XP immediately detected the network and put an icon in the systray.

I clicked right on it and chose the menu <show the wireless networks>
Then I chose the configured connection of the Freebox
then <Connect> and I typed the access key. No problem 

I have another Asus 701 4G on Ubuntu netbook remix 2.0

How do I start the connection procedure ?
How do I know if the network has been detected ?

Thanks for your guidance :P

---

### Post by t0mppa on 2009-10-09
You click on the Network Manager icon on the top panel and choose which wireless network to connect to. See the screen shot for details (the desktop is not from UNR, but should help you find the correct icon to click). If it's your first time connecting, the system will ask you for the necessary details.

If you can't see any networks there, then open up a terminal (under Accessories), run the command **lshw -C network** and post back with the output to check if everything is ok with your wireless interface and its drivers.

---

### Post by jrev on 2009-10-10
Thanks for your reply.
I eventually found my way to the wifi connection :P

---

