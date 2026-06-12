---
title: "Success VPN from KUBUNTU to Cisco/Windows"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by RudyG on 2011-07-01
Well after countless hours of searching and trial and error I seem to have finally got it to work.
I did not use the kvpnc as it crashes on my setup every time I try to start it. I'm told by the network admin that this is theMicrosoft VPN I'm logging into. Anyway here are the steps I took:

1. System Setting -> Manage Connections
2. Click the VPN tab
3. Click Add
4. At the top give your connection a meaningful name like the name of the company
5. In the Gateway enter the ip address or server string name for the VPN box. On my Windows XP this value is called "Host name or IP address of the destination"
6. Enter your Login name, Password and domain just like in Windows.
7. Click on Advanced and make sure that only MSCHAP, MSCHAPv2 and Allow TCP header compression are checked. Everything else must be unchecked.

In order to actually connect you'll need to click on the network plug looking icon that is in the lower right hand corner of your screen. If your newly created connection doesn't show up there, then you'll need to reboot.

Hope this helps another frustrated soul.

---

