---
title: "get command - getting my atheros to work."
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by maxpull on 2009-01-18
I<ve been trying, for the past few days, to get my Atheros wireless to work...i've tried many things and some of the solutions I found requires me to download files with the get command or the synaptic pkg manager (which requires internet)...however, the point of getting my wireless to work is to access the internet. 

The only way i can download is by booting with Vista, many of the files i'm looking for are very hard to find.

Can anyone tell me where i can find "linux-restricted-modules" ?

Thank you.

---

### Post by pastalavista on 2009-01-18
Can you not hook directly to your router via ethernet cable? That would be the simplest way. You can download the restricted-modules here 

[http://packages.ubuntu.com/feisty/linux-restricted-modules-2.6.20-16-generic](http://packages.ubuntu.com/feisty/linux-restricted-modules-2.6.20-16-generic)

or more specifically here:

[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-2.6.20-16-generic_2.6.20.6-16.30_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-2.6.20-16-generic_2.6.20.6-16.30_i386.deb)

after you get the .deb file on your Ubuntu comp, just double-click it to install.

---

### Post by kevdog on 2009-01-18
Well if you could tell us something about your Atheros chipset it would probably be a lot more informative.  Can you post:

lspci -nnm
lshw -C network


Thanks.

---

### Post by diablo75 on 2009-01-19
I second the suggestion to temporarily use a hardline ethernet connection.  Download all available updates, then check System>Administration>Hardware Drivers (after updating and rebooting if necessary) to see if there are restricted drivers that need to be enabled (you'll need an internet connection for that too).

---

