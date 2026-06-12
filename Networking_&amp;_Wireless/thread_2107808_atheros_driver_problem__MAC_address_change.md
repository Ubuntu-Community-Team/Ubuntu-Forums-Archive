---
title: "atheros driver problem :\ MAC address change"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by nmorst on 2013-01-22
Hi all,

Pretty noob with ubuntu... really need some assistance.

Here's the deal. I want to change my MAC address so I can (more) anonymously connect to a wireless network. Unfortunately, I cannot connect to a wifi network after having changed the MAC (I used macchanger (AND manual ether cmd)), after which the MAC is usually automatically reset to default and I can access network again. Now, I have been working on this for a good 20 hrs, reading through fora and trying to get my head around the actual issue. 

This is what I assume is the issue: my atheros wifi adapter has a generic driver (something with ath5k & ath9k), so I should get it to use madwifi drivers instead. I followed this guide in order to do that: 

[[http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_MadWiFi_Wireless_Drivers_on_Ubuntu_10.04]](http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_MadWiFi_Wireless_Drivers_on_Ubuntu_10.04])[1]


So I followed the whole guide, which is pretty up-to-date, but alas, to no avail. After a reboot, the adapter did not work at all and I could not even connect with my default MAC anymore. At startup Lubuntu also took a while to start up, and eventually told me that lubuntu would start up without network settings. 
To get back to "status quo" I had to go back into **/etc/modprobe.d/blacklist.conf** and remove the  "#block ath5k" ,  "blacklist ath9k"  and  "blacklist ath5k" . My card works again, but obviously I still have the same issue. Strongly seems like this is the issue:[[http://forums.eeebuntu.org/viewtopic.php?f=28&t=1997&start=0]](http://forums.eeebuntu.org/viewtopic.php?f=28&t=1997&start=0])[2]. In this thread someone is advocating using "madwifi-hal-0.10.5.6-r3998-20090413.tar.gz" driver, but I have no clue how to do this and not sure if I would be missing anything else to do if I just plainly instally this new driver... Any experience with this?

Possible malfunctions:
- The only deviation from the guide was that when I was going to add  "ath_pci"  in **/etc/modules**, it was already in there! 
- Also, I assume that  "#blacklist ath_pci"  in **/etc/modprobe.dk/blacklist-ath_pci.conf** should indeed be with the "#" in front when saving and exiting.
- Should the newly created "options ath_pci autocreate=adhoc" file be saved in a specific folder maybe?
- In the very last step of the guide, are the parameters maybe off or outdated? ie I just copied and pasted his text in the box into /etc/network/interfaces

My atheros adapter has following parameters (before using the above mentioned guide):

01:00.0
0280: 
168c:002b (rev 01)

AR9285 wireless network adapter (PCI Express)
phys id: 0
logical name wlan0
00:25:d3:78:9b:74
driver=ath9k
driver version=3.2.0-36-generic
802.11 bgn

I really hope someone can help me with getting the new driver installed. It is still quite opaque to me but I need a helping hand with this. Anyone? 
Cheers, much appreciated!

Best Regards,
N LW
PS I run Lubuntu thru a wubi install dual boot, Asus EEEPc 2gb ram

  [1]: [http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_MadWiFi_Wireless_Drivers_on_Ubuntu_10.04](http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_MadWiFi_Wireless_Drivers_on_Ubuntu_10.04)
  [2]: [http://forums.eeebuntu.org/viewtopic.php?f=28&t=1997&start=0](http://forums.eeebuntu.org/viewtopic.php?f=28&t=1997&start=0)

---

### Post by TheOnlyChosenOne on 2013-08-13
*Bump*

I'm having the same issue. Please help!
It works on eth0 tho.

Network card:
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)

---

