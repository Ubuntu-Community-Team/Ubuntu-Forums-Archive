---
title: "Wireless Stopped Workig After Update/B43 Disappeared from Hardware Drivers"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by ciamele on 2009-10-09
I downloaded some updates and now my wireless no longer works.

- Clicking on the icon on the system bar does not show me wireless options.
- Where I used to get a blue light on the physical button on my laptop, it no longer lights up, despite pressing the button.
- I noticed that the B43 driver has disappeared from Hardware Drivers/Restricted drivers (see attached images).
- When changing the kernal that I boot from in the grep menu to the previous version, it all works just fine.
- Old Kernal: 2.6.28-11-generic
- New Kernal: 2.6.28-15-generic
- I am not using ndiswrapper, just the restricted driver.

Has this happened to anyone else? Or does anyone know the solution? Thanks in advance for your comments.

---

### Post by Metaljaz on 2009-10-11
When you use the new kernel have you noticed rather or not the fwcutter in synaptic package manager is still showing installed?

---

### Post by kevdog on 2009-10-11
You'll need to reinstall the fwcutter package along with proprietary firmware or just boot into the old kernel.

---

### Post by ciamele on 2009-10-12
> **Metaljaz said:**
> When you use the new kernel have you noticed rather or not the fwcutter in synaptic package manager is still showing installed?

Yes, fwcutter shows as being installed in synaptic.

---

### Post by ciamele on 2009-10-12
> **kevdog said:**
> You'll need to reinstall the fwcutter package along with proprietary firmware or just boot into the old kernel.

I tried your suggestion using the instructions at the link below, but I'm still not seeing wireless networks, and the driver still hasn't returned to the Hardware Drivers Menu.

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Any other ideas? Using the previous kernal isn't all that appealing.

---

### Post by ciamele on 2010-05-06
I this issue was resolved with the installaion of Ubuntu 10.04 alpha.

---

