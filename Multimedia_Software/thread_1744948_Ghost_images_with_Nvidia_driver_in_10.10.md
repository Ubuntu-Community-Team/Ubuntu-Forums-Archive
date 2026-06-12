---
title: "Ghost images with Nvidia driver in 10.10"
date: 2011-04-30
forum: Multimedia Software
---

### Post by dvarrazzo on 2011-04-30
Hello,

I have a Toshiba R780 laptop with video card: "VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)"

I've switched from 10.04 to 10.10 and I have a memory display problem: instead of the black parts of the screen I see images from the background or from other programs already closed.

Is this problem known? I probably don't know the exact keywords so I've not been able to google anything relevant.
I blame the nvidia-current driver upgraded from 195.36.15 to 260.19.06. I've tried to uninstall the newer driver from synaptic and to install the older manually, but the ubuntu software centre gave me an error and when I looked back synaptic I found the newer driver install again... so I've suspended further tries before making a mess in the system packages.

I've tried the free software driver but it crashes the computer every few hours: not an option.

So, I'd like to know:

- is the problem known? any reference to it?
- can the problem be fixed within the current driver?
- what is the correct way to install the 10.04 driver on 10.10?

Thank you very much.
[B]
[/B]

---

### Post by G_Dem on 2011-04-30
I had the same issue too. It seemed like a flash problem, as it would only happen when flash crashed on a website, then i'd get those ghost images of a flash video or website advert. Ive just tried uninstalling "adobe flash plugin 10" and installing "adobe flash plug-in" instead. Hasn't crashed yet in firefox. Will post back here if the problem comes back.

---

### Post by dvarrazzo on 2011-04-30
I don't think it's a flash problem: The ghost image is over screen areas whatever the application. No such issue with the free driver instead (but too instable to be used).

---

### Post by dvarrazzo on 2011-05-02
FYI, I've given up and moved to 11.04. After update, the graphics couldn't start and the boot process remained stuck on the purple splash screen: I've fixed by starting in safe mode, removing the xorg.conf and the Nvidia driver.

So I won't be able to test any solution for the ghost problem.

The driver currently using seems holding ok (maybe it's nouveau, but not sure). Still system freezes, but not related to the video anymore. If it holds ok, else I'll revert everything to 10.04.

---

### Post by RatOmeter on 2011-05-12
I'm pretty sure it's an NVidia driver problem that primarily shows up when flash apps are run.  I have the problem with Fedora 14, using a similar version of the NVidia driver (260.19.36).  I'll try a manual install of an older driver rev.

---

