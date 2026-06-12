---
title: "Any Plug &amp; Play Wireless Experiences??"
date: 2004-10-24
forum: Networking &amp; Wireless
---

### Post by kingnubian on 2004-10-24
I am very impressed by Ubuntu and am interested in user experiences with wireless network cards. I am more interested in PCI bases cards which Ubuntu autodetected at the install and setup properly. Also I would like to focus 802.11G capable examples. 

If Ubuntu recognized and properly setup your wireless nic please post the make, model and card version (revision) in this thread. If you happen to knoow of the chipset that the card in question uses then by all means post that as well.

If ndiswrapper or DriverLoader was needed to get the card working then it's not what I'm after. I've already had one person post that they have a Dlink, model not stated, that uses the Atheros chipset which Ubuntu recognized and setup properly.

As a side note, I am also interested in knowing if any people who will post in this thread, actually have WPA as opposed to WEP working and if so, how they got it to work.

---

### Post by sfw5000 on 2004-10-25
I use the dlink 520G with the atheros chipset. The GUI wizard detected it and set it up with no work on my part. This, I thought, was amazing. The trick is, that dlink makes a few different versions of this card with different chipsets. I went to office depot and actually looked at the boxes. I got the one that said atheros on the back. Other versions of the exact same card use a different chipset -- so you have to be careful which one you get and probably have to go a brick and morter store to be sure you have the right card in hand.

---

### Post by normnmiles on 2004-10-25
My Netgear WG511 was plug in play.  Haven't bothered with the encryption stuff though so I can't say whether they work or not.

---

### Post by sfw5000 on 2004-10-25
Oh, yeah -- forgot to mention that. I haven't done the encryption either. Will post back when I do that.

---

### Post by kingnubian on 2004-10-25
That's interesting and thankfully expected. The D-Link uses the Atheros and the Netgear uses the PrismGT chips which are both official kernel included modules. Seems I can't go wrong either way. I'll get what is cheapest  :-D .

One thing though, both chipsets do not have mature WPA support even though it is available with an additional  "WPA Suplicant" . The cards with the atheros chips seem closer to having native WPA in the included driver but who knows. WPA is my encryption of choice.

Anyone out there using WPA with a wireless nic in Ubuntu??

---

### Post by Jspired on 2004-10-25
Both these worked out of the box:

Linksys WPC11 v.3 (b)
DLink G650 (g)

---

### Post by mduduzi on 2004-10-28
Just be carefull of the stuff from Netgear. They have not been consistent is their implementations. I had to return a cardbus adptor that had otherwise been well reported. It turned out that the cards made in China had soft MAC while the ones from Taiwan were OK. lspci -v had an identical output but the card could not work.
Moral: Take seriously the disclaimer that says the manufacturer reserver the right to modify the products and is no obliged to notify of such change.

I agree with others on the Atheros chipset (AR5212). My cardbus is D-Link DWL-G650 ver.C2. and it worked immediately after I disabled WEP on my AP (Netgear DG834G).


[QUOTE=normnmiles]My Netgear WG511 was plug in play.  Haven't bothered with the encryption stuff though so I can't say whether they work or not.[/QUOTE]

---

### Post by Silwenae on 2004-10-29
The D-Link DWL-660AG card (dual A & G) worked out of the box in 54g mode, everything was installed, just had to activate it in networking settings.

After all the trials & tribulations I had with madwifi in a different distro, I was blown away.

Currently using WEP.

silwenae

---

### Post by stretch on 2004-10-29
My Netgear WG511T doesn't work.. No plug and play for me. I am too much of a n00b to know how to set it up manually :(

---

### Post by GaibryelRemorse on 2004-10-29
SMC 6835w Wireless Plug&Played quite easily

However there apparently is a new chipset that came out a few months ago, that doesn't play so nicely. A friend of mine picked one of those up. Under windows you have to "turn on" the card via drivers, so the "card control" command might be a solution

---

### Post by chogey on 2007-01-12
Network Everywhere model NWP11B  PCMCIA  Wireless 2.4 ghz
Running on an old  Toshiba Satllite Pro.  Recognized by 6.10 installed and worked no problems.

---

