---
title: "Samba: Error while copying/Invalid Argument"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by hundred1906 on 2009-06-06
I am trying to copy large video files across from my Windows XP Host into Ubuntu Guest. The Guest is on a virtual machine running under VMWare and Samba is used as the transfer.

The first few 3-4Mb get copied then a Ubuntu error box pops up with "Error While Copying" and the detail "Invalid Argument".

Meanwhile the host (XP) Log shows an Event ID 2025 and messages explaining that it relates to a perceived Denial of Service Attack (ie from my Ubuntu guest).

This error would not be noticed if copying only smallish files.

Disabling the firewall on the host has no effect.

Has anyone come across this? I can't find any references on the Forums.
My feeling is that this has nothing to do with VMWare itself and that the problem solution lies within Windows protection somewhere.

Ubuntu 8.04

PS. For those interested I am only using Windows as the host because Linux has no drivers for my TV Card. Otherwise the host would be Ubuntu for sure.

---

