---
title: "Graphics card not detected"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by kernco on 2006-10-20
I have installed Edgy on my laptop, but it was set to use the vesa driver by default.  I went to edit xorg.conf, and saw that the name of the video device in the file is "Generic Video Card".  I have a VIA k8n890, so I changed the driver from "vesa" to "via", but X failed to start with the "no devices found" error.  How can I get it to detect my video card?

---

### Post by kernco on 2006-10-20
I went to VIA's website to download the driver.  They had precompiled versions for redhat, fedora, suse, but not Ubuntu or even Debian.  I downloaded the source, but it seems to require that you use XFree86 not Xorg.

---

### Post by tseliot on 2006-10-20
you might want to wait for Ubuntu Edgy Eft which might have a more recent version of that driver

---

