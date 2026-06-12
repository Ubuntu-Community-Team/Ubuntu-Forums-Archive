---
title: "Clonezilla &quot;without network card, we cannot go on&quot;"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by fishman35 on 2011-07-23
Hello all. I am running Lucid with DRBL 1.9.9 and after 3 agonizing days, everything is working perfectly on existing systems. I now need to make an image for a brand new system and the Intel 82579 NIC is not detected. When pushing an image, it states: "without network card, we cannot go on" It did capture that system's MAC address.
 
I had this years ago when my exisiting lab systems were brand new, but cannot remember how to fix it. I know the driver code needs to be entered, but is there a way to add the code without having to entirely reinstall DRBL? I believe I have the latest kernel. This nic is brand new. 
 
 
Thanks for any assistance!

---

### Post by fishman35 on 2011-07-24
K. So I installed the latest kernel 2.6.38 and the appropriate e1000e.1.3.17 Intel driver for that client system and nogo. I need to know how to update the system so it can see  the client system with the Intel 82579 NIC card.
 
If this is in the wrong forum, I will move it. I know there has to be some Clonezilla experts out there. 
 
I am always telling people in the industry that the GNU support community is better than Windows support. Don't make me look bad. :D

---

