---
title: "Intel 3945ABG"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by oboedad55 on 2009-08-18
I had this card working with no problems. I had to reinstall jaunty and now it can't see the card. I know this card has been discussed before but I didn't find enough about it.
This is on an Acer laptop #5672WLMI, 2 gigs ram, ATI Mobility Radeon X1400, Duo core 1.66 gHz.

Thanks!

---

### Post by SoftwareExplorer on 2009-08-19
Does windows see the card?

---

### Post by oboedad55 on 2009-08-19
> **SoftwareExplorer said:**
> Does windows see the card?

Yes it does. And it worked yesterday, but today no livecd or installation sees the wireless connection. Very frustrating! I suppose I could grab one of those USB wireless gizmos. You  have any experience with those things?

Jon

---

### Post by SoftwareExplorer on 2009-08-19
> **oboedad55 said:**
> Yes it does. And it worked yesterday, but today no livecd or installation sees the wireless connection. Very frustrating! I suppose I could grab one of those USB wireless gizmos. You  have any experience with those things?

Jon
I had one that didn't have a native linux driver and it was a pain to set up. So get one that's linux supported if you get one. (I'm wishing you a non-sarcastic good luck with that, you might need it) Of course, there's ndiswrapper, but it isn't always easy to get working.

---

### Post by oboedad55 on 2009-08-19
> **SoftwareExplorer said:**
> I had one that didn't have a native linux driver and it was a pain to set up. So get one that's linux supported if you get one. (I'm wishing you a non-sarcastic good luck with that, you might need it) Of course, there's ndiswrapper, but it isn't always easy to get working.

What's so puzzling is that it was working without any extra badgering until today. If it didn't work in windows it would make sense.

---

### Post by Gausian on 2009-08-19
what happens when you...

```
sudo modprobe iwl3945
```

does the wireless "wake up"?

---

### Post by scorp123 on 2009-08-19
> **oboedad55 said:**
> I had this card working with no problems. I had to reinstall jaunty and now it can't see the card.  If I had to guess I'd say a kernel-module (= "drivers") package is missing. Can you please type this into a terminal and post the output:```
 dpkg -l linux* | grep ii
```

---

### Post by slakkie on 2009-08-19
Could you post the output of the following commands:

```

lsmod | grep iwl
lspci | grep -i Network
sudo lshw -C network

```

---

### Post by scorp123 on 2009-08-19
Turns out that the laptop I am writing this from has the same Intel 3945 WiFi chipset. So I can follow my own advice :)

So ... typing the command I mentioned above gives me these results:

```
> dpkg -l linux* | grep ii

ii  linux-firmware                                              1.11                                      Firmware for Linux kernel drivers
ii  linux-generic                                               2.6.28.15.20                              Complete Generic Linux kernel
ii  linux-headers-2.6.28-15                                     2.6.28-15.48                              Header files related to Linux kernel version
ii  linux-headers-2.6.28-15-generic                             2.6.28-15.48                              Linux kernel headers for version 2.6.28 on x
ii  linux-headers-generic                                       2.6.28.15.20                              Generic Linux kernel headers
ii  linux-image-2.6.28-15-generic                               2.6.28-15.48                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-generic                                         2.6.28.15.20                              Generic Linux kernel image
ii  linux-libc-dev                                              2.6.28-15.48                              Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.28-15-generic                  2.6.28-15.20                              Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common                             2.6.28-15.20                              Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic                            2.6.28.15.20                              Restricted Linux modules for generic kernels
ii  linux-sound-base                                            1.0.18.dfsg-1ubuntu8                      base package for ALSA and OSS sound systems
```

What's important here are the "linux-firmware" and "linux-restricted-modules" packages. Without those two it's likely WiFi won't work as most WiFi cards need some firmware that the OS loads at boot time. And here on Ubuntu it's those two packages that provide this.

Can you please check if have those packages are installed?

---

### Post by slakkie on 2009-08-19
I don't recall I needed all those restricted or common linux kernel things for my iwl to work (using the same card as OP).

Could you check wheter you have the iwl3945.ko file?

```

ls -l /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko

```

Or simple apt-file search iwl3945.ko and check if you have that package installed.

---

### Post by scorp123 on 2009-08-19
> **slakkie said:**
> I don't recall I needed all those restricted or common linux kernel things for my iwl to work (using the same card as OP).  You're right, I just confused this with the Atheros card in my previous laptop. Oh well. Never mind.

Doing "dpkg -S /lib/modules/`uname -r`/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko" on my laptop shows that the module is part of this package:

**linux-image-2.6.28-15-generic**

The kernel release number (2.6.28.15 in my case) will vary depending on what kernel is installed (check with: uname -r). The same package also contains the kernel image that's being loaded during boot.

So unless OP compiled his own kernel by hand somehow or manually deleted a few files the iwl3945.ko file definitely should be there because it gets installed together with the rest of the bootable kernel. So without that package the system would not boot in the first place unless you have another kernel package somewhere somehow.

@OP ... out of curiosity: Can you please give me your GRUB config? e.g. post the output of this command:
```
cat /boot/grub/menu.lst
``` ... I just want to be sure about what gets booted or not when you turn on your system ....

---

### Post by oboedad55 on 2009-08-19
> **Gausian said:**
> what happens when you...

```
sudo modprobe iwl3945
```

does the wireless "wake up"?

Wireless does not wake up. I get a return message; All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future realease.

Not a clue.

Jon

---

