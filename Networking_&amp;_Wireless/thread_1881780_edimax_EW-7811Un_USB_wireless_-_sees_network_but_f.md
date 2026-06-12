---
title: "edimax EW-7811Un USB wireless - sees network but fails to connect to it"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by talgalili on 2011-11-16
Hello all,

Yesterday I got my first Ubuntu (11.10 32 bit) installation (wish me luck), and I ran into a problem with my USB network card.

I use a wireless USB stick by edimax (it is called IEEE802.11b/g/n nano USB adapter or also EW-7811Un).

My problem is that Ubuntu seems to be able to use the USB to see the networks around me, but when I try to connect to my network - it just keeps trying and failing.

I am connected to the internet through a

300M Wireless N Router Model No. TL-WR841N / TL-WR841ND

I have other computers in the house which are able to connect to the internet.  And the same computer previously had Windows on it - and it managed to connect to the internet with no problem.

Can you please advise on how this can be resolved?
(what output should I send you?)

Thanks!

---

### Post by praseodym on 2011-11-16
Hi,

this device normally only needs the firmware copied to another location. Open a terminal (CTRL+ALT+T) and type in (or copy/paste):
```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/
```
replug the stick and check:

```
dmesg | egrep 'rtl8|r8'
iwconfig
rfkill list
lsmod
```

---

### Post by talgalili on 2011-11-16
Hello again,

I tried as you have suggested - but the network stick is still unable to connect to the wireless (while it still sees the network)

Bellow is the output, any more suggestions will be welcomed:



tal@Tal-home-desktop:~$ sudo mkdir /lib/firmware/RTL8192SU
[sudo] password for tal: 
tal@Tal-home-desktop:~$ sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/
tal@Tal-home-desktop:~$ dmesg | egrep 'rtl8|r8'
[    1.231866] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.231893] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.231946] r8169 0000:02:00.0: setting latency timer to 64
[    1.232201] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.233046] r8169 0000:02:00.0: eth0: RTL8101e at 0xf8014000, 00:1f:d0:6d:37:bd, XID 94200000 IRQ 42
[    9.706680] r8169 0000:02:00.0: eth0: link down
[    9.706694] r8169 0000:02:00.0: eth0: link down
[   11.238366] r8169 0000:02:00.0: eth0: link up
[   12.536697] rtl8192cu: MAC address: 80:1f:02:11:87:fe
[   12.536707] rtl8192cu: Board Type 0
[   12.552039] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   12.561859] usbcore: registered new interface driver rtl8192cu
[   12.587693] rtl8192cu: MAC auto ON okay!
[   12.825461] rtl8192cu: Tx queue select: 0x05
[   12.826216] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 4274.391624] Error: Driver 'rtl8192cu' is already registered, aborting...
[ 4378.774991] rtl8192cu: MAC address: 80:1f:02:11:87:fe
[ 4378.775001] rtl8192cu: Board Type 0
[ 4378.779993] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 4378.872115] rtl8192cu: MAC auto ON okay!
[ 4378.911755] rtl8192cu: Tx queue select: 0x05
[ 4378.912511] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
tal@Tal-home-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
tal@Tal-home-desktop:~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
tal@Tal-home-desktop:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
rtl8192cu              97651  0 
ppdev                  12849  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
snd_hda_codec_realtek   254125  1 
uvcvideo               67271  0 
snd_usb_audio         100880  1 
usbhid                 41905  0 
videodev               85626  1 uvcvideo
snd_usbmidi_lib        24558  1 snd_usb_audio
hid                    77367  1 usbhid
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80468  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  505108  3 
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32889  1 i915
snd_timer              28932  2 snd_pcm,snd_seq
drm                   192226  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
binfmt_misc            17292  1 
snd                    55902  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
r8169                  43104  0 
floppy                 60310  0







> **praseodym said:**
> Hi,

this device normally only needs the firmware copied to another location. Open a terminal (CTRL+ALT+T) and type in (or copy/paste):
```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/
```
replug the stick and check:

```
dmesg | egrep 'rtl8|r8'
iwconfig
rfkill list
lsmod
```

---

### Post by praseodym on 2011-11-16
Just to be sure:

```
uname -a
lsusb

```
please. If it is ID 7392:7811 you can update the driver via cable.

---

### Post by talgalili on 2011-11-17
Hi again,

So indeed I got 7392:7811
How do I "update the driver"? (my network cable is connected - so I have Internet).

Here's the output:


tal@Tal-home-desktop:~$ uname -a
Linux Tal-home-desktop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
tal@Tal-home-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0824 Logitech, Inc. 
Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 005 Device 002: ID 1532:0103 Razer USA, Ltd 
Bus 003 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 005 Device 003: ID 1532:0200 Razer USA, Ltd 






> **praseodym said:**
> Just to be sure:

```
uname -a
lsusb

```please. If it is ID 7392:7811 you can update the driver via cable.

---

### Post by praseodym on 2011-11-17
Here we go:
```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```
Reboot after that.

---

### Post by talgalili on 2011-11-17
Thank you very much praseodym!
It appears that there are several more problems in order to make this work.

1) The driver needs to be manually adjusted for ubuntu 11.10
2) The old driver needs to be blacklisted.

I have followed all the steps - and it now works!

(problem resolved)

I will soon write a blog post explaining all the steps I have taken - so future users may benefit from it.

With regards,
Tal


> **praseodym said:**
> Here we go:
```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```
Reboot after that.

---

### Post by talgalili on 2011-11-17
ok, I have managed to fix the problem.

I gave the detailed solution on my blog here:

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

Thank you for your help!

With regards,
Tal

---

