---
title: "How stable is Ubuntu Studio for an always-on system?"
date: 2008-01-03
forum: Multimedia Production
---

### Post by hollywoodb on 2008-01-03
I'm thinking about using UbuntuStudio as my audio distro, or at least giving it a test drive, but there are a few things it *needs* to be able to do:
[LIST]
[*]madwifi drivers
[*]NFS server
[*]full range of LADSPA plugins available to all applications with support for LADSPA
[*]full JACK support built into all applications that support JACK (this includes things like Audacious)
[*]lowest possible latency (low-latency kernel, etc)
[/LIST]

Currently all of the above needs are satisfied using Fedora+PlanetCCRMA but I don't like having to update Fedora as often as I do.  Ubuntu Studio appears to have a simpler upgrade path and a saner repository.

The system will serve primarily as an audio workstation but also needs to be able to serve general desktop role (should be able to, same as Ubuntu proper) and offer NAS/NFS to my LAN.  Right now my Fedora+PlanetCCRMA box has an uptime of about 4 months (since I upgraded it) and I'd expect no less out of Ubuntu Studio.

Anyone see any problems with using Ubuntu Studio to meet my needs, are there any obvious pitfalls I'm going to encounter?

I've read the wiki pages about Ubuntu Studio and it seems it would fit the bill, it's mainly the stability of the system that I'm most concerned about at this point, and finding madwifi drivers for the low-latency kernel.  I'm competent in writing RPM spec files and building RPMs, but I've never really dealt with deb packages before.

---

### Post by Dark Hornet on 2008-01-03
From what I know, and my experience with Ubuntu, you should have no issues with stability as far as the OS is concerned.  Usually if there is a crash, etc it is due to a piece of software that may conflict with something else, (for ex: running a KDE software on Gnome.), or always trying new software that may still be in development.  Hope this helps, and good luck!

---

