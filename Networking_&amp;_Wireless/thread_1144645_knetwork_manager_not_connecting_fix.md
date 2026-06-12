---
title: "knetwork manager not connecting fix?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Butthead on 2009-04-30
Hi,

I'm having a strange problem.  I'm running Hardy 8.04.1 (I think?) LTS along with Mandriva Spring 2009.1 on a dual Hard Drive x64 system that is connected by cable (Comcast) to a router and cable modem to port ETH0.  Last night, after upgrading Mandriva online to Spring 2009.1, I booted into Kubuntu later that night and saw that Knetworkmanager claimed it's status was off line (red "X").  Well, it turns out Knetworkmanager doesn't seem to want to acknowledge ETH0 anymore in Kubuntu (it still works fine in Mandriva though (where I am currently posting this from :P ).  I don't know if this is because of the Mandriva upgrade I did, or that I had a package upgrade in Hardy that same night that I don't remember installing.  Searching the forums here, I see this seems to be a problem with recent Ubuntu versions and wireless cards.  Is there any fix to this problem that anyone knows about?  I have been running Kubuntu problem free  for at least a year now, so this is a recent problem.  I'm not all that technical with figuring out port #'s and such (to try and manually re-configuring it), and commands like "ifconfig" really don't show me anything that helps me any.  Anybody else on the forum here running a cable connection has had this problem, and figured out a way to get it fixed and working again?  I'd really appreciate any help concerning this, because I almost do like using relic Hardy more than fancier Mandriva :).  Thanks for any help or suggestions!

---

### Post by Butthead on 2009-05-01
Ran the "Recovery" option in the Grub menu and had it fix broken packages.

Seems to be working good now, only hope it stays that way. :guitar:

---

### Post by Butthead on 2009-05-01
I stand corrected.  It works sometimes (rarely though). :(

Seems an recent upgrade (new networkmanager perhaps?) has screwed things up royally in Ubuntuland. :cry:

---

