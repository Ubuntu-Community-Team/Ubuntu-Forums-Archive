---
title: "Wireless connects, but network manager still says im disconnected"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by option94 on 2010-05-03
I just installed 10.04, and everything works great, excet for the network manager app. When the computer turns on, it automatically connects to my wireless, and In get the pop up that says connected, but the icon in the taskbar still shows that im disconnected. Any ideas?

---

### Post by Iowan on 2010-05-03
Wireless in Lucid is still a bit "unpolished". Check */etc/network/interfaces* to see if it has more than the two lines defining "lo".

---

### Post by option94 on 2010-05-03
No, just those two lines. It really is the strangest thing. Im connected, but the icon doesn't show it. If I right click and click on connection info, it gives me all of the info about the network im connected too.

---

### Post by Roasted on 2010-05-21
I'm in the same boat. Oddly, I had 10.04 installed before and did not have this issue. I only re-installed 10.04 after I realized that there's ONE particular WPA network that I have to manage that my Ubuntu 10.04 laptop doesn't connect to. Works in 9.10, works in Windows, but not in 10.04. I re-installed thinking something was goofy the first time. The result? I still cannot connect to that WPA network, despite being able to connect to dozens of other WPA networks, yet now it shows I'm disconnected when I'm really connected.

---

### Post by mltriebe on 2010-05-22
Anybody ever solve this issue, I have the same problem.

Mike

---

### Post by olivierb2 on 2010-05-23
Same issue, no problem with my laptop, but same issue on two desktop with same wireless card.
My card are BCM43XG.

---

### Post by thyquest on 2010-05-28
I currently run 10.04 on 2 laptops and one netbook. My main laptop is a Thinkpad using an Intel pro wireless N, the network manager is behaving as expected and displays fine whether connected or not. The other laptop and the netbook are both HP with Broadcom Corporation BCM4328 802.11a/b/g/n, using the proprietary driver broadcom STA wireless driver. Both HP machines are displaying the same behavior, the network manager applet shows as disconnected, although both are connected to my wifi just fine. So, it appears that the problem is limited to a certain type of wireless card. Can anyone else confirm?

---

### Post by luomo on 2010-05-29
I have been facing this problem for a long time. My network Card is BCM b4311. Could anyone help??

---

### Post by scottykal12 on 2010-09-12
Has anybody found a solution to this yet. I have yet to find a solution.

---

### Post by thyquest on 2010-09-13
To resolve this issue, add the following PPA to your sources.list:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) lucid main 

Then: apt-get update 
     apt-get upgrade


To add the signing key, here is the reference page:

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

---

### Post by MaindotC on 2010-09-14
> **thyquest said:**
> To resolve this issue, add the following PPA to your sources.list:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) lucid main 

Then: apt-get update 
     apt-get upgrade


To add the signing key, here is the reference page:

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

This is like telling a windows user "just download and install this file and everything will be fine."  Why are you advising users to add this repository?  What packages or updates does it contain?  How does it pertain the NetworkManager?

Please clarify these things before you adviser users to add an unknown repository to their sources.

---

### Post by thyquest on 2010-09-14
strAlan,

A bug had been reported for this issue if you bother searching for it. 

Here is the link for this bug referencing the workaround I posted.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270)

The link I included as a reference page shows the packages updates that are included in this PPA:

ifupdown 	
isc-dhcp 	
mobile-broadband-provider-info 	
modemmanager
network-manager
network-manager-applet
network-manager-pptp
network-manager-vpnc

Try not to be too aggressive when posting a reply. We leave that to Windows users. :)

Thank you

---

### Post by MaindotC on 2010-09-14
Yeah it wasn't till after I posted that I saw it was the official NetworkManager project page on launchpad.  Sorry about jumping the gun like that.

---

### Post by kriukov on 2011-04-19
I had the same problem. Found a solution (not the best one, but works) here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/539300/comments/34](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/539300/comments/34)

---

