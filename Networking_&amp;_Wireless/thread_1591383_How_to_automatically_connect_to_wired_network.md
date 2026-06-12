---
title: "How to automatically connect to wired network"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by mohanr on 2010-10-09
Hello All,

    I am running lucid. I have to type in 

sudo ifdown eth0
sudo ifup eth0

    each time I want to connect to the internet wiredly.

   I am running the latest network manager - It manages my wireless but I am unable to get it to also manage my wired connection. 

    What files do I edit?

Thanks in advance.

---

### Post by grahammechanical on 2010-10-09
You should not need to edit any files. The network manager should do it for you. Click on the icon. Select Edit Connections. Select eth0 and select Edit. Now tick Connect Automatically on the dialog box that pops up. Eth0 should now become Auto eth0. 

regards

---

