---
title: "Trouble With /etc/kismet/kismet.conf on Ubuntu Maverick 10.10 With Atheros AR928X."
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by pizzaholic on 2010-12-02
I have Kismet installed on my HP Pavilion DV7 Notebook which is using an Atheros network card. In **etc/kismet/kismet.conf** I don't know what to enter in order to get the program up and running. I have set

```
suiduser=myusername
```

but I don't know what to put for

```
source=
```

I found out by browsing around forums and Google that my Atheros chipset was an AR928X by using the ```
lscpi | grep Network
``` command. In a few forums they are saying to put ```
source=madwifi_g,ath0,madwifi
``` , but when I type ifconfig I see wlan0 and nothing at all related to ath0. Trying this with sudo kismet while my source=madwifi_g,**wlan0**,madwifi results in this error:

[B]Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (madwifi): Enabling monitor mode for madwifi_g source interface wlan0 channel 6...
ERROR:  Unable to create VAP: Operation not supported
ERROR:  Unable to create monitor-mode VAP
WARNING: wlan0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.
[/B]
In some [other forum]("http://ubuntuforums.org/showthread.php?t=1186348") on UbuntuForums someone said to make some changes under SYSTEM>>ADMINISTRATION>>HARDWARE DRIVERS, but I don't have HARDWARE DRIVERS under that submenu. I don't see an option for it anywhere in my version of Ubuntu (Maverick 10.10).

Do I even need madwifi? I hardly know anything about it other than the fact that it's a driver for wireless cards. My wireless card seems to work just fine as I'm online right now...but I don't know what information to put into **sources=** in my **/etc/kismet/kismet.conf** file.

Thanks for your help

---

