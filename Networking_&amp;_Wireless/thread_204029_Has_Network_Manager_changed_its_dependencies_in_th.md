---
title: "Has Network Manager changed its dependencies in the last few weeks? - WPA issue."
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by nzruss on 2006-06-26
Hi, 

(See the list at the bottom of my post for my hardware / op-sys / networking config) 

[B][COLOR="Red"]Has network manager changed in the last few weeks? Here's why:
[/COLOR][/B]
I did a fresh install on my laptop a *few weeks ago* and got the driver for my my wireless card working with ndiswrapper, no problem. I could iwlist scan ok, etc.  I then installed network-manager-gnome, and it installed the following (from mem) **as dependencies**:
 - network manager
 - wpa_supplicant 
 - (one or two more ? was it wpagui?)
After reboot, it found my WPA network, and asked me for the WPA Key! **ALL GOOD!**

**[COLOR="Red"]Then,  [/COLOR]**
Yesterday, I go through *the same steps *with my other box, and did the following:

Wireless card recognised from install, will 'iwlist scan' and can 'see' network ok. 

Selected 'network-manager-gnome' and the **only dependency **was 'network manager'. 

I then had to instal wpa_supplicant from synaptic *as it wasnt installed as a dependency.*

When I select the network manager interface, firstly it is slightly different than the laptops, and, more importantly:  

[COLOR="Red"]**Network manager only asks me for a WEP Key,  I dont have the the option for a WPA key.** [/COLOR]

I've tried every different combo of installing in a different order, rebooting etc. Network manager just cant seem to recognize my WPA network as WPA!

[COLOR="Green"]**Ive tried**: [/COLOR]

- sources.list = identical (default USA with universe and multiverse added)
- copying the sources.list from the laptop to the other machine
- removing, re-installing nework manager, wpa supplicant, in different orders
- rebooting... Plenty.
- restarting the router (in case it was a broadcast issue)
- Remming (#) the wpasuplicant.conf file exept for Lo, like plenty of forum suggestions. 
- manually configuring wpa.conf files, and init.d/networking files (one time causing it to hang a the start of the x session) But have put them all back to their default.
- reinstalling dapper from the CD, and installing network-manager-gnome from  synaptic *before* doing any updates. 
[added 26 Jun 06 2:18pm CST] - The whole hardware setup worked on the network under Breezy.
- 

[COLOR="Green"]**Ive read through the forums, read as many how-to's as i can find**[/COLOR], but they all want to cofigure the files manually - and some call on files from areas outside my sources.list (so they could be anything!!!). I didnt have to manually configure any files for my laptop, and I do not want to manually configure wpa supplicant files - it is messy and I lose the flexibilty network manager offers(?) 

So my only thought is that somewhere, network-manager changed, or, wpa supplicant changed....?

Is nework manager not 'looking at' wpa_supplcant? - how do I make sure it does?

[COLOR="Red"]**Any assitance to get my mythtv-to-be box to recognize my network as WPA, by Network manager accepting a WPA key, is appreciated. **[/COLOR]

It could be my sources list, if anyone wants to generate the perfect list from here 

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

... I'd appreciate it...

I'll try tonight without universe and multiverse enabled, as I could be getting some crazy later development version..... 

--------------------------------------------------------
Operating systems on both: Dapper-Gnome with all updates

Network: WRT 54G, WPA, PSK-TKIP, SSID B-cast = on, Mac filtering = off, DHCP=on

Laptop: Compaq armada 110s with Linksys WPC54G v 3 (Wlan0), ndiswrapper, Network manager-gnome, - *working flawlessly*

MythTV to be box: AMD ~1.1GHz, Linksys WMP54G v4 (Ra0), etc, network manager(-gnome), WPA supplicant, Driver ok (will iwlist scan) but **[COLOR="Red"]wont recognize my network as a WPA network, and will only accept a Wep key.[/COLOR]**

---

### Post by jml on 2006-06-26
One idea I have is to make sure that the wireless hardware in your second computer is first, capable of supporting WPA encryption.  And second, make sure that the chipset of your second computer's wireless card is supported by wpa_supplicant.  If you go to the wpa supplicant web site, you will find a list of supported chip sets.  

Joe

---

### Post by nzruss on 2006-06-26
Yep the card itself supports WPA, as it was working on the WPA network under Breezy with wpasupplicant.  

(I'm considering reverting to Breezy as this will be my mythtv box and Ive read a few isssues regarding mythtv and dapper.... )

---

