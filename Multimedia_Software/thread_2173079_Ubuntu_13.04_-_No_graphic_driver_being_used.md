---
title: "Ubuntu 13.04 - No graphic driver being used"
date: 2013-09-07
forum: Multimedia Software
---

### Post by cubiks on 2013-09-07
Hello

I have a Lenovo Y 510p running Ubuntu 13.04. The system has both an integrated Intel Haswell graphic card and a dedicated nVidia one.

sudo lshw -c display
*-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107M [GeForce GT 750M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:4000(size=128) memory:a2000000-a207ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Haswell Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:c2000000-c23fffff memory:b0000000-bfffffff ioport:5000(size=64)


I see none of them being used.
I installed the intel drivers using the intel-linux-graphics-installer, still the same.
I also tried installing the nVidia drivers but as I understand there are still issues in supporting the Optimus Drivers and it result was the unity env was not loading at all.

Without the graphic cards I have a constant 30% CPU utilization from compiz.

Any help is appreciated, thank you.

---

### Post by bcschmerker on 2013-09-07
If you decide to use the nVIDIA® GK107M as primary for X, Unity, &c., you'll almost certainly need the Packages jockey-text, nvidia-current, and nvidia-settings; xserver-xorg-video-nouveau *will not* work with certain nVIDIA® GPU's.  There may also be some BIOS/UEFI settings to make that I don't know about from the system description to date.

The jockey-text program is needed to properly configure the nVIDIA® drivers and settings applications for your GK107M.

---

### Post by bcschmerker on 2013-10-03
**Update:**  I ran across a Thread describing a situation with hardware similar to yours:  "[Use ONLY nVidia discrete graphics on Optimus laptop N56VZ Ubuntu 13.04](http://ubuntuforums.org/showthread.php?t=2174499)."  The Bumblebee Project&#8482; is supported at Launchpad&#8482;.
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update

```

---

### Post by Bucky Ball on 2013-10-03
*Thread moved to **Multimedia & Video**.*

---

### Post by Yellow Pasque on 2013-10-05
The easiest way to do it would be to install 'buntu 13.10 and then install bumblebee package (which in the repos beginning with 13.10).

If using 13.04, I would install a 3.11 kernel and use xorg-edgers PPA ( [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ) to get the intel GPU working. Next, I would add x-swat PPA to use nvidia-319 driver ( [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa))
And finally, I would install bumblebee from the repo: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

