---
title: "Sharing internet through Ethernet port. (Ubuntu 11.04)"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by ryandushane on 2011-06-21
Hello!
I am running Ubuntu 11.04 and i am curious to if there is a way to share my established wireless connection through my Ethernet port..... I know it was possible in Windows by going to adapters and bridging the wireless, and Ethernet adapters. Any ideas on how to make this work in Ubuntu? 
Thanks
-Ryan (Ubuntu newbby)

---

### Post by Beacon11 on 2011-06-22
This information is from [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) . Turning it into a more Unity-friendly guide off the top of my head might be wrong, but I'll give it a go.

You need to open you Network Connections. If I remember correctly, you can do that by right clicking on the network applet by your clock and selecting View Network Connections or something similar. When you get there, you should see a couple of connections, one of which is your wireless connection (e.g. wlan0). Find your ethernet connection (e.g. eth0) and click it, then click Edit. In the new window, select the IPv4 tab and change the Method to "Shared to Other Computers." After that's done, you should be able to reboot and connect with your second machine.

---

