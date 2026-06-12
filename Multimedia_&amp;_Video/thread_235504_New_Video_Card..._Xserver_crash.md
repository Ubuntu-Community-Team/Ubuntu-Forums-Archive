---
title: "New Video Card... Xserver crash"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by Pocadotty on 2006-08-13
old video card i915 (integrated intell)
new video card NVIDIA GeForce 6200 TurboCache (PCI Express)

After installing it I booted Dapper and got an Xserver crash which ultimately kicked me to a shell and told me I would have to reconfigure Xserver.

I dont know how to do that (especially from a shell)

I would hate to have to reformat and install from scratch (I tried installing without formatting, from live an alternate CD, but that caused the installer to crash in each case)

Can someone please tell me how to fix it...

---

### Post by tseliot on 2006-08-13
read this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by Pocadotty on 2006-08-13
It looks like that guide is made for agp cards... will that also work for PCI Express cards?  is there anything I have to change?

---

### Post by tseliot on 2006-08-13
> **Pocadotty said:**
> It looks like that guide is made for agp cards... will that also work for PCI Express cards?  is there anything I have to change?

It works also with PCI-E cards. Just don't put Option "NvAGP" "1".

---

### Post by Pocadotty on 2006-08-13
still doesnt work...

During the startup it takes far too long on "loading hardware drivers" and then it fails it and sends me to a shell

any more ideas?

---

### Post by tseliot on 2006-08-13
> **Pocadotty said:**
> still doesnt work...

During the startup it takes far too long on "loading hardware drivers" and then it fails it and sends me to a shell

any more ideas?

Enter the BIOS and disable the integrated card (or set the graphical adapter to PCI-E from there)

---

