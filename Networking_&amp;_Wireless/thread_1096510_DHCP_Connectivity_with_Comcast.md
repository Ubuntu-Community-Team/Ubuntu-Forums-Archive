---
title: "DHCP Connectivity with Comcast"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by bzachd on 2009-03-15
I loaded Debian up for a buddy, and everything worked great, I had it on my 192 subnet with static IP. When I moved it back to his place, he has no router, just the modem from Comcast, which uses DHCP. I reset the wired onboard to DHCP. I get NO DHCP received.
Connecting with the laptop running XP, it picks up the IP DHCP no problem. I know I should have loaded Ubuntu but... was playing around with Debian at the time. Anyone know if I load Ubuntu is there a chance that it wont pick up the IP from Comcast? Dont want to waste my time, I can load 2000 up, then upgrade to Vista... but he seems to really like Linux. Any thoughts?

Thanks,
Zach

---

### Post by mocoloco on 2009-03-15
Something must have gone wrong when you went from static to DHCP.  There should be absolutely no issue with either Ubuntu or Debian.  If your able to, I would fire up a LiveCD while at his place to double-check that you're able to resolve an IP.  Either way I'd be confident Ubuntu would have no issues with it if that's the route you go.

---

### Post by Paul Coleman on 2009-03-15
I have 13 working Linux machines running on my network. Most of them Ubuntu. I also have Comcast. The only problem I have ever had if and when I connect a single machine to the cabel modem directly, is that Comcast will recongnize the machine better if I first unplug the modem, wait about 5 minutes and plug it back in. I then wait about 4 minutes before plugging the ether cable into the modem and booting the machine. 

There have been no issues using this method when not using a router. On occasion I run tests wherein I want the Linux box pugged directly in. For normal operations, I use the router.

Comcast prefers to see just one IP on the user side of the modem. It seems that adding or removing a machine without "rebooting" the modem itself causes some conflict. 

Recommend you give it a try or use a router.

---

### Post by bzachd on 2009-03-15
mocoloco, Paul,

Thanks for the advice. Not really sure why its just not grabbing the IP, but I think I will load up Ubuntu, Ubuntu seems to be just slightly more "user" friendly than Debian right now.

Thanks again,

Z.

---

### Post by HermanAB on 2009-03-15
ISPs usually track the MAC address of the ethernet adaptor connected to their modem.  If you use a 3rd party router, then that is what will be visible to them.  If your PC plugs directly into the router, then they will see the MAC of the PC ethernet adaptor.  On Windows, you can see the MAC with "ipconfig /all" and on Linux with "ifconfig".

```
You can set the MAC of your machine the same as the expected MAC with:
$ sudo ifconfig hw ether xx:xx:xx:xx:xx:xx

Dhclient should then be able to get the IP address:
$ sudo dhclient -D eth0
```

The -D will show you what is going on.

Cheers,

Herman

---

### Post by bzachd on 2009-04-19
Thanks for all your help. I didnt get back to this until just recently. 
Looking at the MAC, I saw it was loading on eth1, I think eth0 was the wireless (guess).

I took the interface down, then back up. I turned off the cable modem for about 3 min. Turned the machine down. Brought the modem back up and let it cycle. Turned the machine on, and it worked.

I rebooted and watched the DHCP grab the IP.
Waiting to see if it works at his house. 

Hope this helps if anyone else comes across this.

Thanks again.

Zach

---

### Post by Iowan on 2009-04-19
If you connect a different machine (or router) to the modem, you will probably need to repeat the process. As Paul pointed out - if you connect via a router, the modem will still see (only) the router MAC, and all should be well.

---

### Post by bzachd on 2009-04-26
Iowan,

Thank you for the input. Your right, when my friend hooked it up, it wouldnt work. I didnt go with him, so he contacted comcast, and they apparently cycled the router, and it came up just fine. I wonder if this is the same as when I took the eth1 up and down?
Not sure, but it worked. I have seen this topic posted on a number of sites, thanks for the help, hopefully it will help someone else out, especially if they move the machine.

Thanks!!

Zach

---

