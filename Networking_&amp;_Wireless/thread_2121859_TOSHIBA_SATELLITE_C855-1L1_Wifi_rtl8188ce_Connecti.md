---
title: "TOSHIBA SATELLITE C855-1L1: Wifi rtl8188ce Connection Issue"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by napril on 2013-03-03
Hi, 
I've been reading several threads on the forums about  people having the same issue as me, which is unstable and slow wifi with  the Realtek rtl8188ce wifi adapter. None of the threads have helped.

Please let me know if you need more info than this:

**Laptop:**
```

TOSHIBA SATELLITE C855-1L1
Ubuntu 12.04 LTS 64-bit

```

**Kernel/architecture (including 32 vs. 64 bit):**
$ uname -mr
```

3.2.0-38-generic x86_64

```

**Wireless Brand, Model and Wireless Chipset:**
$ lspci | grep Network
```

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

**Modules:**
$ lsmod | grep 8192
```

rtl8192ce              84872  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111245  1 rtl8192ce
mac80211              506862  3 rtl8192ce,rtl8192c_common,rtlwifi

```

**Kernel boot messages:**
$ dmesg | grep 8192
```

[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88014ec00000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[    9.027829] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.027842] rtl8192ce 0000:08:00.0: setting latency timer to 64
[    9.027917] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: Unknown. Bug?
[    9.138519] rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!
[    9.138564] rtl8192ce 0000:08:00.0: PCI INT A disabled

```

**Network configuration:**
$ sudo lshw -C network
```

  *-network UNCLAIMED     
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c3000000-c3003fff

```

Thanks in advance.

---

### Post by chili555 on 2013-03-03
> rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!We have a slight mystery on our hands: is the firmware in place and the driver didn't see and grab it or is the firmware missing? For the benefit of the driver dawgs out there, the driver rtl8192ce looks for required firmware:```
$ modinfo rtl8192ce
filename:       /lib/modules/3.5.0-25-generic/updates/cw-3.6/rtl8192ce.ko
[COLOR="#FF0000"]firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin[/COLOR]
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>

```Let's see if it's present and readable:```
ls -al /lib/firmware/rtlwifi | grep cfw
```We hope we see:> chili@Think410:~$ ls -al /lib/firmware/rtlwifi | grep cfw
-rw-r--r--  1 root root  13540 Aug  3  2012 rtl8192cfw.bin
-rw-r--r--  1 root root  14800 Aug  3  2012 rtl8192cfwU_B.bin
-rw-r--r--  1 root root  14818 Aug  3  2012 rtl8192cfwU.binIn this example, the firmware exists and is 'r' readable. If you have none, install it with:```
sudo apt-get install linux-firmware
```If you have it, it's readable and the driver still doesn't grab it, let's see why:```
dmesg | grep rtl
```Thanks.

---

### Post by napril on 2013-03-05
> **chili555 said:**
> 
Let's see if it's present and readable:
```
ls -al /lib/firmware/rtlwifi | grep cfw
```


```

-rw-r--r--  1 root root  16192 mar  3 16:26 rtl8192cfw.bin
-rwxr-xr-x  1 root root  14800 mar  3 16:26 rtl8192cfwU_B.bin
-rwxr-xr-x  1 root root  14818 mar  3 16:26 rtl8192cfwU.bin

```

```

$ dmesg | grep rtl
[   11.217213] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.217229] rtl8192ce 0000:08:00.0: setting latency timer to 64
[   11.560677] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.561199] rtlwifi: wireless switch is on

```

It's allright now?

Thanks a lot.

---

### Post by chili555 on 2013-03-06
> It's allright now?Looks very fine indeed! May I assume it connects and works as expected? If so, please use thread tools at the top to mark Solved.

---

### Post by napril on 2013-03-06
> **chili555 said:**
> 
May I assume it connects and works as expected? 


Yes, it connects as expected,
thanks!

---

