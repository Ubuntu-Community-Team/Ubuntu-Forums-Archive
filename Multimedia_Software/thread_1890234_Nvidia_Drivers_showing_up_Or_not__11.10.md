---
title: "Nvidia Drivers showing up? Or not ? 11.10"
date: 2011-12-03
forum: Multimedia Software
---

### Post by blazerboy777 on 2011-12-03
This is my log output from $sudo lspco | grep nvidia

01:00.0 VGA compatible controller: nVidia Corporation GF100 [GeForce GTX 470] (rev a3)
01:00.1 Audio device: nVidia Corporation GF100 High Definition Audio Controller (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GF100 [GeForce GTX 470] (rev a3)
02:00.1 Audio device: nVidia Corporation GF100 High Definition Audio Controller (rev a1)

So it looks like my GTX 470s are installed....but when I hit system info
Memory 7.9 GBs
Processor Intel® Core™ i7-2600K CPU @ 3.40GHz × 8 
***Graphics Uknown***
OS Type 32Bit
Disk 976.1 GB

Again running 11.10.
Is my GTX 470 actually working, is it not? Is it a system bug where it just doesnt show up in system info, or do i need to do something else?

Ok And the X.org drivers...im sorry about how long this is going to be.




[    16.322] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.322]     compiled for 4.0.2, module version = 1.0.0
[    16.322]     Module class: X.Org Video Driver
[    16.330] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
[    16.331] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.331] (++) using VT number 7

[    16.336] (II) Loading sub module "fb"
[    16.336] (II) LoadModule: "fb"
[    16.336] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.336] (II) Module fb: vendor="X.Org Foundation"
[    16.336]     compiled for 1.10.4, module version = 1.0.0
[    16.336]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.336] (II) Loading sub module "wfb"
[    16.336] (II) LoadModule: "wfb"
[    16.336] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.344] (II) Module wfb: vendor="X.Org Foundation"
[    16.344]     compiled for 1.10.4, module version = 1.0.0
[    16.344]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.344] (II) Loading sub module "ramdac"
[    16.344] (II) LoadModule: "ramdac"
[    16.344] (II) Module "ramdac" already built-in
[    16.346] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    16.346] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.346] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.347] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    16.347] (==) NVIDIA(0): RGB weight 888
[    16.347] (==) NVIDIA(0): Default visual is TrueColor
[    16.347] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.047] (II) NVIDIA(GPU-0): Display (Panasonic-TV (DFP-1)) does not support NVIDIA 3D
[    17.047] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.048] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 470 (GF100) at PCI:1:0:0 (GPU-0)
[    17.048] (--) NVIDIA(0): Memory: 1310720 kBytes
[    17.048] (--) NVIDIA(0): VideoBIOS: 70.00.21.00.03
[    17.048] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[    17.048] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    17.048] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 470 at PCI:1:0:0
[    17.048] (--) NVIDIA(0):     Panasonic-TV (DFP-1)
[    17.048] (--) NVIDIA(0): Panasonic-TV (DFP-1): 165.0 MHz maximum pixel clock
[    17.048] (--) NVIDIA(0): Panasonic-TV (DFP-1): Internal Single Link TMDS
[    17.055] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    17.055] (**) NVIDIA(0):     enabled on all display devices.
[    17.074] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    17.074] (==) NVIDIA(0): 
[    17.074] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    17.074] (==) NVIDIA(0):     will be used as the requested mode.
[    17.074] (==) NVIDIA(0): 
[    17.074] (II) NVIDIA(0): Validated modes:
[    17.074] (II) NVIDIA(0):     "nvidia-auto-select"
[    17.074] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    17.101] (WW) NVIDIA(0): Panasonic-TV (DFP-1)'s EDID does not contain a maximum image
[    17.101] (WW) NVIDIA(0):     size; cannot compute DPI from Panasonic-TV (DFP-1)'s
[    17.101] (WW) NVIDIA(0):     EDID.
[    17.101] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    17.101] (--) Depth 24 pixmap format is 32 bpp

---

### Post by efflandt on 2011-12-03
Maybe it is due to the dual video cards.  Are they SLI connected?

I am using newer 290.10 drivers from x-swat repository and **System Info** shows my single card:

Memory 7.7 GiB
Processor Intel® Core™ i5 CPU 650 @ 3.20GHz × 4
Graphics GeForce GTX 550 Ti/PCI/SSE2
OS type 64-bit
Disk 82.9 GB (running 11.10 from SSD)

BTW unless you are running a PXE kernel, 32 bit cannot take advantage of all of your RAM like 64-bit could

```
**free**
             total       used       free     shared    buffers     cached
Mem:       8121084    1195752    6925332          0      60600     466764
-/+ buffers/cache:     668388    7452696
Swap:            0          0          0
```

If you want to post something long (so it can scroll) or want to keep it formatted, highlight it and click **#** in message window to wrap it with code tags.

---

### Post by blazerboy777 on 2011-12-03
Yes they are sli, but i mean id like to keep em sli if u know what  mean, they werent cheap lol. id rather use 32 bit to avoid compatability issues

---

### Post by blazerboy777 on 2011-12-03
Tried doing

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

When i rebooted i didnt get any error messages, and also now whenever i push alt+ctrl +f1 it hangs and crashes, same with f2 etc

---

### Post by blazerboy777 on 2011-12-03
Ok i went in and unblacklisted all the ones that i blacklisted, and now terminal alt+ctrl f1 etc loads up fine and can switch back to f7 with ease. 

But now the problem remains that I cannot get this driver to load.

---

### Post by blazerboy777 on 2011-12-03
Im going to try this all over again, if it doesnt work, im just going to head back to windows. Retarded I cant use my video card, and every option im trying is either making it worse or not doing anything. Windows boom double click done. I prefer ubuntus OS for alot of reasons, but this is just getting ridiculous. I cant do anything I normally do on my pc, I havent even had the time to watch a couple episodes of some programs on my pc since i uninstalled windows. My home network is down and I dont know how to get it back up among other things. Im going to atempt to give it one last shot....if not then im out of here.

---

### Post by blazerboy777 on 2011-12-03
Ok i just scrapped the whole thing and am going to try running 10.04 LTS

---

### Post by efflandt on 2011-12-04
Not sure which version nvidia drivers 10.04 uses currently.  But for both 10.10 and 11.10 I am using most recent 290.10 drivers by adding x-swat repository.[FONT=monospace]

[/FONT]```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

Then if you just installed 10.04 (or 10.10), go to System > Additional Drivers.  Or if you already did that, or for 11.10 (not sure about 11.04) just use the Update Manager to **Check** for updates and install.

Web search "x-swat" to see the latest.

---

