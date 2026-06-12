---
title: "Multiple dsl connection"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by persiangulf on 2012-07-31
Hi

Here is what I want to do... If it is not possible and not logical, forgive me because i'm not professional.

I have three PCs and all of them connected to internet through a router and a bridge dsl connection. Now I want to make VM to do the same except that I only have one ethernet card.

I'm using Ubuntu 12.04 as OS and VitualBox as VM Software.

Thanks

---

### Post by miegiel on 2012-07-31
I wouldn't use a VM but just build it on the machine, though building it in a VM should be possible too. However you'll need 2 ethernet cards. I use my old laptop for that, with the built in ethernet connected to the LAN and an USB ethernet "card" connected to the bridge/DSL-modem. But if you have a desktop PC, a PCI or PCIe ethernet card will work better (faster). The 1Gbit/s USB ethernet connection only does about 100Mbit/s, but that's still faster than my internet connection. :D

---

### Post by persiangulf on 2012-07-31
Thanks Miegiel

Here is a blueprint of my network ....

I connected dsl modem to wireless router and my laptop connected to it through wireless connection. Of course I have an ethernet card so I think It counts as two. 

Can you tell me exactly what should I do? How should I config host and guest systems?

Thanks

---

### Post by miegiel on 2012-07-31
> **persiangulf said:**
> Thanks Miegiel

Here is a blueprint of my network ....

I connected dsl modem to wireless router and my laptop connected to it through wireless connection. Of course I have an ethernet card so I think It counts as two. 

Can you tell me exactly what should I do? How should I config host and guest systems?

Thanks

Sorry I can't really give you advice on VM's. I've looked into it in the past, but my main machine is a atom netbook and my other desktop machines are really to old and slow to play with it without getting frustrated. (I'll get there one day when I have upgraded my hardware.)

That said, my intuition tells me setting up a VM as a firewall/gateway/router on a PC or laptop won't be as secure as using a dedicated machine to do the job. Though most accesspoint/gateway/router devices have impy firewalls and are not really secure either, it still might be a better solution for you. Unless you're doing this to experiment and learn.

In any case, with the hardware you have, this is how I'd do it:
[LIST]
[*]Connect the ethernet of the laptop/PC you'll use as firewall/gateway/router to the modem/bridge and set the bridge to be transparent if it isn't already (no NAT of firewall on the bridge). And put it between your (wireless) LAN and the internet connection.
[*]Disconnect the access-point/gateway/router from the bridge (internet), but keep using it as an accesspoint and DHCP server, so that the machines on your network will automatically get IP addresses etc. The wifi network interface on your laptop probably can't opperate in "master mode" (most can't), which is necessary for a wifi interface to function as an accesspoint.
[*]Setup a wireless (and wired) LAN to connect all your machines in one network and to the laptop/PC that you setup to function as a firewall/gateway/router.
[/LIST]

Stuff you'll enjoy reading :D
[LIST]
[*]Man pages of [iptables]("http://manpages.ubuntu.com/manpages/precise/en/man8/iptables.8.html"), ifconfig, iwconfig, iw and tc.
[*][Iptables-tutorial]("http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html")
[*][Netfilter/iptables HOWTO's on networking filtering and NAT]("http://www.iptables.org/documentation/index.html") (a bit old but still good inspiration).
[/LIST]

---

### Post by persiangulf on 2012-08-01
Thanks miegiel
I had to do it with VM and finally I got it!!!

I didnot change anything in my current network but connecting my Ethernet to wireless router and changing VirtualBox default Ethernet type to Bridge Mode and now I have more than one dsl connection and I'm only limited to my max concurrent dsl connection that my ISP restricted..

Thanks again

---

