---
title: "missing network manager"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by rcayea on 2009-11-23
Is there anyway to reinstall gnome-network-manager from the live cd?

What happened was I installed LXDE thinking if I don't like it, I could uninstall like KDE. However, it removed all my network manager stuff and now I can't connect to the internet. I did remove LXDE and all its network components too.

Any ideas how to reinstall the network packages from the dvd?

I have tried to enter it as a source for the package manager but i must be doing something wrong, because it doesn't work. 

Thanks,
Randy

---

### Post by rcayea on 2009-11-23
bump....any ideas out there?

---

### Post by TBerk on 2009-11-27
> **rcayea said:**
> bump....any ideas out there?

I am trying this too; I was trying to use Synaptic to change over to WICD and it fubar'd my existing NetworkManager install.

I've tried uninstalling (both apt-get & Synaptic) and rebooting and installing via the CD added to the repositories. 

I believe I should have payed more attention to the fleeting dependency warning that flashed by in my haste to plunge ahead; I think I'm missing a python widget that networkmanager (and gnome...) are looking for.

If I get any joy, I'll report back. (Right now I'm dual booting into WinXP to download and search for answers...)


berk

---

### Post by TBerk on 2009-11-27
Well, I'm back online, and likely could have been sooner. 

A) I added a RC version of Karmic to the Repositories in Synaptic.

B) I reinstalled Networkmanager.

C) I rebooted and it seemed to work; connected to router BUT but failed to grant IP address.

D) Discovered I had a typo in my password (remember they are case-sensitive).

E) Came back to mea-culpa myself.  

Now, my only task is to clean up the wicd that I tried manually installing and tries to run on startup but isn't seen via the apt-get nor synaptic utils.


berk

---

