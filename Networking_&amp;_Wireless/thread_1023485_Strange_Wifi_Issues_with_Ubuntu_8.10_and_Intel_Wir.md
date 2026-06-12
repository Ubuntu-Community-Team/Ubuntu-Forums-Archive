---
title: "Strange Wifi Issues with Ubuntu 8.10 and Intel Wireless 5100 on Sony notebook"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by MavericKiller86 on 2008-12-28
I just slapped a fresh install of Ubuntu 8.10 on my notebook and everything worked pretty well out of the box did the updates and attempted to get wifi working. My wireless network is hidden but network manger had an option for that. Entered all the required information and was on my way but kept getting prompted to re-enter password, after about 4 or 5 times of this it finally connected! Then the light for my wireless card started to flash on and off at random intervals. It would stay solid then start flashing, then I'd also randomly get disconnected. I'm a complete noob and have no clue why this is happening or how to fix the problem tried doing some googling and looking on the forums to no avail. I have to go through this process every time I use my computer. Oh and ubuntu did recognize the network card and installed proper driver for it. Any help would be much appreciated. 

My set-up:
Sony VGN-FW290 (CO)
Ubuntu 8.10
Intel Wireless wifi link 5100
D-Link Dir 855 router broadcasting in b, g, and N
WPA2 security

---

### Post by pshootr on 2008-12-28
> **MavericKiller86 said:**
> I just slapped a fresh install of Ubuntu 8.10 on my notebook and everything worked pretty well out of the box did the updates and attempted to get wifi working. My wireless network is hidden but network manger had an option for that. Entered all the required information and was on my way but kept getting prompted to re-enter password, after about 4 or 5 times of this it finally connected! Then the light for my wireless card started to flash on and off at random intervals. It would stay solid then start flashing, then I'd also randomly get disconnected. I'm a complete noob and have no clue why this is happening or how to fix the problem tried doing some googling and looking on the forums to no avail. I have to go through this process every time I use my computer. Oh and ubuntu did recognize the network card and installed proper driver for it. Any help would be much appreciated. 


My set-up:
Sony VGN-FW290 (CO)
Ubuntu 8.10
Intel Wireless wifi link 5100
D-Link Dir 855 router broadcasting in b, g, and N
WPA2 security


It would be interesting to see if you would still have the same problem when using a different router. I have heard nothing but horror stories about D-Link routers.

---

### Post by MavericKiller86 on 2008-12-28
doubt it's the router, its pcmag's top rated router haha or at least was a little while ago. besides I don't think that would explain the flashing wireless light or why it works fine under windows with no additional router software needed :(

---

### Post by MavericKiller86 on 2008-12-28
Anyone anything? This is a real pain :( any help would be appreciated. Thanks again.

---

### Post by The Cog on 2008-12-28
It may be worth trying wicd instead of network-manager. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) You can get a .deb for wicd here:
[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=649033](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=649033)

---

### Post by MavericKiller86 on 2008-12-28
Ok so installed wicd and it seems to be working flawlessly with no problems. But I think I may have messed up the network manager un-install, I went to synaptic package manager and removed it, but the network manager applet is still there and there's no wicd applet??? I know this probably seems pretty noobish but any help would be appreciated on how to remove the net-manager applet and add the wicd applet if there is one. Thanks again

---

### Post by MavericKiller86 on 2008-12-29
Never mind a restart fixed all of the issues everything's up and running now as far as I can tell. Thanks for the suggestions and help.

---

