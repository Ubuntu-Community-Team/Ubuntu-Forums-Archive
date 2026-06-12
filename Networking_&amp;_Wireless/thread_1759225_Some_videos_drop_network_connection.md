---
title: "Some videos drop network connection"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by nc_jed on 2011-05-15
Folks, I am running 10.10 with the Macbuntu addon (theming, if that makes a difference).  I've noticed for a long time, when I play some videos, my network connection (on this computer only) drops.  For instance, while posting this, I began to watch this video: [HTML]<iframe id="tsFrame55086" src="http://cdn.topspin.net/api/v2/widget/player/55086" style="width:400px;height:300px;border:none;" frameborder="0"/>[/HTML]
About 2 minutes in, my connection is dropped -- I see my Network Manager applet is doing the 'searching' thing.  When I right-click it and uncheck 'Enable Wireless', and then press the physical 'Enable Wireless' button on the laptop, it reconnects.  

My Netgear router has some pretty poor logging and doesn't really reflect anything going on at the time of the problem (just the DHCP assignment on reconnect).  Nothing else loses connectivity, just this machine.  Is it possible something internally is disconnecting me?

- ABT

---

### Post by slooksterpsv on 2011-05-15
Is it just some videos, all videos, certain videos?
Does it happen on youtube videos?
Have you done any recent firmware upgrades on your netgear router?
Does it happen with just videos or do music, games, large downloads cause it to happen to?

---

### Post by nc_jed on 2011-05-15
> Is it just some videos, all videos, certain videos?
I'd say some videos. I'm not sure which ones, I just seem to have to find them.  For instance, Boxee works fine with Hulu videos. 

> Does it happen on youtube videos?
Not that I have noticed.  Perhaps I have just not found the "right ones".

> Have you done any recent firmware upgrades on your netgear router?
No firmware updates ever for me.  FWIW, the firmware always shows as being the most current.  Not sure it's the router, per se, I can watch the same video on my wife's Windows XP Dell laptop without issue (doing so now).  It definitely seems centralized to this machine or installation.

> Does it happen with just videos or do music, games, large downloads cause it to happen to?

Only videos.  I download a lot of torrents from etree ~ 1 GB a piece, stream music via Rhythmbox and every once in a while play only games like OpenArena or Armagetron AD.  It only seems to happen with streaming some/certain videos.

Is there a log that might fit this bill?  Some software I may have installed, like Firestarter/firewall?  Not sure I even have that, but throwing that out there.

- Jed

---

### Post by slooksterpsv on 2011-05-15
May want to try and change your MTU for your wireless to 1400, as sometimes that can fix some wireless issues. If it breaks it we can change it back to Auto.

So go to Dash -> search for: System Settings (click on it) -> Network -> Wireless -> Edit -> MTU 1400


[OFF TOPIC]
I think I found a bug, when I go and edit my wireless it prompts me for authentication - I authenticate. But everything is still grayed out, I have to click close then Edit again to edit the settings.

---

### Post by nc_jed on 2011-05-16
In following some text I found on launchpad, I uninstalled network-manager.  i have my original install cd but can't find it in the list.  I'm screwed.  Any ideas how to install just this package from the original install cd?

---

### Post by nc_jed on 2011-05-16
> **nc_jed said:**
> In following some text I found on launchpad, I uninstalled network-manager.  i have my original install cd but can't find it in the list.  I'm screwed.  Any ideas how to install just this package from the original install cd?

unscrewed.  Booted from live cd, went to ubuntu package search and downloaded network-manager and network-manager-gnome to disk.  rebooted and installed from gdebi.  phew.

---

### Post by nc_jed on 2011-05-16
> **slooksterpsv said:**
> May want to try and change your MTU for your wireless to 1400, as sometimes that can fix some wireless issues. If it breaks it we can change it back to Auto.

So go to Dash -> search for: System Settings (click on it) -> Network -> Wireless -> Edit -> MTU 1400


no effect.

---

### Post by nc_jed on 2011-07-17
Solution: Upgraded to Natty Xubuntu.  Problem solved.

---

