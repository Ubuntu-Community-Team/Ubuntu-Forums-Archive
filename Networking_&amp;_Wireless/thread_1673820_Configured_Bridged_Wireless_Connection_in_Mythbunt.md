---
title: "Configured Bridged Wireless Connection in Mythbuntu 10"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by allbread on 2011-01-23
Although I do have an alternate means of connecting to my home wireless network I'm approaching this issue now as I'm going to have to figure it out down the line anyways:

I have a (0) Trendnet Wireless-N router that I use for my home network, a (1) Win7 workstation with a companion (Trendnet) wireless-N PCI card installed (this is the connection that I have bridged) and a newly installed Mythbuntu box that I am attempting to update via the bridged ethernet connection. 

(2) Mythbuntu -> (1) Windows 7 -> (0) Trendnet N Router

I am currently getting an IP address conflict on the Mythbuntu box (2) when I attempt to connect to my wireless network (0). Initially this issue was affecting my Win7 box (1) however after reconfiguring the assigned IP address on my router (0) I was able to get the Win7 machine (1) working again. 

I think I've found directions to configure my Mythbuntu box with a static IP address online:

[http://en.kioskea.net/faq/1089-sharing-internet-connection-using-bridge-mode](http://en.kioskea.net/faq/1089-sharing-internet-connection-using-bridge-mode)

However even if I get this working it will be a temporary fix as the MAC address from my Mythbuntu box (2) is seen as 0x0 by my wireless router (0) and thus the router cannot reserve an IP address. 

I'm planning to have my Mythbuntu box operate as my primary media center at which point it will be hardwired however I expect to run into a similar issue as I will need to create a virtual XP machine (using virtualbox) to run Netflix and I expect to have to perform a similar operation with the the virtual machine in order to connect to the network.

What is the best way of accomplishing this - a stable connection to a bridged network connection - in Ubuntu?

---

### Post by allbread on 2011-01-23
Well, I think I figured out a temporary solution; using ICS in Win7 you can pair a single ethernet port with your wireless connection and have it act as a DHCP server. This is a more limited solution than what I was looking for as I currently have two unused ethernet ports however it will suffice for the time being.

In any case this possibly also strays from the realm of Linux towards that of Windows... I knew I was walking a think line to start with. 

If anyone here knows if it's possible to get an Ubuntu box to pass it's MAC address through to a wireless router via a bridged wireless connection let me know. I'd rather have a reserved IP for each of my boxes on my router than be forced to rely on a second layer of DHCP via my Win7 box.

---

