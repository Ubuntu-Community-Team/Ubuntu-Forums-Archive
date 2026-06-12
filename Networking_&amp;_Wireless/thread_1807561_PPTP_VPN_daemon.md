---
title: "PPTP VPN daemon"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by MrDudemeister on 2011-07-19
I've created a VPN server using "pptpd - PPTP VPN daemon" on my Ubuntu computer. I manage to connect to the server via VPN with my windows XP computer and also with my Motorola Xoom.
 
The problem is that I don't get access to the LAN which is what I want. Being able to access the internet via my VPN server is of no interest - just the LAN.
 
Any solutions?

---

### Post by MrDudemeister on 2011-07-20
Is it possible that UFW is blocking port 1723 and that's why I don't get access to LAN, or shouldn't I even be able to connect if that's the case?
 
Also, is it safe to allow TCP traffic on port 1723 in UFW?

---

### Post by entropictrophy on 2011-07-20
Use this guide: [http://eran.sandler.co.il/2010/08/30/pptp-vpn-on-ubuntu-10-04-for-your-iphone-ipad/](http://eran.sandler.co.il/2010/08/30/pptp-vpn-on-ubuntu-10-04-for-your-iphone-ipad/)

If you DID want to access the internet, do the following:
Change the MTU in "/etc/ppp/ip-up", by adding a line after the header: "ifconfig $1 mtu 1400".

You should be able to access your router homepage and other network resources.

Good Luck.

---

