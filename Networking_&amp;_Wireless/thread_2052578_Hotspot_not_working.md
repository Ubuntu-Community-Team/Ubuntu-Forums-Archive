---
title: "Hotspot not working"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by patman0623 on 2012-09-03
I am trying to configure Ubuntu to work as a wireless hotspot for the ethernet connection, so that I can attach wireless-only devices to the internet. I went through all the simple steps at [http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/). However, it is not appearing: my phone is reporting that there are no visible networks available under the name that I gave it (in my case, *patrick-Ubuntu*), and it does not have the option to connect to a hidden wireless network. How do I get my wireless hotspot to appear?

Some notes:
*I know that the wireless connection on the laptop *does* connect to wireless networks, because I've tried it elsewhere.
*My phone also connects to wireless connections properly
*I am using wireless card BCM4313 (for 11.10, I had to implement the fix at [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868) in order to get it to work, but the issue appears to be obsolete since I installed 12.04)

---

### Post by patman0623 on 2012-09-08
bumping; this shouldn't be unanswerable.

---

### Post by Aparajita on 2013-07-02
Probably this reply is too little, too late, but is it because Android devices are not capable of connecting to ad-hoc wifi networks??

[http://thesillyclone.wordpress.com/2012/06/27/connect-android-to-ad-hoc-wifi-network/](http://thesillyclone.wordpress.com/2012/06/27/connect-android-to-ad-hoc-wifi-network/)

Hoping this may help out others who see this question in future.

---

### Post by spyro777 on 2013-07-18
Yes, Android devices cannot connect to Ad Hoc networks. I found a workaround for this here:

AP-Hotspot
[http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html)

In my case I also needed to change /etc/NetworkManager/NetworkManager.conf and comment out the line
"dns=dnsmasq" since Network Manager was not allowing AP-Hotspot to assign IP address to connected clients. 

Reference: [http://sokratisg.net/2012/03/31/ubuntu-precise-12-04-get-rid-of-nms-dnsmasq-and-setup-your-own/](http://sokratisg.net/2012/03/31/ubuntu-precise-12-04-get-rid-of-nms-dnsmasq-and-setup-your-own/)

Hope this helps.

---

