---
title: "Problems about wpa2 on Ubuntu 9.04"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by bruce85 on 2009-05-22
Hello,
I have a problems with Network Manager on Ubuntu 9.04 and a network protected by WPA2. When I try to connect to network, even if I write correctly the password, it 
[LEFT]is required each time. Who can help me?

P.S. Sorry for my bad english.
[/LEFT]

---

### Post by Aen107 on 2009-05-22
> **bruce85 said:**
> Hello,
I have a problems with Network Manager on Ubuntu 9.04 and a network protected by WPA2. When I try to connect to network, even if I write correctly the password, it 
[LEFT]is required each time. Who can help me?

P.S. Sorry for my bad english.
[/LEFT]

I have the same problem (only with Kubuntu).
Networkmanager is just requesting the password over and over again even though I am 100% sure it's correct.

Installing wicd is not possible, because i have to remove networkmanager first. After that, I do not have access to the internet which is required to install wicd (even installing a deb file is not possible without inet connection. i always get an error message).
It's a nice catch 22. 
Does anyone has a solution? If not, I have to downgrade to 8.04, which worked very well.

thanks!

regards,
Aen

---

### Post by Nakor BlueRider on 2009-05-22
You can install it just like this:

```
sudo apt-get install wicd
```

It will say nm must be removed first, but it's ok to say yes to that as it will download the new packages before starting the removal.

However, I am suffering the same problem, and installing wicd didn't help much.  I can actually connect to the WPA2-PSK AES network I have at home, but the WPA2-PSK TKIP network at work will not work.

This is my card:

```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I'm using ndiswrapper with net5211.inf.

One last thing:  I noticed by each network in wicd it shows what type it is, and that it does distinguish between WPA and WPA2.  I saw one in the list with WPA2 next to it.  However the network I want to connect to, which I know is WPA2, only says "WPA" and of couse, the menu to choose network type includes "WPA/WPA2 Personal" as a single option.

Is it possibly trying to connect to the network as though it were WPA (not WPA2) and thus causing the problem?  If so, what can I do to ensure it's recognized as WPA2?

---

