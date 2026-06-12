---
title: "VPN or something?"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2011-01-06
Hello

I am traveling to the UK next week, and whilst I am there, I need to be able to access my SAMBA shares hosted on my HOMESERVER, via my laptop in england.

I have tried Hamachi before, which works fine on windows, but the linux version is awful, and hardly works. So I need an alternative. I did a bit of googling, but I don't know what "bridged" means when I found a OpenVPN tutorial

I was wondering if anyone could give me some information as to what I'll need, and what I'll need to do on both my homeserver and my laptop?

Thanks

---

### Post by thefix0r on 2011-01-06
oh man I just installed vpn server on my machine, it was SOOO easy to install man!

just apt-get install pptpd

that will get your box accepting incoming connections, and the configuration is so simple, just google pptpd install.

Then you can just use windows to dial into it, you wont need hamachi or anything else, nice and simple and it 
just works.

here is the easy tutorial i used

[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

---

### Post by Colo2 on 2011-01-06
> **thefix0r said:**
> oh man I just installed vpn server on my machine, it was SOOO easy to install man!

just apt-get install pptpd

that will get your box accepting incoming connections, and the configuration is so simple, just google pptpd install.

Then you can just use windows to dial into it, you wont need hamachi or anything else, nice and simple and it 
just works.

here is the easy tutorial i used

[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

thank you for the reply :) I'll check this out tomorrow morning

---

### Post by thefix0r on 2011-01-06
yeah I was really surprised how easy that was to setup, oh btw I tried openvpn first, and I was not impressed and it didnt work as I expected, pptpd will allow incoming connections seamlessly

---

### Post by perspectoff on 2011-01-06
> **thefix0r said:**
> yeah I was really surprised how easy that was to setup, oh btw I tried openvpn first, and I was not impressed and it didnt work as I expected, pptpd will allow incoming connections seamlessly

PPTP is a Microsoft protocol, I believe, and was denigrated for a long time as being a less secure protocol. Still, if you are using Samba that means you are likely primarily a Windows user, so it makes sense to stick with Microsoft protocols.

I started using WebDAV recently, on both Kubuntu and Windows and am quite pleased. I can access files by web browsers in addition to Windows Explorer or Nautilus or Dolphin. Plus, the speed is phenomenal compared to anything else. 

Lots of ways to skin the cat, though. BTW, it's

 sudo apt-get install pptpd

Official documentation is at

[http://poptop.sourceforge.net/dox/](http://poptop.sourceforge.net/dox/)

---

