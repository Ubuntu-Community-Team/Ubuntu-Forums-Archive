---
title: "Network (Wireless) Bridging, help please!"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by sh_son on 2008-12-12
Hi,

I just moved my house and ran kismet to find a best spot for cable modem and wireless router. But since the house is huge, I had to drag a LAN wire through the hall or purchase two cheap APs to bridge the connection from first to third floor.

I've a up-to-date DI-524 wireless router hooked up with the modem, DI-624S for network sharing + printer for me. So, I want to bridge those two separated routers together with 'Access Points'.

I attached my network topology, is this possible?
I'm not sure i'm thinking right though, please fix me if I got anything wrong.

Thank you and sorry for my bad English :)

---

### Post by jmoorse on 2008-12-12
This should work fine for your setup:

Internet--Router--AP ~~~~~~~~~ AP--Switch--Devices



I would highly recommend Buffalo Access Points supported by DD-WRT (supports bridging) [http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)

No need to setup a separate routed segment unless absolutely necessary

You could even collapse the Router--AP into one of said devices if desired

---

