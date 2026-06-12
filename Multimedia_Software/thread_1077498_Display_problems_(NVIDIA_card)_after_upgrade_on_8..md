---
title: "Display problems (NVIDIA card) after upgrade on 8.04"
date: 2009-02-22
forum: Multimedia Software
---

### Post by sroy on 2009-02-22
Hello everybody,

I ran into problems with my desktop display after I installed one of the upgrades recently. Here is a brief description of the problems that I am facing.

I have Ubuntu 8.04 running on a Dell machine which has an NVIDIA graphics card. I had twinview working on it with Dell and HP monitors. I also configured it to get my Wacom Intuos tablet working on it. A week ago, I upgraded my system with Linux kernel 2.6.24-23 and since then I have been stuck with display problems on my desktop. Here is a sequence of problems and troubleshooting that I did to fix them.

1. First, it would get stuck during reading files to boot up with a "qc timeout error". To fix that, I added the parameters "noapic and acpi=off" to the boot command.

2. After that fix, boot up started to happen correctly but it would now get stuck while starting up Xserver (only a blank screen). So, after making a backup copy of my customized xorg.conf file, I reset the xorg.conf by booting through the "recovery mode".

3. The above got the Xserver started but my screen resolution got set at 800x600 resolution. I had the "nvidia-glx-new" package installed. So, I tried to reconfigure the nvidia settings by "dpkg-reconfigure nvidia-glx" but, after all the settings, it kept on giving me an error about a battery: 
"FATAL: Error inserting battery (/lib/modules/2.6.24-23-generic/kernel/drivers/acpi/battery.ko)"

So, currently, I am stuck at 800x600 resolution on my machine. I remember to have seen problem #1 earlier (after one of the upgrades) and I had fixed it back then, just by following some instructions from various forums. However, this "battery" error is new to me, although I am not sure if it has anything to do with the Xserver configuration.

I have attached my current "xorg.conf" (the one with 800x600) resolution and my original xorg.conf (xorg.conf.nvidia_and_wacom) with this post.

I would really appreciate it if someone could give me any pointers to fixing the aforementioned problems.

JFYI, the specs of my desktop are:
Dell Vostro 400 Mini Tower, Intel(R) Core™2 Quad Proc Q6600, 2.40GHz, 2GB RAM, 160GB, 16X (DVD+/-RW) Burner Drive, Dell 20 inch Widescreen E207WFP Analog Flat Panel Display, 128MB NVIDIA(R) GeForce(R) 8300GS

regards,
Soumyaroop.

---

