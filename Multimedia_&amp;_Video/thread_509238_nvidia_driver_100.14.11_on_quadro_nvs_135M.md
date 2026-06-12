---
title: "nvidia driver 100.14.11 on quadro nvs 135M"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Gan Quan on 2007-07-25
Hi,

I installed Feisty Fawn on my Dell D630 recently, but it didn't recognize my video card (nVidia Quadro NVS 135M), and I couldn't do startx either. So I downloaded and installed the nvidia driver version 100.14.11 from nvidia's website, after the installation, nvidia-xconfig (a program shipped with nv driver) updated my xorg.conf, now I can start my desktop environment, and glxgears gives me around 5000 fps.

The problem is, I don't know whether the nv driver is functioning properly, because lspci still show my video card as "nVidia Corporation Unknown device 042b (rev al)", and not like [this howto](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) indicated, the Restricted Driver Manager on my system keep saying that "Your hardware does not need any restricted drivers.".

So how can I know that whether my video driver is properly installed? if it is, how to get rid of that "unknown device" message showed by lspci? and what is "restricted driver" anyway? is it better than the official driver from nvidia?
any input would be appreciated.

best regards!

---

### Post by MrHippocampus on 2007-07-25
If glxgears is running at 5000fps then your drivers are almost certainly installed correctly. If you want to be sure, try running "nvidia-settings", this program will complain if the nvidia driver isnt running.

To solve the unknown device problem try running "sudo update-pciids" in a terminal, this will download the latest pciid's which should help lspci to recognise your card.

Restricted drivers are basically drivers for which the source code is not open and freely available (i.e. not open source). The official nvidia driver falls into this category.

Hopefully that helps :)

---

### Post by Gan Quan on 2007-07-25
Thank you MrHippocampus, that helps.
I got a new problem.. I can't get into X after a reboot! startx gives the following error message:
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
that there is a supported NVIDIA GPU in this system, and that the nvidia device
files have been created properly. Please consult the NVIDIA README for details
```
But I can start X just before the reboot, and I didn't change anything, any idea?

EDIT:
I see this in Xorg.0.log:
```
Error: API mismatch: this NVIDIA driver component has version
100.14.11, but the NVIDIA kernel module's version does not match.
Please make sure that the kernel module and all NVIDIA driver
components have the same version
```
I guess this is the problem, but the NVIDIA kernel module is compiled on my system during the driver's installation, and I've logged into gnome once after that, how can its version not match after a reboot?

---

### Post by Gan Quan on 2007-07-25
OK, problem solved.
I installed nvidia-glx-new before the 100.14.11 version driver, although I have removed it before installing the new driver, I forgot remove nvidia-kernel-common which came with nvidia-glx-new. purge both packages and reinstall the new driver solved this problem.

Hey MrHippocampus, I tried "sudo update-pciids", it still can't recognize my video card.. :(

---

### Post by MrHippocampus on 2007-07-25
I just checked the online database and found that the id for your card has been submitted but not approved yet ([link]("http://pci-ids.ucw.cz/iii/?i=10de"), your card is listed a fair way down the page). I dont know how long it takes for things to be approved there but I assume a couple of days since theres only a small bit of information per device.

So try and update the id's again in a few days and it should be recognised :)

---

