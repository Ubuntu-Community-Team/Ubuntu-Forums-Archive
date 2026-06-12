---
title: "You do not appear to be using the NVIDIA X driver"
date: 2012-09-15
forum: Multimedia Software
---

### Post by vishalnshekhar on 2012-09-15
my laptop has nvidia GT540m
yesterday i install nvidia-current after updating fromsudo apt-add-repository ppa:ubuntu-x-swat/x-updates then i write sudo nvidia-xconfig  and then reboot my desktop visual effect changes and it look good like nvidia is working but still glx i not working and nvidia-setting tells me that You do not appear to be using the NVIDIA X driver my dkms status is nvidia-current, 304.43, 3.2.0-30-generic-pae, i686: installed
lspci |grep VGA output :
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
also i can not login to my admin account 
but when i login to standard user or guest it works but still NVIDIA X driver is not working 
can any one suggest something so that NVIDIA X Driver start working
as i seen many forum but none worked for me
earlier i tried nvidia-173 ,nvidia-current(before x-swat/updates reprository) but none works for me

[B][COLOR=#073763]
[/COLOR][/B]

---

