---
title: "Can't enable WOL with ethtool on Broadcom 5708 nic"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by micster on 2009-04-24
Hi,
  I have a Dell Poweredge 1950 with onboard networking. According to Dell, wake-on-lan is supported by my device, a Broadcom NetXtreme II. Indeed there seems to always be a flshing light near the ethernet port when the server is off. So at least it looks like it has power and is ready to wake itself up.

  The Bios setting was hard to get to, you have to press "ctrl + s" when booting which I did and set the "pre boot wake-on-lan" to enabled. That was the only setting that looked like anything to do with WOL.

   The driver used by the Broadcom NetXtreme II is called "bnx2", which loads fine. I updated to the most recent version which at this time is 1.8 I think.

   I read several guides on how to setup WOL within Ubuntu and after making sure it's enabled in the BIOS, they say to run the command
```
sudo ethtool eth0
```
to see if it supports WOL. This is where my problem begins. Ethtool unfortunately reports the following: 
```
Supports Wake-on: d
         Wake-on: d
```
Which means that it is disabled and contradicts what Dell says about this device. In fact, I have read several places on the Internet where other people have WOL working with this device. However, I have not read of any that use Ubuntu. If I try to ignore the fact that ethtool says the device does not support WOL and issue the command```
ethtool -s eth0 wol g
``` it just returns an error.

I would really appreciate any help I could get to help me get this fixed.

Sincerely,
Mic

---

### Post by micster on 2009-04-24
So I did some digging and came across this tasty nugget from [Dell Support]("http://support.dell.com/support/edocs/network/BroadCom/R125805/en/linux.htm")> NOTE: For Broadcom NetXtreme II BCM5708 devices with a silicon revision prior to B2, the open source bnx2 driver does not support the reporting and configuration of NetXtreme II WOL settings via ethtool. For silicon revisions of B2 or later, the bnx2 driver reports support for Magic Packet WOL via ethtool. Enabling support via ethtool is mandatory to successfully wake the system. To determine the silicon revision of your Broadcom NetXtreme II device, use the lspci command, where "10" = revision B0, "11" = revision B1, and "12" = revision B2. 

Guess which revision I don't have... That's right the one that is suppose to work with ethtool. I issued the command *lspci* and figured that I have revision B1. What does that revision mean anyway? Is it like a software version? Or is it more like the physical hardware version? I think it is the latter because I couldn't find any information on updating the revision number.

The other interesting thing here  is the part that says "Enabling support via ethtool is mandatory to successfully wake the system." Is there really no other way than using ethtool?

---

### Post by micster on 2009-04-26
I decided to try and modify the *bnx2* driver to work with my revision of the Broadcom NetXtreme... that was a bad idea.

Everything seemed to work okay at first, I had Internet access and I was able to activate the setting for WOL through ethtools (which I couldn't before). So I finished up the install of my modified driver and rebooted.

Now I can not finish booting up at all. I don't even get to grub before the machine just chokes. The LCD on the front panel starts to issue an error at this point which reads *cpu1 ierr 1410*. I looked up that error and it means there could be a hardware malfunction or a bad driver, duh.

The Instructions to fix it are to reseat the cpu. I'm not sure what that means, I assume it means to pull out the cpu and then put it back in. If I do that the error goes away, but comes back again the next time I boot.

Is there anyway I can totally remove the bad driver I created so I can boot my machine again?

---

