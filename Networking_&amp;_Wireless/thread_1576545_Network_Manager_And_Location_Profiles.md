---
title: "Network Manager And Location Profiles"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by crokett on 2010-09-17
I tried searching the forum but mostly got back a lot of hits on Samba.   Google didn't come back with much.  What I want is a location, say at home where I might use the wired connection on my laptop or the wireless.  Likewise at work, I am usually on a wired connection but sometimes need a wireless connection. Can/does Network Manager let me configure a location with preferred adapter, etc and automatically switch or do I need to install something like Wicd?  I don't see anything in Network Manager to do this.

---

### Post by grahammechanical on 2010-09-17
What about using network manager to Edit Connections and then Add a connection? Set up a wireless connection for work. Do not set it up to connect automatically. How you do all of this I cannot tell you because I have never tried it, but I guess you will need the wireless network wireless key. The laptop should detect available networks that should (may be, I am guessing) give you the SSID. Check the settings that are already in network manager for the your home wireless connection. See if you can work out what information is needed to set up a connection with your work wireless network. Does your employer have an IT section that can give you the information you need?

My wireless is detecting seven nearby wireless networks. Two are actually unsecured. If I knew the wireless key of any of the others, I could set up a connection to those networks. When you are not in range you cannot connect. So, there should not be a conflict between the two connections that you want to set up. Sorry for the length of this reply. I must be in one of my long speech moods.

Regards.

---

### Post by crokett on 2010-09-17
thanks but that is not quite what I want.  What I want is a location called, say, 'home' with 2 possible connections.  1 is eth0 (wired)  The other is wireless with the appropriate SSID and security settings.   When I am at home and on wireless, if I plug in a cable, my laptop will automatically switch to a wired connection.  

When I go to work, I choose the profile called Work and Network Manager or whatever changes to the Work profile. Then if I take my laptop off the docking station, it switches to wireless but uses LEAP instead of the WPA I have at home.

As it is now, Network  Manager didn't do a very good job of autoconnecting my wireless.  I had to edit my interfaces file with my home wireless settings to make it truly automatic.

---

