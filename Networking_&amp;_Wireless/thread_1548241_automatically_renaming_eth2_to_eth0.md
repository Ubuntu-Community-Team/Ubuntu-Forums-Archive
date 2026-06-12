---
title: "automatically renaming eth2 to eth0"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Milkyrice on 2010-08-08
Ok. So I managed to do an ubuntu minimal install on a usb stick. I made this usb stick so i could use ubuntu with some of my own bought programs. The specific programs i installed have a license file. 

Whenever i try my usb stick in a different computer, a new PCI interface entry is added into my /etc/udev/rules.d/70-persistent-net.rules and is named in ascending order from eth0 (eth1, eth2...etc).

In order for my program to work it requires my eth0 mac address to stay the same. I followed what it said in the comments in this link: [https://answers.launchpad.net/ubuntu/+question/62716](https://answers.launchpad.net/ubuntu/+question/62716) . This works in the short term but whenever i go to a new computer i have to do the same thing again.

Is there any way to get ubuntu to automatically assign/rename "eth2 to eth0" everytime i plug my usb stick into a new computer? Or is there any way to overwrite the eth0 interface in 70-persisten-net.rules each time rather than having it increment to eth1, eth2, eth3...etc...?

---

