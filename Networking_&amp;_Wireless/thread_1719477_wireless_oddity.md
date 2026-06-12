---
title: "wireless oddity"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by acecase on 2011-04-01
Sorry for the lame title, but I couldn't think of a way to summarize the problem.

I have a MSI Wind (U100) with a Realtek RTL8187SE wireless chipset.
Kernel = 2.6.35-28-generic
Ubuntu 10.10

I am able to connect to my wireless-b access point using the gnome NetworkManager Applet 0.8.1, and everything works fine. However, I do not run X most of the time. When I try to connect manually I cannot get the card to associate.

My access point uses no encryption and no mac filtering or anything of that nature. Following is what I am doing (one command per line)
[starting with all interfaces except for lo down]
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid aceAir2 key off
     (I have also tried setting the ap XX:XX:XX:XX:XX:XX)
sudo dhclient wlan0

Of course dhcp fails as the adapter is not associated.


The only thing that I have noticed (dmesg) that is happening differently when the applet configures my connection is that the adapter is set to use B rates, which I cannot figure out how to set manually. (rate 11 ?)

I would like to find a way to log exactly what the applet does, and/or see more than I am seeing in /var/log/messages when the connection is successfully configured via the applet.

Any help/suggestions are appreciated.

---

