---
title: "Realtek RTL 8110s Problem"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by knichel on 2009-10-15
I am running Kubuntu Jaunty.  I added a network card to my computer.  I am trying to make my computer a firewall/web filter for my house.  I added the card and connected it to my wifi router (which gives out dhcp 192.168.1.0/24).  When I checked the ip of the card, 
```
eth1      Link encap:Ethernet  HWaddr 00:1e:2a:c2:0a:a6
          inet addr:208.67.217.132  Bcast:208.67.217.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```
 address?  What the heck?

dmesg | grep eth1 shows... 

```
[    3.789573] eth0: RTL8168b/8111b at 0xffffc2000005a000, 00:1d:7d:09:94:0f, XID 38000000 IRQ 2299
[    3.792310] eth1: RTL8110s at 0xffffc20000040000, 00:1e:2a:c2:0a:a6, XID 04000000 IRQ 18
[   14.378526] r8169: eth0: link up
[   14.378534] r8169: eth0: link up
[   21.752338] r8169: eth0: link up
[   32.360014] eth0: no IPv6 routers present

```

I booted this computer into windows to check the card and it worked fine.  So, I am lead to believe that this is an issue with the linux driver.  I downloaded the newest driver from Realtek and installed it but no luck.

I don't know what else to do...  Please help.

Mike

---

### Post by dandnsmith on 2009-10-15
Are you saying that you added a card which gave a second ethernet port?
There seems to be a mix of messages as if there are 2 interfaces, one of which is fully operational (and has an external IP address), and we don't have a lot of info about the second - but there is an inference that something is trying to use IPv6, and ther may not be adequate provision (perhaps you need to override to use IPv4)

---

### Post by knichel on 2009-10-15
Yes, I have 2 interfaces now.  eth0 is the onboard lan adapter of my mobo and eth1 is the Netgear card I just added.  The card appears to be using the rt8110s while the onboard is using rt8169.

I do not know where the IPv6 is coming from.  eth0 is working fine as always.  It is eth1 I am having trouble with.

---

### Post by dandnsmith on 2009-10-16
I'd be looking to try using ifconfig, both to get info and also to 'start' eth1 (have a look at the Man pages, and use the *up* with suitable other parameters, to see if you can get it lively.
Linux seems to configure the interfaces when installed, but may need a helping hand when one is installed post linux installation (possibility: try a liveCD to see if both interfaces get activated)

---

### Post by knichel on 2009-10-17
OK, I tried a live CD.  It sees the card but the adapter fails to get an IP address from the router.  I have tried disabling the other  adapter in the bios (it is onboard LAN and also Realtek as my new card) but no luck. 

Here is what I know...
[LIST=1]
[*]The router that the card is plugged into IS handing out dhcp addresses
[LIST]
[*]when onboard adapter plugged into second router, it gets appropriate IP address.
[*]when PCI card plugged into main router it does NOT get ip address 
[*]when 
[/LIST]
[*]The interface is UP 
[LIST]
[*]sudo ifconfig eth1 up
[*]sudo dhclient eth1 - no joy
[/LIST]
[*]The network adapter works under windows
[*]I tried several show info commands and the card appears to be working as far as ubuntu can tell (lshw, lspci, dmesg etc)
[/LIST]

This is very frustrating, because the card seems to be ok as far as ubuntu can tell, but it is not working.

Any other suggestions?

---

### Post by knichel on 2009-10-17
OK, now something is very fishy here.  I walked away from this problem for about 6 hours  and when I came back to the computer, the damn thing is working.  I did absolutely nothing and it now has an IP address from my test router.  I didn't even do an update so I don't know why it is working.  I think that is the worst part, not knowing why it works now...

So, another question if I may.  Once I have 2 NIC's in the computer, one will connect to my internet router and the other to my home LAN.  Should I configure the interfaces in /etc/network/interfaces?  If so, do I remove the auto statement for eth0 and eth1?  And how do I force the default gateway to be out eth0?

---

### Post by dandnsmith on 2009-10-18
> **knichel said:**
> OK, now something is very fishy here.  I walked away from this problem for about 6 hours  and when I came back to the computer, the damn thing is working.  I did absolutely nothing and it now has an IP address from my test router.  I didn't even do an update so I don't know why it is working.  I think that is the worst part, not knowing why it works now...

I had no end of trouble with a users laptop (running Windows) when it had 2 interfaces trying to talk to the same router. I 'fixed' it in the end by disabling one of them, and then the traffic 'knew' which path to take.

> So, another question if I may.  Once I have 2 NIC's in the computer, one will connect to my internet router and the other to my home LAN.  Should I configure the interfaces in /etc/network/interfaces?  If so, do I remove the auto statement for eth0 and eth1?  And how do I force the default gateway to be out eth0?

I'd make sure the 2 interfaces were on different IP networks (eg use 192.168.1.x, and 192.168.2.x with suitable masks) and then organise the routing table accordingly with 'routes' for each interface.
I suspect you're aiming at some sort of isolation of the local network.

HTH

---

### Post by knichel on 2009-11-05
Thanks for assisting.  I  have not idea  why, but all of a sudden the interface works.  SO I won't look a gift horse in the mouth...

---

