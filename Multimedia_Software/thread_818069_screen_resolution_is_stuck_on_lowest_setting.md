---
title: "screen resolution is stuck on lowest setting"
date: 2008-06-04
forum: Multimedia Software
---

### Post by sprightlyone on 2008-06-04
hi 
  ihave tried to download via package manager driver package for my video card  (nvidia geforce 6500) &have made a total mess of it 
 nothing i have downloaded has fixed the problem 
 what is the correct way to down load drivers &install
 i want to be able to select other resolutions than std 
 what i have installed is atotal mish-mash of nvidia files in package manager 
  there is no option under hardware drivers to do any sel. or installing 
i`m new to ubuntu &learning the hardway via my fustration
  lyle

---

### Post by wdaniels on 2008-06-04
> **sprightlyone said:**
> there is no option under hardware drivers to do any sel. or installing

Go to "Software Sources" under System->Administration menu and check the box that says "Proprietary drivers for devices (restricted)". Then you should have the option to enable the NVIDIA driver in Hardware Drivers.

---

### Post by sprightlyone on 2008-06-04
> **wdaniels said:**
> Go to "Software Sources" under System->Administration menu and check the box that says "Proprietary drivers for devices (restricted)". Then you should have the option to enable the NVIDIA driver in Hardware Drivers.
 that doesn`t give me that option but i have an issue with some windows not fitting the page so some windos have bits trimmed usally at the bottom but i don think the optionis not visible 
 lyle

---

### Post by wdaniels on 2008-06-04
Do you mean that you don't see the option to enable proprietary drivers, or the one for the NVIDIA driver in hardware afterwards?

---

### Post by sprightlyone on 2008-06-04
hi 
  the one for nvidia drivers in hardware drivers

---

### Post by wdaniels on 2008-06-04
Maybe you need to do this first:

```
sudo apt-get update
```

(though I thought it does that automatically anyway)

I know you said you installed various packages, but unless you added some non-standard repositories I don't see how you could cause a problem with this. I don't suppose you downloaded and installed any NVIDIA package manually, like a .tar.gz file or something?

If you still can't get the option in Hardware Drivers, the equivalent command is:

```
sudo apt-get install nvidia-glx-new
```

You should reboot after installing this.

---

### Post by wdaniels on 2008-06-04
I forgot to ask, what Ubuntu version are you using?  I'm assuming it's Hardy (8.04)?

---

### Post by sprightlyone on 2008-06-04
> **wdaniels said:**
> I forgot to ask, what Ubuntu version are you using?  I'm assuming it's Hardy (8.04)?

yes this is the version i`m using 

lyle

---

