---
title: "Ubuntu-to-XP network question."
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by DarthAceris on 2011-08-30
I have a wireless network at home, which I use to access the internet with my laptop running Ubuntu 11.04, and I was wondering if it would be possible to connect my desktop (XP Professional) to my laptop via an ethernet cable, and access the internet through the laptop.

---

### Post by astroboy78 on 2011-08-30
What you want to do is enable Internet Connection Sharing.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

from the article:
> 
GUI Method via Network Manager (Ubuntu 9.10 and up)

In order to share an Internet connection, the computer that will do the sharing must have two network cards or ports. This assumes that you are using at least one Ethernet port and that it is identified as "eth0". eth0 will be the port that other computers will connect to you on.

When you are logged in:

- Go to "System" on your top bar
- Navigate to "Preferences" and select "Network Connections"
- When that window opens, select "Auto eth0" and press "Edit" (This assumes that you are connected to the internet on some other port, for ex. wlan0 using wireless)
- A new window will open. Navigate to the tab titled "IPv4 Settings" and change the Method to "Shared to other computers". - - After restarting the computer you should now be able to plug in any computer into your other Ethernet port or share through your wireless card.

Note: To clarify the above example here is an example configuration that will work -

- You are already connected to the internet using your wireless on port wlan0
- The ethernet port eth0 is connected to the PC that needs to share your internet connection (or you could wire eth0 to a router for multiple machines)


There you go!

---

