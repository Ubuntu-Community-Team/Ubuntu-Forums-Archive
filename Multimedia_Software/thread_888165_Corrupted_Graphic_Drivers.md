---
title: "Corrupted Graphic Drivers"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Blaze611 on 2008-08-12
I had everything working properly until someone said to me to install EnvyNG to run WoW better. Well that corrupted my crap and now I'm stuck with an "unknown" graphics card that only will let me have 640x460 Resolution.

When I tried to do the restricted drivers it tells me to restart my computer and will only let me operate in low graphics mode...

Any help?

---

### Post by ZeldaFan on 2008-08-12
Which graphics card do you have? And I'm assuming you're running Ubuntu Hardy?

---

### Post by tuxxy on 2008-08-12
Search for the driver in synaptic, for example if nvidia, search that and find the insalled glx/glx-new driver, remove any you installed.

Now try and install the driver as usual from hardware drivers

---

### Post by Blaze611 on 2008-08-12
Yes Ubuntu Hardy 8.04 I think the version is.. and ATI Radeon x1900 series

---

### Post by Blaze611 on 2008-08-12
> **tuxxy said:**
> Search for the driver in synaptic, for example if nvidia, search that and find the insalled glx/glx-new driver, remove any you installed.

Now try and install the driver as usual from hardware drivers

I use ATI Radeon, and I can't remove anything. It won't let me.

---

### Post by tuxxy on 2008-08-12
Search for **fglrx** in synaptic

---

### Post by Blaze611 on 2008-08-12
> **tuxxy said:**
> Search for **fglrx** in synaptic
Okay I deleted all the installed components and when I try to reinstall ATI's drivers it tells me that I can't.

---

### Post by ZeldaFan on 2008-08-12
If you have ATI, EnvyNG should work with no problem. I have Nvidia and it worked perfectly for me. Upon opening up the GUI for EnvyNG, did you choose the option saying "Install the ATI driver (Automatic Hardware Detection)" and click apply? I'm pretty sure upon installing with Envy, it removes any existing drivers first anyway. If you want to however, you can choose the uninstall option in EnvyNG and then install fglrx.

---

### Post by tuxxy on 2008-08-12
You could try envy as suggested but remove the driver you have installed now first, search for eny-gtk in synaptic

---

