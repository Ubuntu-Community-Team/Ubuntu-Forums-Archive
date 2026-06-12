---
title: "Compiz not working on NVIDIA 5600 FX after upgrade to 8.04"
date: 2008-04-29
forum: Multimedia Software
---

### Post by huckey on 2008-04-29
Hi all,
  I have recently upgraded to 8.04 from 7.10. As one of the consequences Compiz stopped working. I have NVIDIA 5600 FX graphic card. Compiz used to work before upgrade.

  When I try running
```
compiz --replace
```

I get the following:
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

When I check in "Screens and Graphics", my system is using "vesa - Generic VESA-compliant video cards" driver, so I guess this can be the reason for Compiz not working. I have however tried what I can to use a different driver but to no avail:
1. I tried changing the driver to nv in "Screens and Graphics" also due to the fact that by default my system started in resolution 800x600 and often showed a message about running in low quality graphics mode due to not being able to detect my hardware. I am able to have a greater resolution but whatever driver I choose, the system reverts to VESA.
2. I tried installing a driver downloaded from NVIDIA's website. The version I installed is 169.12 (that is what NVIDIA's website showed to me when I submitted my details). Only immediately after driver install, compiz would start (I saw the logo) but then the system was not workable as no icons were visible since the white color behind the logo did not disappear. It was though possible to rotate the cube. After restart I was back to the situation in point 1.

I noticed also that when I go to System->Administration->Drivers then the line with NVIDIA's driver says it is being used but the check-box showing if it is on is empty.

I probably should give you something from my terminal to give better background but as I am a newbie I do not know what it should be - please direct me.

Can you help me with getting Compiz working?

Thank you!

Best regards

Huckey

---

### Post by litmos95 on 2008-04-29
Try to uninstall your Nvidia driver (you might want to use the tool envyNG - search google). And then use the restricted driver. I wasn't able to use compiz/visual effect with Nvidia driver too, but with the restricted driver, it works now.
So if you have uninstall it maybe a restart (don't bother with low resolution or color-bit for a while), and then go to System > Administration > Hardware Driver, activate the NVidia driver, and once again restart. Well at least that's what I did to get it run.

---

### Post by huckey on 2008-04-29
Hi,
  thanks for the tip. I tried it but unfortunately still can not get Compiz working - messages are still the same.

  Any other tips regarding what I could change to get it running?

Thanks!

Best regards

Huckey

---

