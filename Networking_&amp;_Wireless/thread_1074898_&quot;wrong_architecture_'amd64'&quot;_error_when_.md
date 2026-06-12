---
title: "&quot;wrong architecture 'amd64'&quot; error when installing ndiswrapper-utils-1.9"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by mulluysavage on 2009-02-19
I am trying to get my Netgear WG311v3 working on my brand-new system, running xubuntu on a Phenom X4 9600 and Asus M3N78 pro. Ndiswrapper common scripts package installed fine. Attempted ndiswrapper-utils-1.9_1.53-2ubuntu1_amd64.deb  package install gave a 'wrong architecture' error. Am I not using an AMD64 architecture?

---

### Post by howefield on 2009-02-19
> **mulluysavage said:**
> Am I not using an AMD64 architecture?

You tell us ?

Type uname -m into a terminal.

---

### Post by mulluysavage on 2009-02-19
i686.

Is the architecture not determined by the processor/mobo?

---

### Post by howefield on 2009-02-19
You might have 64 bit capable hardware, but you appear to be running a 32 bit operating system on it.

---

### Post by mulluysavage on 2009-02-19
I see. There seem to be 2 versions of the utils avail, the amd64 version and the i386 version. Should I be installing the 386 version then?

Ps I'd just go ahead and try it but I do not have internet access where this machine is- I have been going elsewhere to get files! :)

---

### Post by howefield on 2009-02-19
Yeah, the i386 is the one you need.

---

### Post by mulluysavage on 2009-02-19
Thanks! This is my first post with my first linux/ubuntu system, and I already love the way people support each other. Truly amazing. Thanks again.

---

