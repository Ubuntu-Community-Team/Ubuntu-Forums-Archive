---
title: "No Wireless after 12.04 upgrade - BCM43224"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by merin_83 on 2012-05-20
Hi guys, i recently upgraded to 12.04 from 11, and the wireless stopped working, its not even showing up in the network tray. I tried with some threads but no success.. so as some initial info which they were asking in other threads, i post some of my info below


```
merin@merin-M15x:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 84:2b:2b:82:42:c0
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.10-6 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f0f00000-f0f1ffff memory:f0f24000-f0f24fff ioport:1800(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0a00000-f0a03fff
```




```
merin@merin-M15x:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
```


version 
3.2.0-24-generic-pae

Please help thank you !!

---

### Post by wildmanne39 on 2012-05-21
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Then reboot.
Thanks

---

### Post by BenginM on 2012-05-21
Salutation.

Hey merin , Yeah .. if you look at the configuration: Line .. you'll see that the driver= , and firmware= .. are missing .

so try wildmanne suggestion , and please report back

cheers .

---

### Post by merin_83 on 2012-05-22
hi Guys, thank you, here are the results

```
merin@merin-M15x:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source 
[sudo] password for merin: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Unable to locate package broadcom-sta-common 
E: Unable to locate package broadcom-sta-source
``` 



```
merin@merin-M15x:~$ sudo apt-get install b43-fwcutter firmware-b43-installer 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Unable to locate package b43-fwcutter 
E: Unable to locate package firmware-b43-installer 
```

Thank you,
merin

---

### Post by merin_83 on 2012-05-22
okey after the above result, i tried to managed an wired connection to my router and updated ubuntu. Then i ran the same commands again, below are results


```
merin@merin-M15x:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[sudo] password for merin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,252 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181221 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
```



```
merin@merin-M15x:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Get:1 http://mirror.anl.gov/pub/ubuntu/ precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Get:2 http://mirror.anl.gov/pub/ubuntu/ precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]
Fetched 22.4 kB in 0s (108 kB/s)                    
Selecting previously unselected package b43-fwcutter.
(Reading database ... 181172 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2012-05-22 22:31:34--  http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... 46.4.11.11
Connecting to mirror2.openwrt.org (mirror2.openwrt.org)|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1.5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'

100%[======================================>] 15,96,823   1.00M/s   in 1.5s    

2012-05-22 22:31:36 (1.00 MB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]

broadcom-wl-5.10.56.27.3/driver/
broadcom-wl-5.10.56.27.3/driver/Makefile
broadcom-wl-5.10.56.27.3/driver/aiutils.c
broadcom-wl-5.10.56.27.3/driver/bcmsrom.c
broadcom-wl-5.10.56.27.3/driver/bcmutils.c
broadcom-wl-5.10.56.27.3/driver/hnddma.c
broadcom-wl-5.10.56.27.3/driver/hndpmu.c
broadcom-wl-5.10.56.27.3/driver/include/
broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h
broadcom-wl-5.10.56.27.3/driver/include/aidmp.h
broadcom-wl-5.10.56.27.3/driver/include/arminc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h
broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h
broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h
broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h
broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h
broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h
broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h
broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h
broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h
broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h
broadcom-wl-5.10.56.27.3/driver/include/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/igs/
broadcom-wl-5.10.56.27.3/driver/include/epivers.h
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev
broadcom-wl-5.10.56.27.3/driver/include/etioctl.h
broadcom-wl-5.10.56.27.3/driver/include/flash.h
broadcom-wl-5.10.56.27.3/driver/include/flashutl.h
broadcom-wl-5.10.56.27.3/driver/include/hndarm.h
broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h
broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/hnddma.h
broadcom-wl-5.10.56.27.3/driver/include/hndgige.h
broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h
broadcom-wl-5.10.56.27.3/driver/include/hndmips.h
broadcom-wl-5.10.56.27.3/driver/include/hndpci.h
broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h
broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h
broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h
broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h
broadcom-wl-5.10.56.27.3/driver/include/linuxver.h
broadcom-wl-5.10.56.27.3/driver/include/min_osl.h
broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h
broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h
broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h
broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h
broadcom-wl-5.10.56.27.3/driver/include/nicpci.h
broadcom-wl-5.10.56.27.3/driver/include/osl.h
broadcom-wl-5.10.56.27.3/driver/include/pci_core.h
broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h
broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h
broadcom-wl-5.10.56.27.3/driver/include/proto/
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h
broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h
broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h
broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h
broadcom-wl-5.10.56.27.3/driver/include/rts/
broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h
broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h
broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h
broadcom-wl-5.10.56.27.3/driver/include/sbgige.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h
broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h
broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h
broadcom-wl-5.10.56.27.3/driver/include/sflash.h
broadcom-wl-5.10.56.27.3/driver/include/siutils.h
broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h
broadcom-wl-5.10.56.27.3/driver/include/typedefs.h
broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h
broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h
broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h
broadcom-wl-5.10.56.27.3/driver/linux_osl.c
broadcom-wl-5.10.56.27.3/driver/nicpci.c
broadcom-wl-5.10.56.27.3/driver/nvram_stub.c
broadcom-wl-5.10.56.27.3/driver/sbutils.c
broadcom-wl-5.10.56.27.3/driver/siutils.c
broadcom-wl-5.10.56.27.3/driver/siutils_priv.h
broadcom-wl-5.10.56.27.3/driver/wl_apsta/
broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_dbg.h
broadcom-wl-5.10.56.27.3/driver/wl_export.h
broadcom-wl-5.10.56.27.3/driver/wl_iw.c
broadcom-wl-5.10.56.27.3/driver/wl_iw.h
broadcom-wl-5.10.56.27.3/driver/wl_linux.c
broadcom-wl-5.10.56.27.3/driver/wl_linux.h
broadcom-wl-5.10.56.27.3/driver/wlc_key.h
broadcom-wl-5.10.56.27.3/driver/wlc_pub.h
broadcom-wl-5.10.56.27.3/nas_exe.o
broadcom-wl-5.10.56.27.3/shared/
broadcom-wl-5.10.56.27.3/shared/Makefile
broadcom-wl-5.10.56.27.3/shared/UdpLib.c
broadcom-wl-5.10.56.27.3/shared/bcmcvar.h
broadcom-wl-5.10.56.27.3/shared/bcmtimer.h
broadcom-wl-5.10.56.27.3/shared/ctype.c
broadcom-wl-5.10.56.27.3/shared/linux_timer.c
broadcom-wl-5.10.56.27.3/shared/netconf.h
broadcom-wl-5.10.56.27.3/shared/opencrypto.h
broadcom-wl-5.10.56.27.3/shared/rte_timers.c
broadcom-wl-5.10.56.27.3/shared/shutils.c
broadcom-wl-5.10.56.27.3/shared/shutils.h
broadcom-wl-5.10.56.27.3/shared/wl.c
broadcom-wl-5.10.56.27.3/shared/wl_linux.c
broadcom-wl-5.10.56.27.3/shared/wlutils.h
broadcom-wl-5.10.56.27.3/wl_exe.o
This file is recognised as:
  filename   :  wl_prebuilt.o
  version    :  508.1084
  MD5        :  490d4e149ecc45eb1a91f06aa75be071
Extracting b43/ucode19.fw
Extracting b43/lp0initvals14.fw
Extracting b43/ucode16_lp.fw
Extracting b43/ucode16_sslpn.fw
  ucode revision: 1084
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/sslpn2bsinitvals17.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/ucode16_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/sslpn2initvals17.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ucode17.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/ucode20.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
merin@merin-M15x:~$

```


but now there is some difference, i can see a tab called wireless in the network settings, and i see available network, but selection on dose not ask password or do nothing.

but even now i dont get anything for dmseg for iwl..

but get the below for rfkill


```
merin@merin-M15x:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by wildmanne39 on 2012-05-22
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep b43
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by merin_83 on 2012-05-22
hi, here is the result


```
merin@merin-M15x:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        C0:CB:38:52:22:C4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
    Shona:           Infra, 08:86:3B:5F:CE:B0, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    erza-HP-Wireless:Infra, E0:91:F5:D6:88:A4, Freq 2422 MHz, Rate 54 Mb/s, Strength 57
    getyourown:      Infra, 20:4E:7F:C4:B0:68, Freq 2442 MHz, Rate 54 Mb/s, Strength 69 WPA2
    getyourown-5:    Infra, 20:4E:7F:C4:B0:69, Freq 5180 MHz, Rate 54 Mb/s, Strength 65 WPA2
    youbelongtome:   Infra, 00:25:9C:C3:23:B1, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Kuni:            Infra, C0:3F:0E:B1:37:9E, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Sami:            Infra, 00:23:69:B8:93:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    MAMC:            Infra, 00:26:B0:FE:D3:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Jaibolo:         Infra, 00:1C:10:55:E2:F5, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Monique:         Infra, 98:FC:11:58:E8:46, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    ShuvraGhosh:     Infra, 00:15:E9:14:E4:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP
    prasanna:        Infra, 00:23:69:44:92:AB, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WEP
    SpotOn:          Infra, 00:03:52:9C:01:20, Freq 2442 MHz, Rate 54 Mb/s, Strength 19
    Monique-guest:   Infra, 98:FC:11:58:E8:47, Freq 2462 MHz, Rate 54 Mb/s, Strength 15
    S1003:           Infra, 00:22:75:63:7B:C0, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        84:2B:2B:82:42:C0

  Capabilities:
    Carrier Detect:  yes
 Wired Properties
    Carrier:         off
```





```
merin@merin-M15x:~$ sudo iwlist scan
[sudo] password for merin:
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:5F:CE:B0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Shona"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000388ce101f
                    Extra: Last beacon: 2588ms ago
                    IE: Unknown: 000553686F6E61
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030044127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100008863B5FCEB01021001242656C6B696E20436F72706F726174696F6E1023000A46394B3130303220763210240007322E30302E30361042000E31323131333447433230313732381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 0706555320010B10
          Cell 02 - Address: E0:91:F5:D6:88:A4
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"erza-HP-Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000baaf8a63c8
                    Extra: Last beacon: 2484ms ago
                    IE: Unknown: 001065727A612D48502D576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700102D791BB28D64D98A53C7C7B8AB2E6C3D1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403001700000000000000000000000000000000000000
          Cell 03 - Address: 20:4E:7F:C4:B0:68
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"getyourown"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cdb5f04187
                    Extra: Last beacon: 2196ms ago
                    IE: Unknown: 000A676574796F75726F776E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16070F1600000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B000103104700106A2DC0BFA93CA6243DE1902D86F310CB1021000D4E4554474541522C20496E632E1023000844474E44333730301024000844474E443337303010420004333730301054000800060050F20400011011000844474E4433373030100800020084
                    IE: Unknown: DD090010180204F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34070F1600000000000000000000000000000000000000
          Cell 04 - Address: 00:03:52:9C:01:20
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"SpotOn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000017c81191
                    Extra: Last beacon: 2240ms ago
                    IE: Unknown: 000653706F744F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
          Cell 05 - Address: 00:22:75:63:7B:C0
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"S1003"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c162a60176
                    Extra: Last beacon: 2160ms ago
                    IE: Unknown: 00055331303033
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010775B6680BFDE11D38D2F002275637BC0103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020035127A
                    IE: Unknown: DD1E00904C33EE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340A000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: 00:25:9C:C3:23:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"youbelongtome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e4696518a
                    Extra: Last beacon: 2048ms ago
                    IE: Unknown: 000D796F7562656C6F6E67746F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 07 - Address: 00:03:52:9E:DF:30
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"SpotOn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000637a9d0923d
                    Extra: Last beacon: 2116ms ago
                    IE: Unknown: 000653706F744F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
          Cell 08 - Address: 98:FC:11:58:E8:47
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"Monique-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000159832c9f1
                    Extra: Last beacon: 2016ms ago
                    IE: Unknown: 000D4D6F6E697175652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:24:01:45:8C:76
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Waves"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a67c7482f
                    Extra: Last beacon: 2528ms ago
                    IE: Unknown: 00055761766573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 10 - Address: 00:21:29:BA:B8:62
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Campbell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012202494fc
                    Extra: Last beacon: 2312ms ago
                    IE: Unknown: 000843616D7062656C6C
                    IE: Unknown: 010882848B96A4B0C8EC
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32048C9298E0
                    IE: Unknown: DD090010180202F5000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 98:2C:BE:A1:56:89
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"2WIRE388"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020d8aec1181
                    Extra: Last beacon: 2216ms ago
                    IE: Unknown: 00083257495245333838
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 12 - Address: 00:03:52:9E:DF:31
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000637a9d0964a
                    Extra: Last beacon: 2116ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600

eth0      Interface doesn't support scanning.
```


nothing happened !
```
merin@merin-M15x:~$ lsmod | grep b43
merin@merin-M15x:~$
```



As i said earlier, i had tried to connect to my wifi, but once you select there is no place to enter password, and nothing happens. and also i tried to switch on and off the wifi switch on my laptop.

```
merin@merin-M15x:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
May 22 23:01:48 merin-M15x dbus[577]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
May 22 23:01:48 merin-M15x kernel: [   16.437003] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 22 23:01:48 merin-M15x dbus[577]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
May 22 23:01:48 merin-M15x NetworkManager[623]: <info> wpa_supplicant started
May 22 23:01:48 merin-M15x NetworkManager[623]: <info> (wlan0): supplicant interface state: starting -> ready
May 22 23:01:48 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 22 23:01:48 merin-M15x NetworkManager[623]: <info> (wlan0): supplicant interface state: ready -> inactive
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) starting connection 'getyourown'
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0/wireless): access point 'getyourown' has security, but secrets are required.
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 22 23:01:52 merin-M15x NetworkManager[623]: <warn> Activation (wlan0) failed for access point (getyourown)
May 22 23:01:52 merin-M15x NetworkManager[623]: <warn> Activation (wlan0) failed.
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 22 23:01:52 merin-M15x NetworkManager[623]: <info> (wlan0): deactivating device (reason 'none') [0]
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) starting connection 'getyourown-5'
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0/wireless): access point 'getyourown-5' has security, but secrets are required.
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 22 23:01:55 merin-M15x NetworkManager[623]: <warn> Activation (wlan0) failed for access point (getyourown-5)
May 22 23:01:55 merin-M15x NetworkManager[623]: <warn> Activation (wlan0) failed.
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 22 23:01:55 merin-M15x NetworkManager[623]: <info> (wlan0): deactivating device (reason 'none') [0]
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) starting connection 'S1003'
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0/wireless): access point 'S1003' has security, but secrets are required.
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 22 23:02:12 merin-M15x NetworkManager[623]: <warn> Activation (wlan0) failed for access point (S1003)
May 22 23:02:12 merin-M15x NetworkManager[623]: <warn> Activation (wlan0) failed.
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 22 23:02:12 merin-M15x NetworkManager[623]: <info> (wlan0): deactivating device (reason 'none') [0]
```

---

### Post by wildmanne39 on 2012-05-23
Hi, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
sudo modprobe b43
```
Thanks

---

### Post by dannodan2008 on 2012-05-23
Looks like there is alot of us with no wireless. Seems to always be broadcom drivers gggrrr. Im in the same boat mate and ive been trying for 15 days now. Good luck. I will be watching this thread closely :-)
Danno

---

### Post by merin_83 on 2012-05-23
> **wildmanne39 said:**
> Hi, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
sudo modprobe b43
```
Thanks
hi, i tried, but dint notice any change,,,


```
merin@merin-M15x:~$ echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for merin:
blacklist bcma
merin@merin-M15x:~$ echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist brcmsmac
merin@merin-M15x:~$ sudo modprobe b43
merin@merin-M15x:~$
```



thanks,
merin

---

### Post by wildmanne39 on 2012-05-23
Hi, please post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
and the output of:
```
lsmod | grep b43
```
Thanks

---

### Post by merin_83 on 2012-05-23
hi here is the result,


```
merin@merin-M15x:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist bcma
blacklist brcmsmac
merin@merin-M15x:~$
```

```

merin@merin-M15x:~$ lsmod | grep b43
merin@merin-M15x:~$
```


thanks,
merin

---

### Post by wildmanne39 on 2012-05-23
Hi, post the output of:
```
lsmod
```
Thanks

---

### Post by merin_83 on 2012-05-23
hi, here the output,



```
merin@merin-M15x:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1
joydev                 17393  0
clip                   17925  1
atm                    44894  3 clip
snd_hda_codec_hdmi     31775  1
dell_wmi               12601  0
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60251  1
r592                   17808  0
fglrx                2909855  74
memstick               15857  1 r592
snd_hda_intel          32765  10
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                72919  0
serio_raw              13027  0
usbhid                 41906  0
snd_seq_midi           13132  0
hid                    77367  1 usbhid
snd_rawmidi            25424  1 snd_seq_midi
i7core_edac            23382  0
edac_core              46858  1 i7core_edac
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17901  0
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
uvcvideo               67203  0
nand_ecc               13070  1 nand
videodev               86588  1 uvcvideo
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  30 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 dell_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
rfcomm                 38139  0
bnep                   17830  2
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0
ppdev                  12849  0
binfmt_misc            17292  1
ir_lirc_codec          12739  0
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0
ir_sony_decoder        12462  0
ir_jvc_decoder         12459  0
ir_rc6_decoder         12459  0
ir_rc5_decoder         12459  0
ir_nec_decoder         12459  0
ite_cir                24743  0
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ite_cir
video                  19068  0
mac_hid                13077  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  4
sdhci_pci              18324  0
sdhci                  28241  1 sdhci_pci
firewire_ohci          40172  0
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140005  0
merin@merin-M15x:~$
```

---

### Post by wildmanne39 on 2012-05-24
Hi, please the output of:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all

```
Thanks

---

### Post by merin_83 on 2012-05-24
Hi , here is the result,


```
merin@merin-M15x:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux merin-M15x 3.2.0-24-generic-pae #38-Ubuntu SMP Tue May 1 16:40:26 UTC 2012 i686 i686 i386 GNU/Linux
```

```
merin@merin-M15x:~$ iwconfig
lo        no wireless extensions.
```


```
merin@merin-M15x:~$ rfkill list all
merin@merin-M15x:~$

```


thanks,
merin

---

### Post by wildmanne39 on 2012-05-24
Hi, try this:
```
sudo rmmod -f dell_wmi
```
if that does not work run this command:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
watch for errors then run:

Also set your wireless speed in your router to b/g and see if that helps.
```
sudo modprobe b43
```
Thanks

---

### Post by merin_83 on 2012-05-24
> **wildmanne39 said:**
> Hi, try this:
```
sudo rmmod -f dell_wmi
```
if that does not work run this command:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
watch for errors then run:

Also set your wireless speed in your router to b/g and see if that helps.
```
sudo modprobe b43
```
Thanks

The first command dint do anything, then i went for send install cmd, but got error, as i dint connect to internet. Then i connected and tried the install command, everything went down fine. But still not wifi connectivity :(

---

### Post by wildmanne39 on 2012-05-24
Hi, please do:
```
sudo modprobe b43
```
give it a few seconds then post the output of:
```
nm-tool
```
Thanks

---

### Post by wildmanne39 on 2012-05-24
Hi, give this a try:
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r wl
sudo modprobe b43
```
Thanks

---

### Post by merin_83 on 2012-05-24
> **wildmanne39 said:**
> Hi, please do:
```
sudo modprobe b43
```
give it a few seconds then post the output of:
```
nm-tool
```
Thanks

when i tried the modprobe, computer hanged... waited for 2-3 minutes.. then i restarted... let me try the other one

---

### Post by merin_83 on 2012-05-24
hi, after the update, i ran modeprobe -r wl below is the result


```
merin@merin-M15x:~$ sudo modprobe -r wl
FATAL: Module wl not found.
```

One more thing i noticed is that , now i dont see the wireless option in the network setting . on wired is visible.


thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, please do:
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo modprobe wl
```
Then post the output of:
```
iwconfig
rfkill list all
nm-tool
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```
Thanks

---

### Post by merin_83 on 2012-05-25
hi the re install went fine, then here is the o/p of the cmds...



```
merin@merin-M15x:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:233
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

merin@merin-M15x:~$
```



```
merin@merin-M15x:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
merin@merin-M15x:~$
```

```
merin@merin-M15x:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
May 25 17:55:10 merin-M15x wpa_supplicant[13153]: nl80211: 'nl80211' generic netlink not found
May 25 17:55:10 merin-M15x NetworkManager[654]: <info> (eth1): supplicant interface state: starting -> ready
May 25 17:55:10 merin-M15x NetworkManager[654]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 25 17:55:10 merin-M15x NetworkManager[654]: <info> (eth1): supplicant interface state: ready -> inactive
May 25 17:55:11 merin-M15x avahi-daemon[655]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::c2cb:38ff:fe52:22c4.
May 25 17:55:11 merin-M15x avahi-daemon[655]: New relevant interface eth1.IPv6 for mDNS.
May 25 17:55:11 merin-M15x avahi-daemon[655]: Registering new address record for fe80::c2cb:38ff:fe52:22c4 on eth1.*.
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) starting connection 'getyourown'
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1/wireless): access point 'getyourown' has security, but secrets are required.
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 17:55:32 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed for access point (getyourown)
May 25 17:55:32 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed.
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 17:55:32 merin-M15x NetworkManager[654]: <info> (eth1): deactivating device (reason 'none') [0]
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) starting connection 'S1003'
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1/wireless): access point 'S1003' has security, but secrets are required.
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 17:55:35 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed for access point (S1003)
May 25 17:55:35 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed.
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 17:55:35 merin-M15x NetworkManager[654]: <info> (eth1): deactivating device (reason 'none') [0]
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) starting connection 'getyourown-5'
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1/wireless): access point 'getyourown-5' has security, but secrets are required.
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 17:55:38 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed for access point (getyourown-5)
May 25 17:55:38 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed.
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 17:55:38 merin-M15x NetworkManager[654]: <info> (eth1): deactivating device (reason 'none') [0]
merin@merin-M15x:~$ 
```



thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, please post the output of:
```
nm-tool
```
Thanks

---

### Post by merin_83 on 2012-05-25
oops sry, i missed that,,, here is the o/p


```
merin@merin-M15x:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        84:2B:2B:82:42:C0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


merin@merin-M15x:~$
```

this i did when the wired net connection was off.

thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, I think we are getting closer please do:
```
sudo rmmod -f wl
sudo modprobe brcmsmac
```
Then post the output of:
```
nm-tool
```
```
sudo cat /var/log/syslog | grep -e brc -e firmware -e wpa -e eth1 -e etork | tail -n55
```
do not restart if this works we will need to make it permanent if not I think we will be close and have to do some fine tuning.
Thanks

---

### Post by merin_83 on 2012-05-25
yes :) i too sense that ...


```
merin@merin-M15x:~$ sudo rmmod -f wl
[sudo] password for merin: 
ERROR: Removing 'wl': No such file or directory
merin@merin-M15x:~$ sudo modprobe brcmsmac
merin@merin-M15x:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             unavailable
  Default:           no
  HW Address:        C0:CB:38:52:22:C4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        02:33:60:33:69:01

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.185
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        84:2B:2B:82:42:C0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


merin@merin-M15x:~$ 

```



```
merin@merin-M15x:~$ sudo cat /var/log/syslog | grep -e brc -e firmware -e wpa -e eth1 -e etork | tail -n55
May 25 18:00:32 merin-M15x NetworkManager[654]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 18:00:32 merin-M15x NetworkManager[654]: <info> (eth1): deactivating device (reason 'none') [0]
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) starting connection 'S1003'
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1/wireless): access point 'S1003' has security, but secrets are required.
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 18:00:35 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed for access point (S1003)
May 25 18:00:35 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed.
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 18:00:35 merin-M15x NetworkManager[654]: <info> (eth1): deactivating device (reason 'none') [0]
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) starting connection 'getyourown-5'
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1/wireless): access point 'getyourown-5' has security, but secrets are required.
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 18:04:23 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed for access point (getyourown-5)
May 25 18:04:23 merin-M15x NetworkManager[654]: <warn> Activation (eth1) failed.
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 18:04:23 merin-M15x NetworkManager[654]: <info> (eth1): deactivating device (reason 'none') [0]
May 25 18:35:13 merin-M15x NetworkManager[616]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 25 19:26:06 merin-M15x NetworkManager[681]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 25 19:28:11 merin-M15x kernel: [  144.682900] brcmsmac 0000:07:00.0: bus 7 slot 0 func 0 irq 7
May 25 19:28:11 merin-M15x kernel: [  144.682925] brcmsmac 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 25 19:28:11 merin-M15x kernel: [  144.682935] brcmsmac 0000:07:00.0: setting latency timer to 64
May 25 19:28:11 merin-M15x NetworkManager[681]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 5)
May 25 19:28:11 merin-M15x kernel: [  144.798035] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
May 25 19:28:11 merin-M15x kernel: [  144.798045] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
May 25 19:28:11 merin-M15x kernel: [  144.798057] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
May 25 19:28:11 merin-M15x kernel: [  144.798064] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
May 25 19:28:11 merin-M15x kernel: [  144.798071] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
May 25 19:28:11 merin-M15x kernel: [  144.798077] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
May 25 19:28:11 merin-M15x kernel: [  144.798085] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
May 25 19:28:11 merin-M15x dbus[635]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
May 25 19:28:11 merin-M15x dbus[635]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
May 25 19:28:11 merin-M15x wpa_supplicant[2557]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
May 25 19:28:11 merin-M15x wpa_supplicant[2557]: Could not set interface 'wlan0' UP
May 25 19:28:11 merin-M15x wpa_supplicant[2557]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
May 25 19:28:11 merin-M15x wpa_supplicant[2557]: Failed to initialize driver interface
May 25 19:28:11 merin-M15x NetworkManager[681]: <info> wpa_supplicant started
May 25 19:28:11 merin-M15x NetworkManager[681]: <error> [1337988491.402540] [nm-supplicant-interface.c:804] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
merin@merin-M15x:~$ 
```


thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, please do:
```
echo "blacklist dell_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Remove [COLOR="Red"]blacklist brcmsmac[/COLOR]
save,close gedit and reboot.

Also reboot your router and modem.
Thanks

---

### Post by merin_83 on 2012-05-25
hi, nope now again the wireless is not showing in the settings-network manager, only wired connections are showing

thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot.
Thanks

---

### Post by merin_83 on 2012-05-25
hi, still the same, dont see wireless in network settings

thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, please post the output of:
```
lsmod
```
Thanks

---

### Post by merin_83 on 2012-05-25
hi, here is the o/p,,


```
merin@merin-M15x:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
clip                   17925  1 
vesafb                 13516  1 
atm                    44894  3 clip
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
fglrx                2909855  103 
psmouse                72919  0 
serio_raw              13027  0 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 41906  0 
snd_seq_midi           13132  0 
i7core_edac            23382  0 
hid                    77367  1 usbhid
snd_rawmidi            25424  1 snd_seq_midi
edac_core              46858  1 i7core_edac
uvcvideo               67203  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               86588  1 uvcvideo
rndis_host             13560  0 
cdc_ether              13312  1 rndis_host
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
usbnet                 25214  2 rndis_host,cdc_ether
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
r592                   17808  0 
memstick               15857  1 r592
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
bnep                   17830  2 
parport_pc             32114  0 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
binfmt_misc            17292  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
ite_cir                24743  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ite_cir
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  4 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140005  0 
merin@merin-M15x:~$ 
```


thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, please do:
```
sudo modprobe brcmsmac
```
then post the output of:
```
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e brc -e firmware -e wpa -e wlan -e eth1 -e etork | tail -n55
```
Thanks

---

### Post by merin_83 on 2012-05-25
Hi, here is the o/p,,



```
merin@merin-M15x:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        C0:CB:38:52:22:C4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Shona:           Infra, 08:86:3B:5F:CE:B0, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    youbelongtome:   Infra, 00:25:9C:C3:23:B1, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Sami:            Infra, 00:23:69:B8:93:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    2WIRE072:        Infra, 64:0F:29:14:AD:11, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    2WIRE388:        Infra, 98:2C:BE:A1:56:89, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WEP
    erza-HP-Wireless:Infra, E0:91:F5:D6:88:A4, Freq 2422 MHz, Rate 54 Mb/s, Strength 64
    getyourown:      Infra, 20:4E:7F:C4:B0:68, Freq 2442 MHz, Rate 54 Mb/s, Strength 67 WPA2
    S1003:           Infra, 00:22:75:63:7B:C0, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    getyourown-5:    Infra, 20:4E:7F:C4:B0:69, Freq 5180 MHz, Rate 54 Mb/s, Strength 65 WPA2


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        02:33:60:33:69:01

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.185
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        84:2B:2B:82:42:C0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


merin@merin-M15x:~$ 

```


i guess some got truncated ...

```

                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503005B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100008863B5FCEB01021001242656C6B696E20436F72706F726174696F6E1023000A46394B3130303220763210240007322E30302E30361042000E31323131333447433230313732381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 0706555320010B10
          Cell 02 - Address: E0:91:F5:D6:88:A4
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"erza-HP-Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4dceb1703
                    Extra: Last beacon: 2484ms ago
                    IE: Unknown: 001065727A612D48502D576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700102D791BB28D64D98A53C7C7B8AB2E6C3D1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403001300000000000000000000000000000000000000
          Cell 03 - Address: 20:4E:7F:C4:B0:68
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"getyourown"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000080ffb578
                    Extra: Last beacon: 2196ms ago
                    IE: Unknown: 000A676574796F75726F776E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16070F1600000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B000103104700106A2DC0BFA93CA6243DE1902D86F310CB1021000D4E4554474541522C20496E632E1023000844474E44333730301024000844474E443337303010420004333730301054000800060050F20400011011000844474E4433373030100800020084
                    IE: Unknown: DD090010180206F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34070F1600000000000000000000000000000000000000
          Cell 04 - Address: 98:2C:BE:A1:56:89
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE388"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000247b7a72181
                    Extra: Last beacon: 11240ms ago
                    IE: Unknown: 00083257495245333838
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 05 - Address: 00:23:69:B8:93:CF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Sami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000147abe3183
                    Extra: Last beacon: 10912ms ago
                    IE: Unknown: 000453616D69
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F4000000
          Cell 06 - Address: 00:25:9C:C3:23:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"youbelongtome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000198736c7e7c
                    Extra: Last beacon: 10824ms ago
                    IE: Unknown: 000D796F7562656C6F6E67746F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000
          Cell 07 - Address: 20:4E:7F:C4:B0:69
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"getyourown-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008016a03d
                    Extra: Last beacon: 10748ms ago
                    IE: Unknown: 000C676574796F75726F776E2D35
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A7E081BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16240D0000000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E081BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34240D0000000000000000000000000000000000000000
          Cell 08 - Address: 00:24:01:45:8C:76
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Waves"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014349ea180
                    Extra: Last beacon: 11928ms ago
                    IE: Unknown: 00055761766573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051900000000000000000000000000000000000000
                    IE: Unknown: 3D1602051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 09 - Address: C4:3D:C7:A6:B3:54
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"TahaAshraf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000023763d80
                    Extra: Last beacon: 11688ms ago
                    IE: Unknown: 000A54616861417368726166
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030104
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404051900000000000000000000000000000000000000
                    IE: Unknown: 3D1604051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000C43DC7A6B354103C000103
          Cell 10 - Address: 00:1C:10:55:E2:F5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Jaibolo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000013e093184
                    Extra: Last beacon: 11452ms ago
                    IE: Unknown: 00074A6169626F6C6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F5000000
          Cell 11 - Address: 00:22:75:13:97:23
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Saturn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000595665c7154
                    Extra: Last beacon: 11532ms ago
                    IE: Unknown: 000653617475726E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 12 - Address: 00:15:E9:14:E4:6A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"ShuvraGhosh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000096c8c817e
                    Extra: Last beacon: 11528ms ago
                    IE: Unknown: 000B53687576726147686F7368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 13 - Address: 00:18:E7:D3:68:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"ArunDevalapalli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004161fd180
                    Extra: Last beacon: 11508ms ago
                    IE: Unknown: 000F4172756E446576616C6170616C6C69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051900000000000000000000000000000000000000
                    IE: Unknown: 3D1606051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD270050F204104A000110104400010110470010565AA94967C14C0EAA8FF349E6F59311103C000101
          Cell 14 - Address: 00:22:75:63:7B:C0
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"S1003"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003fb900252b7
                    Extra: Last beacon: 2028ms ago
                    IE: Unknown: 00055331303033
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340A000000000000000000000000000000000000000000
                    IE: Unknown: DDA90050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F002275637BC01021001442656C6B696E20496E7465726E6174696F6E616C102300114E20576972656C65737320526F757465721024000C463544383233362D342076331042000E32303931343832333630313035361054000800060050F20400011011001842656C6B696E204E20576972656C65737320526F75746572100800020084103C000101
          Cell 15 - Address: 08:86:3B:99:F9:92
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"belkin.992"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014318e413a
                    Extra: Last beacon: 11072ms ago
                    IE: Unknown: 000A62656C6B696E2E393932
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545700010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860108863B99F992103C000101
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1609000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502000B127A
                    IE: Unknown: DD07000C4307000000
          Cell 16 - Address: 20:4E:7F:9B:3B:A8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"9B3BA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f401ff5193
                    Extra: Last beacon: 10868ms ago
                    IE: Unknown: 0006394233424139
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD270050F204104A0001101044000102104700102EB960398DD43484537136DB920B7E76103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000

eth0      Interface doesn't support scanning.

merin@merin-M15x:~$ 

```

```
rin@merin-M15x:~$ sudo cat /var/log/syslog | grep -e brc -e firmware -e wpa -e wlan -e eth1 -e etork | tail -n55
May 25 20:27:19 merin-M15x kernel: [  537.492152] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 25 20:27:19 merin-M15x dbus[605]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
May 25 20:27:19 merin-M15x dbus[605]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
May 25 20:27:19 merin-M15x NetworkManager[645]: <info> wpa_supplicant started
May 25 20:27:19 merin-M15x NetworkManager[645]: <info> (wlan0): supplicant interface state: starting -> ready
May 25 20:27:19 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 25 20:27:19 merin-M15x NetworkManager[645]: <info> (wlan0): supplicant interface state: ready -> inactive
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) starting connection 'getyourown'
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0/wireless): access point 'getyourown' has security, but secrets are required.
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 20:27:23 merin-M15x NetworkManager[645]: <warn> Activation (wlan0) failed for access point (getyourown)
May 25 20:27:23 merin-M15x NetworkManager[645]: <warn> Activation (wlan0) failed.
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 20:27:23 merin-M15x NetworkManager[645]: <info> (wlan0): deactivating device (reason 'none') [0]
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) starting connection 'S1003'
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0/wireless): access point 'S1003' has security, but secrets are required.
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 20:27:26 merin-M15x NetworkManager[645]: <warn> Activation (wlan0) failed for access point (S1003)
May 25 20:27:26 merin-M15x NetworkManager[645]: <warn> Activation (wlan0) failed.
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 20:27:26 merin-M15x NetworkManager[645]: <info> (wlan0): deactivating device (reason 'none') [0]
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) starting connection 'getyourown-5'
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0/wireless): access point 'getyourown-5' has security, but secrets are required.
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 25 20:27:29 merin-M15x NetworkManager[645]: <warn> Activation (wlan0) failed for access point (getyourown-5)
May 25 20:27:29 merin-M15x NetworkManager[645]: <warn> Activation (wlan0) failed.
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 25 20:27:29 merin-M15x NetworkManager[645]: <info> (wlan0): deactivating device (reason 'none') [0]
merin@merin-M15x:~$
```


thanks,
merin

---

### Post by wildmanne39 on 2012-05-25
Hi, there is an error message and I think we can get rid of it by using one of the other drivers for your device but please go into your router settings first and see if turning off encrpytion for a minute will allow you to connect.
Thanks

---

### Post by merin_83 on 2012-05-29
Hi, Sorry for the late reply, it was long week end :D ... I tried that but dint work, what i noticed was that there is no wireless this time in network manager.

pls see this...

```
merin@merin-M15x:~$ rfkill list all
merin@merin-M15x:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        84:2B:2B:82:42:C0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


merin@merin-M15x:~$ lsmod | grep b43
merin@merin-M15x:~$ 
```


thanks,
merin

---

### Post by wildmanne39 on 2012-05-30
Hi, are you sharing an internet connection on this computer? there is a driver loaded for sharing a connection.
Thanks

---

### Post by merin_83 on 2012-05-30
hi, no i dont share a net connection from my laptop.. mm infact i dont know how to do that, i use tethering from my mobile as i dont have wifi in ubuntu.. thats all realted to internet i do in ubuntu.

thanks,
merin

---

### Post by wildmanne39 on 2012-05-30
Hi, have you had your phone tethered to your computer this whole time? you can not have the wireless working from the internal card if you have another internet connection going at the same time.
Thanks

---

### Post by merin_83 on 2012-05-30
oops not all the time, but couple of last times.... i will try with out the tether and let you know...

---

### Post by merin_83 on 2012-05-30
Hi, disconnected the tethering and disabled the wifi security, then tried the below commands, please let me know if you need any other logs.

```
merin@merin-M15x:~$ sudo modprobe brcmsmac 
[sudo] password for merin: 
merin@merin-M15x:~$ nm-tool 

NetworkManager Tool 

State: disconnected 

- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            brcmsmac 
  State:             disconnected 
  Default:           no 
  HW Address:        C0:CB:38:52:22:C4 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points 
    Shona:           Infra, 08:86:3B:5F:CE:B0, Freq 2417 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2 
    Happyhome:       Infra, A0:21:B7:5E:FD:86, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2 
    youbelongtome:   Infra, 00:25:9C:C3:23:B1, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 
    Kuni:            Infra, C0:3F:0E:B1:37:9E, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 
    Sami:            Infra, 00:23:69:B8:93:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2 
    NETGEAR51:       Infra, 20:4E:7F:18:DD:3A, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2 
    Jaibolo:         Infra, 00:1C:10:55:E2:F5, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2 
    9B3BA9:          Infra, 20:4E:7F:9B:3B:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2 
    erza-HP-Wireless:Infra, E0:91:F5:D6:88:A4, Freq 2422 MHz, Rate 54 Mb/s, Strength 57 
    SpotOn:          Infra, 00:03:52:9E:DF:30, Freq 2457 MHz, Rate 54 Mb/s, Strength 17 
    SpotOn:          Infra, 00:03:52:9C:01:20, Freq 2452 MHz, Rate 54 Mb/s, Strength 15 
    getyourown:      Infra, 20:4E:7F:C4:B0:68, Freq 2442 MHz, Rate 54 Mb/s, Strength 49 WPA2 
    S1003:           Infra, 00:22:75:63:7B:C0, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 
    getyourown-5:    Infra, 20:4E:7F:C4:B0:69, Freq 5180 MHz, Rate 54 Mb/s, Strength 67 WPA2 
    Campbell:        Infra, 00:21:29:BA:B8:62, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA 
    RAMYA-PC_Network:Infra, A0:21:B7:6C:8A:1F, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA 
    ArunDevalapalli: Infra, 00:18:E7:D3:68:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2 
    belkin.992:      Infra, 08:86:3B:99:F9:92, Freq 2452 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2 
    2WIRE388:        Infra, 98:2C:BE:A1:56:89, Freq 2447 MHz, Rate 54 Mb/s, Strength 29 WEP 
    ShuvraGhosh:     Infra, 00:15:E9:14:E4:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WEP 
    CHERYL:          Infra, 00:13:10:01:0E:8F, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WEP 


- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            e1000e 
  State:             unavailable 
  Default:           no 
  HW Address:        84:2B:2B:82:42:C0 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


merin@merin-M15x:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 08:86:3B:5F:CE:B0 
                    Channel:2 
                    Frequency:2.417 GHz (Channel 2) 
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on 
                    ESSID:"Shona" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000020595db1e9 
                    Extra: Last beacon: 2352ms ago 
                    IE: Unknown: 000553686F6E61 
                    IE: Unknown: 010882848B961224486C 
                    IE: Unknown: 030102 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 32040C183060 
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: 3D1602050000000000000000000000000000000000000000 
                    IE: Unknown: 3E0100 
                    IE: WPA Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: 0B0500004C127A 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100008863B5FCEB01021001242656C6B696E20436F72706F726174696F6E1023000A46394B3130303220763210240007322E30302E30361042000E31323131333447433230313732381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084 
                    IE: Unknown: 0706555320010B10 
          Cell 02 - Address: E0:91:F5:D6:88:A4 
                    Channel:3 
                    Frequency:2.422 GHz (Channel 3) 
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off 
                    ESSID:"erza-HP-Wireless" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000000a1169318e 
                    Extra: Last beacon: 2432ms ago 
                    IE: Unknown: 001065727A612D48502D576972656C657373 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030103 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1603080000000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700102D791BB28D64D98A53C7C7B8AB2E6C3D1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084 
                    IE: Unknown: DD090010180202F0050000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3403080000000000000000000000000000000000000000 
          Cell 03 - Address: 20:4E:7F:C4:B0:68 
                    Channel:7 
                    Frequency:2.442 GHz (Channel 7) 
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on 
                    ESSID:"getyourown" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000012a291a197 
                    Extra: Last beacon: 2152ms ago 
                    IE: Unknown: 000A676574796F75726F776E 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030107 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000 
                    IE: Unknown: 3D1607071700000000000000000000000000000000000000 
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B000103104700106A2DC0BFA93CA6243DE1902D86F310CB1021000D4E4554474541522C20496E632E1023000844474E44333730301024000844474E443337303010420004333730301054000800060050F20400011011000844474E4433373030100800020084 
                    IE: Unknown: DD090010180205F0050000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3407071700000000000000000000000000000000000000 
          Cell 04 - Address: 00:03:52:9C:01:20 
                    Channel:9 
                    Frequency:2.452 GHz (Channel 9) 
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off 
                    ESSID:"SpotOn" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000000a7ad26e 
                    Extra: Last beacon: 2144ms ago 
                    IE: Unknown: 000653706F744F6E 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 030109 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600 
          Cell 05 - Address: 00:22:75:63:7B:C0 
                    Channel:10 
                    Frequency:2.457 GHz (Channel 10) 
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on 
                    ESSID:"S1003" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000045e284a80df 
                    Extra: Last beacon: 2084ms ago 
                    IE: Unknown: 00055331303033 
                    IE: Unknown: 010882848B961224486C 
                    IE: Unknown: 03010A 
                    IE: Unknown: 32040C183060 
                    IE: Unknown: 33082001020304050607 
                    IE: Unknown: 33082105060708090A0B 
                    IE: Unknown: DD270050F204104A000110104400010210470010775B6680BFDE11D38D2F002275637BC0103C000101 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2D1AEE1113FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: 3D160A000000000000000000000000000000000000000000 
                    IE: Unknown: 7F0101 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: 0B0500002B127A 
                    IE: Unknown: DD1E00904C33EE1113FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: DD1A00904C340A000000000000000000000000000000000000000000 
                    IE: Unknown: DD07000C4307000000 
          Cell 06 - Address: 00:03:52:9E:DF:30 
                    Channel:10 
                    Frequency:2.457 GHz (Channel 10) 
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off 
                    ESSID:"SpotOn" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000006d46f817181 
                    Extra: Last beacon: 2088ms ago 
                    IE: Unknown: 000653706F744F6E 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 03010A 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600 
          Cell 07 - Address: 00:23:69:B8:93:CF 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on 
                    ESSID:"Sami" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000000931089185 
                    Extra: Last beacon: 2052ms ago 
                    IE: Unknown: 000453616D69 
                    IE: Unknown: 010882848B9624B0486C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32048C129860 
                    IE: Unknown: DD0E0050F204104A0001101044000102 
                    IE: Unknown: DD090010180200F4000000 
          Cell 08 - Address: 00:13:10:01:0E:8F 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on 
                    ESSID:"CHERYL" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000002ab8ca8e183 
                    Extra: Last beacon: 2296ms ago 
                    IE: Unknown: 000643484552594C 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD06001018010201 
          Cell 09 - Address: 00:26:B0:FE:D3:EF 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on 
                    ESSID:"MAMC" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000057f91cb490 
                    Extra: Last beacon: 2620ms ago 
                    IE: Unknown: 00044D414D43 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 030101 
                    IE: Unknown: 050401030006 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD07000393016C0320 
                    IE: Unknown: DD070017F203020180 
                    IE: Unknown: DD0E0017F207000101060026B0FED3F0 
          Cell 10 - Address: 00:03:52:9E:DF:31 
                    Channel:10 
                    Frequency:2.457 GHz (Channel 10) 
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on 
                    ESSID:"" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000006d46f81758e 
                    Extra: Last beacon: 2084ms ago 
                    IE: Unknown: 0000 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 03010A 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600 

eth0      Interface doesn't support scanning. 

merin@merin-M15x:~$ sudo cat /var/log/syslog | grep -e brc -e firmware -e wlan -e eth1 -e etork | tail -n55 
May 30 18:07:03 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0] 
May 30 18:07:03 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 30 18:07:03 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7] 
May 30 18:07:03 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed for access point (getyourown) 
May 30 18:07:03 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed. 
May 30 18:07:03 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0] 
May 30 18:07:03 merin-M15x NetworkManager[600]: <info> (wlan0): deactivating device (reason 'none') [0] 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) starting connection 'getyourown' 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0] 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0] 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0/wireless): access point 'getyourown' has security, but secrets are required. 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0] 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7] 
May 30 18:09:26 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed for access point (getyourown) 
May 30 18:09:26 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed. 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0] 
May 30 18:09:26 merin-M15x NetworkManager[600]: <info> (wlan0): deactivating device (reason 'none') [0] 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) starting connection 'S1003' 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0] 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0] 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0/wireless): access point 'S1003' has security, but secrets are required. 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0] 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7] 
May 30 18:10:22 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed for access point (S1003) 
May 30 18:10:22 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed. 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0] 
May 30 18:10:22 merin-M15x NetworkManager[600]: <info> (wlan0): deactivating device (reason 'none') [0] 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) starting connection 'getyourown-5' 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0] 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0] 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0/wireless): access point 'getyourown-5' has security, but secrets are required. 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0] 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7] 
May 30 18:10:25 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed for access point (getyourown-5) 
May 30 18:10:25 merin-M15x NetworkManager[600]: <warn> Activation (wlan0) failed. 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0] 
May 30 18:10:25 merin-M15x NetworkManager[600]: <info> (wlan0): deactivating device (reason 'none') [0] 
merin@merin-M15x:~$ 
```

Note:, in the above logs, "getyourown" is the network which has security disabled,,,,,, and NOT "getyourown-5",, this is different.
thanks,
merin

---

### Post by wildmanne39 on 2012-05-30
Hi, if you are trying to connect to getyourown-5 change the name so you do not have this - in it.

Go into your router settings and change the channel to 11 and see if that help because you have many other networks close to you on the same channel.

Both have security enabled.
Thanks

---

### Post by merin_83 on 2012-05-30
Hi, I was trying to connect to getyourown (2.4GHz) -security disabled. The getyourown-5 is a 5GHz network, it has security enabled.(but dono how in logs its trying to connect to getyourown-5 also.

Thanks,
merin

---

### Post by wildmanne39 on 2012-05-30
Hi, the network you are wanting to connect to has a weak signal get closer and see if you can connect.

---

### Post by merin_83 on 2012-05-30
hi, i tried very near to router, and with security disabled, but dono why the log says "has security"..


```
merin@merin-M15x:~$ sudo cat /var/log/syslog | grep -e brc -e firmware -e wlan -e eth1 -e etork | tail -n55
May 30 20:56:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 30 20:56:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 30 20:56:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 30 20:56:23 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed for access point (S1003)
May 30 20:56:23 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed.
May 30 20:56:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 30 20:56:23 merin-M15x NetworkManager[629]: <info> (wlan0): deactivating device (reason 'none') [0]
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) starting connection 'youbelongtome'
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0/wireless): access point 'youbelongtome' has security, but secrets are required.
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 30 20:56:50 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed for access point (youbelongtome)
May 30 20:56:50 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed.
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 30 20:56:50 merin-M15x NetworkManager[629]: <info> (wlan0): deactivating device (reason 'none') [0]
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) starting connection 'getyourown'
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0/wireless): access point 'getyourown' has security, but secrets are required.
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 30 20:58:23 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed for access point (getyourown)
May 30 20:58:23 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed.
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 30 20:58:23 merin-M15x NetworkManager[629]: <info> (wlan0): deactivating device (reason 'none') [0]
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) starting connection 'getyourown-5'
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0/wireless): access point 'getyourown-5' has security, but secrets are required.
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 30 20:59:00 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed for access point (getyourown-5)
May 30 20:59:00 merin-M15x NetworkManager[629]: <warn> Activation (wlan0) failed.
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 30 20:59:00 merin-M15x NetworkManager[629]: <info> (wlan0): deactivating device (reason 'none') [0]
merin@merin-M15x:~$ 

```

thanks,
merin

---

### Post by wildmanne39 on 2012-05-31
Hi, let's do this install wicd it is another type of network manager then get rid of network manager like this:
```
sudo apt-get purge network-manager network-manager-gnome
```
you have to install wicd first.
Reboot

With wicd you will need to open dash to set it up it does not put it in the top panel.
Thanks

---

### Post by merin_83 on 2012-06-01
> **wildmanne39 said:**
> Hi, let's do this install wicd it is another network manager then get rid if network manager like this:
```
sudo apt-get purge network-manager network-manager-gnome
```
you have to install wicd first.
Reboot

With wicd you will need to open dash to set it up it does not put it in the top panel.
Thanks

I executed the command, everything went fine, but after reboot, its i got a window saying system software internal error, and when i tried to open the network manager, it said, its not supported in the current version of software...


thanks,
merin

---

### Post by wildmanne39 on 2012-06-02
I did you go to dash and click on wicd then set the connection for wireless up.
Thanks

---

### Post by merin_83 on 2012-06-03
> **wildmanne39 said:**
> I did you go to dash and click on wicd then set the connection for wireless up.
Thanks

Hi, I searched in the dash, but dint find it. I searched in the ubuntu software center, i can see wicd 3(types) to install, but the button is disabled, now i can't connect to net thru direct lan cable or thru tether. Dono how it install it properly.

:confused:

thank you, for being patient with me :) ... 

thanks,
merin

---

### Post by wildmanne39 on 2012-06-03
Hi, you read post #48 carefully?

You did not remove network manager before you install wicd correct?
Thanks

---

### Post by merin_83 on 2012-06-03
> **wildmanne39 said:**
> Hi, you read post #48 carefully?

You did not remove network manager before you install wicd correct?
Thanks

i suck :( .. now i see that !!


thanks,
merin

---

### Post by wildmanne39 on 2012-06-03
Hi, see if this command turns on your wired connection if it does install all wicd packages.
```
sudo dhclient eth0
```
Thanks

---

### Post by merin_83 on 2012-06-03
> **wildmanne39 said:**
> Hi, see if this command turns on your wired connection if it does install all wicd packages.
```
sudo dhclient eth0
```
Thanks

Hi, This cmd dint work, i tried in the ubuntu site for wici and found 4 packages for manula download thru win OS and install it,,, wicd dameon,clinet meta,, and one more.. but after trying to install, at last found dameon had dependency on python-wicd package.. now am searching that ....


thanks,
merin

---

### Post by wildmanne39 on 2012-06-03
Hi, I found a link to help reinstall network manager so you can then install wicd.
[http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection)
Thanks

---

### Post by merin_83 on 2012-06-04
Hi, thank you for the link, i downloaded all the packages, but when i click on the packages, the package manager has some issue "Cannt install or remove until package catalog is repaired",,, after this it tries to got to internet, but we don't have it.. so i tried to install it manual ,, and it has many dependencies...



```
merin@merin-M15x:/media/01CB98052419A530_/copy/nwm$ ll
total 1644
drwx------ 1 merin merin   4096 Jun  3 21:50 ./
drwx------ 1 merin merin  32768 Jun  4 19:06 ../
-rw------- 2 merin merin 349040 Jun  3 21:47 network-manager_0.8-0ubuntu3.2_amd64.deb
-rw------- 2 merin merin 317416 Jun  3 21:47 network-manager_0.8-0ubuntu3.2_i386.deb
-rw------- 2 merin merin 496728 Jun  3 21:48 network-manager-gnome_0.8-0ubuntu3_amd64.deb
-rw------- 2 merin merin 473000 Jun  3 21:50 network-manager-gnome_0.8-0ubuntu3_i386.deb
merin@merin-M15x:/media/01CB98052419A530_/copy/nwm$ sudo dpkg -i network-manager_0.8-0ubuntu3.2_i386.deb
Selecting previously unselected package network-manager.
dpkg: regarding network-manager_0.8-0ubuntu3.2_i386.deb containing network-manager:
 libpurple0 conflicts with network-manager (<< 0.9.0)
  network-manager (version 0.8-0ubuntu3.2) is to be installed.
dpkg: error processing network-manager_0.8-0ubuntu3.2_i386.deb (--install):
 conflicting packages - not installing network-manager
Errors were encountered while processing:
 network-manager_0.8-0ubuntu3.2_i386.deb
merin@merin-M15x:/media/01CB98052419A530_/copy/nwm$ sudo dpkg -i network-manager-gnome_0.8-0ubuntu3_i386.deb
Selecting previously unselected package network-manager-gnome.
(Reading database ... 184257 files and directories currently installed.)
Unpacking network-manager-gnome (from network-manager-gnome_0.8-0ubuntu3_i386.deb) ...
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on libglade2-0 (>= 1:2.6.1); however:
  Package libglade2-0 is not installed.
 network-manager-gnome depends on libgnome-bluetooth7 (>= 2.27.8); however:
  Package libgnome-bluetooth7 is not installed.
 network-manager-gnome depends on libnm-glib2 (>= 0.8~rc2~git.20091229t135236.302e62d); however:
  Package libnm-glib2 is not installed.
 network-manager-gnome depends on libnm-util1 (>= 0.8~a~git.20090930t162132.866d48b); however:
  Package libnm-util1 is not installed.
 network-manager-gnome depends on libnotify1 (>= 0.4.5); however:
  Package libnotify1 is not installed.
 network-manager-gnome depends on libnotify1-gtk2.10; however:
  Package libnotify1-gtk2.10 is not installed.
 network-manager-gnome depends on network-manager (>= 0.8~rc2); however:
  Package network-manager is not installed.
 libnm-gtk0 (0.9.4.1-0ubuntu2) breaks network-manager-gnome (<< 0.9.1.90-0ubuntu2) and is installed.
  Version of network-manager-gnome to be configured is 0.8-0ubuntu3.
 gnome-bluetooth (3.2.2-0ubuntu5) breaks network-manager-gnome (<< 0.9.0-3) and is installed.
  Version of network-manager-gnome to be configured is 0.8-0ubuntu3.
 libnm-gtk-common (0.9.4.1-0ubuntu2) breaks network-manager-gnome (<< 0.9.1.90-0ubuntu2) and is installed.
  Version of network-manager-gnome to be configured is 0.8-0ubuntu3.
dpkg: error processing network-manager-gnome (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gconf2 ...
Errors were encountered while processing:
 network-manager-gnome
merin@merin-M15x:/media/01CB98052419A530_/copy/nwm$

```



so i decided to continue install wicd manually, but after 4 -5 dependencies, like ;libglade, libgtk,, again there are like 10+ ... am not sure what to do :( .. is there a way to do complete install :confused:


thanks,
merin

---

### Post by wildmanne39 on 2012-06-04
Hi, if it were me I would reformat the drive and install a fresh copy of 12.04 and go from there.
Thanks

---

### Post by merin_83 on 2012-06-04
> **wildmanne39 said:**
> Hi, if it were me I would reformat the drive and install a fresh copy of 12.04 and go from there.
Thanks

yup, am too getting that feeling... am goin to install 64-bit PC (AMD64) desktop CD .....i guess previously i had 32 bit.... omg as now i dont have a empty cd, only DVD.... can i burn image to DVD ?

thanks,
merin

---

### Post by wildmanne39 on 2012-06-04
Hi, yes you can but if you have a flash drive just burn it to it and save your dvd.
Thanks

---

### Post by merin_83 on 2012-06-04
> **wildmanne39 said:**
> Hi, yes you can but if you have a flash drive just burn it to it and save your dvd.
Thanks

earlier i tried with USB, but dint work,,, i tried as per the unbuntu website only, with that flash usb tool,,,,

thanks,
merin

---

### Post by wildmanne39 on 2012-06-04
Hi, okay that is a topic for another thread in another section of the forum good luck with the reinstall.

---

### Post by merin_83 on 2012-06-04
> **wildmanne39 said:**
> Hi, okay that is a topic for another thread in another section of the forum good luck with the reinstall.

yes you are correct :), when i went for forumns, there was a whole lot of threads for that issue :D ,, will concentrate on one

will update you of the progress..


thanks,
merin

---

### Post by merin_83 on 2012-06-04
Hi, I completed installation from DVD, every thing works fine :D, i guess last time the upgrade from 11.10 t0 12.04 caused the issue. :)

thanks a lot for your time !!

thanks,
merin

---

### Post by wildmanne39 on 2012-06-04
Hi, the is great and it is likely it is always better to do a clean install, please use thread tools at the top of the page and mark the thread solved.
Enjoy

---

### Post by G M on 2012-06-05
Hi,

I am writing just to say that I followed closely this thread in order to (try to) solve my very similar issue but I am still stuck in the middle of nowhere.

By the way: could somebody drop by one of my threads in order to shed some light to a poor Ubuntu-beginner pilgrim?
[http://ubuntuforums.org/showthread.php?t=1993245](http://ubuntuforums.org/showthread.php?t=1993245)
[http://ubuntuforums.org/showthread.php?t=1996915](http://ubuntuforums.org/showthread.php?t=1996915)

Thanks in advance,

Giulio

---

