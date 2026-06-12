---
title: "Booting into older kernel causes error with graphics drivers installed with Automatix"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by aswells on 2007-02-22
I needed to boot into an older kernel in order to be able to use my wireless card. When I boot into the older kernel, my nvidia drivers installed through automatix2 no longer work. I tried uninstalling them in the newer kernel and reinstalling them in the older kernel, but automatix insisted that the drivers were still there. I said to install them anyways, which still didnt help. They still worked in the newer kernel after this.

Any help would be appreciated.

*EDIT* I tried the uninstall-reinstall steps taken above again, and after a reboot everything works fine. Not sure why it took two tries, but sorry for the needless post.

---

### Post by MasterOfDisaster on 2007-02-22
Assuming you use the proprietory Nvidia driver, after a kernel update the drivers will be broken.  This is due to the driver headers having been built for a different kernel.  The suggested action is to 'pin' the kernel in Synaptic, and not update until an Nvidia-related update is available.

---

