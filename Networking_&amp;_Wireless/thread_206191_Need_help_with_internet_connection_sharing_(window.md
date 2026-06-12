---
title: "Need help with internet connection sharing (windows host, ubuntu client)"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by seeknowsage on 2006-06-29
Please forgive me for the cross post from the desktop forum, but I'm fairly desparate for a solution.

I am a complete newbie to LINUX/Ubuntu and I need some aid in getting a network I've setup up and running so both machines can connect to the net. As it is, I've followed the HOW-TO found at [http://ubuntuforums.org/showthread.php?t=72076](http://ubuntuforums.org/showthread.php?t=72076). My setup is almost exactly the same: I have a cable modem connected to an onboard nic on my windows machine, which is in turn connected to my ubuntu machine through a second onboard nic. I am able to ping either machine in my network from one another just fine. My windows machine can connect to the net just fine. However, I can't connect to anything on the Ubuntu side. Any and all help would be greatly appreciated (though I ask you kindly to not suggest reversing it so the Ubuntu machine is the gateway; remember, I'm still trying to get the hang of new razz-a-matazz. ;)

Also...

I somehow managed to get it working last night, but for the life of me I don't recall how (and I was moronic enough not to record the url of the steps I believe I followed). However, after messing around with things I didn't quiet grasp (again, my own ignorance for the win!), I decided to reinstall ubuntu 6.06 from the cd. I followed the guide listed in the first post for setting up my two machines to connect to the net. However, I'm back to square one again: My client ubuntu machine can ping my Windows XP host machine/nic and even my cable modem. However, it can't connect to the net at all. On the other hand, my Windows XP system can access the net. Any and all advice would be greatly appreciated. (If I run the cable modem directly to the ubuntu machine, I am able to access the net. This is not a viable solution since my primary machine will continue to be the Windows system I run for the immediate future.) Thank you.

---

### Post by seeknowsage on 2006-06-29
Further update: When I setup ICS on my WinXP machine and assign the sharing nic an ip of 192.168.0.1, and when I setup the nic on the client Ubuntu system with an ip of 192.168.0.2 and a gateway of 192.168.0.1, I'm able to ping the host nic, 127.0.0.1/cable modem, and the ip assigned by my isp. Moreover, it appears as though I can ping ip's for various websites (yahoo, digg, etc.). However, I am only able to do so one time; if I ping another ip or close the networking tools window in Ubuntu, I can't ping the same ip. Nevertheless, I am able to still ping other ip's.

Is this a DNS issue? (I know for a fact that I didn't alter this when it was running last night.) Do I have to do some special configuration to my nic I have yet to see? (As it is, the various pages I've read covering this suggest I only need to assign an ip and gateway to the shared system/nic.)

---

