---
title: "Configure Wireless at Boot"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by icanfly0307 on 2009-06-14
Hi, I have a wireless adapter that automatically gets started at boot time. However, it doesn't connect to my wireless network until I log on and Network Manager takes over. I want to get Network Manager out of the way and configure my wireless the "traditional" ifconfig way. Since I am running KDE, I don't have access to GNOME's network configuration tools. So I have two questions:

1. Can someone point me to a guide which describes how to configure my network through the configuration files?

2. Which packages do I need to install in order to get the GNOME network configuration tools?

I am trying to get my problem solved by either of the two approaches. Any help on this issue would be really appreciated. Thanks. :D

---

### Post by cpdondo on 2009-06-14
I have the same problem except worse.  I authenticate via ldap.  I need the network connection to reach the ldap server.

I can't get wireless to start unless I log in.
I can't log in until I get wireless going.

Surely someone has solved this?  How do you start wireless without logging in?

Better yet, how does one configure a laptop with Ubuntu?  I'm an ubuntu newbie but I've worked with Debian for years.  I've already learned that the debian way is not always the ubuntu way.  :-)

---

### Post by icanfly0307 on 2009-06-14
Hi, cpdondo. I managed to fix my problem. Here's how:

1. Make sure that your wireless device is started at boot time (ie, the correct modules are loaded)
2. Add the following lines to your "/etc/network/interfaces" file:

# Wireless Network Configuration
auto wlan0
iface wlan0 inet dhcp
wireless-essid  <i>your essid here</i>
wireless-key     <i>your network key here</i>
wireless-channel 11
wireless-mode    managed

3. Save the file, reboot and you should have your wireless running.

Post back if you run into problems and I'll try my best to sort out your issue. Hope this helps. :)

---

### Post by cpdondo on 2009-06-15
I was able to connect after login from the nm-applet widget.  But I cannot connect from the command line:

root@ariel:/etc/network# cat interfaces
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
	wireless-essid xx
	wireless-key s:xx
	wireless-mode managed
	wireless-channel 13


root@ariel:/etc/network# ifup ra0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Network is down.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ra0 ; Network is down.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device ra0 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Network is down.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:15:af:bb:48:70
Sending on   LPF/ra0/00:15:af:bb:48:70
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

If I kill nm-system-settings I can connect...  So how do I deal with this?

---

### Post by icanfly0307 on 2009-06-15
From what I see above, I think you need to disable NetworkManager completely. Since NetworkManager is set as your default network configurer, it won't let the "traditional" ifup command take over your interfaces. Try this:

1. Open up a terminal: Type "sudo apt-get install sysv-rc-conf"
2. After the installation is complete, type: "sudo sysv-rc-conf"
3. This will give you the list of services that startup at boot. Scroll down (with your keyboard arrow buttons) until you see "NetworkManager".
4. There should be a few of these thingys: [X]. Highlight each [X] and press space to clear the box: [].
5. Once all of the [X] have been changed to [] (ONLY for NetworkManager), press "q". Reboot and try to connect from the commandline again.

Hope this helps.

---

### Post by BCCS on 2009-08-20
icanfly0307,

I am running Ubuntu 9.04.  I modified the interfaces file and turned off Network Manager.  At the login screen when I try to log in as an ldap user without the network cable plugged in, it tells me, Incorrect username...

If I log in as the local administrator I can log in but Firefox will not let me go on-line.
If I run ifup wlan0, it says ifup: interface wlan0 already configured.

What setting do I still need to modify to log in as an ldap user with only wireless?

---

### Post by BCCS on 2009-08-25
I found the answer on a different thread: [http://ubuntuforums.org/showthread.php?t=1149770&highlight=wireless+ldap](http://ubuntuforums.org/showthread.php?t=1149770&highlight=wireless+ldap)

---

