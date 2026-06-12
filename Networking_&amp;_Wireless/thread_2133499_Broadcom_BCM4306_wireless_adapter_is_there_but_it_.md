---
title: "Broadcom BCM4306 wireless adapter is there but it doesn't work"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by dave247 on 2013-04-08
I have a weird issue and I will provide a back story first: Basically I have this older laptop that I once used to install Linux Mint on with Snort and I was using it as an IDS for testing my home network. This was the last time the wireless adapter worked. I was using the wired LAN port for sniffing raw network packets (it had an ip of 1.1.1.1) and then I used my wireless adapter to connect to the local network like normal. This worked fine until later I eventually re-formatted and re-installed Linux and realized my wifi card wasn't working like it used to. It used to work fine right after an install of Linux Mint, then it stopped. Before that, it had Windows XP on it and it worked in there as well. Anyway, I am assuming that I somehow messed up the wifi card when I was using Snort, even though it doesn't seem like that would be the case.

Later, I installed Ubuntu 10 version on it and it still didn't work. Then I tried installing XP on it again just to see if it was a Linux problem. Still didn't work. Now like a year and half later of not doing anything with it, I decided to install Ubuntu 12.04 on it and still the wireless does not work. I am assuming it simply died, but I am suspicious of that. I am thinking that I actually somehow changed something on the card itself (even though this seems like it shouldn't happen).

I ran lspci in the terminal and it actually lists the wireless device as: 02:02:0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

So I'm thinking, if it's really dead, shouldn't it not be listed? And I am wondering if it is possible to mess around with the card in the command line to somehow get it working again. 

Thanks

---

### Post by Hadaka on 2013-04-08
Hi Dave and welcome !
let's see if we can wake it from the dead.
Please COPY and paste...

```
lspci -nn | egrep '0200|0280"
```
```
rfkill list all
```
```
lsmod
```
post the results.
thanks.

---

### Post by dave247 on 2013-04-08
```
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)


```

rfkill list all doesn't output anything to the screen.

```
Module                  Size  Used by
joydev                 17394  0 
snd_intel8x0           33463  2 
snd_ac97_codec        106118  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  2 snd_intel8x0,snd_ac97_codec
pcmcia                 39855  0 
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
nouveau               855013  2 
b43                   351489  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
ttm                    76326  1 nouveau
mac80211              475488  1 b43
drm_kms_helper         47459  1 nouveau
snd_timer              28932  2 snd_pcm,snd_seq
drm                   240232  4 nouveau,ttm,drm_kms_helper
cfg80211              181041  2 b43,mac80211
i2c_algo_bit           13317  1 nouveau
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
bcma                   34573  1 b43
psmouse                91022  0 
mxm_wmi                12894  1 nouveau
yenta_socket           27465  0 
pcmcia_rsrc            18368  1 yenta_socket
serio_raw              13032  0 
snd                    62675  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38104  0 
k8temp                 12913  0 
bnep                   17791  2 
soundcore              14636  1 snd
shpchp                 32326  0 
ppdev                  12850  0 
bluetooth             189585  10 rfcomm,bnep
i2c_nforce2            12907  0 
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
video                  19070  1 nouveau
wmi                    18745  2 nouveau,mxm_wmi
parport_pc             32115  1 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 ppdev,parport_pc,lp
8139too                23312  0 
8139cp                 26760  0 
ssb                    50757  1 b43
pata_amd               13751  2 

```

---

### Post by Hadaka on 2013-04-08
Hi, it looks like you have the b43 driver loaded.
let's pull that rascal out,buff him up a little and
then put him back.please do.
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
```
sudo modprobe -r b43
```
then reinstall.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
then lets see if there are any moans and groans in..
```
dmesg | grep b43
```
thanks.

---

### Post by dave247 on 2013-04-08
Moans and groans:
```
[   26.104808] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   28.137200] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.137207] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   28.137210] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

I don't understand why it didn't work. I went to that site it told me to go to and the instructoins for Ubuntu is the same thing you told me to do (run the b43 installer).

This is the output of the installation of the b43 firmware installer:
```

user@R3000:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image linux-image-3.2.0-39-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer linux-image linux-image-3.2.0-39-generic-pae linux-image-generic-pae
0 upgraded, 5 newly installed, 0 to remove and 149 not upgraded.
Need to get 38.3 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-39-generic-pae i386 3.2.0-39.62 [38.2 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main b43-fwcutter i386 1:015-9 [18.9 kB]                                   
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]                    
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.39.47 [2,600 B]            
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image i386 3.2.0.39.47 [1,708 B]                        
Fetched 38.3 MB in 16s (2,278 kB/s)                                                                                           
Selecting previously unselected package linux-image-3.2.0-39-generic-pae.
(Reading database ... 141802 files and directories currently installed.)
Unpacking linux-image-3.2.0-39-generic-pae (from .../linux-image-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb) ...
Done.
Selecting previously unselected package b43-fwcutter.
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Selecting previously unselected package linux-image-generic-pae.
Unpacking linux-image-generic-pae (from .../linux-image-generic-pae_3.2.0.39.47_i386.deb) ...
Selecting previously unselected package linux-image.
Unpacking linux-image (from .../linux-image_3.2.0.39.47_i386.deb) ...
Processing triggers for man-db ...
Setting up linux-image-3.2.0-39-generic-pae (3.2.0-39.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
Your card is BCM4306/3 [14e4:4320] (rev 03), firwmare 5.10.56.27.3 will be used
--2013-04-08 15:08:09--  http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... 46.4.11.11
Connecting to mirror2.openwrt.org (mirror2.openwrt.org)|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1.5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'

100%[=====================================================================================>] 1,596,823    844K/s   in 1.8s    

2013-04-08 15:08:11 (844 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]

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
Setting up linux-image-generic-pae (3.2.0.39.47) ...
Setting up linux-image (3.2.0.39.47) ...


```

---

### Post by Hadaka on 2013-04-08
Hi Dave this is the problem..

b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
so let's try to fix it...please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```
and since you were snorfing around in the past...its possible
your wlan0 is sleeping...so please also do..
```
sudo ifconfig wlan0 up
```
report back please
thanks.

---

### Post by dave247 on 2013-04-08
Hey that got it working. I guess I must have jacked up my card's firmware way back when I was using this computer with Snort and I must have forgotten about it. Is that the only option? Otherwise wifi should have worked after installing Ubuntu.

Thanks a lot!

---

### Post by Hadaka on 2013-04-08
Glad you got it working 
have fun !

---

