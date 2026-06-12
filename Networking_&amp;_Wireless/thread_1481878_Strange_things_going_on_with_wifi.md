---
title: "Strange things going on with wifi"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by rostislav_lalalalala on 2010-05-13
Hey. Okay, so basically I got a desktop thats connected to the internet via ethernet, and i got an asus eee 1005ha that connects to the desktop via wifi (the desktop's got a belkin usb wireless adapter). Desktop runs winxp, netbook runs winxp and ubuntu. I've been connecting the netbook to the pc for a month under winxp with no problems. Now, the interesting stuff.
Downloaded ubuntu 10.04, it didn't detect any networks, i installed the official ralink driver (RT3090), nothing happened, then i followed [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) , specifically (as I couldn't stop the network manager): 

"Configuration
Switch the card into ad hoc mode 
sudo iwconfig eth1 mode ad-hoc
Set the channel/frequency that you want to use. 
sudo iwconfig eth1 channel 4
Add the name (ssid) for the network you want to create/join. Use single quotes if there is a space in the name. 
sudo iwconfig eth1 essid 'name'
Add a WEP encryption key 
sudo iwconfig eth1 key 1234567890

Activation
Bring the interface back up 
sudo ifconfig eth1 up
Start dhclient to get an address 
sudo dhclient eth1
If you want to do it manually, you will have to make up an IP address."
And it started to detect networks and connected to an unsecured guest network no probs. But, when i try to connect to my pc, it does so, but no data is being transmitted (dhclient doesnt connect, it doesn't ping either). Now, ONCE after i for the n-th time went through the commands above it connected and worked well, but after i rebooted - same thing.
But thats not all - my desktop started playing up (note it never happened before when i used winxp on the asus) - the ethernet connection stopped working (it connected, but no data went through), i had to reinstall the driver. then it happened again (i never even touched the eth connection!), i also reinstalled it. And when the desktop couldn't connect to the internet - the netbook could connect to the netbook fine.
So yeah. whats going on? i feel like a pawn in some diabolical game of chess

---

### Post by rostislav_lalalalala on 2010-05-13
come on almighty gurus, save my ***. please.

---

### Post by Justice Bucket on 2010-05-16
we're in the same boat. Can't detect any wifi networks.

---

