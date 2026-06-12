---
title: "How do I use my laptop as a wireless hotspot?"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by jmmL on 2009-12-20
Currently my laptop is connected via ethernet to our router. I recently got a phone which has wifi and I'd like to avoid expensive carrier charges by connecting via wifi to my laptop's internet connection.

I found [a page]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") in the community documentation, but the instructions were written for feisty. I'm wondering if there is a different or more simple way to do this now in karmic. Thanks!

---

### Post by garvinrick4 on 2009-12-20
Your phone is a WIFI router? Or your router is WIFI enabled?

---

### Post by amp_man on 2009-12-20
I think his router is wired-only, and he wants to use his laptop to bridge from the wifi phone to the router. I'd just go buy a wifi router, you can get a decent Netgear/Linksys/DLink/etc unit at Walmart or Best Buy for like $50, or cheaper if you hop on newegg.

---

### Post by jmmL on 2009-12-20
> **amp_man said:**
> I think his router is wired-only, and he wants to use his laptop to bridge from the wifi phone to the router. I'd just go buy a wifi router, you can get a decent Netgear/Linksys/DLink/etc unit at Walmart or Best Buy for like $50, or cheaper if you hop on newegg.

Yeah, my phone is wifi-enabled. Effectively I want to make my laptop the router.
I know wireless routers are cheap (and I have one at home, but not here) but this is an opportunity for FOSS to save me £40!

---

### Post by DrMelon on 2009-12-20
Logically speaking it should work.

---

### Post by jmmL on 2009-12-20
Looks like it already is included in ubuntu by default, and it's as simple as it should be.

Left click on the nm-applet and select "Create New Wireless Network".

NetworkManager has had this feature for a while:```
network-manager (0.7.1~rc4-0ubuntu1) jaunty; urgency=low

  * upstream release 0.7.1 rc4
    + http://git.freedesktop.org/NetworkManager/NetworkManager/
    + NETWORKMANAGER_0_7 (branch)
      - dont send AT commands to serial consoles that are not using a modem driver 
      - nozomi probing (LP: #351803)
      - allow users with polkit authorization to view/edit secrets for system connections
      - fix crash that might be LP: #319918
  * allow connection sharing out of the box; we add dnsmasq-base to Recommends:
    - update control
```

---

### Post by madnoob on 2010-01-09
> **jmmL said:**
> Looks like it already is included in ubuntu by default, and it's as simple as it should be.

Left click on the nm-applet and select "Create New Wireless Network".

NetworkManager has had this feature for a while:```
network-manager (0.7.1~rc4-0ubuntu1) jaunty; urgency=low

  * upstream release 0.7.1 rc4
    + http://git.freedesktop.org/NetworkManager/NetworkManager/
    + NETWORKMANAGER_0_7 (branch)
      - dont send AT commands to serial consoles that are not using a modem driver 
      - nozomi probing (LP: #351803)
      - allow users with polkit authorization to view/edit secrets for system connections
      - fix crash that might be LP: #319918
  * allow connection sharing out of the box; we add dnsmasq-base to Recommends:
    - update control
```

Hi, jmmL! Can you please post the exact steps you did to accomplish that? I'm trying to share the laptop internet connection to a a wi-fi enabled phone (LG gt505) and it just won't connect in vista, so i really want to give it a try in ubuntu.Sorry for the noobish request, but a noob i am:). Thanks in advance!

---

### Post by jmmL on 2010-01-09
[LIST=1]
[*]Left click on the NetworkManager icon in the panel.
[*]Enter a name for your network.
[*]Choose the security you want your network to have (if any)
[*]Enter a key for the security (if applicable)
[*]Click "create"
[*]Wait for NM to set it up (takes 5 or so seconds on my laptop)
[*]Scan on your phone for the new network
[*]Connect!
[/LIST]


It's funny. I was re-visiting this today. I wanted to connect my android phone (a T-Mobile Pulse) to my laptop, but it turns out android doesn't (currently) support connecting to ad-hoc networks by default. There are [work-arounds available]("http://modmygphone.com/forums/showthread.php?t=22681") for the G1 and the Hero, but none for the pulse yet, which uses a different wifi chipset. Oh well.

---

### Post by Ekeluo on 2010-12-28
> **jmmL said:**
> [LIST=1]
[*]Left click on the NetworkManager icon in the panel.
[*]Enter a name for your network.
[*]Choose the security you want your network to have (if any)
[*]Enter a key for the security (if applicable)
[*]Click "create"
[*]Wait for NM to set it up (takes 5 or so seconds on my laptop)
[*]Scan on your phone for the new network
[*]Connect!
[/LIST]


Thank you so much for this. Well there's one less need for win xp. Never thought it could be that easy.

---

