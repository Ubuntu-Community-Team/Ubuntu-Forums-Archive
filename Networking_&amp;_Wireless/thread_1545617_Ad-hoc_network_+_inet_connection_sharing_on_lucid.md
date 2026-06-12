---
title: "Ad-hoc network + inet connection sharing on lucid"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Palal on 2010-08-04
Here's the setup:
I have 2 laptops:
1. Dell Inspiron 8600 with an intel 2200BG wifi card (Ubuntu 10.04)
2. Asus eeePC 1000 (Ubuntu 9.04)

Internet setup: 
Laptop 1 connects to a 3G connection and shares it with laptop 2 using an ad-hoc network.

I upgraded to Lucid on Laptop 1. Prior to the upgrade everything was working.

Now, when laptop 1 tries to connect to the ad-hoc network it almost immediately disconnects and tries to reconnect again.

Ad-hoc network settings:
The ad-hoc network uses a WEP key. In IPv4 settings, "Share to other computers" is selected. 

Dmesg output:
```
are: requesting ipw2200-bss.fw
[ 1551.015706] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1552.607729] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1556.007822] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1557.512530] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1561.077797] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1564.535341] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1565.215610] pidgin[2399]: segfault at 0 ip 00410c25 sp bfde9f80 error 4 in libpurple.so.0.7.0[3df000+fb000]
[ 1568.005199] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1569.516652] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1573.004207] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1574.533915] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1578.006554] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1579.528254] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1583.005841] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1584.534866] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 1588.005410] ipw2200 0000:02:03.0: firmware: requesting ipw2200-ibss.fw
[ 1589.532357] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
...keeps going forever...

```nm-applet output:

```

alex@laptop11:~$ nm-applet
** (nm-applet:4259): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4259): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4259): DEBUG: foo_client_state_changed_cb
** (nm-applet:4259): DEBUG: foo_client_state_changed_cb                                         <<=== 3G NETWORK CONNECTED
** (nm-applet:4259): DEBUG: old state indicates that this was not a disconnect 9

** (nm-applet:4259): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/326: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist     <<===== TRYING TO CONNECT TO THE AD-HOC NETWORK ======



** (nm-applet:4259): WARNING **: _nm_object_get_property: Error getting 'Default' for /org/freedesktop/NetworkManager/ActiveConnection/326: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:4259): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:4259): DEBUG: old state indicates that this was not a disconnect 9

** (nm-applet:4259): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/327: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:4259): WARNING **: _nm_object_get_property: Error getting 'Default' for /org/freedesktop/NetworkManager/ActiveConnection/327: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:4259): DEBUG: going for offline with icon: notification-network-wireless-disconnected

```Thanks.

---

### Post by Palal on 2010-08-04
To add to this, if I set up the ad-hoc network using any of the other methods (Manual, DHCP, etc.) then it sets up fine and "connects" to itself. However, this sort of defeats the purpose of sharing the Internet  connection.

If I connect the two computers manually, they connect fine, but I can't share the internet connection between the two, and laptop 1 is also unable to connect to the internet using the 3G connection.

---

### Post by manishrana on 2010-08-04
Can Anyone tell me how to share internet between two laptops.. I have USB mobile broadband connection of tata photon+..
Plz tell me for both of following cases :
case 1. The two laptops have ubuntu 10.04 installed on them.
case 2. One laptop has windows 7 & other has ubuntu 10.04.

Tell me on which system i should connect the modem & how to access internet with that.

---

### Post by philetus on 2010-08-04
Here's my immediate problem:

I open "Create new wireless network"

Network Name: UbuntuAdhoc
Wireless Security:none 

The create button is unavailable

---

### Post by Palal on 2010-08-04
> **philetus said:**
> Here's my immediate problem:

I open "Create new wireless network"

Network Name: UbuntuAdhoc
Wireless Security:none 

The create button is unavailable
I can reproduce your problem. Change "UbuntuAdhoc" to "UbuntuAdho" and then back to "UbuntuAdhoc". The button should become enabled.

---

### Post by Palal on 2010-08-04
Found someone else with this problem:
[http://ubuntuforums.org/showthread.php?t=1412707](http://ubuntuforums.org/showthread.php?t=1412707)

---

### Post by philetus on 2010-08-04
> **Palal said:**
> I can reproduce your problem. Change "UbuntuAdhoc" to "UbuntuAdho" and then back to "UbuntuAdhoc". The button should become enabled.

That did work. Thanks.

The adhoc is up.
The other computer sees it and asks for a network/WPA key.

Is this the password I put in WPA & WPA2 personal?

also, the up and down arrows have disappeared from my tray.

---

### Post by Palal on 2010-08-04
I'm not sure that WPA/WPA2 works with Ad-hoc in Ubuntu (it might, but I haven't gotten it to work). It will definitely not work if you want to connect other devices that don't support WPA. Try using WEP for now and switch to WPA/WPA2 if it works. 

The network key is what you entered on your first computer. The second computer will ask for it when you connect.

---

### Post by Palal on 2010-08-04
So can anyone help me with my problem?
How can I get inet sharing on 2 computers when one of them uses a 3G connection?

---

### Post by Palal on 2010-08-04
In the end what worked is this:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
which I don't think is necessary
and uninstaling dnsmasq. Apparently I had 2 versions installed and they were both trying to work at the same time.

Problem solved.

---

### Post by djbelieny on 2010-09-01
Just did this on Lucid and it was quite simple:
- click on network manager and select create a new wireless network
- Fill in the network name
- Select the Security settings (WPA did not work had to fall-back to WEP)
- Type in your key or pass-phrase
- Click Create and wait for the popup saying that you are now connected to the [network name].

Go to your other computer and choose the new ad-hoc network which should be showing there by now.

Voila! Working ad-hoc network.
My setup now looks like this: 

MAC <----WIFI----> PC(Ubuntu 10.4) <-----USB+3G----> Intertubes 

Nice little emergency setup.

---

### Post by lomuk on 2011-03-26
Ubuntu 10.10
Standard install

Go to System | Preferences | Network Connections

Select the 'Wireless' tab.
Click the 'Add' button.
Enter a Connection name - say 'Ad-hoc wireless'
Enter your SSID - say 'seungmongx'
**Select 'Ad-hoc' from the 'Mode' drop-down.**
 
Select the 'Wireless Security' tab
Suggest WEP 40/128-bit key, assuming the other machine(s) support it.
Suggest you click the 'Show key' box
Enter the key - 13 characters, such as AB321zx43mnKB

Select the 'IPv4 Settings' tab
**From the 'Method' drop-down select 'Shared to other computers'.**

Click the 'Apply' button.

Your chosen SSID should appear in the other machine's wireless network list within a few seconds and you can connect.
Worked for me (cable modem - Ubuntu 10.10 - wireless - Mac OSX)

---

