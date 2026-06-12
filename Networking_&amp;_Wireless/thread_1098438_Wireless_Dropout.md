---
title: "Wireless Dropout"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by utterly on 2009-03-17
I am using the last three Ubuntu releases on two laptops and 8.10 on a desktop. I have the same proplem on each of them. Wireless networking drops out randomly every 10 sec to 2 - 3 min. This is a problem that is taking up a huge amount of web space and no one seems to have a solution other than a panel launcher to restart the network. This works about 4 times and then the system crashes, requiring a reboot. I wonder why nobody can fix this problem. It makes Ubuntu unusable as a wireless solution.

I am not a computer programmer and I would like to publish some observations that might give someone with the necessary knowledge an idea to create a workaround for this problem.

I recently learned about NetApplet after starting it in a terminal, every few seconds it reports:

Got ssid 0.940407 1
Got ssid 0.922549 1
Got ssid 0.943245 1
Got ssid 0.928666 1
Got ssid 0.940407 1

When the connection drops out, this changes to:

Got ssid 0.000000 1
Got ssid 0.000000 1
Got ssid 0.000000 1
Got ssid 0.000000 1
Got ssid 0.000000 1

Clicking on the NetApplet icon and selecting wireless: wlan0 (active) seems to shortly reconnect the network. This is much more efficient and does not seem to be limited in the number of times it is used.

Maybe,when the connection dies, something could be done to re-establish it.

---

### Post by sonicb00m on 2009-03-17
I think it depends on the chipset of the wireless card but like you've i've also experienced the same behaviour.

My laptop wireless is very good but the usb one i had was a nightmare. After the 810 update the thing run at 10% of it's potential speed.

The network applet is fine when you have a working connection but useless to report anything on why the wireless is failing to connect. It doesn't even tell you if the password is wrong.

---

