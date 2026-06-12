---
title: "Broadcom BCM43224: Wireless not working Works in Windows"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by dosh on 2013-07-18
My notebook has Broadcom BCM43224 wireless. It looks like the driver Broadcom 802.11 Linux STA wireless driver is installed properly, however no possible connections are showing. Windows shows all possible connections and connects and works. Have Ubuntu 13.04 and it had been working before. Any help much appeciated.

---

### Post by praseodym on 2013-07-18
Hi,

deactivate the STA driver and install the missing firmware for the native driver:
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
```
Reboot.

---

### Post by dosh on 2013-07-18
The remove commands ... files not found
After rebooting same result.
I checked the Software & Updates / Addiional Drivers area Using Broadcom... was not checked so clicked it and Apply Changes it just reverted to Do not use the device.

Same result no connections

> **praseodym said:**
> Hi,

deactivate the STA driver and install the missing firmware for the native driver:
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
```
Reboot.

---

### Post by praseodym on 2013-07-18
Ok, lets check:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by dosh on 2013-07-18
~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:21e2]
	Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:0576] (rev 01)
	Subsystem: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:0576]
	Kernel driver in use: bcma-pci-bridge

~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  12 
bnep                   17669  2 
binfmt_misc            17260  1 
coretemp               13131  0 
kvm                   376505  0 
arc4                   12543  2 
joydev                 17097  0 
brcmsmac              521468  0 
uvcvideo               71279  0 
aesni_intel            18156  0 
videobuf2_vmalloc      12920  1 uvcvideo
aes_i586               16995  1 aesni_intel
videobuf2_memops       13042  1 videobuf2_vmalloc
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     36185  1 
cordic                 12518  1 brcmsmac
i915                  535544  3 
ablk_helper            13357  1 aesni_intel
brcmutil               14355  1 brcmsmac
cryptd                 15613  1 ablk_helper
snd_hda_codec_conexant    52256  1 
mac80211              526519  1 brcmsmac
drm_kms_helper         47545  1 i915
snd_hda_intel          38307  6 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
drm                   228489  4 i915,drm_kms_helper
cfg80211              436177  2 brcmsmac,mac80211
btusb                  17986  0 
thinkpad_acpi          69384  0 
nvram                  13986  1 thinkpad_acpi
lp                     13299  0 
i2c_algo_bit           13197  1 i915
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                81038  0 
bluetooth             202069  22 bnep,btusb,rfcomm
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
parport                40753  3 lp,ppdev,parport_pc
serio_raw              13031  0 
mei                    36197  0 
bcma                   39645  1 brcmsmac
lpc_ich                16925  0 
mac_hid                13037  0 
video                  18894  1 i915
soundcore              12600  1 snd
microcode              18286  0 
r8169                  61531  0 
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
ahci                   25507  2 
libahci                26108  1 ahci

iwconfig
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.

 rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

iwlist chan
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
lo        no frequency information.

eth0      no frequency information.

~$ sudo iwlist scan
[sudo] password for philip: 
wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


> **praseodym said:**
> Ok, lets check:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by kc1di on 2013-07-18
try doing the following in a terminal:

```
 sudo apt-get install linux-headers-generic
    sudo apt-get install --reinstall bcmwl-kernel-source
    sudo modprobe wl
```
then issue this command also:
```
rfkill unblock all
```

should work for you.

---

### Post by praseodym on 2013-07-18
Hi,

there is no need to install the STA driver (package bcmwl-kernel-source) again, the card is off:
```

sudo rfkill unblock all
```
should do the trick or looking for a button or switch

---

### Post by dosh on 2013-07-18
Thanks all. I rebooted into windows. Then came back and yes it all working again, I think I reset the Wireless switch. I also think some of the above commands helped.

---

