---
title: "TP-Link TL-WN751ND and Ubuntu 13.04 - Will not connect to network"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by skanger on 2013-07-19
I had a group of Ubuntu 10.04 systems (all AMD) for which I installed TP-Link TL-WN751ND PCI card. It was necessary to switch from ethernet cable to wi-fi because of an office location change and an internet service change. 

The systems were functioning perfectly, however, with the installation of the TP-Link cards, the internet connection was lost. After checking all of the machines, it was clearly not a network settings problem since all of the desktops behaved the same and all settings were correct.

I had tried everything possible to get those cards to connect in 10.04 but was told the kernel did not have the ath9k driver. Using one machine to experiment on, I tried updating the kernel but that soon became convoluted and the system would no longer boot. I decided to upgrade all the machines to 13.04 to get this problem resolved as soon as possible but quickly found that I could not get any of the systems to connect to the network under 13.04 either. Again, all network settings were checked and double checked but the results were the same: no connection.

What specifically happens is, Ubuntu shows that its trying to connect to the network, but never does. This can last for several minutes until a request for a network password appears or a message of "not connected" is given. Entering the correct password begins the above process again. 

The network is seen by the system but fails to connect. The network name and other information is passed to the system but it never connects. 


Any help with this problem is greatly appreciated.

---

### Post by TheFu on 2013-07-19
[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) should help you to help us figure this out.  We need to know the chips and drivers loaded.  

You might want to consider my signature too. LTS is your friend when you are a non-expert.

---

### Post by skanger on 2013-07-19
> **TheFu said:**
> [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) should help you to help us figure this out.  We need to know the chips and drivers loaded.  

You might want to consider my signature too. LTS is your friend when you are a non-expert.

thank you for the reply. i'm going to run the commands and post the terminal text here soon. i went through these commands before in another with an individual who took considerable time trying things, but despite that no results. it seems to be a difficult problem.

Lspci shows that the card is recognized by Ubuntu and even with all the correct drivers we could not get the wi-fi to connect.

---

