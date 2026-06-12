---
title: "Mixed Windows XP and Ubuntu wireless network ?"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by fivefour on 2009-06-18
I have been told by Linksys support that their WRT110 wireless router is incompatible with Linux. I have a desktop (wired) that runs their LELA software. I have a laptop (wireless) that was formerly running XP (now Ubuntu). I don't need the LELA software on the laptop. What I don't understand is why I can't have a mixed XP/Linux network. Is it true what the support tech said (impossible to do), or is he wrong? I have seen networks running Linux and Windows machines. Why should this router be any different?

---

### Post by Amilo1718 on 2009-06-18
there's nothing i can think of...

do those thechnicians actually know their job?

---

### Post by fivefour on 2009-06-18
Yeah, I can't think of a reason why either. Problem is I still can't get it on the network. Anybody know? Much appreciated...

---

### Post by xanfantasy on 2009-06-18
can you connect to other networks?

---

### Post by fivefour on 2009-06-18
No, but I couldn't before when it was running XP. All in range are secure.

---

### Post by xanfantasy on 2009-06-18
You might want to try to find an unsecured router or ask your neighbors for help and see if they will let you try to connect to their router temporarily. It may be your wireless card isn't working right.

Some things you could check is to see if the card is even recognized. Open Applications >> Accessories >> Terminal (comand line) and type "sudo lshw -C network" without the quotes. This should show all of your network adapters that are recognized. If could post the output it can help others see what might be wrong.

The next step would be to check to see if you need restricted drivers. You can check this by going to System >> Administration >> Hardware Drivers. This will search for any drivers that may be needed for your hardware. If there are any listed, look for a wireless driver and see if it has been activated, if not click the driver and then click activate. Try connecting again and post the results.


The worst part about the lynksys technician is that he may not know that your router actually runs a modified linux.


Hope this helps,
Xan Fantasy

---

### Post by fivefour on 2009-06-18
Thanks. Will try that.

---

### Post by fivefour on 2009-06-19
Did as xanfantasy suggested and got "multicast=yes wireless=unassociated". And no restricted drivers were listed either. I think the problem is that I am not configuring the network properly. Should I be using DHCP or enter static address? How do I get that address. It lists loopback 127.0.0.1 right now.

---

### Post by xanfantasy on 2009-06-22
If your windows obtains it's ip address automatically then Ubuntu should too whenever you connect to the point. It seems that your computer isn't seeing the point or can't connect. You could try Wifi Radar (it's in the add/remove programs) to see if it will help you connect to your wireless.

As for testing the ip, you have to be connected first. Once you are on, most access points use 192.168.1.x for their DHCP pool where x is between 2-255 with a network mask of 255.255.255.0 and Gateway 192.168.1.1.

Other than that I'm not sure what else could help you. I will do some research but hopefully another user may have some insight.

Xan Fantasy

---

