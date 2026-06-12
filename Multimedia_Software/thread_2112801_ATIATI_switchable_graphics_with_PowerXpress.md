---
title: "ATI/ATI switchable graphics with PowerXpress"
date: 2013-02-05
forum: Multimedia Software
---

### Post by jfmatt000 on 2013-02-05
I'm running the proprietary drivers on Precise 64bit (fglrx from the standard repositories) on an HP Pavilion dv6 with switchable graphics. I have an ATI HD5450 as the discrete chip and ATI HD4200 as the integrated chip with an AMD Phenom II CPU.

Simply put, PowerXpress doesn't work. I am entirely unable to switch into high-power mode, which I've been living with for the past year and a half (had the same problem on Oneiric) but would now really like to get fixed now that TF2 is available on Ubuntu. This problem also seems to be preventing me from using a dual-monitor setup; even in Windows (I dual-boot Win7), I can't do an extended display with the integrated chip.

Here are the things I've tried, and the results:

[LIST]
[*]**Standard install of fglrx, aticonfig --initial, reboot:** Current situation. Everything except TF2 and other high-graphics-requirement programs works perfectly. fglrxinfo shows only the ATI drivers being used, as expected. Unfortunately, using aticonfig --px-dgpu AND changing PowerXpress through the Catalyst GUI have no effect; after restarting X, --px-l will report being in high-power mode, but the GUI will not, and fglrxinfo still shows the 4200 being used.
[*]**fglrx-updates and fglrx-experimental-9:** Failure to boot. Usually the infamous "check battery state" freeze. Reinstalling the old drivers from ctrl-alt-f2 not always sufficient to put things right; I've reinstalled Ubuntu twice in the past 24 hours.
[*]**Installing the newest Catalyst manually, using the download from AMD:** Same results as above.
[*]**aticonfig --initial -adapter=all:** This one was interesting. After rebooting, fglrxinfo showed both cards (4200 and 5000-series), but upon consulting the CCC GUI it turns out that what it had done was create separate displays for each one. I tried disabling the copy of my laptop screen connected to the 4200, and got boot problems again - reverting to the cached xorg.conf fixed that.
[/LIST]

I don't know what else to try. Everything I can find online about switchable graphics is weird workarounds for AMD/Intel combinations, which is not what I have. I'm sick of reinstalling, and I'm sick of having to boot Windows for any gaming more strenuous than FTL and Nethack. I know it's not a hardware error, because the driver *did* realize the other card exists when configured with adapter=all, I just don't know how to convince it to use the high-power card.

EDIT:

I tried playing around with the --adapter=? setting, and setting it to 2 does generate an xorg.conf for the discrete GPU. Rebooting with these settings, however, gets me stuck at the purple "ubuntu" screen with the dots. Xorg.log has fglrx complaining about RandR 1.2. I tried both of the fixes described [here]("http://us.cqday.com/thread-6584-1-1.html") (disabling RandR in both amdpcsdb and xorg.conf), with no change. Is this RandR thing the problem, or am I barking up the wrong tree?

2nd Edit:

The exact lines from /var/log/Xorg.0.log are the following:

[    15.605] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
...
[    16.645] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments

but before that, there's the much juicier sounding:
[    14.858] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:0) found

(PCI 2 is where the discrete GPU lives, or so I've gathered from aticonfig's output.)

---

### Post by neonfsh on 2013-07-31
I have the exact same problem. Seems like Ati is not supporting this configuration as this is Purely HP pavilion setting (Ati4200/Ati5000).So ati says we should contact HP for solution.I dont have the link but I am 100%  sure I ve read it somewhere.I also found that on ARCH linux they somehow managed to work this out by combining 2 different driver versions For the cards in use.I did not try it yet.Not sure thou if I understood correctly. I will never by switchable Grapic again.

---

### Post by danjohansen on 2013-12-10
I'm in the exactly same boat. I'm running the Open Source driver, as it is the best solution right now. But my CPU runs up to 85 degrees and GPU is at 75 degrees. Really want a solution for this. :P

---

