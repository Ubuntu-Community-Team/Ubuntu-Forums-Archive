---
title: "nvidia + amd = no go?"
date: 2008-12-14
forum: Multimedia Software
---

### Post by l_b on 2008-12-14
Hi all,

I'm running Ubuntu Intrepid (amd 64) and I have a mainboard in my box with has an onboard AMD gpu. And I have an PCI-E nvidia videocard. So I wanted to install both drivers. 

But when I do: aptitude install nvidia-glx-177 xorg-driver-fglrx

I get:

```
The following packages have unmet dependencies:
  xorg-driver-fglrx: Conflicts: nvidia-glx which is a virtual package.
                     Conflicts: nvidia-glx-177 but 177.80-0ubuntu2 is to be installed.
  nvidia-glx-177: Conflicts: xorg-driver-fglrx but 2:8.543-0ubuntu4 is installed.
The following actions will resolve these dependencies:

Remove the following packages:
fglrx-amdcccle
xorg-driver-fglrx
```

Is there a way of installing both drivers? Why are they conflicting? What's the problem?

---

### Post by l_b on 2008-12-15
Well, I've installed both drivers for AMD/ATI and Nvidia manually and they both work now.

Why are the packages conflicting? Because one can't both have an nvidia and ATI videocard?

---

### Post by Nepherte on 2008-12-15
During the installation of Ubuntu, it will probably have detected your on board amd graphics card as your primary vga. It then installed the drivers for that card only and used only that card, as your computer can only use one card at the time (unless you use some kind of SLI or Crossfire which is not the case). When you instruct Ubuntu to install the nvidia driver package, it sees that the system already uses a driver for another card and correctly says it will conflict.

When you install the nvidia driver manually, it will not look for any conflicts. Remember that your computer can only use one graphics card at the time so now it's a matter of figuring out which one Ubuntu uses. This can be done by opening up /etc/X11/xorg.conf and by looking for the "Device" Section. See what "Driver" it is using. If it says nvidia, it uses the propriatary nvidia drivers you manually installed. If not, it uses the other driver.

I'd disable the on board video card in your bios. It might save you some problems in the future. Only do this when you are sure it uses the nvidia driver. Otherwise The X server (the gui part of your computer) will probably not launch.

---

### Post by l_b on 2008-12-16
I'm now using the onboard videocard with a 15" touchscreen and the PCI-E videocard for my (old) tv. I'm currently only using the svideo output of the pci-e videocard. Both have their own x-server. So it is using both videocards at the same time. It's a setup similar to this one: [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

