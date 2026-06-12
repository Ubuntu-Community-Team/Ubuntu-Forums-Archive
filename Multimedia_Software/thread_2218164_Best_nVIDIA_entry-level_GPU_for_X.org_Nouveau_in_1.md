---
title: "Best nVIDIA entry-level GPU for X.org Nouveau in 14.04-LTS?"
date: 2014-04-19
forum: Multimedia Software
---

### Post by bcschmerker on 2014-04-19
I have been testing an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon 64® LE-1620; nVIDIA® MCP78S chipset/C77 GPU) upgraded with a Shuttle® PC6300001 power supply and Western Digital® 2.5" HDD in a custom shock mount under Ubuntu® 13.12a1, 14.01a2, 14.02b1, and 14.03b2 (Trusty Tahr&#8482; development cycle), in anticipation of a mission as a projector driver; the basic system is stable in 14.04-LTS.  To date, X.org Nouveau (package: **xserver-xorg-video-nouveau**) has run consistently with two video displays on one nVIDIA® GT218 GPU (in the PCIe x16 card slot) alone, but been unable to dual-head on this system between the C77 and the GT218, in these tests; and nVIDIA® GeForce® Software for LinUX 304.x (package: **nvidia-304**) has resulted in consistent KSOD's.  Any attempt to use an ATi® half-height as the main GPU is contraindicated by a long history of hardware and driver conflicts between ATi Technologies and nVIDIA Corporation.

It appears that, due to the need to free the PCIe x1 slot on this system for a video input card, the operational solution will be an nVIDIA® NVS-Series half-height VDA based on either the GT218 (Tesla) or GF119 (Fermi) GPU; the NVS 400 (GK109 (Kepler) GPU), however, is less than ideal due to the use of quad mini-DisplayPort connections where I need dual analog XGA feeds in at least the short term.  Although Phoronix® noted that the Nouveau Project has successfully reclocked the nVIDIA® GT216 GPU, no manufacturer uses the GT216 for the single-half-height-card solution I need for this system.  On account of ongoing development of reclocking support for all nVIDIA® CUDA GPUs outside of the Maxwell architecture for LinUX Kernels 3.14-up, I have a new Kernel, probably 3.15-*n*-generic (probable metapackage: **linux-image-generic-lts-utopic**) wishlisted.

Between the GeForce® 8400 GS Rev. 3/210/GT 305 family and GT 520/610 family, which group performs more reliably?  Links to reports would be appreciated.

---

### Post by bcschmerker on 2015-02-21
**Update:**  As of 29 November 2014, the Kernel developers had run across a [security issue for Kernel 3.18 involving frequent hard lockups](http://www.phoronix.com/scan.php?page=news_item&px=MTg1MDc), something known to have happened with [certain nVIDIA® Driver releases with the GF119 GPU and previous Kernels](http://www.phoronix.com/forums/showthread.php?70619-Logout-freeze-using-Nvidia-Proprietary-driver-%28latest-and-even-older-versions%29).  This contraindicates the PNY® NVS 310 and 315, both of which use the GF119.  The PNY® NVS 285, which uses the GT218, is too slow for my requirements; and as far as I am aware the PNY® NVS 510 (nVIDIA® GK107 GPU) is still unsupported in X.org Nouveau, whose developers are still gathering information about the Kepler architecture as of 20 February 2015.  Due to previous no-login-screen conditions encountered with UbuntuGNOME® 14.04.1-LTS, the proprietary drivers are not an option.

As of 20 February 2015, it appears that I will have to restart the OMS Japanese Christian Church projection-computer project on Advanced Micro Devices® hardware, which is unaffected by the hard-lockup problems reported at Phoronix®.  The Asus® CM1630-06 (AMD® Athlon II® X2 220, 760G/SB700 chipset; augmented with RV970 Pro GPU) should be available for the project, once I have a new system in hand for Microsoft® Windows® 10.0.12000 (MultiProcessor Kernel 6.5.10400).

---

### Post by bcschmerker on 2015-11-09
**Update 2:**  X.org may finally have some help from nVIDIA®, as reclocking is now available up through at least Fermi GPU's; but now it appears that I need a Kepler.  OMS Japanese Christian Church having installed a Samsung® UN75J630AF flat-screen display unit as a "Retina display" upgrade from the failing Sharp® projector, HDMI will be needed for 1920x1080px@120Hz, which a Tesla such as the GT218 cannot drive.  The likeliest candidate for the eMachines®/Acer® EL1210-09 as upgraded to date is the PNY® VCGGT7302D3LXPB (700 MHz nVIDIA® GK107, 2 GiB DDR3-1070 video memory).

---

### Post by bcschmerker on 2015-12-02
Closing this Thread, as Kepler support is currently being developed for LinUX Kernel 4.2, slated for initial availability in Ubuntu® 15.12a1 (part of the 16.04-LTS development cycle).

---

### Post by Yellow Pasque on 2015-12-03
If you want to "close" the thread, please use the thread tools menu above the first post to mark the thread solved.

---

