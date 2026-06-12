---
title: "Internet Connection Sharing Issues"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by GeoffVanstone on 2009-11-23
Hey Everyone,

I am trying to share my internet connection to my Xbox 360. I have two network cards in my computer, eth0 is the one connected to my 360 and eth1 is the one that is used to connect me to the internet.

I just recently switched back to ubuntu, and having been reading some tutorials on how to do this, as I knew fairly well how to do it on Windows. One tutorial I read was:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

And I started doing some of the stuff in there, and found i couldn't get it to work, or maybe was due to the fact that the tutorial was a bit old and stuff. So I did do some of the steps, but soon stopped when I got to the 4th step as I couldn't find out how to restart dnsmasq-base, which is what was installed already on my cpu. So I decided to move on to another tutorial I found, on hopes that this one may get the job done. So I found this tutorial:

[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)

And all seemed to be going perfectly fine untill I got to step where I start firestarter firewall and it says:
```
[B][SIZE=4]Failed to Start Firewall[/SIZE]
[/B]the device eth0 is not ready.
please check your network device settings and make sure your internet connection is active.
```

Obviously my internet is working, because I am posting this via the computer I am trying to ICS with my Xbox 360. So, if anyone knows how to fix this issue that would be wonderful. 

PS: Could the firewall be failing due to the steps I followed on the first tutorial? And if so, how can I reverse it, or make my network cards back to their original state?

Thanks Again!

---

### Post by Marogian on 2009-11-23
I had this successfully working on mine in the past after a lot of fiddling, although I'm unable to find the thread which explained how to do it.

I did have it working through firestarter although one of the key components I had setup which appears to be missing from the tutorial you linked to (I did only just glance though) is setting up both the PC Ethernet Connection(via Ubuntu Network Manager) and the X360 connection to different static IPs on a different IP range to your normal network. Then you have to setup the X360's gateway manually to point to your router's IP and have firestarter setup to share Internet. I believe firestarter had DHCP server disabled, although I could be wrong.

The key bit which enabled me to get it working was setting the ethernet connection on the PC to a static IP via the Ubuntu Network Applet, though. After that it was just a matter of fiddling with the X360 settings until everything was pointing at the right place...

I definitely didn't have to fiddle around with any stuff in the terminal or editing the configuration files.

Sorry I can't be more help ^_^

---

### Post by GeoffVanstone on 2009-11-23
Thanks for the help. I think what happened was due to the first tutorial I read, and I may have jacked up my settings on my network card.

Atleast the settings that are saved in ubuntu for that card, so I am probably just gonna re-install ubuntu and not do all the craziness in the terminal and just follow the second tutorial as it seems to work.

---

### Post by GeoffVanstone on 2009-11-23
Okay, well I re-intalled ubuntu 9.10 and I still get the error:

```
[B][SIZE=4]Failed to Start Firewall[/SIZE]
[/B]the device eth0 is not ready.
please check your network device settings and make sure your internet connection is active.
```

I have the settings on my Xbox 360 with the same settings that I have for eth0 with is attached to the 360, plus with the DNS of my ISP Connection. Also, I put the gateway on there that matches my Gateway.

eth1 settings(gets me on the NET):
IP:42.28.41.82
Gateway:42.28.41.81
Subnet Mask:255.255.255.252
Primary DNS: 129.107.62.80
Secondary DNS: 129.107.31.80

eth0 settings (connected to 360):
IP:42.28.41.83
Gateway:42.28.41.81
Subnet Mask:255.255.255.252
Primary DNS: 129.107.62.80
Secondary DNS: 129.107.31.80

---

### Post by Iowan on 2009-11-23
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is (yet another) ICS page.  Hope this one helps - it's not 4 years old.
You may want to choose a different subnet for the sharing connection - otherwise routing gets confused.

---

