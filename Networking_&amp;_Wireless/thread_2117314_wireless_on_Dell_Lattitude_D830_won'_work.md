---
title: "wireless on Dell Lattitude D830 won' work"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by goodbye-windows(tm) on 2013-02-18
Hi All,
 

 I'm working on my brothers new laptop, which can't connect to the internet using the wireless. However the ethernet cable works great.
 

 My gut feeling is that something in the laptop is not searching for wireless networks, so his wireless network can't connect to his router. When booting up, his wireless icon never flashes-it's like it doesn't try to connect at all.
 


**Here's some Basic details:**
 >  
 OS is 12.10 Unity running in a Dell D830 laptop. It worked under windows and the windows hard drive has been removed without mods, so the original windows HD can be reinstalled to aid in the diagnosis if needed.
 

 The router is a fiber optic unit, model number M1424WR. The ISP is Verizon. Wireless units always work without difficulty. He has another wireless computer in the house that connects and works great, so the D830 laptop is suspected.
 

 The D830 has a wireless lan on/off switch, it is in the proper position to enable wireless, and the associated blue LED also turns on properly when the switch is moved to enable wireless lan connections.
 
**Here's what we've found by poking around:**
 > Initially, the wireless icon was not showing up at all. This was fixed by manually entering details of the wireless network (such as ssid, type of encryption (WPA/WPA2) and the proper passphrase). Now the wireless icon shows up in the upper panel, and the new wireless network shows up as well.
 

 Logging into the router shows that the D830 wireless has NEVER been heard by the router, so it has never been assigned an ip address by the DHCP server in the router. The D830 ethernet connection shows up properly in the routers listings and all the other wireless computers in the house show up properly as well. The connection to the D830 wireless laptop is totally missing in the routers listings.
 

 While logged into the router, the proper passphrase and encryption type have been confirmed to be correct. Checking the D830's wireless setup confirms that the wireless networking parameters are properly setup. And the 'connect automatically' and the 'use this connection for all users' boxes in the D830 wireless setup have checks in the check boxes.
 

 When the ethernet cable is disconnected, and the computer is booted, the wireless icon on the upper panel never flashes and there is no error message saying the wireless network can't be found. So it appears that the wireless in the D830 isn't even trying to connect.
 

 Normally  at least 2 other wireless networks from his neighbor's systems can be detected. But, these other wireless networks do not show up when the wireless on the D830 is interrogated.  
 I'm stuck-any suggestions?
 

 TIA.
 

 Art

---

### Post by mörgæs on 2013-02-18
I happen to be troubleshooting one of these right now, and everything works well. Later today I can take a look and post back.

Meanwhile please post the output of **sudo lshw -short** to confirm that we have the same hardware.

---

### Post by goodbye-windows(tm) on 2013-02-20
Hi mörgæs,

Sorry for the delay in replying, it took me awhile to figure out where the laptop was. It turned out my brother has it with him and he is delivering a truckload of cargo from MD>FL>MD. 

So, he is only reachable via cell phone until he returns (likely Friday).

However, I did some digging.

The configuration for his computer is found on the Dell website, click on the 'system configuration" tab for a list of his hardware.

> [http://www.dell.com/support/troubleshooting/us/en/19/Servicetag/h3vwnd1](http://www.dell.com/support/troubleshooting/us/en/19/Servicetag/h3vwnd1)

I also tracked down the DW1390 wireless transceiver. DW1390 is an alias for the Broadcom 4311. Broadcom 4311 is also aliased to a B4311, a BC4311 or a BCM4311.

I can get the output of the **sudo lshw -short **command on Friday or first thing Saturday. Will post the output here when I can.
Regards,

Art

---

### Post by bkratz on 2013-02-20
> **goodbye-windows(tm) said:**
> Hi mörgæs,

Sorry for the delay in replying, it took me awhile to figure out where the laptop was. It turned out my brother has it with him and he is delivering a truckload of cargo from MD>FL>MD. 

So, he is only reachable via cell phone until he returns (likely Friday).

However, I did some digging.

The configuration for his computer is found on the Dell website, click on the 'system configuration" tab for a list of his hardware.



I also tracked down the DW1390 wireless transceiver. DW1390 is an alias for the Broadcom 4311. Broadcom 4311 is also aliased to a B4311, a BC4311 or a BCM4311.

I can get the output of the **sudo lshw -short **command on Friday or first thing Saturday. Will post the output here when I can.
Regards,

Art



If it is a BCM4311 these should take care of it ( do with an ethernet connection)

sudo apt-get remove --purge bcmwl-kernel-source 
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

---

### Post by goodbye-windows(tm) on 2013-02-20
> If it is a BCM4311 these should take care of it ( do with an ethernet connection)

sudo apt-get remove --purge bcmwl-kernel-source 
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43 	

Many thanks.

But, I have another concern.........

Before I heard about the problem, my brother installed all kinds of utility programs related to wireless, which he found in the software center. I have no idea which utility programs he installed.

Also, another family member had my brother try a bunch of stuff (also unknown what). But I do know that ndis wrapper and the associated windows driver were tried.

Since these other repair modes have been tried and might interact, should I have my brother try a fresh install before trying the above fix???? The laptop is new to him, so there is no important data on it, and he has 25 mb per second internet, so he can do a fresh install pretty quickly.

Should I get him to do the above fix as the computer is now, or do the fresh install before trying the fix?

TIA.

Art

---

### Post by bkratz on 2013-02-20
Since we would have to remove whatever the previous tries were (esp ndiswrapper!) it would probably be easier to start from scratch.  If the system asks him to install the STA driver make sure he doesn't do that either or we will have to remove that too>

---

### Post by goodbye-windows(tm) on 2013-02-20
Excellent, tnx so much. I'll email my brother now, even though he won't get the email until he returns home from his delivery.

Regards,

Art

---

