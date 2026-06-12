---
title: "Sharing Internet/LAN eth0 connection via wi-fi ad-hoc network"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by fhsm on 2010-12-01
I'm running Ubuntu 10.10. I've got access to my LAN and the Internet via my wired ethernet connection. I'd like to share that access with my iPod Touch (device shouldn't really matter) via an Ad-hoc wi-fi network.

[This tutorial in the docs]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") seems to describe the right setup but is very out of date (7.04). Instead I found [this tutorial]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") and followed it to create the Ad-hoc wireless network. I was able to connect my touch to the resulting ad-hoc network without a problem, but I didn't have LAN/Internet access.

What's the next step to get the clients on the ad-hoc network out to the Internet?

I found [this page]("https://help.ubuntu.com/community/Internet/ConnectionSharing") in the docs that says I'd need to install dnsmasq-base and uninstalling dnsmasq. I checked and dnsmasq-base is already installed but dnsmasq is not. I do have dnsmasq in /usr/sbin but the package description makes it sound like this should come with dnsmasq. Is the page out of date? Will uninstalling dnsmasq cause other problems?

(for anyone trying to do the reverse - connect wired clients to your Ubuntu system and get them online via your wireless connection - here's a good current [how to]("http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/").)

---

### Post by alan2796 on 2010-12-01
This something i am also trying to do at the moment.

a couple months ago when I was in Portugal I did this with my 3G Dongle to allow my friends we were on holiday with to use my internet connection with a iPhone and a iTouch via a ad-hoc network and from what I remember it just worked out of the box.

if you create a ad-hoc network I think you need to enable internet connection sharing on the wired connection before it works ?

and does anyone know if it's possible to connect all via wifi ?

iTouch > Ubuntu > Router > Internet

or would you need 2 wireless networking adapters ?

---

### Post by lrgmmc on 2010-12-01
please dont double post.

---

### Post by fhsm on 2010-12-01
Somehow I double posted this halfway through writing it. The other thread is at [http://ubuntuforums.org/showthread.php?t=1635039](http://ubuntuforums.org/showthread.php?t=1635039) and should be ignored. I've market that one solved, although the actual issue is not & this thread isn't market as solved.

---

### Post by spiky001 on 2010-12-01
If you have set up the connection that yo want the other devices to connect to as shared connection all should be good

---

### Post by dckirba on 2010-12-03
Hi guys,

I was trying a similar setup today though it's not exactly the same as what you've mentioned.

* I have internet access via wireless broadband on my Ubuntu laptop. 
* I want to share it to one Mac and another Windows laptop via wireless.

I followed these steps and all went well:

1. Set up a new wireless connection, give it any name you like
2. In the drop-down menu under Mode, choose Ad-hoc
3. under the IPv4 settings tab, change the method to 'Shared to other computers'
4. Click Apply

That's it.

I connected to the new wireless network on the Mac and it was able to connect to the internet via the mobile broadband on the Ubuntu laptop.

I hope this helps, please let me know if it does.

I'm using Ubuntu 10.10.

---

### Post by fhsm on 2010-12-03
I got it working. I followed [this guide]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Wireless Ad-Hoc connection sharing scenario").

Additional observations / changes: 
[LIST]
[*]I had dnsmasq-base installed and not dnsmasq, not sure if that's specific to my system or everyones baseline.
[*]*WPE128* and WPA aren't supported. WEP40 and wide open were the only two setups I got working.
[*]Restarting network-manager isn't adequate. I have to do a full restart.
[*]The network has to be named UbuntuAdhoc (case sensitive).
[/LIST]

A lot of this seems arbitrary to me but it reliability works this way and stops working if I change any of these things.

---

### Post by alan2796 on 2010-12-04
> **dckirba said:**
> Hi guys,

I was trying a similar setup today though it's not exactly the same as what you've mentioned.

* I have internet access via wireless broadband on my Ubuntu laptop. 
* I want to share it to one Mac and another Windows laptop via wireless.

I followed these steps and all went well:

1. Set up a new wireless connection, give it any name you like
2. In the drop-down menu under Mode, choose Ad-hoc
3. under the IPv4 settings tab, change the method to 'Shared to other computers'
4. Click Apply

That's it.

I connected to the new wireless network on the Mac and it was able to connect to the internet via the mobile broadband on the Ubuntu laptop.

I hope this helps, please let me know if it does.

I'm using Ubuntu 10.10.

When i create a new ad-hoc network which I can connect to with my iTouch it subsequently disconnects my connection to my wireless router and my connection to the internet any ideas what im doing wrong ?

---

### Post by alan2796 on 2010-12-04
Sorry I just picked up on  a slight bit of confusion here,

I Did this  without any problems it "Just Worked" Connect a 3G Dongle or Mobile Phone to Ubuntu and setup a Adhoc network for others to use and it worked just fine.

iTouch > Ubuntu Wireless > Mobile Broadband > Internet

Howeveri am now replacing my Mobile Broadband with a Wired Connection or a Wireless Connection.

eth0 = Wired Network Adapter
eth1 = Wireless Network Adapter
wlan0 = Wireless USB Adapter

iTouch - eth1  eth0 - Internet
iTouch - eth1  wlan0 - Internet

---

### Post by alan2796 on 2010-12-05
Have Successfully set this up now with my 2 Wireless adapters.

Upgraded to 10.10
Installed Firestarter

Setup a Ad-hoc Network Connection and set the IPV4 Tab to shared to other computers and started it on eth1 (Laptop Wireless Card)

Then Connected to my Wireless Router with wlan0 (USB Wireless Adapter)

Opened up Firestarter and enabled Internet Connection Sharing on  eth1 and wlan0, then Firestarter was blocking the iTouch from accessing the internet, so unblocked it and away it worked.

---

### Post by dckirba on 2010-12-22
Does anyone know how to get security going on an adhoc connection? The network shows up on every laptop in the compound and I don't need everyone sharing the internet connection because we pay by data transfer.

---

### Post by lrgmmc on 2010-12-22
have you looked into firestarter? i think you can set rules.

---

