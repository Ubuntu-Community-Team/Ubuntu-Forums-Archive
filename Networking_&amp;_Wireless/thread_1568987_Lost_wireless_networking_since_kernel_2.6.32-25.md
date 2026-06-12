---
title: "Lost wireless networking since kernel 2.6.32-25"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by RavanH on 2010-09-06
Hi,

Since yesterday, after the latest kernel upgrade from 2.6.31-24 to -25, I have no wireless networking anymore :cry: . Now I have been left in the dark before by Ubuntu so I'm not saying I'm surprised here :roll: just glad there is always this marvellous community that has answers most of the time...

My wireless is a ZyXel ZyAIR G-100 PCMCIA card which worked out of the box on 9.10 but since Ubuntu 10.04 I had to install linux-backports-modules-wireless-lucid-generic which was actually a meta package depending on linux-backports-modules-wireless-2.6.32-**24**-generic

Along with the kernel update, linux-backports-modules-wireless-lucid-generic upgraded to version 2.6.32.25.27 but it  currently (suddenly?) depends on linux-backports-modules-**compat**-wireless-2.6.34-2.6.32-**25**-generic... (notice the 2 differences!)

The old linux-backports-modules-wireless is still installed but I guess the new linux-backports-modules-**compat**-wireless is being used now. I notice that there is a linux-backports-modules-wireless-2.6.35-lucid-generic available but it conflicts with linux-backports-modules-wireless-lucid-generic so I hesitate to install that one and loose my networking completely (I have no eth available, just wlan!) like I have had before...

**DMESG when I boot with kernel 2.6.32-24 (and working wlan0)**:
```
...
[   27.740133] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   27.740201] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[   27.740291] pci 0000:03:00.0: supports D1 D2
[   27.740295] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[   27.740302] pci 0000:03:00.0: PME# disabled
[   27.821823] cfg80211: Calling CRDA to update world regulatory domain
[   27.870641] cfg80211: World regulatory domain updated:
[   27.870647]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.870651]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.870655]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.870658]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.870661]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.870664]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.905196] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   27.905212] p54pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.905229] p54pci 0000:03:00.0: setting latency timer to 64
[   27.932591] phy0: p54 detected a LM86 firmware
[   27.932596] p54: rx_mtu reduced from 3240 to 2376
[   27.932600] phy0: FW rev 2.13.12.0 - Softmac protocol 5.9
[   27.932603] phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
...
[   28.817832] phy0: hwaddr 00:a0:c5:92:72:f4, MAC:isl3890 RF:Frisbee
[   28.827085] phy0: Selected rate control algorithm 'minstrel'
[   28.828114] Registered led device: p54-phy0::assoc
[   28.828140] Registered led device: p54-phy0::tx
[   28.828163] Registered led device: p54-phy0::rx
[   28.828189] Registered led device: p54-phy0::radio
[   28.828201] p54pci 0000:03:00.0: is registered as 'phy0'
...
```

**DMESG when I boot with kernel 2.6.32-25 (and no wlan0)**:
```
...
[   27.490116] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   27.490185] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[   27.490273] pci 0000:03:00.0: supports D1 D2
[   27.490276] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[   27.490283] pci 0000:03:00.0: PME# disabled
...
```

Anybody an idea how to get my wireless card working again under 2.6.32-25 and up?

Thanks :)

---

### Post by RavanH on 2010-09-06
**More info**
Note: this is taken when using kernel 2.6.32-24 with **active networking**!

```
uname -mr
2.6.32-24-generic x86_64

```

```
lspci -v
...
03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Tekram Technology Co.,Ltd. Device 1605
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 84000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: p54pci
        Kernel modules: p54pci, prism54
```


```
$ lsmod | grep "p54pci"
p54pci                  8723  0 
p54common              27327  1 p54pci
led_class               3764  1 p54common
mac80211              261314  2 p54pci,p54common
cfg80211              169518  2 p54common,mac80211
compat_firmware_class     7842  1 p54pci
```

---

### Post by seanlynch on 2010-09-18
I had wireless stop working this morning after a kernel update. reverting the kernel did not help. I have an intel 3945 bag wireless card that has been supported for as long as I've had the laptop (ubuntu 7.10).

I installed wicd and set it to start automatically.
Wicd is working fine, so I'm guessing the bug is in the ubuntu network manager. I've tried twice to open a bug report in launchpad, but the aport 'timed out' each time. I'll keep trying.

I would suggest installing wicd and seeing if this helps with your wireless situation

---

### Post by sfarid on 2010-09-29
It's not just affecting wireless.  My wired network card stopped working after upgrading to 2.6.32-25. 

 r8168 Gigabit Ethernet

---

### Post by Sir James Johnson on 2010-09-30
I've had an analogous problem with my Ethernet Controller (Realtek RTL811/8168B) and it seems it's fixed now.
I simply reinstalled the driver as suggested here [http://ubuntuforums.org/showthread.php?t=582453](http://ubuntuforums.org/showthread.php?t=582453)
Here is the link to the Realtek drivers [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

---

### Post by sfarid on 2010-10-02
> **Sir James Johnson said:**
> I've had an analogous problem with my Ethernet Controller (Realtek RTL811/8168B) and it seems it's fixed now.
I simply reinstalled the driver as suggested here [http://ubuntuforums.org/showthread.php?t=582453](http://ubuntuforums.org/showthread.php?t=582453)
Here is the link to the Realtek drivers [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Thanks!

---

### Post by RavanH on 2010-10-08
> **seanlynch said:**
> I had wireless stop working this morning after a kernel update. reverting the kernel did not help. I have an intel 3945 bag wireless card that has been supported for as long as I've had the laptop (ubuntu 7.10).

I installed wicd and set it to start automatically.
Wicd is working fine, so I'm guessing the bug is in the ubuntu network manager. I've tried twice to open a bug report in launchpad, but the aport 'timed out' each time. I'll keep trying.

I would suggest installing wicd and seeing if this helps with your wireless situation

Thanks for the suggestion, but I've been using Wicd for years and still am now, so that's not fixing it for me ... Neither has the latest update for linux-backports-modules-compat-wireless-2.6.34-2.6.32-25-generic ;(

---

### Post by juha_teuvonnen on 2010-10-23
same issue for me, the wireless networking does not work with the .25 kernel and with .24 everything works fine.

---

### Post by RavanH on 2010-10-23
> **juha_teuvonnen said:**
> same issue for me, the wireless networking does not work with the .25 kernel and with .24 everything works fine.

Do you know what wifi card you are using? Could you give me the output of the command **lspci -v** in terminal screen?

Thanks :)

---

