---
title: "Amilo Pa2548 wireless not working"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by dagenhamdaniel on 2010-12-25
Hi,

I'm brand new to Ubuntu (ver. 10.10), and have a problem regarding my wireless connection: It isn't there!

I have an Amilo Pa2548 laptop with build-in wireless usb adapter.

The wlan-adapter should be this:

> lsusb
Bus 002 Device 002: ID 0bf8:100f Fujitsu Siemens Computers 

I installed ndiswrapper and installed the driver sis163u.inf (XP compitable) as some guide said I should. Blacklisted the bcm43xx-drivers and restarted a few times. Nothing has happended. I have no wireless.

Can anyone help me, please?:)

---

### Post by grahammechanical on 2010-12-25
Here is a link to a trouble shooting guide:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

You have checked the obvious, I suppose? Is the wireless adapter switched on by a FN+ function key combination? I have read that Windows switches off the wireless adapter when it shuts down.

Is wireless set to Automatically Connect? Right click the network manager icon. Select Edit Connections.

While you are right clicking the icon check to see if there are tick marks against Enable Networking and Wireless Networking. If they are not there, then put them there by selecting and clicking. Removing the tick mark switches off Networking. Sometimes disabling Networking and then enabling it  again (switching it off and the on) has the effect of activating the wireless adapter to scan for wireless networks. Sometimes a reboot will get things working.

Regards.

---

