---
title: "AR242x Atheros - Wont detect wireless - please help !"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by noob03 on 2008-12-27
Hello,

I must be the newest Ubuntu user in the whole world, cos I just installed it a few minutes ago. I have never worked on Linux before and the only technical thing I know is to turn on a computer.

My problem: My Dell notebook cannot detect wireless network in my home. My other laptop which works on Windows is connected to this network.

My config:

Notebook: Dell Vostro A840
OS: Ubuntu 8.04
Wireless adapter: Atheros Communication Inc 802.11abg Wireless PCI Express Adapter

Observations:
1. I can connect to internet through hard wired connection.

2. The System>Administration>Hardware Drivers shows:
Atheros Hardware Access Layer (HAL) - Enabled - In use
Support for Atheros 802.11 wireless LAN cards. - In use

Please take a look at the attachment for a screenshot of what I see in Network Manager and Wireless Networks.

I need all the help you can give! Thank you all.

Anupam

---

### Post by noob03 on 2008-12-27
> **noob03 said:**
> Hello,

I must be the newest Ubuntu user in the whole world, cos I just installed it a few minutes ago. I have never worked on Linux before and the only technical thing I know is to turn on a computer.

My problem: My Dell notebook cannot detect wireless network in my home. My other laptop which works on Windows is connected to this network.

My config:

Notebook: Dell Vostro A840
OS: Ubuntu 8.04
Wireless adapter: Atheros Communication Inc 802.11abg Wireless PCI Express Adapter

Observations:
1. I can connect to internet through hard wired connection.

2. The System>Administration>Hardware Drivers shows:
Atheros Hardware Access Layer (HAL) - Enabled - In use
Support for Atheros 802.11 wireless LAN cards. - In use

Please take a look at the attachment for a screenshot of what I see in Network Manager and Wireless Networks.

I need all the help you can give! Thank you all.

Anupam

I got this fixed. So it seems, that I had an older kernel or something that I had to download. I wish I knew much more so that I could share in this forum. If anyone's interesting in knowing more, I can refer you to the person who helped me. Not sure if that qualifies as help in this forum.

Anupam

---

### Post by sanmitra on 2008-12-27
> **noob03 said:**
> Hello,

I must be the newest Ubuntu user in the whole world, cos I just installed it a few minutes ago. I have never worked on Linux before and the only technical thing I know is to turn on a computer.

My problem: My Dell notebook cannot detect wireless network in my home. My other laptop which works on Windows is connected to this network.

My config:

Notebook: Dell Vostro A840
OS: Ubuntu 8.04
Wireless adapter: Atheros Communication Inc 802.11abg Wireless PCI Express Adapter

Observations:
1. I can connect to internet through hard wired connection.

2. The System>Administration>Hardware Drivers shows:
Atheros Hardware Access Layer (HAL) - Enabled - In use
Support for Atheros 802.11 wireless LAN cards. - In use

Please take a look at the attachment for a screenshot of what I see in Network Manager and Wireless Networks.

I need all the help you can give! Thank you all.

Anupam
i successfully run vostro a840 ubuntu wireless ( atheros )

step 1 install ubuntu  8.1 intrepid ibix ( driver will not run on  old hardy heron )
step 2 goto [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
step 3 download and extract ( using right click )  [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

step 3 open text terminal and go to directory where driver is extracted 
step 4 enter commands mentioned on the download page 
step 5 you should have active wireless around you 
step 6 wireless is up, set up wireless and surf

---

