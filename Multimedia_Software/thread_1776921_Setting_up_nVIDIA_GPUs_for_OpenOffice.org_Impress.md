---
title: "Setting up nVIDIA GPUs for OpenOffice.org Impress"
date: 2011-06-07
forum: Multimedia Software
---

### Post by bcschmerker on 2011-06-07
I am currently rebuilding an eMachines®/Acer® EL1210-09 (Advance Micro Devices® Athlon 64® LE-1620, nVIDIA® MCP78S chipset/GeForce® 8200 IGP, VGA plus HDMI) as a 64-bit Lucid box and could use some help setting up a dedicated projector video feed for Sun® OpenOffice.org Impress.  nVIDIA® supports several generations of GeForce® GPU with a proprietary driver and settings-application package in the Restricted repository.  Should a dedicated VDA for the projector be necessary, the EL1210-09 (which now packs a Shuttle® upgrade power supply that can drive PCI-Express video cards) can take a low-profile GeForce® 8400 card---that is, unless upgrading the entire VDA set to a GeForce® 220, 430 or 520 would be more cost-effective on account of improved GPU capabilities.

Several Users ran into problems with multiple displays in previous versions of Ubuntu®; the issue, apparently centered around the then-current version of Sun® OpenOffice.org shipped with Ubuntu® 8.04-LTS, was reported as fixed per [Bug 181819](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/181819) at Launchpad.  Since then, XRandr has replaced Xinerama; don't know what effect this will have on the interaction of Impress with the involved parts of the X Window System.

Any recommendations on how to proceed with this dedicated projector feed set-up task would be greatly appreciated.

**Update:**  I installed an Asus® EN210/DI/512MD2(LP) in the system and nVIDIA® Settings detected it immediately; still unanswered as of 6 August 2011 is how the GPU for the projector should be set up.  Disabled, Separate X window, how? is one way to put the issue.

---

### Post by bcschmerker on 2011-08-16
I found OpenLP™ 1.9.3 (ppa:openlp-core/release) on my own, as it turns out.  Assuming the latest nVIDIA® drivers (package: nvidia-current) are used, OpenLP™ will handle the secondary Video Device as a projector feed, provided that Xinerama is active in nVIDIA® Settings.  OpenLP™ is designed to take input from Sun® OpenOffice.org (preliminary for LibreOffice®) Impress™ slideshow files; an option is available for handling Microsoft® Office™ PowerPoint™ slideshow files.

I recommend OpenLP™ for dual-VDA desktop systems for running projectors in Ubuntu® CE™; I've yet to test it with KUbuntu® and Ichthux® (Gk. *&#921;&#967;&#952;&#965;&#958;*).

---

