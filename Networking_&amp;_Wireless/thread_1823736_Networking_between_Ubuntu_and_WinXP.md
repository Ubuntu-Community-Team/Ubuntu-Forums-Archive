---
title: "Networking between Ubuntu and WinXP"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by Jamie_Edwards on 2011-08-12
I'm going to have two PC's in my house (Going as I'm building one right now). One is my dads and the other mine.

My dads computer runs on Windows XP and mine will run both Ubuntu 11.04 and Windows 7, but I will definitely be using Ubuntu more than Win7. The only problem is that the only printer is connected to my dads computer and I may need to use it.

Here's my question. Is there a way of networking Ubuntu and my dads computer so that I can use said printer?

And to go a little further is there also a way of transferring files to and from both OS's? (although if this is not possible then just say)

Although I have been using Ubuntu for around 2 months I'm still a noob so try to make your answer as noob friendly as possible. Thanks.

Oh and one more thing that isn't really relevent to this but still curious, are there and Ubuntu stickers available to buy? You know, the ones that you stick onto your tower/laptop to let people know its has Ubuntu running in it? 





If you want to know the specs of my build here it is:

Processor: AMD Athlon II X2 Processor.
Motherboard: Asus M4A78LT- M.
RAM: 4Gb Corsair TW3 X4G1333 DDR3 (2 x 2Gb).
CPU: Fan: Arctic Freezer 7 Pro Rev.2 CPU Cooler.
HDD: 1Tb Western Digital Caviar. (800Gb will go to Ubuntu and 200Gb will go to Win7)
GPU: Ati Sapphire Dual HDMI 1Gb DDR3.
Wireless Card: Belkin Wireless G Desktop Card.

---

### Post by realmkeeper on 2011-08-26
> **Jamie_Edwards said:**
> I'm going to have two PC's in my house (Going as I'm building one right now). One is my dads and the other mine.

Here's my question. Is there a way of networking Ubuntu and my dads computer so that I can use said printer?


You will need a network. Simplest and cheapest solution is a cross-over ethernet cable assigning static IPv4 addresses for both, say 192.168.0.1 and 192.168.0.2. Share the printer on the XP Box and Add the printer on the Ubuntu Box as a Network printer. 
If the XP Box has a Wireless card then you could setup a wireless adhoc network. 
If there is a ADSL router then you just need to connect the Ubuntu box to the network.

> **Jamie_Edwards said:**
> And to go a little further is there also a way of transferring files to and from both OS's? (although if this is not possible then just say)

Sharing between the dual boot will require that you set-up a separate partition using FAT or NTFS for both OSes to use. When installing Ubuntu this can be set-up.

---

### Post by Jamie_Edwards on 2011-09-17
Thank you for the reply, I shall have a go once I have built my PC XD

---

