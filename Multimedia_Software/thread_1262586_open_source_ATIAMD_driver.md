---
title: "open source ATI/AMD driver"
date: 2009-09-10
forum: Multimedia Software
---

### Post by g-raf on 2009-09-10
I'm currently using the ATI/AMD propriety FGLRX graphics driver. The main problem is that i can't load the realtime kernel in ubuntu studio using this driver. 

Is it possible to share some info/ideas about how i can replace the FGLRX driver with an open source driver that would be supported by the realtime kernel?

---

### Post by g-raf on 2009-09-10
Ok, I'm using the open source radeon driver i found in synaptic and then shut down the FGLRX driver. It works for the realtime kernel. However, it doesn't work for video games and such things.

---

### Post by markbuntu on 2009-09-10
Did you install the driver while running the rt kernel, you need to do that so the kernel module gets built with the rt patch. For about a year the rt patch was misplaced in the fglrx installer but that is fixed now so it should work.

---

### Post by g-raf on 2009-09-11
> **markbuntu said:**
> Did you install the driver while running the rt kernel, you need to do that so the kernel module gets built with the rt patch. For about a year the rt patch was misplaced in the fglrx installer but that is fixed now so it should work.

Do you mean the fglrx driver works in the rt kernel if i load up the rt kernel, install the fglrx and remove the open source radeon driver? Sorry, i need to make sure this is what you were saying here.

---

### Post by g-raf on 2009-09-11
Can you send me a link to more information about this? If i proceed on my own, i'm going to end up destroying my whole system on accident. If there is a guide somewhere, please send me the link. Thanks.

---

### Post by g-raf on 2009-09-11
If i load the rt kernel and then go to system-administration-hardware drivers and install fglrx from there, will the kernel module be built with the rt patch during installation? Will that work out?

---

### Post by markbuntu on 2009-09-11
You need to install fglrx while running the rt kernel. I do not think the driver available with hardware manager has the patch so you should get the latest driver from ati. Be sure to read the relase notes and installer instructions.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by g-raf on 2009-09-12
> **markbuntu said:**
> You need to install fglrx while running the rt kernel. I do not think the driver available with hardware manager has the patch so you should get the latest driver from ati. Be sure to read the relase notes and installer instructions.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Sorry for asking a dumb question, but do you know which one of these (in the link) is the "fglrx" driver?

---

### Post by markbuntu on 2009-09-12
fglrx is the linux driver for ati cards. You need to choose linux and then x86 0r x86_64 from the list depending on what you installed and then your card to get to the driver download page.

---

