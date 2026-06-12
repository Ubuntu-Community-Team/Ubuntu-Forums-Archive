---
title: "Netopia 3-D Reach"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by AmateurDev on 2010-02-01
Ok, so I have two computers and 2 wireless adapters. One comp is mine and the other is my brother, but they're both the same: Acer Veritron. The Wireless adapters are both Netopia 3D Reach, but different models: one is TER/GUSB-N and the other is TER/GUSB2-N. The GUSB2 will connect easily. The GUSB will not, however. We have WPA2 encryption on our network. I type in the network key and on Windows (my dual boot computer) it will keep saying: "Acquiring Network Address" On Ubuntu 9.10 (Bro's computer) it will try to connect, but will fail. I looked at the specs here: "http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf" and I think the problem might be the TKIP vs. AES. Is there a way to set this up on Ubuntu?. I have a program called Network Magic (Piece of junk, but I'm forced to use it:-x). I know I could connect with both adaptors w/o Network Magic. I couldn't find any solutions on the net. A little help?

EDIT: My brother's PC can connect with a LAN cable, but since we moved, it's not viable use the wired Ethernet anymore.

---

### Post by fagan on 2011-01-14
I am having the same problem with my new Netopia (GUSB2-N) and finding the drivers for Mint 10. I found a thread here so I figured I'd ask you. I am running WIN XP-SP3 on a Compaq Evo N400c INTEL PENT.III/846MHz/384MB-RAM/20G HD so, you see my reasons for switching to a lighter OS. Please help if your able. Thanks in advance.

---

### Post by AmateurDev on 2011-01-15
You could try getting the drivers from this website: [http://www.fastaccess.drivers.bellsouth.net/#netopia](http://www.fastaccess.drivers.bellsouth.net/#netopia), then try using ndiswrapper (a program that allows you to use Windows wireless drivers on Linux) to utilize them. I haven't tried this because I think my cards are completely broken, testing them with generic and official drivers on Windows with no luck, but I hope this works for you!

---

### Post by AmateurDev on 2011-01-15
You could try getting the drivers from this website: [http://www.fastaccess.drivers.bellsouth.net/#netopia](http://www.fastaccess.drivers.bellsouth.net/#netopia), then try using ndiswrapper (a program that allows you to use Windows wireless drivers on Linux) to utilize them. I haven't tried this because I think my cards are completely broken, testing them with generic and official drivers on Windows with no luck, but I hope this works for you!

---

### Post by AmateurDev on 2011-01-15
You could try getting the drivers from this website: [http://www.fastaccess.drivers.bellsouth.net/#netopia](http://www.fastaccess.drivers.bellsouth.net/#netopia),  then try using ndiswrapper (a program that allows you to use Windows  wireless drivers on Linux) to utilize them. I haven't tried this because  I think my cards are completely broken, testing them with generic and  official drivers on Windows with no luck, but I hope this works for you!

---

### Post by AmateurDev on 2011-01-15
You could try getting the drivers from this website: [http://www.fastaccess.drivers.bellsouth.net/#netopia](http://www.fastaccess.drivers.bellsouth.net/#netopia),  then try using ndiswrapper (a program that allows you to use Windows  wireless drivers on Linux) to utilize them. I haven't tried this because  I think my cards are completely broken, testing them with generic and  official drivers on Windows with no luck, but I hope this works for you!

---

