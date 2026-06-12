---
title: "Can not install Nvidia Gforce 2 MX-400 drivers in Gusty"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by jfd on 2007-10-19
Hey.

I can't find/install the Nvidia Gforce 2 MX-400 drivers so that i can see if destop effects in Gusty will work with it.

I'm using SIS 65x/M650/740 PCI/AGP VGA Display Adapter at the moment and that says that desktop effects can't be enabled with it.

Also the Nvidia Gforce 2 Mx-400 doesn't show up in the device manager either.

---

### Post by 505 on 2007-10-19
Download the Nvidia drivers from their site. You need the 9631 drivers, newer once will not work. You also need the header files for your kernel, because you need to compile a module. If you have all that, press ctrl+alt+F1, log in, cd to the directory where you downloaded the file and type:

chmod +x filename.xxx
sudo /etc/init.d/gdm stop
sudo ./filename.xxx

and reboot after that.

---

### Post by jfd on 2007-10-19
Sorry I'm fairly new to this, I don't know the header files for my kernel or how to compile a moule =/

---

### Post by froy02 on 2007-10-20
Open synaptics package manager and find the nvidia-glx-legacy package, mark it for installation then click apply.

---

### Post by jfd on 2007-10-20
OK I've done that and enabled it but it doesn't appear in the device manager so I can't actualy engable the hardware itself. Any ideas why?

---

