---
title: "Problems Adding 3rd Screen to Xinerama Setup"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by rapha on 2006-09-06
Hi all!

I've got a computer with a Matrox Millenium graphics card set up with Xinerama for 2 screens. Now, I'd like to expand that to 3 screens using an older GeForce2 MX400. I plugged it in, booted up (the GeForce took the lead and displayed POST and Ubuntu bootup), hoping to only having to change my xorg.conf accordingly. However, the Matrox card doesn't want to do ANYTHING anymore. The log just says there was no matching device section for PCI:1:0:0, but there is. This is the same even when I remove the NVidia card entirely from my xorg.conf.

Is it me or is a setup like this not possible at all. If it is, what am I doing wrong?

Regards,
Raphael

**Edit:** you can set the BIOS to prefer AGP. I did that but it doesn't help much; now the NVidia driver is complaining of no matching device section for instance PCI:0:9:0...

---

### Post by Ziox on 2006-09-06
what is your xorg.conf?

also, what is the output of this command:

lspci -v

---

