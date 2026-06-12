---
title: "Struggling with Ralink RT5370 card"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by _jpg_ on 2012-01-05
I've been trying to get this usb wifi adapter working on Ubuntu 11.10 but haven't had much success so far. I've downloaded and compiled the driver, and I can load the driver, but cannot bring up the interface. All I get is:


```
=== pAd = c94fc000, size = 509880 ===

<-- RTMPAllocTxRxRingMemory, Status=0
<-- RTMPAllocAdapterBlock, Status=0
usbcore: registered new interface driver rt2870
(Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]
NICLoadFirmware: MCU is not ready


ERROR!!! NICLoadFirmware failed, Status[=0x00000001]
!!! rt28xx Initialized fail !!!
```

Note that I'm on PPC, but I'm assuming this shouldn't affect the firmware loading?

Does anyone have any suggestions? Or any ideas on what I can try next? Any help would be appreciated.

Thanks

jpg

---

### Post by chili555 on 2012-01-05
Please show us:```
modinfo rt5370sta
```Let's see what firmware it wants. Also, let's see:```
dmesg | grep -e rt5 -e firm
```

---

### Post by _jpg_ on 2012-01-05
modinfo ra5370sta:

```
filename:       /lib/modules/3.0.14/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     BECD45954752CD686B2920E
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:
vermagic:       3.0.14 mod_unload
parm:           mac:rt28xx: wireless mac addr (charp)

```

Nothing in dmesg about firmware; dmesg | grep -e firm gives nothing.

Another thing to note here - I've built my own kernel - I don't think that the stock kernel supports my hardware.

---

### Post by chili555 on 2012-01-05
> I don't think that the stock kernel supports my hardware.Tell me more. Maybe so and maybe not.

As you can see, rt5370sta does not ask for firmware. Can you confirm that no firmware is included in the package you built? You might be interested in this: [http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)

The poster tricked rt2800usb to drive his 5370 device. Interestingly, rt2800usb requires firmware! ```
modinfo rt2800usb
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
[COLOR="Red"]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     61CFBA7ACB6A210B48AA6CB
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
<snip>
```

---

### Post by _jpg_ on 2012-01-05
Thanks for the info! I checked out the package which I got from the ralink website, and indeed there is firmware included, and it is the same as that other thread:

```
$ find . -name \*.bin
./common/rt2870.bin

```

Any idea why this isn't getting referenced from my module?

Also my hardware is a [Kurobox HG]("http://en.wikipedia.org/wiki/Buffalo_network-attached_storage_series#Kuro_Box"). It's PPC, and requires some bits in the kernel to disable it's watchdog to make it not shut down. It also requires some DTC stuff, which I don't know much about - I'm not sure if it is required by the hardware, or by Uboot which I use to boot it. I'm happy to give a stock kernel a try if I can't get it working this way (but it's a bit of a pita as I have no display, not even a console).

---

### Post by chili555 on 2012-01-05
> Also my hardware is a Kurobox HG. It's PPC, and requires some bits in the kernel to disable it's watchdog to make it not shut down. It also requires some DTC stuff, which I don't know much about - I'm not sure if it is required by the hardware, or by Uboot which I use to boot it. I'm happy to give a stock kernel a try if I can't get it working this way (but it's a bit of a pita as I have no display, not even a console).Is this Chinese or Klingon?? Seriously, I have little to no understanding of these matters. Better to ask in General Help.> Any idea why this isn't getting referenced from my module?None. Is the file in the place where modules usually look; i.e. /lib/firmware?```
$ locate rt2870.bin
/lib/firmware/rt2870.bin
```Can you please try copying it there and unload/reload the module and check dmesg again?

I have abbreviated my suggestion; you know what you're doing!

---

### Post by _jpg_ on 2012-01-05
Don't worry about the hardware! I know it's somewhat foreign but it does seem to be working ok - support was added to linux mainline a while back so it's currently running fine.

Just checked and the firmware _is_ in the /lib/firmware directory, it's 8192 bytes (and has symlinks pointing to it from rt3070 and rt3090 in there too). So it looks like for some reason my module is failing to recognised that the firmware is required?

---

### Post by chili555 on 2012-01-06
I'm not at all sure it is a firmware issue. Your *modinfo* makes no mention of firmware. I built a copy of the package and mine is identical. Even if it wants firmware and *modinfo* is incorrect, the firmware is there.

When I built the package, there were many and numerous warnings and I wonder if all the inconsistencies add up to not allow the driver to function on this later kernel. I have no idea how to mend it.

If you'd like to try, instead, to get rt2800usb to drive your device, I'll be glad to help.

---

### Post by _jpg_ on 2012-01-07
I'm happy to give the rt2800usb driver a go, and would certainly appreciate your help!

I'm not at home this weekend, but I'll give it a go on mon/tues.

Thanks again!

---

### Post by chili555 on 2012-01-07
> **_jpg_ said:**
> I'm happy to give the rt2800usb driver a go, and would certainly appreciate your help!

I'm not at home this weekend, but I'll give it a go on mon/tues.

Thanks again!If you need some assistance, post back and I'll be happy to help.

---

### Post by _jpg_ on 2012-01-09
Just thought I'd post to say that I tried this with the rt2800usb driver, and it worked fine. I'm using wpa_supplicant and now the NAS boots and gets itself onto the network using the USB wifi card.

Thanks very much for your suggestions chili, don't think I'd have got it working without your suggestions!

_jpg_

---

### Post by chili555 on 2012-01-09
> **_jpg_ said:**
> Just thought I'd post to say that I tried this with the rt2800usb driver, and it worked fine. I'm using wpa_supplicant and now the NAS boots and gets itself onto the network using the USB wifi card.

Thanks very much for your suggestions chili, don't think I'd have got it working without your suggestions!

_jpg_Awesome! Glad it's working.

---

