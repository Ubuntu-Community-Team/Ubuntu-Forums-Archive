---
title: "Newbie networking tutorial?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Mylorharbour on 2011-01-05
Does anyone know of a decent Ubuntu networking tutorial I can work through?

I'm struggling to get a new install of Lucid to see anything on my home network. The current state of play is:
[LIST=1]
[*]I can browse the internet and the router. 
[*]I have several laptops running Ubuntu and a NAS drive but the HP desktop PC with the new Lucid installation can't see them. 
[*]The NAS and the HP are wired to the router. 
[*]I installed Lucid because I never got Maverick to see the network either.
[*]Lucid on my laptop can see the NAS drive over wireless. 
[*]I can see the NAS drive but not the other machines if I boot the HP into WinXP. I'm not much good at XP networking either so perhaps that needs configuring too. 
[/LIST]
A decent tutorial would be useful, especially one that doesn't assume I have Windows machines on the network as we rarely use Windows now.

---

### Post by Mylorharbour on 2011-01-06
Bump

Grief, one day old and this is on page 9 already! This is a busy old forum eh?

Anyway I know 79 have looked at it but I've had no response. Could this be hardware/router related?

---

### Post by perspectoff on 2011-01-06
In my File Manager, I refer to my NAS by its LAN IP address as its Location and add it as an entry. (Sorry, my terminology is for Dolphin in Kubuntu -- it's probably similar in Nautilus in Ubuntu).

So I refer to my NAS as

[http://192.168.0.104](http://192.168.0.104)

for example.

That is the most reliable way to always have it accessible instantly, IMO.

---

### Post by perspectoff on 2011-01-06
Also, I have the problems you describe more frequently in Windows than in Linux. I hate, hate, hate Windows networking.

Having said that, 80% of the time, the firewall and Windows is conflicting somehow. Troublsehooting the firewall is usually the solution.

---

### Post by Iowan on 2011-01-06
> **Mylorharbour said:**
> Grief, one day old and this is on page 9 already! This is a busy old forum eh? Some days, yes...

Can you ping other network machines by IP?

---

### Post by Mylorharbour on 2011-01-07
> **Iowan said:**
> Some days, yes...

Can you ping other network machines by IP?
There's only one other and the NAS drive on at the moment but yes, I can ping them.

---

### Post by Mylorharbour on 2011-01-07
> **perspectoff said:**
> In my File Manager, I refer to my NAS by its LAN IP address as its Location and add it as an entry. (Sorry, my terminology is for Dolphin in Kubuntu -- it's probably similar in Nautilus in Ubuntu).

So I refer to my NAS as

[http://192.168.0.104](http://192.168.0.104)

for example.

That is the most reliable way to always have it accessible instantly, IMO.
It's not obvious how to do that in nautilus perspectoff. I'm using DHCP. It appears you may be thinking I should have fixed IP addresses for the devices?

---

### Post by Mylorharbour on 2011-01-11
Well, yesterday I lost my sanity.

Nearly eight hours following very useful networking threads and at each turn the situation got a little better. Then, when I was almost there........nothing! Nothing at all. Suddenly, when I was reconfiguring smb.conf on one machine not a single PC could see could see any other. How could that be? I went to bed depressed.

Then today, Victory! Something that I didn't find on any networking thread popped into my head. Sometimes we get so engrossed with setting up Ubuntu we fail to check what else could be happening. Only 4 days ago I asked if it could be hardware related then promptly forgot about it but today I proved conclusively it was the router. I just swapped it for a different make and all the networking just burst into life.

Suffice to say if anyone's having issues seeing other computers or printers on the network, especially if their router's a Netgear DG834PN, they should have a good look at that as part of the diagnosis. Specifically are all 'attached devices' displayed in the list.

Thanks all for your help. At least I now KNOW my network's set up correctly.

---

