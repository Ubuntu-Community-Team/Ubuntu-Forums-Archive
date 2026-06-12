---
title: "ATI Open Source drivers?"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Cam! on 2011-03-25
Although Ubuntu doesn't officially support the Radeon HD 6850, I heard that installing an alternative, open-source driver will give me the support.

How do I go about doing this?

---

### Post by anders_c_ on 2011-03-25
You could try the xorg-edgers ppa, but expect some serious bugs =)

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty")

---

### Post by Cam! on 2011-03-25
I added the PPA. What exactly do I install?

---

### Post by Veikk0 on 2011-03-25
You should make sure you have removed the ATI/AMD proprietary drivers before you use the repository.

I'm using 10.04 right now so I dunno how different things are. I'm not sure if 11.04 still has Synaptic Package Manager but if it does, you can use it to update your package list and then download the updates it offers. If there's some other program that can check for updates and install, then use that.

You don't need to mark any packages to be installed since you'll only be upgrading from an older driver version (that comes pre-installed) to a newer one.

Alternatively you can just use the command line:
```
sudo apt-get update && sudo apt-get upgrade
```
Reboot, and keep your fingers crossed. The code in the repository is highly experimental. Works like charm with my Radeon X1950 Pro though, gives me over 40 FPS in Minecraft! :)

Btw, if you want to keep track of the features the open source driver has, bookmark _[this page]("http://www.x.org/wiki/RadeonFeature")_. Your card is one of the Northern Islands ones and it seems there's very basic 3D support for it.

Good luck! :P

---

### Post by cariboo on 2011-03-25
Unless you are running Natty, please don't give advice on how to install ATI drivers. Xorg-xserver has changed in Natty, and what works for previous versions won't work here. I'd suggest using the open-source drivers until ATI/AMD releases working drivers.

This happens every release cycle, you just have to be patient.

---

### Post by Harry33 on 2011-03-26
> **Cam! said:**
> Although Ubuntu doesn't officially support the Radeon HD 6850, I heard that installing an alternative, open-source driver will give me the support.

How do I go about doing this?

You should explain a bit more what are you trying to achieve.
Obviously, if you have Natty installed, you cannot use ATI proprietary drivers (because of the incompatibility for xserver 1.10 support).
So, I assume you are already using xserver-xorg-video-ati (ATI open source drivers) from Natty repos.
Now then, what alternative do you mean?

---

