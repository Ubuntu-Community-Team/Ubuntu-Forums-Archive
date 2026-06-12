---
title: "PPTPD Internet Issue"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Jake.Debord on 2011-07-09
I have pptpd server setup on a headless ubuntu server and everything works fine except when i connect to it, the client vpn uses the default gateway on the server. I can uncheck use default gateway on client but i want to setup the pptpd server so i dont have to do this because there are alot of clients going to be using this and it would cut down on support calls if they did not have to go in and disable use default gateway.

This is probably some easy fix by adding a DNS line somewhere but I just do not know where to start!

TIA

---

### Post by jmoorse on 2011-07-12
You are talking about split tunneling right?

What VPN client are they using?  If this is Windows integrated I think you can set this by default when you build the PPTP virtual adapter.  

I recall once I created an installer package for Windows that built all the settings.  Microsoft has some free tool to do this.

---

