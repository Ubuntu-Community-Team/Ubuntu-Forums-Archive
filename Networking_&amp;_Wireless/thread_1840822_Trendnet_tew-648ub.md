---
title: "Trendnet tew-648ub"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by visarz on 2011-09-08
Can you help me finding drivers on this trendnet tew-648ub?

lsusb:

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0557:2008 ATEN International Co., Ltd UC-232A Serial Port [pl2303]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod:

```

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   21708  0 
fat                    61374  1 vfat
usb_storage            53538  0 
uas                    17996  0 
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
vboxdrv               286726  3 vboxpci,vboxnetadp,vboxnetflt
vmnet                  55734  13 
vmblock                18923  1 
vsock                  47659  0 
vmci                   64490  1 vsock
vmmon                  89333  0 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
arc4                   12529  2 
snd_hda_codec_realtek   336771  1 
snd_hda_codec_si3054    13084  1 
snd_hda_intel          33176  5 
snd_hda_codec         103804  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
iwl3945               152278  0 
snd_hwdep              13604  1 snd_hda_codec
fglrx                2739144  85 
snd_pcm                96391  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
8712u                 345700  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
iwlcore               167502  1 iwl3945
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
mac80211              294370  2 iwl3945,iwlcore
snd_timer              29602  2 snd_pcm,snd_seq
joydev                 17606  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
r8712u                307592  0 
lirc_ite8709           13336  0 
pl2303                 17991  1 
lirc_dev               19232  1 lirc_ite8709
cfg80211              178528  3 iwl3945,iwlcore,mac80211
snd                    67382  18 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19438  0 
lp                     17825  0 
psmouse                73535  0 
usbserial              42908  3 pl2303
parport                46458  3 parport_pc,ppdev,lp
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
ahci                   25951  2 
r8169                  48022  0 
libahci                26642  1 ahci

```

sudo lshw -C network:

```

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:67:46:25
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-11-generic firmware=15.32.2.9 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f0200000-f0200fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:8d:bb:b3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1
       logical name: wlan1
       serial: 00:14:d1:b6:38:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
```

When trying this:
[http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104](http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104)
I get:

```
install r8192s_usb modprobe --ignore-install r8192s_usb ; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id
ln: creating symbolic link `/lib/firmware/RTL8192SU/RTL8192SE': File exists
WARNING: All config files need .conf: /etc/modprobe.d/r, it will be ignored in a future release.
FATAL: Module r8192s_usb not found.
WARNING: All config files need .conf: /etc/modprobe.d/r, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/r, it will be ignored in a future release.
FATAL: Module r8192s_usb not found.
sh: /sys/bus/usb/drivers/rtl819xU/new_id: No such file or directory
FATAL: Error running install command for r8192s_usb
```

---

### Post by praseodym on 2011-09-08
Hi,

which Ubuntu-version do you use? There are 2 drivers loaded:

```
sudo modprobe -rf 8712u r8712u
sudo modprobe -v 8712u
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You may reboot.

---

### Post by visarz on 2011-09-08
> **praseodym said:**
> Hi,

which Ubuntu-version do you use? There are 2 drivers loaded:

```
sudo modprobe -rf 8712u r8712u
sudo modprobe -v 8712u
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You may reboot.

How do I revert the effects of this code? Now when I insert the Wireless USB adapter the computer freezes :S

Maybe the other driver is the built-in wireless of the laptop (the Intel® PRO/Wireless 3945ABG).

Also, I am on Ubuntu 11.04

---

### Post by visarz on 2011-09-08
> **visarz said:**
> How do I revert the effects of this code? Now when I insert the Wireless USB adapter the computer freezes :S

Maybe the other driver is the built-in wireless of the laptop (the Intel® PRO/Wireless 3945ABG).

Also, I am on Ubuntu 11.04

Also, now even the laptop's wireless doesn't work! After the reboot it works for a while, and then it disconnects from the wireless network

---

### Post by praseodym on 2011-09-08
The Intel driver is iwl3945. Which encryption mode do you use? The network-manager mostly has problems with mixed WPA/WPA2, better use WPA2-AES instead. Check:

```
iwconfig
lsmod
dmesg | grep 8712
sudo iwlist scan
```

---

