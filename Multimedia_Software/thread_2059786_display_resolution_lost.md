---
title: "display resolution lost?"
date: 2012-09-18
forum: Multimedia Software
---

### Post by user001001 on 2012-09-18
My machine has two hard drives, one has Fedora 64bit and one has XUbuntu 12.04 64bit. When running Fedora, I can select the resolution up to 1600x1200. But I can only up to 1280x1024 when XUbuntu is running.


Same machine, just boot from different hard drive, so the hardware should be the same for Fedora and Ubuntu.

Why the 1600x1200 is missing and how can I get it back?

I am new to Ubuntu and I am not an expert on linux. Please help.  More info followed:


**lspci | grep -i vga** shows:
*06:00.0 VGA compatible controller: NVIDIA Corporation NV37GL [Quadro PCI-E Series] (rev a2)*

[B]
sudo lshw -C video[/B] shows:
[I] *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV37GL [Quadro PCI-E Series]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:dd000000-ddffffff memory:c0000000-cfffffff memory:de000000-deffffff memory:df800000-df81ffff[/I]


**xrandr** shows:
[I]xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0[/I]

---

### Post by TheFu on 2012-09-18
Check if you have the nvideo drivers installed.
```
$ lsmod |grep nvidia
```a) Install the nVidia GPU drivers using APT (do not get them directly from nvidia)
b) reboot 
c)  sudo nvidia-xconfig 
d) sudo nvidia-settings

Sorry, the GPL drivers might be fantastic, but I don't know how to make them work.

---

### Post by user001001 on 2012-09-19
> **TheFu said:**
> Check if you have the nvideo drivers installed.
```
$ lsmod |grep nvidia
```


Return nothing from above command. That means there is no drive installed.

> **TheFu said:**
> 
a) Install the nVidia GPU drivers using APT (do not get them directly from nvidia)


I don't know how to do this. Anybody can give me the command? 
[I]
"sudo apt-get install **????**"[/I]

---

### Post by TheFu on 2012-09-19
> **user001001 said:**
> I don't know how to do this. Anybody can give me the command? 
[I]
"sudo apt-get install **????**"[/I]

I don't use Xubuntu, but in both Unity-Ubuntu and Lubuntu, there is a proprietary drivers option in the System menu.  The first reboot after the OS is installed, a popup should have been displayed telling you that proprietary drivers were available.

On my nvidia-running box, there are 3 nvidia specific packages:
* nvidia-current
* nvidia-current-modaliases
* nvidia-settings

You could try installing those.

BTW - a quick google found this: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

