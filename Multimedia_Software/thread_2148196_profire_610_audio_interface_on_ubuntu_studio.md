---
title: "profire 610 audio interface on ubuntu studio"
date: 2013-05-24
forum: Multimedia Software
---

### Post by lorinduq on 2013-05-24
Hi,

I'm running Ubuntu studio and trying to install my profire 610.

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

I was following this 'howto' [http://subversion.ffado.org/wiki/StepByStepUbuntu12.04](http://subversion.ffado.org/wiki/StepByStepUbuntu12.04) but got stuck at following command

ffado-test ListDevices

I keep getting this output :
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------


=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000d6c0404400002  0x00000D6C  0x00000011   M-Audio - ProFire 610
00845433422: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0

As you might have already guessed, I'm pretty new to linux :)

Browsing the forum I've found that I must enable raw1394 in Ubuntu Studio Controls but this doesn't seem to make any difference... Any word of advice?

gr

---

