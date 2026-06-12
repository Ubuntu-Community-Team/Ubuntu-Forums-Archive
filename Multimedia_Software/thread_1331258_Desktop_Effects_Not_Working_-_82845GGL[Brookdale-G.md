---
title: "Desktop Effects Not Working - 82845G/GL[Brookdale-G]/GE Chipset"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Johnsie on 2009-11-19
Hi, I'm having problems getting desktop effects to work on this computer:

lshw:

> 
*-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device



When I try to enable the effects it says desktop effects cannot be enabled.


Output when I try to start compiz-manger:
> 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 



I see the PCIID is blacklisted. Is there a workaround for this?

---

### Post by redzsky on 2009-11-26
i think you have to find it in the whitelist

---

### Post by _mikec_ on 2009-11-27
i am having the same problem.

---

### Post by _mikec_ on 2009-11-28
maybe this will help you..
[http://ubuntuforums.org/showthread.php?t=1339415](http://ubuntuforums.org/showthread.php?t=1339415)

---

