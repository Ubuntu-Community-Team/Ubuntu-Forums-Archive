---
title: "WPA Wireless Tutorial"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by COKEDUDE on 2011-02-13
Does someone have an updated WPA Wireless Tutorial? I found a old one here. 

[http://www.linux.com/news/enterprise/networking/8259-making-wireless-work-in-ubuntu](http://www.linux.com/news/enterprise/networking/8259-making-wireless-work-in-ubuntu)

---

### Post by dmizer on 2011-02-13
Are you trying to do all of your networking via the command line? The NM-Applet shipped in modern Ubuntu should allow you to configure your wireless (including WPA) without ever touching the command line.

---

### Post by nitishpandey on 2011-02-13
I am not sure about nm-tools, i have struggled 2-3 days just trying to configure my broadcom chipset on hp pavillion. The problem is that there are 2 broad variations of solutions out there. One says go with NDISWrapper and the other with firmware installation (cutting edge! my foot). Then within each solution there are so many variations. The most scary for me, i think, was that the scan on network manager would show up after sometime and i would think it happened because of what i was doing (struggling) in the shell. Then at times iwlist scan would show Access points in shell but none in knetwork manager. When nothing was of any use, i just decided to follow this thread -http://ubuntuforums.org/showthread.php?t=590942#6 (this was mentioned in [http://ubuntuforums.org/archive/index.php/t-838291.html](http://ubuntuforums.org/archive/index.php/t-838291.html)). These threads had nothing to do  with my chips (but i had reached the stage where DHCPDISCOVER was not yielding any IP address...and no one would tell why! is the chipset not transmitting or what). I saw someone was very happy with wicd. I installed it again. I failed to see where he was saying he entered the password because wicd from shell would give nothing!. Luckily i searched its icon in the menu (use search box in kde menu). I launched it, it has such a clear set of instructions - networks listing, status, connect /dinsconnect buttons and security setttings. knetwork manager should be stopped right away. Of course let me mention that i have used ndiswrapper approach ....may be the firmware approach would have worked with wicd installed. ANyway....whoever is ubuntu  geek should stop worrying about adding new funny names and releases. First make things work.

---

