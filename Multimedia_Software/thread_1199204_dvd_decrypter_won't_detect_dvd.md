---
title: "dvd decrypter won't detect dvd"
date: 2009-06-28
forum: Multimedia Software
---

### Post by sofasurfer on 2009-06-28
I have DVD Decrypter installed under Wine. When I run it, it says "no device detected". I had this happen before but do not remember how to fix it. Can someone tell me?

---

### Post by starcraft.man on 2009-06-28
> **sofasurfer said:**
> I have DVD Decrypter installed under Wine. When I run it, it says "no device detected". I had this happen before but do not remember how to fix it. Can someone tell me?

I can't help with this problem with WINE. I can recommend 3 different apps that do the same thing and run native on Linux. K9copy, thoggen and acidrip all do the same job. Give em a whirl.

If that isn't satisfactory then you'll have to wait for someone else. I'm not an expert on WINE nor do I use DVD Decrypter.

---

### Post by mc4man on 2009-06-28
You could try winecfg and under the drives tab - autodetect

What may be better is to open dvdd and ck under the tools -> settings (?) and see if there is an I/O tab.
If so then change from the default of SPTI to ASPI-WNASPI32.DLL (that takes drive detection away from wine and gives directly to the program (in this case dvdd

I believe you should find this setting based on ImgBurn (same author as dvdd

Edit: if you're gonna use dvdd then it would be prudent to make sure it doesn't auto ck. for updates (considering that as part of the 'forced' settlement with Luk macrovision now owns dvdd

---

### Post by sofasurfer on 2009-06-28
Thamks guys. I will try the programs you recommended. And the setting you recommended made DVD Decrypter work properly.
Thanks...

---

### Post by TRANQU111TY on 2009-09-05
> **mc4man said:**
> What may be better is to open dvdd and ck under the tools -> settings (?) and see if there is an I/O tab.
If so then change from the default of SPTI to ASPI-WNASPI32.DLL (that takes drive detection away from wine and gives directly to the program (in this case dvdd

Thanks it worked for me as well!

---

