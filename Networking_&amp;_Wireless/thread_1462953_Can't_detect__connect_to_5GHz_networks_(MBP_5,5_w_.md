---
title: "Can't detect / connect to 5GHz networks (MBP 5,5 w/ bcm4322)"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by Taoye on 2010-04-26
Hey all,

I'm currently running the Lucid release candidate on my MacBook Pro 5,5 (late 2009). My access point is a Linksys WRT610n, dual band simultaneous, I've got the first set up as mixed-GN on 2.4GHz and the second is N-only 5GHz. The MacBook has a Broadcom 4322 chip for wireless and is reported to be able to connect to basically any network on both frequencies.

At home I'm able to connect to the 2.4GHz network no problem, but I cannot even see the 5GHz network. If I try to "connect to hidden wireless network" then it searches for the network and after a minute it asks for the WPA password, I put it in, and it works for a minute and then asks me for the WPA password again... it keeps doing this and never connects. Is there a way to tell it to look for, or connect to, a 5GHz network?

Using the latest Broadcom driver via bcmwl-kernel-source.

Can anyone provide any help?

---

### Post by bkratz on 2010-04-26
> **Taoye said:**
> Hey all,

I'm currently running the Lucid release candidate on my MacBook Pro 5,5 (late 2009). My access point is a Linksys WRT610n, dual band simultaneous, I've got the first set up as mixed-GN on 2.4GHz and the second is N-only 5GHz. The MacBook has a Broadcom 4322 chip for wireless and is reported to be able to connect to basically any network on both frequencies.

At home I'm able to connect to the 2.4GHz network no problem, but I cannot even see the 5GHz network. If I try to "connect to hidden wireless network" then it searches for the network and after a minute it asks for the WPA password, I put it in, and it works for a minute and then asks me for the WPA password again... it keeps doing this and never connects. Is there a way to tell it to look for, or connect to, a 5GHz network?

Using the latest Broadcom driver via bcmwl-kernel-source.

Can anyone provide any help?

Apparently there is more than one 4322 chipset, with different abilities. The following table is copied from 

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)


SUPPORTED DEVICES
-----------------
The cards with the following PCI Device IDs are supported with this driver.
Both Broadcom and and Dell product names are described.  Cards not listed here
may also work.

	   BRCM		    PCI		  PCI		  Dell
	  Product Name	  Vendor ID	Device ID	Product ID
          -------------	 ----------	---------   	-----------
          4311 2.4 Ghz	    0x14e4	0x4311  	Dell 1390
          4311 Dualband	    0x14e4	0x4312  	Dell 1490
          4311 5 Ghz	    0x14e4    	0x4313  	
          4312 2.4 Ghz	    0x14e4	0x4315  	Dell 1395
          4313 2.4 Ghz	    0x14e4	0x4727 		Dell 1501
          4321 Dualband	    0x14e4	0x4328  	Dell 1505
          4321 Dualband	    0x14e4	0x4328  	Dell 1500
          4321 2.4 Ghz	    0x14e4	0x4329  	
          4321 5 Ghz        0x14e4	0x432a  	
          4322 	Dualband    0x14e4	0x432b  	Dell 1510
          4322 2.4 Ghz      0x14e4 	0x432c  	
          4322 5 Ghz        0x14e4 	0x432d  	
          43224 Dualband    0x14e4	0x4353  	Dell 1520
          43225 2.4 Ghz     0x14e4	0x4357  	

To find the Device ID's of Broadcom cards on your machines do:
# lspci -n | grep 14e4


Is your chipset one of the ones supposedly supported at the higher speed?

---

### Post by Taoye on 2010-04-26
This is the output of that command:
```

$ lspci -n | grep 14e4
03:00.0 0280: 14e4:432b (rev 01)
```

I think that corresponds to one of the dualband cards: 4322 Dualband 0x14e4 0x432b Dell 1510, no? Although it's not in a Dell. I changed the channel my router operates the 5GHz AP on to 52+54 (rather than one of the upper channels) and now I can connect to the network if I try to connect to a hidden network, but it still doesn't show up under the list of networks and won't connect automatically.

---

### Post by bkratz on 2010-04-26
> **Taoye said:**
> This is the output of that command:
```

$ lspci -n | grep 14e4
03:00.0 0280: 14e4:432b (rev 01)
```

I think that corresponds to one of the dualband cards: 4322 Dualband 0x14e4 0x432b Dell 1510, no? Although it's not in a Dell. I changed the channel my router operates the 5GHz AP on to 52+54 (rather than one of the upper channels) and now I can connect to the network if I try to connect to a hidden network, but it still doesn't show up under the list of networks and won't connect automatically.

According to the table you are correct ( it just gives the Dell part numbers since they are so popular and have been renamed).  It sounds like you are making progress by changing the channel info, that readme file does mention to stay away from certain ones.  I am afraid I have never setup a hidden network, but I don't understand how you would "see" it in the list of networks when you left click on the network icon, it is hidden, maybe I just don't have any near me to understand.  I did look at the setup for one though and don't see any means of connecting automatically. Perhaps someone else can help, sorry--but congratulations on at least getting it working.

---

### Post by Taoye on 2010-04-26
> **bkratz said:**
> According to the table you are correct ( it just gives the Dell part numbers since they are so popular and have been renamed).  It sounds like you are making progress by changing the channel info, that readme file does mention to stay away from certain ones.  I am afraid I have never setup a hidden network, but I don't understand how you would "see" it in the list of networks when you left click on the network icon, it is hidden, maybe I just don't have any near me to understand.  I did look at the setup for one though and don't see any means of connecting automatically. Perhaps someone else can help, sorry--but congratulations on at least getting it working.

Well, it's not supposed to be hidden, it's set to broadcast the SSID, but it doesn't show up on the list when I click the network manager icon. I can connect to it manually by specifying an SSID to search for, it's just annoying because it can't find the network on its own it won't connect automatically.

---

### Post by vinicius.vbf on 2010-06-23
Exactly same problem, another hardware setup. Running Lucid in a Aspire One w/ wireless card upgraded to Intel 4965AGN. Router is a "Linksys by Cisco WRT610N". Can't "see" any 5 Ghz network.

---

### Post by jmblock2 on 2010-08-05
Any update on this?  I was going to get a dual band simultaneous, but I think I might be having similar problems.  I was trying to verify I was on the 5ghz at a friends house, but it never listed those as possible channels (through iwlist scan).

---

### Post by vinicius.vbf on 2010-08-06
I've noticed that I was able to connect to 5GHz networks once I've configured my router to use a fixed wide channel (I've used 38) and a fixed channel width (40MHz only). Standard channel was 40 - 5200GHz.

---

### Post by nightalon on 2010-10-27
This is still an issue on MBP 6,2 with an upgrade from 10.04 to 10.10.

I cannot see my 40 MHz-wide 5 GHz network with the BCM94322 STA.

---

### Post by dnns on 2010-11-03
Same problem here (Brand new Dell laptop, 10.10 installed, Broadcom BCM43224 Wifi N chip) 

Funny enough I can connect to the 5Ghz network (Netgear WNDR3700) when searching for hidden networks. But it is not listed as an option in the detected networks. In conclusion the chip seems hardware capable as I'm on the 5 GHz network right now posting this message. Might it be a linux driver issue?

---

### Post by nightalon on 2012-04-02
I have this issue too on a Dell Precision M4400 with a Broadcom BCM90432b chipset.  It supports agn, but 5 GHz networks don't show up in Network Manager.  Since I also have the WNDR3700, I cannot set it to fixed width bands...only "up to 300 MBps".

I tried reinstalling the wl driver...no luck.  Apparently b43 supports my chipset, so I might try that.

---

### Post by howefield on 2012-04-02
Old thread closed.

---

### Post by wjamoore on 2012-05-12
old thread closed???   But no fixes..  Very useful moderation there

---

