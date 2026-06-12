---
title: "Network OS over wifi?"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by AcidRain0 on 2010-01-26
Hi! I run ubuntu over network with pxe boot and I thought that maybe if I connect to my wifi and then disconnect the ethernet, the nfs connection will reconnect over the wifi.. but that didn't work. Anyone know how to make it work? seems like it should be simple

---

### Post by lisati on 2010-01-26
Have a look here: [http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)

---

### Post by AcidRain0 on 2010-01-26
I know what PXE is, i'm using it. And what i'm asking is on the operating system level after PXE so I don't think it has anything to do with PXE. Anyone else?

---

### Post by ant2ne on 2010-01-26
Are you trying to use PXE over wireless?

---

### Post by AcidRain0 on 2010-01-29
kinda. What I am trying to do is past the PXE phase and into the operating system.  After the kernel is loaded and the whole OS is up.. I want to disconnect the thernet, and so I think that the wifi should be able to take over the NFS connection. Is this not possible?

---

### Post by ant2ne on 2010-01-29
> **AcidRain0 said:**
> kinda. What I am trying to do is past the PXE phase and into the operating system.So you want to PXE boot over wifi or ethernet? >  After the kernel is loaded and the whole OS is up.. I want to disconnect the ethernet, and so I think that the wifi should be able to take over the NFS connection. Is this not possible?I'm thinking you want ot PXE boot via ethernet and then disconnect the ethernet and continue OS operation, and re-establish network and file sharing over wifi. In theory that would work. I'm not so sure how it works in practice. Does you PXE boot image load completely into RAM? Or does it still access the PXE info on the PXE server? If it loads the entire OS into RAM, and you have the wifi drivers configured on the PXE image then I don't see why you couldn't disconnect the ethernet and then reconnect to the wifi. HOW you do all this is a mystery, and I think you would be moving into uncharted waters. But hey, let me know how it works out. I'm curious.

---

