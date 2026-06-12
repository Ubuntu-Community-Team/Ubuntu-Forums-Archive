---
title: "Strange DWL-G520 problem."
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by Misht86 on 2005-12-14
My wireless card should be compatible (according to this site). During my Ubuntu installation, the DHCP couldn't be detected, so I now have to manually configure my network I guess.

This is the strange part.

Unless the drivers come pre-loaded, I havn't put any drivers on, and yet it is still detecting the wireless network. I have the CD with the windows drivers on, but even if they work on Linux, I don't know where to put them.

So to summarise:

Are the drivers pre-loaded?
Should I install them from my CD?
What might they be called?
Where should they go?

DHCP? What am I meant to do with that?

Thanks in advance,

Mike

---

### Post by Lambert on 2005-12-14
The g520 shows an atheros chipset in the card which uses the madwifi driver (which is built into breezy) So when you plug your card in it should automatically load the driver for the device. You know your driver is working if you see the card in the list in system>admin>networking or if you run the command *iwconfig*.

to verify it's atheros you can run the command *lspci -v*

So you say dhcp couldn't be detected. What kind of wireless set up do you have. oepn? wep? wpa? If wep, open or shared? hexa or ascii key?

---

### Post by Pimpity Snicket on 2006-05-01
I just got mine G520 rev b1 working a few minutes ago.  It's been a pain in the neck but I finally figured out what my problem was.  To answer your question, the madwifi drivers should preload and come w/ Ubuntu.  If you type 'iwconfig ath0' you should get some info about the card meaning the modules loaded properly.

I just came across this guide which solved my problem:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

I had my key set and everything but I couldn't figure out why I couldn't get online.  I used dhclient to try and get an IP but it wasn't working.  I read through that guide and it says:
```
 When using wep, check driver files such as README as some drivers need a command to adjust the mode to work properly. Here are a couple examples.

*Madwifi driver needs to change to authmode 2 when using shared key setting.

o  manually from command line iwpriv ath0 authmode 2
o  add line pre-up iwpriv ath0 authmode 2 to interfaces file to automate during boot
```

That little piece of info was very important.  I entered it in (using sudo of course) and then tried 'sudo dhclient ath0'.  w00t!  and I'm online.  Hopefully that fixes your problem.

---

