---
title: "Linux Newbie - need help with wireless, etc"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by ccdwiu on 2010-10-26
Ok I got my linux machine up and running. I had to wrap a windows driver for my wireless USB (netgear wpn111) using ndiswrapper. 

My first question is...is there a native linux driver that I could use for this device?
And second...I have set up the driver to load whenever the computer is booted but I am wondering if there is a way to use sudo so that I don't have to type:
sudo dhclient wlan1
every time I boot up. 
I attempted to create a BASH script to run at start up but I am sure most people reading this would know that is not the answer. 

Any input would be great. Thanks!

---

### Post by Der Ritter on 2010-10-26
> **ccdwiu said:**
> 
My first question is...is there a native linux driver that I could use for this device?


No, I don't believe there is a native driver yet. Since it has an Atheros chipset it's under the jurisdiction of [madwifi]("http://madwifi-project.org/wiki") but I don't believe the stick's particular chipset is supported yet.  All three of the madwifi project's drivers (madwifi, ath5k, and ath9k) should be loaded and ready to go if appropriate hardware is detected.

Unlike Windoze, if there is a driver available, when you connect the hardware the correct driver should automatically load. I've only run across one time where I have had to download and install a driver the good old fashioned way.


> **ccdwiu said:**
> 
And second...I have set up the driver to load whenever the computer is  booted but I am wondering if there is a way to use sudo so that I don't  have to type:
sudo dhclient wlan1
every time I boot up. 


Can you see the wireless connection in Network Manager? Head to System -> Preferences -> Network Connections. Click on the Wireless tab and if the connection appears then click on it and then click Edit... Make sure you tick "Connect automatically" at the top of the window, and on the IPv4 Settings tab that Method is set to Automatic (DHCP).

Or, if you've tried that, and it doesn't work...

Open a terminal and run ```
gksudo gedit /etc/network/interfaces
``` and add ```
auto wlan1
iface wlan1 inet dhcp
```to the top of the file, on two separate lines exactly as shown.

---

### Post by ccdwiu on 2010-10-27
> **Der Ritter said:**
> No, I don't believe there is a native driver yet. Since it has an Atheros chipset it's under the jurisdiction of [madwifi]("http://madwifi-project.org/wiki") but I don't believe the stick's particular chipset is supported yet.  All three of the madwifi project's drivers (madwifi, ath5k, and ath9k) should be loaded and ready to go if appropriate hardware is detected.

Unlike Windoze, if there is a driver available, when you connect the hardware the correct driver should automatically load. I've only run across one time where I have had to download and install a driver the good old fashioned way.




Can you see the wireless connection in Network Manager? Head to System -> Preferences -> Network Connections. Click on the Wireless tab and if the connection appears then click on it and then click Edit... Make sure you tick "Connect automatically" at the top of the window, and on the IPv4 Settings tab that Method is set to Automatic (DHCP).

Or, if you've tried that, and it doesn't work...

Open a terminal and run ```
gksudo gedit /etc/network/interfaces
``` and add ```
auto wlan1
iface wlan1 inet dhcp
```to the top of the file, on two separate lines exactly as shown.

Thank you for the reply but unfortunately the connection is not listed under network connections. I also had to set up as static IP because whenever I would request an IP under dhcp my request would just time out. 
Could you possibly tell me how to set it up under static? 
Also, my home network has WEP encryption. That being said, I am also forced to type 

sudo iwconfig wlan1 key xxxxxxx 

every time I boot up

Can you help me with this also? Thank you

---

### Post by Der Ritter on 2010-10-28
> **ccdwiu said:**
> Thank you for the reply but unfortunately the connection is not listed under network connections. I also had to set up as static IP because whenever I would request an IP under dhcp my request would just time out. 
Could you possibly tell me how to set it up under static? 
Also, my home network has WEP encryption. That being said, I am also forced to type 

sudo iwconfig wlan1 key xxxxxxx 

every time I boot up

Can you help me with this also? Thank you

OK, go back and edit /etc/network/interfaces. Add this (and remove the text from my other post if you added it):

```
iface wlan1 inet static
wireless-essid [SSID]
wireless-key [KEY]
address [ADDRESS]
netmask [ADDRESS]
gateway [ADDRESS]

```

obviously replacing [ADDRESS], [SSID] and [KEY] with the appropriate values. Save and restart and see if that works.

---

### Post by ccdwiu on 2010-10-28
AH yes thank you so much, I was missing the wireless-key in that file.
Thanks a ton!

---

