---
title: "Adobe flash player will NOT work"
date: 2008-10-22
forum: Multimedia Software
---

### Post by AudioDef on 2008-10-22
I can't get Adobe Flash Player to work in Firefox. I'm not a big noob, but I'm stumped. I've tried installing/uninstalling various flash packages through Synaptics and installing the flash player directly from Adobe, all to no avail.   I'd appreciate any tips. I'm sure I'm missing something I'm like to kick myself for.

---

### Post by NilsE on 2008-10-22
Try going into Synaptic package manager and search on the word flash.  Then remove anything with the word flash in the package name that is marked in green.

Now, find adobe-flashplugin in Synaptic and install it.

---

### Post by surfed on 2008-10-22
> **AudioDef said:**
> I can't get Adobe Flash Player to work in Firefox. I'm not a big noob, but I'm stumped. I've tried installing/uninstalling various flash packages through Synaptics and installing the flash player directly from Adobe, all to no avail.   I'd appreciate any tips. I'm sure I'm missing something I'm like to kick myself for.

make sure you have no left over flash files from manual installs in /usr and ~/.mozilla/firefox before using synaptic to install flash.

---

### Post by gandaran on 2008-10-22
open synaptic package manager, look for **gnash**, **swfdec** and **libflash**, remove any of these if they are installed (complete removal), if you haven't installed any adobe flash package from the adobe site look for **flashplugin-nonfree** (adobe flash) in synaptic, mark for install and click the apply button.

---

### Post by AudioDef on 2008-10-22
surfed and NilsE, thanks. The combination of both your posts solved it.

---

