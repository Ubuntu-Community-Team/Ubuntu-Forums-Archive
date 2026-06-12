---
title: "ATI Radeon 8600 XT woes with Mythbuntu"
date: 2008-02-04
forum: Mythbuntu
---

### Post by wo_shi_big_stomach on 2008-02-04
Greetings. I'm getting errors like this in Xorg.0.log when trying to use ATI's Catalyst 8.1 driver with a Radeon 8600 XT card:

(EE) fglrx(0): [pcie] Failed to gather memory of size 262144Kb for PCIe. Error (-1007)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) AIGLX: Screen 0 is not DRI capable

Moreover, no matter what I do with either the open-source driver or the ATI driver, running "fglrxinfo" says the Mesa driver and not fglrx is running (though lsmod does show fglrx loaded).

I've tried the methods listed at wiki.cchtml.com as well as following the mythbuntu routine for loading the opensource driver.

Has anyone successfully gotten the Radeon 8600 to load with mythbuntu? If so, how?

My setup:
Asus M2A-VM HDMI mobo
Athlon 64 X2 4800 CPU
Sapphire 8600 XT video card
Hauppage WinTV-PVR 500 dual tuner
Sony KDS-R50XBR1 TV (connected to video card using DVI-HDMI cable)
Mythbuntu 7.10 x86_64

Alternatively, if your advice is "throw that ATI card on the rubbish heap" what's your advice for an alternative for mythbuntu and the above setup?

thanks

/wsbs

---

