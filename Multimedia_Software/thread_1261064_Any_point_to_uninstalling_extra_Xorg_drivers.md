---
title: "Any point to uninstalling extra Xorg drivers?"
date: 2009-09-08
forum: Multimedia Software
---

### Post by fh_scott on 2009-09-08
When I 'dpkg -l | grep xorg' I see all sorts of video drivers installed.

Is there any point/benefit to uninstalling the ones I'm not using?

---

### Post by markbuntu on 2009-09-08
Only if you need the space.

---

### Post by fh_scott on 2009-09-08
so it isn't actually loading those drivers into the kernel unless the hardware is present?

---

### Post by Yellow Pasque on 2009-09-08
> **fh_scott said:**
> so it isn't actually loading those drivers into the kernel unless the hardware is present?
Correct. I also uninstall them so that I don't have to download/install unnecessary updates to those packages.

---

