---
title: "wicd issues"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by crokett on 2009-03-07
I was having problems with connecting to my LEAP wireless network at work so on a suggestion I read here I installed wicd.  It let me connect at work just fine but at home it takes 3-4 minutes to receive an IP address from my router each time my laptop comes out of suspend mode.  I have 3 windows machines with no issues and before I installed wicd the default network-admin had no issues.  I finally uninstalled it and am back to network-admin.  

I think part of the problem with wicd was confusing my home and work networks.  I went through wireless-settings.conf and the section with the SSID for my home network had wmy work username LEAP logon in it. My home network does not broadcast the SSID.  For some reason wicd also insisted that there were two networks, one hidden and one that matched my SSID. It seems a good program but does not appear stable.  Any suggestions?

---

