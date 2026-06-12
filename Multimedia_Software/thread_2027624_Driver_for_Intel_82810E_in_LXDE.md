---
title: "Driver for Intel 82810E in LXDE"
date: 2012-07-16
forum: Multimedia Software
---

### Post by iskyfire on 2012-07-16
Hello, I've just installed lubuntu onto computer built in 2001. I'm pretty sure the LXDE I'm in is using the VESA driver. 
I've already tried to install the Intel driver by using "add-apt-repository ppa:glasen/intel-driver".

Using "sudo lshw -c video" shows the following:
```

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82810E DC-133 (CGC) Chipset Graphics Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-fbffffff memory:f4000000-f407ffff

```
The configuration line doesn't show any driver installed.

I also do not have an Xorg.conf file. I tried to boot into recovery mode and generate one using X -configure so that I could force the Intel driver, but it just gave me an error saying it couldn't create the tmp file.

Does anyone know what else I should do?
Thanks, 
iskyfire.

---

