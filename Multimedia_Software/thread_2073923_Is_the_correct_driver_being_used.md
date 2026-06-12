---
title: "Is the correct driver being used?"
date: 2012-10-20
forum: Multimedia Software
---

### Post by ArsThaumaturgis on 2012-10-20
How might I confirm which driver is being used for my graphics card?

I've recently been having some graphics trouble with Wine, and, in attempting to resolve it, I realised that I don't actually have confirmation that the graphics driver that I intend to be in use is actually the one being loaded.

The intended driver should be installed, but I'm not confident that it's actually being used instead of the driver that comes with Ubuntu.

I have both Ubuntu 11.10 and 12.04 loaded, so solutions for either (or, better yet, both) are welcome.

My system:
Gigabyte Q2005 (A netbook)
CPU: Intel Atom N550
Graphics: Intel GMA 3150
Memory: 2GB
OS: Ubuntu 11.10 and Ubuntu 12.04

Intended driver: [The "Glasen" driver.]("https://launchpad.net/~glasen/+archive/intel-driver")

Having done a bit of searching regarding this matter, I include the following outputs in case they're found useful; it's entirely possible that the relevant information is somewhere in here, and that I'm simply missing it.

From System Settings -> System Info -> "Graphics" tab:
```
Driver: Intel® IGD
```From "lspci":
```
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

```Output of "sudo lshw -C display":
```
  *-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0300000-f037ffff ioport:18e8(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0380000-f03fffff

```

---

### Post by ArsThaumaturgis on 2012-10-22
I've done a little more digging - is "i915" the default driver (as opposed to the "Glasen" driver")?  If so, how might I switch over to the "Glasen" driver?

---

### Post by ArsThaumaturgis on 2012-11-17
*Bump*
I've returned to this issue after some time away from it.  I've made a few attempts at instructing Ubuntu to use the "Glasen" driver, but, since I'm still not sure of how to check that it is indeed using that driver, I don't know whether the lack of results thus far indicates that I'm failing to switch drivers or that the problem doesn't lie with the driver. :/

---

### Post by ArsThaumaturgis on 2012-11-21
Another bump, the final for this topic, I intend.

If no-one has any suggestions, would someone please point me towards any other resources that might help me with my driver trouble?

---

### Post by Yellow Pasque on 2012-11-21
> **ArsThaumaturgis said:**
> I've done a little more digging - is "i915" the default driver (as opposed to the "Glasen" driver")?

i915 is the correct driver. The Glasen PPA just contains a newer version of it. To confirm the version, you can probably look at /var/log/Xorg.0.log

---

### Post by ArsThaumaturgis on 2012-11-22
Ah, thank you for the reply!

I feel a little silly for not having thought to check the log through all this time; thank you for pointing me towards it!

Hmm... It does appear as though the correct version number is being noted there, which leaves the graphical issues that I've been having somewhat mysterious... :/

I recently remembered that I've seen some issues outside of Wine as well, so I may open a new thread for said trouble - thank you again for your reply. ^_^

---

