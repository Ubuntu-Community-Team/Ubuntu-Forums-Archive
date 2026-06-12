---
title: "Gaming, steam, proton and gpu. nothing works"
date: 2019-02-07
forum: Multimedia Software
---

### Post by sebastianmm on 2019-02-07
So I have been using Ubuntu and Mint trying to make some windows games work like Final Fantasy XIV or The Witcher 3 with proton, wine, lutris etc.
Nothing works I don't know if it's my graphics card support, I have a Radeon RX 560

lshw -c video
**&#8203;**-display                 
       description: VGA compatible controller
       product: Baffin [Polaris11]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: cf
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:127 memory:90000000-9fffffff memory:a0000000-a01fffff ioport:4000(size=256) memory:a2200000-a223ffff memory:c0000-dffff
What should I do?

---

### Post by CatKiller on 2019-02-07
[https://github.com/ValveSoftware/Proton/wiki/Requirements](https://github.com/ValveSoftware/Proton/wiki/Requirements)

> 
Linux users with AMD or Intel Graphics Technology should install recent versions of Mesa and LLVM through this repository: [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)
```
sudo add-apt-repository ppa:paulo-miguel-dias/pkppa
sudo apt dist-upgrade
sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
```
 Provide your user password when requested and reboot after the last  command completes to ensure the driver has updated correctly.


---

