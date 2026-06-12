---
title: "problem updating madwifi driver r3916"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by Dr. Feelgood on 2009-03-15
Before I get started I'm using Hardy 8.04 with a Dlink AirPlus DWL-G510 PCI card with an Atheros AR2413 chipset

I've recently decided to play around with aircrack-ng which requires me to update and patch my madwifi driver.  I attempted to do this with the directions they provided on their site:

```

 ifconfig ath0 down
 ifconfig wifi0 down
 svn -r 3925 checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
 cd madwifi-ng
 wget http://patches.aircrack-ng.org/madwifi-ng-r3925.patch
 patch -N -p 0 -i madwifi-ng-r3925.patch
 ./scripts/madwifi-unload
 make
 make install
 depmod -ae
 modprobe ath_pci

```

I used these instructions verbatim with the exception that I had to add 'sudo' a few times.  Everything seemed to go fine until I checked 'modinfo ath_pci':

```

filename:       /lib/modules/2.6.24-19-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3916
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     8ABF446081459912D675AA0
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)

```

As you can see it still says I'm using revision 3916.  Although I didn't save the output from the update (I'll do it again and list it if it helps), it clearly stated that it had downloaded r3952, the latest revision.  I'm just wondering what I'm missing to get the driver updated.  I already checked packet injection (the reason why I am doing this) and it does not work, so the patched driver was definitely not implemented.  Probably a stupid oversight somewhere on my part but any help is appreciated.  Thanks in advance

---

### Post by Dr. Feelgood on 2009-03-15
ttt

---

### Post by Sprut1 on 2009-03-16
I did a reinstall today and when I tried to install the patched madwifi-ng drivers this exact thing happened to me. I have no idea what's causing this, I've done this several times before and it always worked.

---

### Post by wannadumpwindows on 2009-03-16
Did you remember to remove the old module before you tried to install the new one?

Also, in 8.10 all I needed to do to get mine working was to disable the Atheros driver in the restricted drivers manager, reboot and then my card worked without needing any patches or Madwifi.

---

### Post by Sprut1 on 2009-03-16
> **wannadumpwindows said:**
> Did you remember to remove the old module before you tried to install the new one?

Also, in 8.10 all I needed to do to get mine working was to disable the Atheros driver in the restricted drivers manager, reboot and then my card worked without needing any patches or Madwifi.

Remember that the point is to use the patched drivers to enable packet injection with aireplay-ng.

---

### Post by wannadumpwindows on 2009-03-16
> **Sprut1 said:**
> Remember that the point is to use the patched drivers to enable packet injection with aireplay-ng.

And injection works for me with that method.

---

### Post by Sprut1 on 2009-03-16
Neither works for me, so this is weird.

---

### Post by wannadumpwindows on 2009-03-16
> **Sprut1 said:**
> Neither works for me, so this is weird.

My luck with Madwifi has been hit or miss. I have two laptops, both of which claim to use the same wireless chipset, the infamous AR5007, however, Madwifi works on one, but not the other. So I'm not all too sure where to point you from here.

Removing the restricted driver on one worked, but not the other. So I'm using one each way. Wish I could offer you guys more help, but I haven't been able to track down what's causing the issue at this point, but I'm still digging around. It's had me curious/frustrated for quite some time.

If I gain any ground, I'll be sure to let you guys know.

Sorry I can't be of more help.

---

### Post by Sprut1 on 2009-03-17
Just did a fresh install (Ubuntu 8.10), disabling the drivers as you suggested (which absolutely makes no sense too me) didn't work, I then had no wifi extension at all. I will try to install the madwifi-ng driver when I'm done updating and report back the result.

---

### Post by Sprut1 on 2009-03-17
Okay, so I tried to checkout 3925, I got 3916. Injection is not working at all, and connecting to a network is not working at all.

This is extremely frustrating. Everything seems to be exactly like it was before, but still everything is broken. *Finds his quite place*

---

