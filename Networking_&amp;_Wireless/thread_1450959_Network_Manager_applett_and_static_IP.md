---
title: "Network Manager applett and static IP"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by pksings on 2010-04-09
Hello all, I have a server in a box that moves between wireless Access Points (APs). I need it to have a static IP and so far cannot get it to do so. As soon as I edit the connection to be static it will no longer connect. This worked fine with previous versions of Ubuntu and I'm stumped as to how to get it to work again. In other words in connects just fine with a DHCP address but not at all with a static one.

Typed in entry in /etc/sysconfig/whatever is not a viable option as there are two different AP's depending on where it is. I was forced into two AP's because of insufficent coverage and neither AP will allow me to assign an IP to a MAC address.

And I couldn't get WICD to work either.

Any help is greatly appreciated.

PK

---

### Post by capscrew on 2010-04-09
> **pksings said:**
> Hello all, I have a server in a box that moves between wireless Access Points (APs). I need it to have a static IP and so far cannot get it to do so. As soon as I edit the connection to be static it will no longer connect. This worked fine with previous versions of Ubuntu and I'm stumped as to how to get it to work again. In other words in connects just fine with a DHCP address but not at all with a static one.

Typed in entry in /etc/sysconfig/whatever is not a viable option as there are two different AP's depending on where it is. I was forced into two AP's because of insufficent coverage and neither AP will allow me to assign an IP to a MAC address.

And I couldn't get WICD to work either.

Any help is greatly appreciated.

PK

The AP does not assign IP addresses.  A DHCP server does.  Your DHCP server is where?  It should assign the IP address you want by MAC address.

---

### Post by Iowan on 2010-04-11
> **capscrew said:**
> The AP does not assign IP addresses.  A DHCP server does.  Your DHCP server is where?  It should assign the IP address you want by MAC address.
+1 I have a couple of my servers set up this way.

---

### Post by pksings on 2010-04-14
Thanks for your assistance. 
If the application doesn't set IP addresses then why does it allow you to type them in after you set it to use a 'manual' address instead of DHCP? Previous versions did indeed let you use a static IP and it was able to be set through this same tool. So I guess either the functionality was removed or it's broken? Neither of those is an acceptable alternative and will result in me having to switch distributions to one that does allow this, and I really don't want to go through all that.

Does anyone else know why this doesn't work anymore?

Oh and by the way, my Linksys AP does assign IP's. It's running the DHCP service, and it does not have the ability to assign IP's by mac address. 

Thanks

---

### Post by capscrew on 2010-04-15
> **pksings said:**
> Thanks for your assistance. 
If the application doesn't set IP addresses then why does it allow you to type them in after you set it to use a 'manual' address instead of DHCP? 
Previous versions did indeed let you use a static IP and it was able to be set through this same tool.

Did I misunderstand you?  You said a static IP address and that you were moving between wireless AP's.  In this situation the typical user uses NM to configure the wireless that uses DHCP to assign an IP address.  This can be random from the pool or reserved (what most would call static).

If you wish to configure the interface through NM *manually *that sure is doable.  If it is set that way with 1 AP it should work with 2 AP's.  It should still be the same wireless network. 
> 
So I guess either the functionality was removed or it's broken? 
No functionality has been removed.  The latest version of NM has changed though.  What version of NM are you using?> 
Neither of those is an acceptable alternative and will result in me having to switch distributions to one that does allow this, and I really don't want to go through all that.
Really?  To bad.> 
Does anyone else know why this doesn't work anymore?

Oh and by the way, my Linksys AP does assign IP's. It's running the DHCP service, and it does not have the ability to assign IP's by mac address.
That indeed is unfortunate.  I would do as Iowan suggested in the past and install DNSMasq.

Either way the choice is still yours.  You can manually configure the interface, either by editing the pertinent files or using NM.  Or by allowing NM to find your wireless and automatically configure itself to receive the IP via DHCP.

---

### Post by pksings on 2010-04-19
Thanks again Capscrew, your reply is insightful.

I am going to put something else on it. The machine in question is on a portable cart that moves from room to room, and at one end of the house it will not connect with the primary AP. So I put another AP at the other end of the house. Only one of them his running DHCP and the other is setup as a wireless relay. Both AP's are connected to my wired network.

In previous versions of Ubuntu I was able to configure NM in such a way that the machine would login to the AP but keep it's fixed/static IP address. So it does seem to me that this functionality has been removed as it is no longer possible. That might be because it's broken or because this behavior is no longer deemed necessary. Really, I have no way of knowing why it doesn't work any longer. I just know that the current NM GUI allows one to type in all the static IP/DNS and default GW information and save it, but after doing so will simply no longer successfully connect with the either AP.  Doing this same thing previously used to work just fine. 
Seems silly to allow one to appear to configure it this way and simply not work afterwards, I would think that functionality should have been removed also with the other capabilities. Which is why I personally think it's now just broken and will probably come back in some future version. 

This was useful as I Rsync to and from it as a methodology for saving stuff I think I should have multiple copies of. And that to me is more important than running Ubuntu. Since it gets it's IP through DHCP now I have no idea what it's IP is, the pool is 20 IP's. And I no longer have a quickie backup target. 

I'm not sure if you are a developer or not, but it seems to me that sometimes developers don't know that people become dependent on functionalities and behaviors, and it the ongoing improvement cycle decisions seem to be made that don't seem to take them into account. This might be because they are unaware that people are using it in these manners or insufficient testing pool size, nobody that was using it that way was included in the test pool. Either way, this sort of seems like one of those cases, the way it used to work is no more. And my feeble attempt to get that functionality back seems to be a failure.

Thanks again for your insight and time, now I begin the process of testing and selecting another distro.

PK

---

