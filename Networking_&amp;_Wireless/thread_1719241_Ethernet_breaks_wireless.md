---
title: "Ethernet breaks wireless"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by macroshaft on 2011-04-01
I've got a pc with two network cards, one wireless and one ethernet (wlan0 and eth0). I'm trying to setup ushare to stream media to an xbox but automatic DHCP isn't connecting and if I specify an IP address for the ethernet I lose internet access on my wireless connection.

I have a feeling everything is set up correctly but that some sort of conflict between the cards is preventing it from working. Can anyone suggest a way to stop them from interfering with each other?

---

### Post by Fire_Chief on 2011-04-01
First, does your XBox have Internet access through its wired connection? Can you provide more information on how everything is connected (maybe a diagram?)?

Cheers!

---

### Post by macroshaft on 2011-04-01
> **Fire_Chief said:**
> First, does your XBox have Internet access through its wired connection? Can you provide more information on how everything is connected (maybe a diagram?)?

Cheers!

The xbox is linked to the pc via cable, works perfectly through windows

---

### Post by Fire_Chief on 2011-04-01
So do you have Windows configure to bridge the wired and wireless connections thereby giving the XBox Internet access?

---

### Post by Seq on 2011-04-01
So the wired connection goes only to the xbox? There is no internet there?

Each interface will have a default route, and wired gets a lower metric (thus being the preferred option, given the choice). You probably have a default gateway, etc specified. You will want to edit the routes for the connection you made, and indicate you wish to use it only for local resources. I have attached a screenshot.

If you did this manually via /etc/network/interfaces, you should be able to just remove the gateway (though I'd have to double check to be sure).

---

### Post by macroshaft on 2011-04-02
> **Seq said:**
> So the wired connection goes only to the xbox? There is no internet there?

Each interface will have a default route, and wired gets a lower metric (thus being the preferred option, given the choice). You probably have a default gateway, etc specified. You will want to edit the routes for the connection you made, and indicate you wish to use it only for local resources. I have attached a screenshot.

If you did this manually via /etc/network/interfaces, you should be able to just remove the gateway (though I'd have to double check to be sure).

I have done as suggested and with some tinkering the server now works and the xbox can see it. However internet works for about 2 minutes after starting the server then dies. Also in order to play the test file the xbox wanted to contact xbox live and of course we're not routing net access to the xbox.

Getting there but it's hard going.

---

### Post by maclenin on 2011-04-04
I just set up ushare (in lucid) - and was having (what seem to me to be) similar questions.

My media "server" (laptop) has both wireless (wlan0) and wired (eth0) cards.

I was trying to figure out how to stay connected "wirelessly" (via wlan0) while, at the same time, connecting to the Xbox360 via wire (eth0).

The solution (for me):

1. Right-Click on Network Manager
2. Select Edit Connections
3. Highlight Auth eth0
4. Click Edit
5. Click the IPv4 Settings tab
6. Under "Method" choose: "Shared to other computers"

I am both serving tunes and allowing the Xbox360 to connect (to Xbox LIVE) via the laptop's wireless connection.

Good luck!

---

