---
title: "Share broadband dongle connection using ad-hoc wireless network"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by vegegoku on 2011-05-20
The following will describe the way if sharing a broadband dungle internet connection with other computers
these steps contains two parts :
1- configure the laptop that has the dongle plugged to it, lets name it here the provider:

steps :

 a- plug the dongle to your laptop and connect internet normaly.
 b- create an ad-hoc wireless network following these steps :

[LIST]
[*]right click the network try icon and select edit connections.
[*]select the wireless tab
[*]click add, a new popup window will show up.
[*]from the mode dropdown select AD-HOC
[*]give it any name you want.
[*]connect to this ad-hoc network.
[*]in the IPv4 settings tab set your settings as the following
[LIST]
[*]address : 192.168.0.x (replace the with any 3 digits number)
[*]Netmask :255.255.255.0
[*]leave the gateway empty or 0.0.0.0
[/LIST]
[*]apply your changes.
[*]install firestarter and run, then follow the wizard and select the following options
[LIST]
[*]first step select Dialup device (ppp0).
[*]second step check the enable internet connection sharing and select your wireless card adapter from the list.
[*]complete the wizard and make sure the firestarter is active if not click the start button.
[/LIST]
[/LIST]
the provider configurations now are done.

2- the laptop that want share this Internet connection lets call it the client :

[LIST]
[*]click the network try icon on the top panel
[*]find the ad-hoc network u created in the provider laptop.
[*]if you didn't find it click on connect to hidden wireless network, and use the dialogue to connect to it.
[*] right click the network try icon and select edit connections.
[*]now from the wireless tab select the ad-hoc network and click edit
[*]in the IPv4 settings tab set the following options as the following :
[LIST]
[*]address : 192.168.0.y (replace y with any 3 digits number that is not equal x which you used in the provider machine)
[*]NetMask : 255.255.255.0
[*]gateway : 192.168.0.x (which is the same ip address you assigned to the provider laptop)
[*]DNS : 208.67.222.222 (or any other dns server you prefer).
[*]apply your changes.
[/LIST]
[*]restart networking and connect again to the ad-hoc network.
[/LIST]
and thats all .. done.
now u have internet on both laptops and even you can use the same client configurations of the client laptop for any device (mobile phone for example), but make sure you assign a unique address for each device.

---

