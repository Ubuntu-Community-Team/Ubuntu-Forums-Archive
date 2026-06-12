---
title: "MSI Wind 100 keeps disconnecting from network"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by cotysoo on 2011-01-25
Hello!
I have a MSI netbook, U100, on which I've installed Ubuntu 10.10. This keeps disconnecting from the network, though the applet shows me that the netbook found it. I mention that I have a wireless network and another laptop, with WIN 7, where I have no problems with the Internet connection. I also have a 3G USB modem, which let me connect without problem. 
I'm a newbie with Linux, so please excuse me if my problem seems to be simple for you.

---

### Post by cotysoo on 2011-01-26
Thank you for so many replies.
However, I solved the problem, it was because I tried to use IPv6 . So, I just deleted the network and then, when I have reconnected, I didn't use the IPv6 settings.

---

### Post by ruegore on 2011-01-26
I used to have this problem with my MSI Wind U123 netbook, but I was using Ubuntu 9.10 at the time. The problem fixed itself when I started using 10.04 LTS (and now 10.10), although I never tried setting up any IPv6 settings in the first place.

---

### Post by idealsceneprod on 2011-03-04
I had this problem with Ubuntu 10.10, and for me, the issue was I had nm-applet and wicd both installed and running. Killing wicd and uninstalling wicd-daemon fixed it for me.  [http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/](http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/)  Val

---

