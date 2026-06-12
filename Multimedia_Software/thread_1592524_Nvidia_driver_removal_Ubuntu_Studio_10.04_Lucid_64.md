---
title: "Nvidia driver removal Ubuntu Studio 10.04 Lucid 64 bit"
date: 2010-10-10
forum: Multimedia Software
---

### Post by Ventai on 2010-10-10
Hi, 

I attempted to install nvidia-current 195.36.24 from Synaptic for an Nvidia GTX 460. 

It didn't appear to work and I want to fully un-install all Nvidia drivers and do the 'official' (convoluted) Nvidia procedure of logging out of x etc: - 
[http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/index.html)

The issue is; I tried to remove via Synaptic, but when I restart the system I get an error stating: -
'Ubuntu is running in low-graphics mode. The following error was encountered. You may need to update you configuration to solve this. (EE) Failed to load module "NVidia" (module does not exist, 0)
(EE) No drivers available. 


This is actually the error that kept appearing and made me want to remove everything. 

My question is: -

Can I just go ahead and install the 'official' Nvidia driver, even though the 'startup' appears to be getting some kind of reference from somewhere? 

I understand that I'll have to remove the Nouveau driver as well some how. . .

Any help would be greatly appreciated :)

---

### Post by ahmet_der on 2010-10-12
Hi,

Same thing has happened to me. Here is how I handled this. First;
```
sudo apt-get --purge remove nvidia*
```
Then I found that manual nvidia driver has created file that prevent open source nvidia driver (nouveau). You can safely delete this file by;
```
sudo rm /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
```
Since nouveau driver does not need xorg.conf, you can also delete this.
```
sudo rm /etc/X11/xorg.conf
```
As I sad you, It works on me. You can wait for more confident way.

Cheers

---

