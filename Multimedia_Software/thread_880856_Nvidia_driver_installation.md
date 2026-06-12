---
title: "Nvidia driver installation"
date: 2008-08-05
forum: Multimedia Software
---

### Post by Featherstone-Hough on 2008-08-05
Greetings.  This is probably about the 10^6th time this has been asked, for which I apologize, but I couldn't find an exact answer to this.

I've installed Ubuntu 8.04.1 on a new system which contains an Nvidia 8400 GS card, and accordingly wanted to install the Nvidia drivers.  From Synaptic I installed the nvidia-glx package, and then the linux-restricted-modules package (which I would have thought would be a dependency for the driver, but wasn't), and all seemed to go fine.  

BUT, in **System -> Administration -> Hardware Drivers**, the driver never appeared, even after a reboot.  I re-installed nvidia-glx, to no avail.  Does anyone know what I've done wrong, and/or what else might be going on here?

Thanks for any info!

---

### Post by pytheas22 on 2008-08-05
An easy way to install the nvidia drivers is through [envy]("albertomilone.com/nvidia_scripts1.html").  It doesn't work 100% of the time, but usually it does.  I'd give it a shot.  If it fails come back here and we can try to figure it out manually, but hopefully envy will "just work."

---

### Post by Erlander on 2008-08-06
> **Featherstone-Hough said:**
> Greetings.  This is probably about the 10^6th time this has been asked, for which I apologize, but I couldn't find an exact answer to this.

I've installed Ubuntu 8.04.1 on a new system which contains an Nvidia 8400 GS card, and accordingly wanted to install the Nvidia drivers.  From Synaptic I installed the nvidia-glx package, and then the linux-restricted-modules package (which I would have thought would be a dependency for the driver, but wasn't), and all seemed to go fine.  

BUT, in **System -> Administration -> Hardware Drivers**, the driver never appeared, even after a reboot.  I re-installed nvidia-glx, to no avail.  Does anyone know what I've done wrong, and/or what else might be going on here?

Thanks for any info!

The nvidia-glx drivers are not the restricted ones hence they don't show up in the Restricted Drivers Manager.

I'm not sure whether the current restricted drivers will work with your card.  On my second system with a 7600Gs I can't get them to work.

If you want to try them you can click on the enable box in the Drivers Manager.  If they don't work you may have a problem and have to uninstall through Synapatic and re-install the nvidia-glx.

Rob

---

### Post by Featherstone-Hough on 2008-08-06
Thanks to you both for your thoughts.  The Envy tool suggested by pytheas turned out to be exactly what I needed -- it did indeed "just work" and I'm now in business.  (Note:  I did have to do some acrobatics-n-surgery to undo the damage I did when trying to "manually" install the drivers the first time, but once that was complete and I was back to a clean state, Envy took over and did exactly the right thing.)  

Thanks again!

---

