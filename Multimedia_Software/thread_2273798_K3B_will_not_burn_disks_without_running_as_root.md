---
title: "K3B will not burn disks without running as root"
date: 2015-04-15
forum: Multimedia Software
---

### Post by patrickross16 on 2015-04-15
I am using Kubuntu 14.04 64 bit. Until recently K3B would burn disks perfectly without any hassle, however I started up a project the other day and K3B is no longer working without running it via sudo.
 
I insert a blank cd, the disk is detected, the device manager registers that a disk has been inserted and asks me what I want to do with it.  I open K3B and the disk is detected and shown with all properties listed. I start an audio project like I have done dozens of times before and everything works until I go to burn.  In the burn dialog the disk drive is visible but greyed out. Unless I run K3B via sudo then everything works as expected.

If I run K3B normally, create a project and save it, then run K3B via sudo and load that project, it also does not work, the disk drive is greyed out just as if I ran it as normal.  It will only function correctly if I do the entire project as root.

What steps can I take to figure out where the problem is, and how to fix it so I can burn CDs without running as root.

---

### Post by ron998 on 2015-04-15
> **patrickross16 said:**
> What steps can I take to figure out where the problem is, and how to fix it so I can burn CDs without running as root.


Hi
These are some notes I kept...
1) First time, use **[FONT=courier new]sudo k3b[/FONT]** to set permissions to 'Default'.
2) Make sure that file is not locked:- /home/user/.kde/share/config/k3brc

---

### Post by QIII on 2015-04-15
Please don't open K3b or any other graphical application with sudo.  Use ```
kdesudo
``` to avoid fouling up permissions -- which can lead to just the sort of things you are encountering.

Did you ever open K3b using just sudo prior to encountering this?

---

### Post by patrickross16 on 2015-04-15
Sorry bout that, I have been using kdesudo, I dont use plain sudo for gui apps, and as ron998 suggested  deleting /home/user/.kde/share/config/k3brc and /home/user/.kde/share/config/k3bsetuprc fixed it .  Thank you for your prompt and helpful reply.

---

