---
title: "How do I remove old ndiswrapper?"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2009-01-12
I have installed ndiswrapper 1.53, but 1.52 keeps loading. Is it compiled to Ubuntu kernel? Just got rid off ath_pci by updating kernel. Do I have to compile my own kernel? No help when I do: apt-get remove ndiswrapper or ndiswrapper-commmon.

---

### Post by gettinoriginal on 2009-01-12
ndiswrapper 1.52 should be in your synaptic package manager.  :p

---

### Post by Ayuthia on 2009-01-12
You might want to try to do another clean install of ndiswrapper.  You will need to remove the wireless driver (ndiswrapper -e or ndiswrapper -r).  Make sure that you have removed all the ndiswrapper packages from Ubuntu (ndiswrapper-utils-1.9 and ndiswrapper-common).  You will then need to go into the 1.53 folder and do a make uninstall, make distclean, and a make clean before you do the make so that it is all cleared out.

Hope that makes sense.  Ubuntu does package the ndiswrapper.ko with the kernel which can be found in /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper.  You can also try moving that out of /lib/modules to see if that fixes it.

---

### Post by cd-r80 on 2009-01-12
Synaptic..Packages 1.50 etc. are not installed, just in archive.

I hope that make install puts 1.53 .ko to it's right place.

---

