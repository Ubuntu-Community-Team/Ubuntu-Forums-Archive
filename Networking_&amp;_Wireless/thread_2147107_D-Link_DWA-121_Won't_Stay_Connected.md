---
title: "D-Link DWA-121 Won't Stay Connected"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by CharleyGnarlyP290 on 2013-05-20
I am running ubuntu 12.04 on a desk top computer and installed a D-Link DWA-121 USB wireless adapter. It has been working fine, but a few days ago it quit. 
When I open wireless settings I can see my wireless access point and the symbol that indicates wireless connectivity in the upper right part of the screen is there but empty of any hashmarks showing I am connected.
What do I need to do. Links or advice (for the new user types like myself) would be greatly appreciated.

---

### Post by varunendra on 2013-05-20
Please open a terminal (Ctrl + Alt + T), run the following commands in it and post back their output here :
```
uname -mr
lsusb
lsmod
iwconfig
rfkill list all
```

While posting the outputs, please use 'Code' tags to preserve their formatting. Follow the example link in my signature if you need to see how.

---

### Post by CharleyGnarlyP290 on 2013-05-21
Here is what I have:

```

brett@brett-MS-7387:~$ uname -mr
3.2.0-41-generic-pae i686

```

```

brett@brett-MS-7387:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2001:3308 D-Link Corp. 
Bus 005 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 004: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick

```

```

brett@brett-MS-7387:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
usb_storage            39646  1 
vesafb                 13516  1 
arc4                   12473  2 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
rtl8192cu              97717  0 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95855  1 rtl8192cu
mac80211              436493  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178877  2 rtlwifi,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_viapro             12969  0 
shpchp                 32265  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
via_rhine              27413  0 
pata_via               13428  0 
floppy                 60184  0 
sata_via               13495  2

```

```

brett@brett-MS-7387:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

```

brett@brett-MS-7387:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

```

Hopefully that is it. Please advise, and thanks for the help.

---

### Post by praseodym on 2013-05-21
Try to update the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential dkms 
wget media.cdn.ubuntu-de.org/forum/attachments/22/19/5210562-rtl8192cu-3.4.4.4749_dkms_.tar.gz
sudo tar xvf 5210562-rtl8192cu-3.4.4.4749_dkms_.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.4.4.4749
sudo dkms build -m rtl8192cu -v 3.4.4.4749
sudo dkms install -m rtl8192cu -v 3.4.4.4749
sudo depmod -a && sudo update-initramfs -u
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot and check:```

dkms status
sudo dkms autoinstall
modinfo 8192cu
lsmod
iwconfig
```

---

### Post by CharleyGnarlyP290 on 2013-05-21
Excellent! Wireless is up and running again after a reboot. Really appreciate the help, amigos.
And I learned a few things as well... like how to get code to show on the forums properly.
Thanks again.

---

### Post by praseodym on 2013-05-22
Please note that this driver version only works with kernel 3.2 and kernel 3.5 until revision 25!

For kernel 3.8 there is a new patched .deb-package:

 [https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/detail?name=rtl8192cu-tjp-dkms_1.6_all.deb&can=2&q=](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/detail?name=rtl8192cu-tjp-dkms_1.6_all.deb&can=2&q=)

---

