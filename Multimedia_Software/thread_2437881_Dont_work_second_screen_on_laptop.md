---
title: "Dont work second screen on laptop"
date: 2020-03-02
forum: Multimedia Software
---

### Post by barbaek on 2020-03-02
Hello!
I have a laptop Asus FX505DD-BQ121 with Kubuntu 18.04. It is AMD Ryzen 5 with AMD Radeon Vega 8 and NVIDIA GeForce GTX 1050 3 Gb.
My second monitor screen connect with HDMI.
When the system starts, the monitor does not turn on.

```
caho@myLaptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     59.98*+
   1680x1050     59.98  
   1280x1024     59.98  
   1440x900      59.98  
   1280x800      59.98  
   1280x720      59.98  
   1024x768      59.98  
   800x600       59.98  
   640x480       59.98
```
```
caho@myLaptop:~$ inxi -MG
Machine:   Device: laptop System: ASUSTeK product: TUF Gaming FX505DD_FX505DD v: 1.0 serial: N/A
           Mobo: ASUSTeK model: FX505DD v: 1.0 serial: N/A
           UEFI [Legacy]: American Megatrends v: FX505DD.306 date: 07/12/2019
Graphics:  Card-1: NVIDIA Device 1c91
           Card-2: Advanced Micro Devices [AMD/ATI] Picasso
           Display Server: x11 (X.Org 1.20.5)
           drivers: ati,amdgpu (unloaded: modesetting,nvidia,fbdev,vesa,nouveau)
           Resolution: 1920x1080@59.98hz
           OpenGL: renderer: AMD RAVEN (DRM 3.33.0, 5.3.0-40-generic, LLVM 9.0.0) version: 4.5 Mesa 19.2.8
``````
caho@myLaptop:~$ uname -r
5.3.0-40-generic
```
```
caho@myLaptop:~$ dpkg -l | grep 'linux-firmware'
ii  linux-firmware                                  1.173.14                                            all          Firmware for Linux kernel drivers
```

```
caho@myLaptop:~$ dpkg -l | grep 'microcode'
ii  amd64-microcode                                 3.20191021.1+really3.20181128.1~ubuntu0.18.04.1     amd64        Processor microcode firmware for AMD CPUs
ii  intel-microcode                                 3.20191115.1ubuntu0.18.04.2                         amd64        Processor microcode firmware for Intel CPUs
ii  iucode-tool                                     2.3.1-1                                             amd64        Intel processor microcode tool
```
Please, help me!

---

### Post by CelticWarrior on 2020-03-02
You need to install Nvidia drivers.
And you should have installed in UEFI mode but that alone should have no impact on graphics but sometimes it does. UEFI, like it's predecessor BIOS, are firmwares responsible for the boot process. How they initialize the hardware right before handing control to the OS often matters.

But start by installing the nvidia drivers and change to the Nvidia card to test. In many system with hybrid graphics, additional monitors (HDMI, DP, etc.) only work with the discrete GPU (you're currently using the integrated GPU).

---

### Post by barbaek on 2020-03-02
> **CelticWarrior said:**
> You need to install Nvidia drivers.

driver is installed. this driver controls:
[IMG]https://i.ibb.co/CBQ4KZ8/driver.png[/IMG]
sorry for russian. it is written that use recomended driver.

---

### Post by CelticWarrior on 2020-03-02
Ok, it should be fine.

Now open Nvidia X Server settings > PRIME profiles, change to Nvidia, reboot and test.

---

### Post by barbaek on 2020-03-02
> **CelticWarrior said:**
> Ok, it should be fine.

Now open Nvidia X Server settings > PRIME profiles, change to Nvidia, reboot and test.

Sorry, I'm fail!
I did not wait for an answer and choose X.Org X server. And now I dont have KDE!!! Only terminal... 
Please, how fix it?

---

### Post by CelticWarrior on 2020-03-02
When booting press SHIFT to bring up the Grub Menu
Press 'e' to edit the first entry.
With the directional keys go to the line where "quiet splash" is and type 'nomodeset' after splash separated by a space.
Press CTRL+X to boot the modified kernel.

This should give you a basic desktop eventually with lower resolution. Open Additional Drivers and reinstall the Nvidia driver.

---

### Post by barbaek on 2020-03-08
hello!
I was able to boot!
but I can not find the desired setting in nvidia-settings...

[screenshot]("https://imgur.com/WdqZ9z4")

---

### Post by CelticWarrior on 2020-03-08
Hello again. Please do not use photo host with p0rn as a bonus. You can use any of the reputable ones like imgur, thank you.

Again, you need to reinstall the Nvidia drivers and if the installation now is properly in UEFI mode then you also need to disable Secure Boot in UEFI settings.

---

### Post by barbaek on 2020-03-08
> **CelticWarrior said:**
> Hello again. Please do not use photo host with p0rn as a bonus. You can use any of the reputable ones like imgur, thank you.
I'm sorry!!! I fixed the image-link and add imgur in bookmarks!

> **CelticWarrior said:**
> Again, you need to reinstall the Nvidia drivers and if the installation now is properly in UEFI mode then you also need to disable Secure Boot in UEFI settings.
I will try again!

---

### Post by barbaek on 2020-03-08
What I've done:
I went to the site nvidia.com and found out the driver version for my video card. Its nvidia-driver-440.
Next removed the old driver with command: apt-get purge nvidia*
Next added a repository: add-apt-repository ppa:graphics-drivers/ppa
Next command ubuntu-drivers devices showed my nvidia-driver-440 as recommended.
I installed this driver. 


and now nvidia-settings is empty
[URL="https://imgur.com/dJDwJgz"]
screenshot[/URL]


```

caho@myLaptop:~$ sudo lspci -vnn | grep -i VGA -A 18
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c91] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device [1043:18f1]
        Flags: bus master, fast devsel, latency 0, IRQ 57
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at f000 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [258] L1 PM Substates
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [420] Advanced Error Reporting
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Capabilities: [900] #19
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
--
05:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso [1002:15d8] (rev c2) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device [1043:18f1]
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=2M]
        I/O ports at c000 [size=256]
        Memory at f7500000 (32-bit, non-prefetchable) [size=512K]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [50] Power Management version 3
        Capabilities: [64] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/4 Maskable- 64bit+
        Capabilities: [c0] MSI-X: Enable- Count=3 Masked-
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [200] #15
        Capabilities: [270] #19
        Capabilities: [2a0] Access Control Services                                                     
        Capabilities: [2b0] Address Translation Service (ATS)                                           
        Capabilities: [2c0] Page Request Interface (PRI)                                                


caho@myLaptop:~$ glxinfo | grep OpenGL | grep renderer
OpenGL renderer string: AMD RAVEN (DRM 3.33.0, 5.3.0-40-generic, LLVM 9.0.0)


caho@myLaptop:~$ nvidia-settings

ERROR: Unable to load info from any available system

(nvidia-settings:2742): GLib-GObject-CRITICAL **: 22:40:59.805: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 22:40:59.808: PRIME: No offloading required. Abort
** Message: 22:40:59.808: PRIME: is it supported? no


```

---

### Post by barbaek on 2020-03-08
secure Boot is disabled in BIOS! I checked

---

