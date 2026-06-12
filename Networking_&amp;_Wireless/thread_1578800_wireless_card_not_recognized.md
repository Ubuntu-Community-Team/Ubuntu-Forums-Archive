---
title: "wireless card not recognized?"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by eudemonis on 2010-09-21
Hi, I'm not sure what the problem is with my wireless but as far as I can tell the wireless card on my other laptop is not being recognized. I've had the wireless working before but either after one of the updates or after my wife played with it now the wireless doesn't work anymore.
 
My machine is HP Pavilion dv2000
I'm running Ubuntu 9.10
kernel 2.6.31-17-genric i686
grafic card: nVidia
wireless card nVidia Corporation MCP51 Ethernet Controler (I guess)

I've been trying to figure this out the prolbem using the     
* WifiDocs * WirelessTroubleShootingGuide
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#manual](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#manual)

this is how for i got...
after typing nm-tool**** command
status shows disconnected
after doing lshw -C network command nothing shows up (which I assume means the card is not recognized)
I've tried following the part called "manual device installation" but I didn't get far. After doing  sudo pccardctl ident command I get no output.
Any ideas what I should do next?

---

