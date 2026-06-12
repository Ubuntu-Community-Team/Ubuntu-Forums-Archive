---
title: "ignored blacklist ath_pci, ath_hal / problems with ar5007eg"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by karomann on 2009-04-12
Hi,
So as to get my ar5007eg working I have installed linux-backports-modules-2.6.27-14-generic, linux-backports-modules-intrepid, linux-backports-modules-intrepid-generic.

I have also blacklisted ath_pci and ath_hal:

```
kamil@Corleone:~$ grep 'ath' /etc/modprobe.d/*
/etc/modprobe.d/blacklist:blacklist ath_hal
/etc/modprobe.d/blacklist:blacklist ath_pci
/etc/modprobe.d/blacklist~:#blacklist ath_hal
/etc/modprobe.d/blacklist~:#blacklist ath_pci
/etc/modprobe.d/blacklist.dpkg-old:blacklist ath_pci
/etc/modprobe.d/blacklist-local:blacklist ath_hal
/etc/modprobe.d/blacklist-local:blacklist ath_pci
/etc/modprobe.d/blacklist-restricted:blacklist ath_hal
```

but the ath_pci and ath_hal modules seem to be loaded on ubuntu startup:

```
kamil@Corleone:~$ dmesg | grep ath
[   24.427244] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   24.502607] ath_pci: 0.9.4
[   24.502659] ath_pci 0000:03:00.0: enabling device (0000 -> 0002)
[   24.502670] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.502687] ath_pci 0000:03:00.0: setting latency timer to 64
[   24.551126] ath_pci 0000:03:00.0: PCI INT A disabled
```

So what's wrong with my configuration??

After booting the system I try to manually insert the ath5k module via sudo rmmod ath_pci, sudo rmmod ath_hal, sudo modprobe ath5k, but I get an error in dmesg:

```
[  141.264828] ath_pci: driver unloaded
[  145.548254] ath_hal: driver unloaded
[  156.340824] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[  156.340848] ath5k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  156.340875] ath5k 0000:03:00.0: setting latency timer to 64
[  156.344492] ath5k 0000:03:00.0: registered as 'phy0'
[  156.354559] ath5k phy0: failed to wakeup the MAC Chip
[  156.354706] ath5k 0000:03:00.0: PCI INT A disabled
[  156.357461] ath5k: probe of 0000:03:00.0 failed with error -5
```

I use the generic kernel image, package linux-image-2.6.27-14-generic

Any help greatly appreciated :)

---

### Post by karomann on 2009-04-13
Googled around and finally this helped me:

```
echo 'blacklist ath_pci' | sudo tee -a /etc/modules
echo 'blacklist ath_hal' | sudo tee -a /etc/modules
```

And also commented out 'ath_pci' in /etc/modules

Although I live in Poland I had also to comment out line 'lbm_cw_cfg80211 ieee80211_regdom=EU' in /etc/modprobe.d/options. I added this line myself because the default regdom was set to US and I thought the EU setting would fit me better. It didn't as it gave me segmentation fault and error:

```
BUG: unable to handle kernel NULL pointer dereference at 00000004
```

---

