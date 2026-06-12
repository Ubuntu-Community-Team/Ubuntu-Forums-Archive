---
title: "cannot enable fglrx in 8.10"
date: 2009-08-15
forum: Multimedia Software
---

### Post by shmish on 2009-08-15
Hi,
I did a new installation of 8.04 and then upgraded to 8.10.  My system has a X700 ATI card.  I then installed the fglrx drivers from synaptic package manager (fglrx-amdcccle, fglrx-kernel-source, fglrx-modaliases).  In system - admin - hardware drivers I now have the fglrx driver showing up as being not actived.  I highlight the driver and click "activate". The downloading and installing dialog box pops up for a few seconds then goes away.  The driver never gets activated.

What can I now try to activate the driver?

I'm not sure what effect this has, but my xorg.conf file has the following lines in it:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```
I don't know if this is should be there since the fglrx driver isn't activated.

thanks

---

