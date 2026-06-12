---
title: "WiFi quit working"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Zylstra555 on 2010-07-03
Hello, 

Yesterday my WiFi completely quit working. The light on the keyboard is not lighting up. I enable and disable my WiFi by pressing Fn+F2, and tried multiple times and also tried restarting twice. 
No WiFi networks appear in the systemtray WiFi manger. 

The last thing that happened to my laptop: I ran the battery completely down. Absolutely empty. 
Possible cause: Some laptops disable WiFi and other external devices when battery level becomes critical. Could it be possible that Ubuntu disabled the device upon draining the battery, and it did not enable it again?

I have a Dell E1505, about four years old. 
Ubuntu 10.04
All the latest updates installed.

---

### Post by Metaljaz on 2010-07-03
As the computer is booting up enter the BIOS and make sure that it was not disabled when the battery totally discharged.

---

### Post by Zylstra555 on 2010-07-03
I looked in the bios, it was enabled. For fun, I disabled and enabled it again to see if it made a change, it did not. 

When I click the WiFi icon in the system tray, the context menu says (grayed out): 
Networking Disabled.

---

### Post by Metaljaz on 2010-07-03
Try resetting your router and then restart the computer

---

### Post by Zylstra555 on 2010-07-03
It is not a router problem. All others computers connected to the same WiFi device are functioning fine. 
At the very least, my laptop should be able to see my networking as well as four others from around the neighborhood. 

I am now trying the solutions listed here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454)

---

### Post by Metaljaz on 2010-07-03
I offered that suggestion because mine has done the same thing. All other computers work fine with the router except one of the laptops but resetting the router by unplugging it and waiting 30 secs. and plugging it back in works.

---

### Post by Zylstra555 on 2010-07-03
I try not to unplug my router because I run a website and support an IRC network. 

I fixed the problem. 
I right-clicked (not left-click) the Network Manager applet in the system tray, and checked "Enable Networking"
Then, I pressed the keyboard combination I use to enable WiFi (Fn+F2), and it came on. 

And now, it works!

---

