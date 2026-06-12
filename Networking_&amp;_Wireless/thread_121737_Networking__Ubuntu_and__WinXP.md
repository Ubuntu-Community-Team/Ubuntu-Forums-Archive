---
title: "Networking  Ubuntu and  WinXP"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by olympic on 2006-01-25
Can anyone point me in the direction of a guide to networking a Ubuntu and a WinXP machine.:confused: 

I have WinXP with a dsl modem, printer connected (which does not work in Ubuntu) and wish to add an Ubuntu machine to access the internet and the printer via the WinXP machine.
Will the printer be accessable and work from Ubuntu[-o< 

Thanks

---

### Post by moephan on 2006-01-25
I assume you've checked here already?:

[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

Cheers, Rick

---

### Post by Adrian on 2006-01-25
[QUOTE=olympic]Can anyone point me in the direction of a guide to networking a Ubuntu and a WinXP machine.:confused: 

I have WinXP with a dsl modem, printer connected (which does not work in Ubuntu) and wish to add an Ubuntu machine to access the internet and the printer via the WinXP machine.
Will the printer be accessable and work from Ubuntu[-o< 

Thanks[/QUOTE]

You can try this to share an Internet connection:

Run the Network Setup Wizard (can be found in the File menu of the Network Connections window). There you can configure Windows to "share an Internet connection". Follow the instructions, and when the wizard finally asks you to create a setup disk for the other computers in the network, just choose "No". 

Now, Windows will act as a DHCP server. This means that you don't have to do any further configuring on the Ubuntu machine (provided that you haven't changed the network settings or disabled the network), since Ubuntu uses DHCP by default.

---

### Post by olympic on 2006-01-26
Thanks Adrian and Rick.

I have tried the "Networking Guide" and I see no problems with the Internet Connection setup.

My main problem is along the line of the printer/scanner which works fine in XP but is not supported by Ubuntu.

I do not particularly want to have to purchase another printer just for Ubuntu - seems to be accepting defeat.

Just have to keep [-o<  and trying.

Cheers

---

