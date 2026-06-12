---
title: "Sharing Internet/LAN eth0 connection via wi-fi ad-hoc network"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by fhsm on 2010-12-01
I'm running Ubuntu 10.10. I've got access to my LAN and the Internet via my wired ethernet connection. I'd like to share that access with my iPod Touch (device shouldn't really matter) via an Ad-hoc wi-fi network.

[This tutorial in the docs]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") seems to describe the right setup but is very out of date (7.04). Instead I found [this tutorial]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") and followed it to create the Ad-hoc wireless network. I was able to connect my touch to the resulting ad-hoc network without a problem, but I didn't have LAN/Internet access.

What's the next step to get the clients on the ad-hoc network out to the Internet?

(for anyone trying to do the reverse - connect wired clients to your Ubuntu system and get them online via your wireless connection - here's a good current [how to]("http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/").)

---

### Post by lrgmmc on 2010-12-01
did you have a look here?
[https://help.ubuntu.com/community/Internet/ConnectionSharing#Wireless Ad-Hoc connection sharing scenario](https://help.ubuntu.com/community/Internet/ConnectionSharing#Wireless Ad-Hoc connection sharing scenario)
 
hope it works?

---

### Post by fhsm on 2010-12-01
I did, in fact I linked to it in my full post. But somehow I seem to have double posted. The full post is actually at: [http://ubuntuforums.org/showthread.php?t=1635043](http://ubuntuforums.org/showthread.php?t=1635043)

If a mod wants to delete this thread that might be a good idea. I'm marking it as solved even though the issue isn't.

---

### Post by BradP on 2011-05-18
I had the same problem as you, and here are the steps I took to solve it:

1. Make sure your Ubuntu machine has a wired and wireless connection.
2. Right-click on Network Manager and select Create New Wireless Network
.....a. Give the network a name (i.e. ipodadhoc)
.....b. Change the wireless security to WEP 40/128-bit Key
.....c. Fill in a key
.....d. Click Create
3. At this point Network Manager should drop your old wireless connection and connect to your new network (ipodadhoc)
4. Right-click on Network Manager and go to Connection Information to verify you now have two active network connections - your wired and your new ad-hoc wireless
5. If you don’t have it already, install the firestarter package from the repository.
6. Once installed, start firestarter and run the wizard
.....a. On the Network device setup
..........i. Select your wired connection for the Detected device(s).
..........ii. If you are on a cable modem or DSL, you should also check the box IP address is assigned via DHCP.
.....b. On the Internet connection sharing setup
..........i. Check the box Enable Internet connection sharing
.....c. On the Ready to start your firewall
..........i. Make sure the box Start firewall now is checked and click Save.
7. Go to your iPod Touch Settings
8. Click on Wi-Fi
9. You should see your newly created ad-hoc network.
10. Click on the network
.....a. You should be prompted for a password.  Enter the password you entered in step 2.c. and click Join
11. Now click on the arrow to the right of your network to get to network settings
.....a. Change it from DHCP to Static
..........i. For an IP address give it an address of one more than the address assigned to your adhoc connection
...............1. To find you adhoc connection IP address, right-click on Network Manager and go to Connection Information.  Then go to the ad-hoc connection tab and look at the IP Address.
...............2. For example, if the ad-hoc IP address is 10.42.43.1, then set the IP address on the iPod Touch to 10.42.43.2
..........ii. Set the Subnet Mask to 255.255.255.0
..........iii. Set the Router to the IP address of your ad-hoc connection (as found in step 11.a.i.1)
..........iv. Set the DNS to the DNS for your wired connection
...............1. To find the DNS for you wired connection, right-click on Network Manager and go to Connection Information.  Then go to the wired connection tab and look at the Primary DNS.
...............2. If you would like to enter more than one DNS, separate the entries by commas.
12. Go back to Wi-Fi Networks and select your ad-hoc network.
13. If all went well and the gods are with you, you should be able to surf the internet on your iPod Touch now.

---

