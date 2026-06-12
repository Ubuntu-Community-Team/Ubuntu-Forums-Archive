---
title: "dial up head scratcher"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by Whydoe on 2009-03-28
I'm attempting to set up a computer for my dad so he can get on the net.  He has only dial up available to him where he lives, as do I.  I've done a fresh install of Ubuntu 8.10 with build-essential installed.  I've installed the appropriate driver for the modem (HSF 127a:2015).  Modem is found using scanModem.  Driver installs no problem.  Modem is found using both Gnome-ppp and wvdial as ttySFSH0 linked to MODEM in /dev/.

I've tried everything so far with all the information in scanModem to solve this problem.  When dialing out, the modem clicks as if to dial, but no dialing.  I have tried hooking up a phone to modem to listen and there is no attempt at a dial out.  The only error is NO CARRIER.  I've tried to following to solve the issue:

- adding X3 to ATZ (ATZX3) to ignore dial tone
- booting with various options ie. acpi=off noapci pci=routeirq or pollirq
- searching for blacklisted modules that may be a problem... blacklisted module snd_hda_intel as a last resort with no result
- switched out modem with one I know that works, the one I use.  Same thing, driver installs, modem is found.  No carrier.
- Carrier Check = no, Stupid Modee = yes, all those varients
- thought it might be something real dumb like the phone jack and or the chord.  Nope... still no go.
- altered BIOS settings from default to everything in between including disabling parts of the system that were not being used to free up some irq's
- changed PCI slots

The only info I've looked at that I can't figure out that may be the problem is a line in the dmesg.txt file about PME# disabled when referring to the irq of my modem (00:07.0).  I don't understand how, if the irq is disabled on bootup, the modem is still found by the system.  There was also a few lines in dmesg.txt that stated the following:

hsfengine: module lincense.... taints kernel

ttySHSF0 at I/O 0xe400 irq=17

snd_hda_intel:disagrees about version
snd_hda_intel:Unknown symbol

The last one leaded me to believe is was a conflict with another driver which tempted me to blacklist it as a last resort.  

Does anyone have any ideas what to try next?  To me, it sounds like a hardware issue as the computer was free.  Any help to get my Dad online would be great.  But I know dial up, especially with HSF drivers can be a PITA!

Also, I've done a fresh install of windows xp on the system to see if it would run the modem.  Works no problem.  Unfortunately, it's windblows.  It's setup as irq 5 in windows.  From what I've read so far, IRQ 17 (in Ubuntu) should not be used by modems.  It's not like I should have to free up resources is it?

---

### Post by Whydoe on 2009-04-02
I give up.  I did a fresh install of Ubuntu 8.04 and followed the driver install for the HSF modem to the letter and still the same result.  It just does not dial out.  I don't know what else it could possibly be.  I have an HCF modem setup on another Ubuntu install and it works fine.  I'm stuck with installing XP.  Which, I guess is ok, just for my dad to get online.  I'll try again if anyone has any suggestions.  It's an M871G PCCHIPS motherboard if that helps.

---

