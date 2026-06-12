---
title: "ipw3945 &amp; dapper 6.06 - having problems please help"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by ungaro on 2006-07-03
Ok, i've tried too much on installing a basic wireless adapter so i'm asking for your help because i don't want to make things worse.  :)

please help me, it was seeing before but now iwconfig says no wireless extensions...

**ipw3945 & dapper 6.06 on dell inspiron e1705**

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition AudioController (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1(rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2(rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3(rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4(rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SerialATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0098(rev a1)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:0c:00.0 
Network controller: Intel Corporation: Unknown device 4
```

```
 uname -r
2.6.15-25-386

```

```

ungaro@medley:~/Desktop/ieee80211-1.1.14$ sudo make
Checking in /lib/modules/2.6.15-25-386 for ieee80211 components...
find: Symbolic link `/lib/modules/2.6.15-25-386/build/linux-headers-2.6.15-25-386' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/lib/modules/2.6.15-25-386/build/linux-headers-2.6.15-25-386' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
make -C /lib/modules/2.6.15-25-386/build M=/home/ungaro/Desktop/ieee80211-1.1.14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'

```


```

ungaro@medley:~/Desktop/ieee80211-1.1.14$ sudo make install
make -C /lib/modules/2.6.15-25-386/build M=/home/ungaro/Desktop/ieee80211-1.1.14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
install -d /lib/modules/2.6.15-25-386/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.15-25-386/net/ieee80211/
install -d `echo /lib/modules/2.6.15-25-386/include | grep "/net\$" || echo /lib/modules/2.6.15-25-386/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.15-25-386/include | grep "/net\$" || echo /lib/modules/2.6.15-25-386/include/net`
mkdir -p /lib/modules/2.6.15-25-386/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.15-25-386/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.15-25-386


```


```

ungaro@medley:~/Desktop/older/ipw3945-1.1.0-pre2$ sudo make
sed: can't read /lib/modules/2.6.15-25-386net/ieee80211.h: No such file or directory

 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


 Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
```

---

### Post by ungaro on 2006-07-04
hey at least please tell me what to investigate, i've now booted into windows and everythings working perfectly here, but i want to use ubuntu. :(

---

### Post by gmc on 2006-07-04
Unfortunately, you're a little a head of me. I plan on trying to install the updated 3945 driver when I get home. However, I noticed that the sed error is missing something...

> 
```

ungaro@medley:~/Desktop/older/ipw3945-1.1.0-pre2$ sudo make
[B]sed: can't read /lib/modules/2.6.15-25-386net/ieee80211.h: No such file or directory
[/B]

```


There should be a / between 2.6.15-25-386 and the word 'net'. I'm not sure why it's not there but that's what's causing your problem. I think somewhere during the installation of the ieee source is where you've missed something.

Gord

---

### Post by ungaro on 2006-07-04
hey do not install ieee80211-1.1.14 instead try ieee80211-1.1.11 if you do not want to waste your full day trying to understand what you messed up.

i've installed 1.1.1 and everything is working fine now.

---

### Post by gmc on 2006-07-04
[QUOTE=ungaro]hey do not install ieee80211-1.1.14 instead try ieee80211-1.1.11 if you do not want to waste your full day trying to understand what you messed up.

i've installed 1.1.1 and everything is working fine now.[/QUOTE]

Thanks for the tip.

Gord

---

### Post by saratoga on 2006-07-15
Did anyone figure out a solution?  I have the exact same issue, and have had no luck resolving it.

---

### Post by Belohin on 2006-07-15
Hello folks!

I have a Toshiba Satellite L100-120 with the same wireless device.
From my viewpoint the first trouble is in the

'Network Controller: Intel Corporation: Unknown device 4'

message.
If the system does not detect the device correctly, it will not apply the driver for it. (Maybe I am wrong.)
I have the same message and suspect the source of problem is that the wireless switch was off during installation (There was not a wireless network around and I have forgot about it).
My hope is in a new installation now.

---

### Post by Belohin on 2006-07-18
Well, after the new installation with wireless switch ON the device and the drivers are OK.

I have problems yet but around the WEP I suppose.

---

