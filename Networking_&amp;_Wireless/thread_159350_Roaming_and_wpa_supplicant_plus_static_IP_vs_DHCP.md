---
title: "Roaming and wpa_supplicant plus static IP vs DHCP"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by Kashirigi on 2006-04-12
Hi everyone,

I apologize if this has been covered somewhere else -- I've looked around for a while and found nothing specifically helpful.

I'm using my laptop wireless and wpa_supplicant to connect to my home WPA and work WEP networks. Configuring wpa_supplicant seems fine enough, and it works OK.

The trick is that I have a static IP at home, and DHCP at work, so when I move from one to the other, it doesn't work.

How can I configure /etc/network/interfaces  (or any related item) so that I don't have to play around  after I boot to get an internet connection.?

I'm relatively new to Linux, so this may be obvious, but judging by the what I dug up, it doesn't seem to be.

Thanks for any help you can provide.

---

### Post by Mr Squiddy on 2006-04-13
Why not use DHCP at home as well?  If you need the same IP address each time then it often possible to configure the DHCP server to give the same address each time.

---

### Post by Kashirigi on 2006-04-13
[QUOTE=Mr Squiddy]Why not use DHCP at home as well?  If you need the same IP address each time then it often possible to configure the DHCP server to give the same address each time.[/QUOTE]

I'll have a closer look at my router and see if it supports that sort of thing. Although I would still prefer to have DCHP off. ..

Has anyone ever used guessnet for this sort of thing?

---

