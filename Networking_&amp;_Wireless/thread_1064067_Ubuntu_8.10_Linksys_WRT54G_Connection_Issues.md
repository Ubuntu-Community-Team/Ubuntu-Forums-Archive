---
title: "Ubuntu 8.10 Linksys WRT54G Connection Issues"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by fjf314 on 2009-02-08
I'm having issues connecting to my WRT54G router from within Ubuntu 8.10. When I set up the router, it was running Windows Vista and could connect successfully, so at the very least I know that the router is working. Both my laptop and my desktop, which has been running Ubuntu all along, can connect successfully via Ethernet cable. Wireless is the only thing giving me trouble and since this is my first wireless router, I'm pretty clueless about what to do.

Ubuntu is able to see the SSID of my router. When I try to connect to it, it asks for my password, which I provide. It then tries to connect for about a minute or two before failing and telling me that "Passwords or encryption keys are required to access the wireless network."

The router is setup with WPA Personal and when Ubuntu asks for the password, I make sure that it is set to WPA & WPA2 Personal. At this point I have no idea what I need to do and after searching through existing threads none of them helped me any. I would greatly appreciate any input.

Edit: I forgot to mention that my driver is:

Broadcom STA wireless driver

from the Hardware Drivers application.

Second Edit: This was resolved thanks to some help I got in the Ubuntu IRC channel. I reset the WPA key and it was able to connect afterward. I would delete the thread but I can't seem to find a way to do it, not sure if that's disabled on this board.

---

### Post by punx45 on 2009-02-08
you should be able to mark it resolved by editing the original post, i think.

---

### Post by fjf314 on 2009-02-08
Unless I'm totally missing something when I try editing the post, I'm not seeing any way to do that.:?

---

