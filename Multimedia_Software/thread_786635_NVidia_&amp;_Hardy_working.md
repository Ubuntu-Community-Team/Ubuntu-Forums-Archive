---
title: "NVidia &amp; Hardy working?"
date: 2008-05-08
forum: Multimedia Software
---

### Post by lessgov2007 on 2008-05-08
Any one have OpenGL &/or Compiz in Hardy working with an NVidia 6200 graphics card?  If so how did you do it?  

Thanks

---

### Post by mistersam on 2008-05-08
I have a 7300LE Nvidia card. To make it work, I went into Synaptics and looked for nvidia. In there you'll find the nvidia drivers and the nvidia drivers-new. The old one works best for my card. Hope this helps.

---

### Post by LucidLoon on 2008-05-11
I uninstalled the Nvidia-glx-new driver and installed the Nvidia-glx driver from the package manager and that solved my openGL not working.

---

### Post by Seks on 2008-05-11
I have it working on a 5500, try installing nvidia-glx-new

---

### Post by a_px on 2008-05-11
> **lessgov2007 said:**
> Any one have OpenGL &/or Compiz in Hardy working with an NVidia 6200 graphics card?  If so how did you do it?  

Thanks

I have an Nvidia 6200 card and managed to get Compiz working with Fiesty, but when I upgraded to Hardy I can no longer get GL/Compiz to work.

When starting compiz I get:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: Illegal instruction
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Illegal instruction
not present. 
aborting and using fallback: /usr/bin/metacity 


Alan

---

