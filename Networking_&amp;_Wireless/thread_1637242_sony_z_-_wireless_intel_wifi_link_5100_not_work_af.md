---
title: "sony z - wireless intel wifi link 5100 not work after apt-get upgrade"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by capede on 2010-12-04
hi y'all, i'd like to extend that ma intel wifi link 5100 is not detected no more after perform upgrade package( upgrade the kernel too ).

i dunno where the exactly problem is ?

when im using command 'lshw -C network' , there is appear to be detected, but not on command 'iwconfig' or even 'ifconfig' it just show nothin. also network-manager no longer show that ma wireless is work properly anymore.

the old kernel : 2.6.25-22 ( my wireless detected and usable )
the new kernel : 2.6.25-23 ( my wireless detected and unusable )

anyone mind to explain ?

---

### Post by chili555 on 2010-12-04
Let's ask your computer to explain. Please open a terminal and do:```
rfkill list all
dmesg | grep iwlagn
```Post the result and we'll proceed.

---

### Post by capede on 2010-12-04
> **chili555 said:**
> Let's ask your computer to explain. Please open a terminal and do:```
rfkill list all
dmesg | grep iwlagn
```Post the result and we'll proceed.

result : 
```


[   16.250237] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.250239] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.250314] iwlagn 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.250343] iwlagn 0000:06:00.0: setting latency timer to 64
[   16.250388] iwlagn 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   16.288305] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.288455] iwlagn 0000:06:00.0: irq 46 for MSI/MSI-X
[   16.301461] iwlagn 0000:06:00.0: request for firmware file 'iwlwifi-5000-2.ucode' failed.
[   16.302851] iwlagn 0000:06:00.0: request for firmware file 'iwlwifi-5000-1.ucode' failed.
[   16.302889] iwlagn 0000:06:00.0: no suitable firmware found!
[   16.303557] iwlagn 0000:06:00.0: PCI INT A disabled

```

looking forward for your proceed .... though:popcorn:

---

### Post by capede on 2010-12-04
mmm i thought, it askin for ucode file, thus download the firmware from [http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz) and extract the exact file to /lib/firmware, and reboot..

then it work properly now

but, im wondering the dmesg below :

```

root@ubuntu:/home/myabi# dmesg | grep iwlagn
[   16.566066] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.566068] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.566159] iwlagn 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.566188] iwlagn 0000:06:00.0: setting latency timer to 64
[   16.566240] iwlagn 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   16.603220] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.603345] iwlagn 0000:06:00.0: irq 46 for MSI/MSI-X
[   16.642272] iwlagn 0000:06:00.0: loaded firmware version 8.24.2.12
[   29.675488] iwlagn 0000:06:00.0: Unable to find TIM Element in beacon
[   29.676715] iwlagn 0000:06:00.0: Unable to find TIM Element in beacon
[   44.928828] iwlagn 0000:06:00.0: Unable to find TIM Element in beacon
[   44.928981] iwlagn 0000:06:00.0: Unable to find TIM Element in beacon
[   50.580842] iwlagn 0000:06:00.0: Unable to find TIM Element in beacon
[   50.580989] iwlagn 0000:06:00.0: Unable to find TIM Element in beacon

```what 'Unable to find TIM Element in beacon' mean ?
is that an issue ?

thx for appreciate :)

---

### Post by chili555 on 2010-12-04
> what 'Unable to find TIM Element in beacon' mean ?
is that an issue ?I don't believe so. I find a very few references in Google, but no answers. As long as you connect, I'd guess it's harmless. Post back if it troublesome.

---

