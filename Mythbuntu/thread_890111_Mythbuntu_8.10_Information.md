---
title: "Mythbuntu 8.10 Information"
date: 2008-08-14
forum: Mythbuntu
---

### Post by DemonBob on 2008-08-14
I was wondering where i could go for Mythbuntu 8.10 development information? I looked on mythbuntu's website and could not find any where to follow progress of the development of 8.10, i.e. new features and such. 

Is their any where to find this information?

---

### Post by tgm4883 on 2008-08-14
[https://blueprints.edge.launchpad.net/mythbuntu/8.10](https://blueprints.edge.launchpad.net/mythbuntu/8.10) for stuff that is 8.10 specific

[https://blueprints.edge.launchpad.net/mythbuntu](https://blueprints.edge.launchpad.net/mythbuntu) for all mythbuntu blueprints (more than just 8.10 requested features)

Alpha 1 should be out in the next week ;)  providing I can get my ssh access back.

---

### Post by DemonBob on 2008-08-15
How would i contact someone reguarding this? [https://blueprints.edge.launchpad.net/mythbuntu/+spec/web-myth-setup](https://blueprints.edge.launchpad.net/mythbuntu/+spec/web-myth-setup)

I have some php experiance, and wouldn't mind taking a look at this and discussing some specifications with one of the development team. 

If i can get some specs on it. I might decide to take a crack at it. 

Issues that need to be discussed would be i.e. If this can be defualty added to the Mythweb Package. 

Please respond to this post or PM me. 

Thanks.

---

### Post by grytpype on 2008-08-21
> **tgm4883 said:**
> [https://blueprints.edge.launchpad.net/mythbuntu/8.10](https://blueprints.edge.launchpad.net/mythbuntu/8.10) for stuff that is 8.10 specific

[https://blueprints.edge.launchpad.net/mythbuntu](https://blueprints.edge.launchpad.net/mythbuntu) for all mythbuntu blueprints (more than just 8.10 requested features)

Alpha 1 should be out in the next week ;)  providing I can get my ssh access back.

Is there any way to upgrade from 8.04 to 8.10 alpha by apt-get, or does it have to be a fresh install?

---

### Post by JugeHuge on 2008-08-22
> **grytpype said:**
> Is there any way to upgrade from 8.04 to 8.10 alpha by apt-get, or does it have to be a fresh install?

update-manager -d ??

---

### Post by DutchLoki on 2008-08-22
> **JugeHuge said:**
> update-manager -d ??

worked for me on my testing machine... but would not advice it for you production system (read: livingroom system).

---

### Post by bmwman on 2008-08-22
I see they have Mythbuntu 8.10 Alfa4 released. Has anyone tested it yet? I'm getting a new motherboard that I've had issues with and had to send it back for replacement, but I hope it'll work with 8.10.

---

### Post by grytpype on 2008-08-23
> **JugeHuge said:**
> update-manager -d ??

Worked for me too, except it needed a little help to finish.  When it tried to restart gdm, the X server started in failsafe mode and didn't accept any input from mouse or keyboard.  So I shelled in and ran apt-get dist-upgrade, and the upgrade completed and the system is back up.  Thanks for the tip!

---

