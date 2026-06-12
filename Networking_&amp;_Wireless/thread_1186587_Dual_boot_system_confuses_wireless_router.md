---
title: "Dual boot system confuses wireless router?"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by FortyArc on 2009-06-13
I've got 9.04 Jaunty installed on a second hard drive that I've just stuck into my Windows box. My USB wireless adapter is a D-Link DWA-142. I've been using the following tutorial to get my drivers set up using ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Everything up to step 3.5 seems to go as it should. (One oddity: the .inf and .sys files for my adapter drivers have different names; if I use ndiswrapper on the .inf, is it able to use the .sys at all?) After that, I run into problems. 

If I go to System -> Administrative -> Network Tools, I can't find the Enable Roaming tickbox described. I can enter my network name and network passkey, after which the little network status icon at the top just ticks around in circles. If I try to do any other network-related things (opening Network Tools again, for example, or typing ifconfig in a terminal), it seems to freeze up. The Network Tools window will actually not load up completely.

I can shut down Ubuntu normally, but if I boot back into Windows, then my network connection is gone there too. I have to reinstall the drivers and connection software from the D-Link disc in order to connect to the internet, and then I'm fine. But I can't get it to work on Ubuntu at all.

Background: I know a little bit about a command line interface, but I've never administered a Linux system before, so I'm unfamiliar with some of the back-end stuff. Thanks in advance for any help.

---

### Post by FortyArc on 2009-06-13
Update: when I try to start nm-applet, I get this error:

> ** (nm-applet:3519): WARNING **: <WARn>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.   Return: 3

---

### Post by FortyArc on 2009-06-13
Correction, I don't have to reinstall all the drivers in Windows, I just have to unplug and reconnect the USB wireless adapter. 

Er, I've just found the post on what to include in a wireless troubleshooting query. Way to RTFM, self. Okay, I'll be back as soon as I have all that info, although I think I may already have included most of it.

---

