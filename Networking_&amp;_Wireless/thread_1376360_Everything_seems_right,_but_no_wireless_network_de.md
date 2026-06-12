---
title: "Everything seems right, but no wireless network detected"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Mitchgo on 2010-01-09
I recently purchased a new windows system, So I turned my old system into the new Ubuntu 9.1 . I'm new to ubuntu and linux in general but I'm a resourceful person.  

My issue is that I do not see a wireless network available after going to System>Admin>Network> Wireless

I have a PCI Airlink AWLH4030 wireless card.
The Support list states this card works fine 'out of the box'
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#PCI)

Before I post the rest of the info I want to say that My router is upstairs and my computer is downstairs. I can take my laptop downstairs and receive full bars.  I also just fixed a friends computer and used the computer set up downstairs-  I used the same Airlink card that I have in the ubuntu system in his computer and I had full bars wirelessly.

Because I can't figure out how to read a ubuntu  text document on a windows I'm posting pictures of  the sudo lshw -C network, Iwconfig, Ifconfig and a picture of the network connections> wireless. 

Also using the wireless trouble shooting
[https://help.ubuntu.com/8.10/internet/C/troubleshooting.html](https://help.ubuntu.com/8.10/internet/C/troubleshooting.html)
After doing the Sudo lshw -c it says You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED"

I don't see any of these anywhere.

I also attempted to manually enter in my network using the router's wireless information. I'm not sure what a BSSID is but after some research it seems to be the same as the mac address for the router?  ( I made these the same)  I entered in the information in correctly with no success

Thank you in advance for helping.

---

### Post by chili555 on 2010-01-09
> My issue is that I do not see a wireless network available after going to System>Admin>Network> WirelessYou are simply looking in the wrong place! You should click the Network Manager icon, usually at the upper right of your desktop. You will see a list of available networks like the attached. Click on yours and you will be prompted for any WEP or WPA key and you should connect.

All the details you have provided indicate a healthy wireless device that's working fine, but simply hasn't yet connected.

---

### Post by chili555 on 2010-01-09
> Because I can't figure out how to read a ubuntu text document on a windows You can convert your terminal output to a text document easily:```
sudo lshw -C network > lshw.txt
```Then you will find a text document in your /home/user directory, in this case *lshw.txt*, which you can drag-n-drop onto a flash drive and see it in Windows with, IIRC, wordpad.

---

### Post by BlackDave on 2010-01-09
Hi I am having the same problem but with My Dell Studio 1555 which dual boots fine with my windows 7 installation.

---

### Post by Mitchgo on 2010-01-09
Thank you so much for your help!
I can't believe it was that easy!

I'm irritated that the 'help' doesn't actually state where the network manager is.. Thus leading me to the network connections.

---

### Post by chili555 on 2010-01-09
Glad it's working! Enjoy!

---

