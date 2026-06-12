---
title: "network-manager doesn't correctly probe broadband capabilities of 3G modem"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by humilleitor on 2010-01-10
Hi. Well, maybe this would go better into hardware & laptops, as I think it isn't strictly a networking problem, but still probably sounds more fit here.


I have a 3G Novatel Merlin UX870 pc card (idxvendor=1410x1430) that I use as a modem. My OS is Xubuntu 9.04 (that's jaunty). My network-manager version is 0.7.1. My present linux kernel is version 2.6.28-17.

So far, everything worked ok. When I plugged in my card, it got detected by the system, properly loaded the modules (usbserial and option) and created the device nodes /dev/ttyUSB0 and /dev/ttyUSB1 (first one is the good one, the other I don't know its use), properly detected by NM, properly been able to create new mobile broadband connections with netrowk-manager-gnome and, in general, all was happiness and joy.

But suddenly, since some days ago, after I-don't-know-what-I-may-have-possibly-done, NM doesn't like my modem any more. The system still sees it, and I can, for example, manually configure and "pon myconnection" (i.e., pppd works perfectly), and get online without problems. But not with NM, which refuses to accept the card.
The only relevant thing I remember having done recently is replacing the 2.6.28-15 kernel with the 2.6.28-17, but I'm not sure if that's the problem, as I think that the date of replacement and that one of the issue appearing don't match exactly. Besides, I've tried with another one kernel (2.6.24-23) and problem remains. So, probably that has nothing to do. I've a badly broken memory (in my head, I mean, not in the computer), but I don't remember having installed or uninstalled anything relevant. So, I'm at a loss.

Useful information for somebody out there who will like to help me:

When plugged the card, or when NM restarted, it logs this:
(ttyUSB0): found serial port (udev: hal:GSM)
(ttyUSB0): ignoring due to lack of probed mobile broadband capabilities
(ttyUSB1): ignoring due to lack of mobile broadband capabilities

So, in theory NM says my 3G card isn't successfully probed. However, if I probe it manually with the very nm-modem-probe tool, belonging to the NM package, the command I issue for the device (/dev/ttyUSB0) says this:
modem_probe_caps(): GCAP response: +GCAP: +CGSM, +DS
ID_NM_MODEM_GSM=1
ID_NM_MODDM_PROBED=1
main(): /dev/ttyUSB0: caps (0x9) GSM

I guess this means that the card is successfully probed!

I've been modifying the rules /lib/udev/rules.d/77-nm-probemodem-capabilities.rules as suggested in this bug:
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/384344](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/384344)
and tried all possible combinations, but NM insists in denying broadband capabilities to my card.
Seems like if NM isn't running nm-modem-probe, or something...

Somebody has any clue? I'd very much appreciate some guideline or hint.
thanks

---

### Post by humilleitor on 2010-01-23
Bump!

---

