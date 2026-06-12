---
title: "How to install Nvidia GeForce 7050 in Intrepid"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Gernot_B on 2009-02-20
Hi everybody,

Is there anybody out there who has already successfully installed the following NVIDIA graphics adapter under Intrepid:
GeForce 7050 / nForce 610i (device ID 0x10de07e3)

This adapter is integrated in the NVIDIA MCP73V chipset, which itself sits on the Elitegroup motherboard GF7050VT-M5.

I've tried all the standard and non-standard installation procedures (Ubuntu and NVIDIA), ran the installation script (NVIDIA-Linux-x86-180.22-pkg1.run) but with no luck. 

Does anybody have an idea what I'm missing here?

Any help is very much appreciated.

Bye
Gernot

---

### Post by norwoods on 2009-02-20
open System--Administration--Hardware Drivers
deactivate any active driver 
activate the NVIDIA accelerated graphics driver(version 180)

---

### Post by more2come on 2009-02-20
Nah, that won't work.

Same problem here, I upgraded my old system, bought a GF7050VT-M5 motherboard (7050/610i chipset) and a GeForce 9800 GT.

Since then no Linux/XOrg is willing to run on my system, as soon as I activate the nvidia-drivers, XOrg refuses to work. I tried so many options, enabling the newest driver, installing the driver manually, using envy to install the driver.

Nothing worked, I tried at least 6 fresh installs and I was very close to eating my keyboard.

If anyone has experience with this very chipset in combination with a Geforce, please give some advice!

---

### Post by more2come on 2009-02-26
*Bump*


Tried latest release of Ubuntu 9.04 (Alpha 4 I guess) in combination with nVidia drivers Rev 180 and it works!

---

### Post by Gernot_B on 2009-03-07
Hi everybody,
I found out that this is apparently a BIOS problem. See the snippet of the nvidia-installer.log below.

   [19907.182241] nvidia 0000:00:10.0: PCI INT A -> Link[SGRU] -> GSI 22
   (level, low) -> IRQ 22
   [19907.182245] NVRM: This PCI I/O region assigned to your NVIDIA device is
   invalid:
   [19907.182246] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0000:10.0)
   [19907.182248] NVRM: The system BIOS may have misconfigured your graphics
   card.
   [19907.184190] nvidia: probe of 0000:00:10.0 failed with error -1
   [19907.184537] NVRM: The NVIDIA probe routine failed for 1 device(s).

I asked nvidia tech support but they replied ask your vendor.
I asked my vendor but they said no Linux support.

At the moment I have no clue how to fix this.
Big frustration.

Has anybody out there had problems of this type?

Any help is much appreciated!

---

### Post by Gernot_B on 2009-05-15
My problem is solved.

I upgraded to Jaunty, installed envyng, ran the script (which installed the nvidia 180.44 driver) and everything worked.

Thanks for your help!

---

### Post by siddtharth on 2009-05-21
> **Gernot_B said:**
> My problem is solved.

I upgraded to Jaunty, installed envyng, ran the script (which installed the nvidia 180.44 driver) and everything worked.

Thanks for your help!

I tried that, didn't work still getting the same error in log[dmesg]

---

### Post by sgxy on 2009-05-25
I had the same problem and I solved it:

You have to install envyng

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

-> run envyng ->select 180.44 (or any newer version) -> activate

then download the kernel-headers for your kernel.I have Kernel 2.6.27-9 running and installed the following package:

[http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9](http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9)

sudo dpkg -i linux-headers-2.6.27-9_2.6.27-9.19_all.deb

You may have to download this package as well:

[http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9-generic](http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9-generic)

re-run envyng and everything should work out :)

I hope this helps to solve to your Problem.

---

### Post by siddtharth on 2009-05-25
> **sgxy said:**
> I had the same problem and I solved it:

You have to install envyng

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

-> run envyng ->select 180.44 (or any newer version) -> activate

then download the kernel-headers for your kernel.I have Kernel 2.6.27-9 running and installed the following package:

[http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9](http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9)

sudo dpkg -i linux-headers-2.6.27-9_2.6.27-9.19_all.deb

You may have to download this package as well:

[http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9-generic](http://packages.ubuntu.com/de/intrepid-updates/linux-headers-2.6.27-9-generic)

re-run envyng and everything should work out :)

I hope this helps to solve to your Problem.

[RIGHT][/RIGHT]

nope, didn't work still the same problem. I have attached the output for dmesg.

Thanks!

---

### Post by sgxy on 2009-05-26
[B]

Download the kernel headers for your Kernel:
[/B]
[http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11_2.6.28-11.42_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11_2.6.28-11.42_all.deb)

sudo dpkg -i linux-headers-2.6.28-11_2.6.28-11.42_all.deb

[B]then download the generic kernel header files:
[/B]
[http://packages.ubuntu.com/de/jaunty/linux-backports-modules-2.6.28-11-generic](http://packages.ubuntu.com/de/jaunty/linux-backports-modules-2.6.28-11-generic)
[B]
then:[/B]

sudo apt-get install libc6-dev

[B]check if you have the right gcc version:
[/B]
```

gcc --version

```should be above 3.4

**then:**

```
killall gdm
```**or:**

```

sudo /etc/init.d/gdm stop

```[B]
try to run the install the nvidia script:[/B]

[http://us.download.nvidia.com/XFree86/Linux-x86_64/180.51/NVIDIA-Linux-x86_64-180.51-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/180.51/NVIDIA-Linux-x86_64-180.51-pkg2.run)

**Then follow the script dialog:**

[COLOR=Black]
[/COLOR] [COLOR=#0000ff][FONT=Tahoma][COLOR=Black]> No precompiled kernel interface was found to match your kernel. Would you like installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site[/COLOR]

[COLOR=Black]choose: YES


**You could also try to update your BIOS since it seems flawed:**


[/COLOR][/FONT][/COLOR]```

                                       [LEFT][   10.303933] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/LEFT]
    [LEFT][   10.303938] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:[/LEFT]
    [LEFT][   10.303939] NVRM: BAR1 is 256M @ 0x00000000 (PCI:0001:00.0)[/LEFT]
    [LEFT][   10.303942] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or[/LEFT]
    [LEFT][   10.303942] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other[/LEFT]
    [LEFT][   10.303943] NVRM: system software do not currently support this configuration[/LEFT]
   
  

```[COLOR=#0000ff][FONT=Tahoma]
[B][COLOR=Black]What's more,check your nvidia installer log:


[/COLOR][/B][/FONT][/COLOR] ```
cat /var/log/nvidia-installer.log > log.txt
```[COLOR=#0000ff][FONT=Tahoma]

[/FONT][/COLOR]

---

### Post by siddtharth on 2009-05-26
> **sgxy said:**
> [B]

Download the kernel headers for your Kernel:
[/B]
[http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11_2.6.28-11.42_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11_2.6.28-11.42_all.deb)

sudo dpkg -i linux-headers-2.6.28-11_2.6.28-11.42_all.deb

[B]then download the generic kernel header files:
[/B]
[http://packages.ubuntu.com/de/jaunty/linux-backports-modules-2.6.28-11-generic](http://packages.ubuntu.com/de/jaunty/linux-backports-modules-2.6.28-11-generic)
[B]
then:[/B]

sudo apt-get install libc6-dev

[B]check if you have the right gcc version:
[/B]
```

gcc --version

```should be above 3.4

**then:**

```
killall gdm
```**or:**

```

sudo /etc/init.d/gdm stop

```[B]
try to run the install the nvidia script:[/B]

[http://us.download.nvidia.com/XFree86/Linux-x86_64/180.51/NVIDIA-Linux-x86_64-180.51-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/180.51/NVIDIA-Linux-x86_64-180.51-pkg2.run)

**Then follow the script dialog:**

[COLOR=Black]
[/COLOR] [COLOR=#0000ff][FONT=Tahoma][COLOR=Black][/COLOR]

[COLOR=Black]choose: YES


**You could also try to update your BIOS since it seems flawed:**


[/COLOR][/FONT][/COLOR]```

                                       [LEFT][   10.303933] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/LEFT]
    [LEFT][   10.303938] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:[/LEFT]
    [LEFT][   10.303939] NVRM: BAR1 is 256M @ 0x00000000 (PCI:0001:00.0)[/LEFT]
    [LEFT][   10.303942] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or[/LEFT]
    [LEFT][   10.303942] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other[/LEFT]
    [LEFT][   10.303943] NVRM: system software do not currently support this configuration[/LEFT]
   
  

```[COLOR=#0000ff][FONT=Tahoma]
[B][COLOR=Black]What's more,check your nvidia installer log:


[/COLOR][/B][/FONT][/COLOR] ```
cat /var/log/nvidia-installer.log > log.txt
```[COLOR=#0000ff][FONT=Tahoma]

[/FONT][/COLOR]

First of all thanks for you help.
I'm assuming that I'll have to first uninstall the nvidia driver installed using Envyng then I'll follow your instructions.
also my laptop is sony vaio vgn fe890 and there is no bios update for it. I have vista as the other OS and it just works fine so I'm assuming that it's not a bios issue.

I'll update thread once I have tried your latest suggestion.

Thanks!

---

### Post by siddtharth on 2009-05-26
didn't work.

---

### Post by sgxy on 2009-05-27
> **siddtharth said:**
> didn't work.

could you please post your nvidia installer log file:

cat /var/log/nvidia-installer.log > log.txt

---

### Post by siddtharth on 2009-05-30
> **sgxy said:**
> could you please post your nvidia installer log file:

cat /var/log/nvidia-installer.log > log.txt

attached with this post is the output for dmesg and nvidia-install.log

Thanks!

---

