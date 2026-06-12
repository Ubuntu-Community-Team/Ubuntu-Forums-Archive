---
title: "Cannot find the wireless network icon"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by SamppaM on 2009-12-14
I have installed Ubuntu 9.10 and everything seems to work perfectly excluding the wireless network. Well, actually the wireless network is working as well, but I just simply cannot login to the network, because the icon of the wireless network is missing from the panel.

I have already tried to add the notification area to the panel, but it seems that only a separator is added. I assume that the icon should be visible even if there are no networks available. When boot the laptop, there is a clear message "Wireless networks available" on the desktop, but the icon is still missing.

What have I missed? If it matters, I am using Lenovo G550 laptop.

---

### Post by uncaspi on 2009-12-14
Did you right click in the upper panel and selected add and then network applet?

---

### Post by SamppaM on 2009-12-14
I right click the upper panel and I select "Add to Panel ...". However, I cannot find anything related to the network. There is quite a lot of stuff from a clock to a system monitor, but nothing related to the network. Perhaps I have not installed all the required packages?

---

### Post by uncaspi on 2009-12-14
You could try connect manually and then try to install nm-applet
Manually wired connection.
Plug in your cable.
Open a terminal window
sudo /sbin/ifconfig eth0 up
sudo dhclient eth0
Type netstat -r to see if you have the default route to your router.
sudo /sbin/ifconfig     and look if the card got an ip-address from the router
If you don't have the default route you must add it.
sudo /sbin/route add default gw <ip-address of your router> eth0

---

### Post by uncaspi on 2009-12-14
You said in your first posting that everything works well except the wireless, so I assume you have a cable connection which is working.
Then you can try to install the applet if it's missing.
sudo apt-get install nm-applet
eventually sudo apt-get install network-manager    if it's missing.

---

### Post by SamppaM on 2009-12-14
Ok, I got the network applet to work. However, the network applet does not display any networks, it just says "no network connection", though there is a message "Wireless networks available" after I boot the computer.

---

### Post by SamppaM on 2009-12-14
Yes! I got it working! Thanks for help :D

---

### Post by SamppaM on 2009-12-14
The solution was actually pretty simple: After I got the network applet there, I just needed to create a wireless connection, set the name of the network (SSID), and the WPA2 password.

It was a little bit more difficult than with Mac, but it works anyway.

---

### Post by uncaspi on 2009-12-14
You welcome:D

---

