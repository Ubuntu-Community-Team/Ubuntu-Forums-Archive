---
title: "Can't connect with Netgear WNA1100"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by LtDarien on 2011-08-10
I've been searching for help on this issue, and I've tried some things, but I can't get my connection to work.

I can see the available networks, and the LED on my device is on, but when I try to connect it can't connect and asks me for the network security key again.

I've installed and run the ath9k-htc installer, but I noticed no change when I did so.  Is there a step I'm missing?

I'm a brand new linux user, so pardon my ignorance.

lsusb: ```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 047f:c001 Plantronics, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 046d:c227 Logitech, Inc. G15 Refresh Keyboard
Bus 003 Device 006: ID 046d:c525 Logitech, Inc. MX Revolution Cordless Mouse
Bus 003 Device 005: ID 1532:0111 Razer USA, Ltd 
Bus 003 Device 004: ID 046d:c226 Logitech, Inc. G15 Refresh Keyboard
Bus 003 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 003 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 003: ID 046d:0808 Logitech, Inc. Webcam C600
**Bus 001 Device 002: ID 0846:9030 NetGear, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```lshw -C network : ```
 *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 30:46:9a:1f:e4:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```EDIT:  I'm running Ubuntu 11.4

---

### Post by LtDarien on 2011-08-11
Some other outputs:
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 
```lsmod | grep ath:
```
ath9k_htc              61400  0 
mac80211              294370  1 ath9k_htc
ath9k_common           13851  1 ath9k_htc
ath9k_hw              323077  2 ath9k_htc,ath9k_common
ath                    23773  2 ath9k_htc,ath9k_hw
cfg80211              178528  3 ath9k_htc,mac80211,ath
```rfkill list all:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by LtDarien on 2011-08-12
I don't know what the problem is.  I've read that the WNA is supposed to work with Natty out of the box, but I'm having so much trouble.  I don't want to have to give up on linux, but I can't rely on a wired connection.

I've tried re-installing Ubuntu, as well as doing a managed connection to my router (rather than DHCP) but nothing  has worked so far.  It's frustrating, because Ubuntu can SEE the available networks but won't connect to mine.

---

### Post by s031jd on 2011-08-19
Get the ndiswrapper and related packages from the Synaptic Package Manager.  Then run the following commands: 

[LIST]
[*]sudo rfkill list all
[*]rfkill unblock wifi
[*]sudo rfkill list all
[*]sudo ifconfig wlan0 up            -------> wlan0 if that is your wireless device in iwconfig.
[/LIST]
The "rfkill unblock wifi" command should work if you have rfkill installed and it's a soft block.

---

### Post by nm_geo on 2011-08-19
> **LtDarien said:**
> I don't know what the problem is.  I've read that the WNA is supposed to work with Natty out of the box, but I'm having so much trouble.  I don't want to have to give up on linux, but I can't rely on a wired connection.

I've tried re-installing Ubuntu, as well as doing a managed connection to my router (rather than DHCP) but nothing  has worked so far.  It's frustrating, because Ubuntu can SEE the available networks but won't connect to mine.

If you are still having issue.

Read this it is my notes on making it work.


[LIST]
[*]    Downloaded the driver installer
[*]    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
[*]    Execute the .deb packet
[*]    Had already connected the WiFi adapter
[*]    Needed the htc_9271.fw (firmware)
[*]    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)
[*]    Moved it to /lib/firmware
[*]    Temporarily blacklisted my internal (b43) driver to stop any confusion
[*]    Rebooted It works my wireless only had g speeds
[/LIST]
You seem to have the driver correct but need the (firmware) and my step on blacklisting probably does not apply.  Wish I had seen this last week..

---

### Post by LtDarien on 2011-08-24
> **s031jd said:**
> Get the ndiswrapper and related packages from the Synaptic Package Manager.  Then run the following commands: 

[LIST]
[*]sudo rfkill list all
[*]rfkill unblock wifi
[*]sudo rfkill list all
[*]sudo ifconfig wlan0 up            -------> wlan0 if that is your wireless device in iwconfig.
[/LIST]
The "rfkill unblock wifi" command should work if you have rfkill installed and it's a soft block.



rfkill list all:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by LtDarien on 2011-08-24
> **nm_geo said:**
> If you are still having issue.

Read this it is my notes on making it work.


[LIST]
[*]    Downloaded the driver installer
[*]    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
[*]    Execute the .deb packet
[*]    Had already connected the WiFi adapter
[*]    Needed the htc_9271.fw (firmware)
[*]    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)
[*]    Moved it to /lib/firmware
[*]    Temporarily blacklisted my internal (b43) driver to stop any confusion
[*]    Rebooted It works my wireless only had g speeds
[/LIST]
You seem to have the driver correct but need the (firmware) and my step on blacklisting probably does not apply.  Wish I had seen this last week..


the link for the firmware doesn't work.

---

### Post by nm_geo on 2011-08-24
I just tested the link seems okay to me.. They are index links not html pages.
See Attached pictures below.

---

### Post by LtDarien on 2011-08-25
Well I feel really stupid, because when I try the browser just times out.  I know I've viewed index pages before.

---

### Post by LtDarien on 2011-08-25
Okay, so I've gotten the firmware and moved it to /lib/firmware (I got it another way, still can't get the index to work)  rebooted and nothing has changed.  lsusb, lshw -C network, iwconfig all have the same outputs as I posted originally.

I can see the wireless networks, but I cannot connect to mine.

---

### Post by nm_geo on 2011-08-26
> **LtDarien said:**
> Okay, so I've gotten the firmware and moved it to /lib/firmware (I got it another way, still can't get the index to work)  rebooted and nothing has changed.  lsusb, lshw -C network, iwconfig all have the same outputs as I posted origin

I can see the wireless networks, but I cannot connect to mine.



Give us the following

```
dmesg | grep ath

```

complete
```
sudo lshw -C network
```

---

### Post by LtDarien on 2011-08-26
```
$ dmesg | grep ath
[    0.660309] device-mapper: multipath: version 1.2.0 loaded
[    0.660311] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.626632] usb 1-1: ath9k_htc: Transferred FW: ar9271.fw, size: 51312
[   13.050508] usb 1-1: ath9k_htc: HTC initialized with 33 credits
[   29.410018] ath: EEPROM regdomain: 0x60
[   29.410022] ath: EEPROM indicates we should expect a direct regpair map
[   29.410026] ath: Country alpha2 being used: 00
[   29.410028] ath: Regpair used: 0x60
[   29.490696] Registered led device: ath9k-phy0::radio
[   29.490771] Registered led device: ath9k-phy0::assoc
[   29.491085] Registered led device: ath9k-phy0::tx
[   29.491166] Registered led device: ath9k-phy0::rx
[   29.491169] usb 1-1: ath9k_htc: USB layer initialized
[   29.491200] usbcore: registered new interface driver ath9k_hif_usb

``````
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:c6:e4:e1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:febe0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 30:46:9a:1f:e4:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb driverversion=2.6.38-11-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by praseodym on 2011-08-26
You also need the firmware package htc_7010.fw

Direct link for the complete firmware package [here]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=snapshot;h=HEAD;sf=tgz")

The actual firmware (Aug-25) package via
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz
sudo tar xvf ath_htc_firmware-1.tar.gz -C /lib/firmware 
```

from [here]("http://forum.ubuntuusers.de/topic/gibt-es-schon-einen-treiber-fuer-wlan-usb-ada/2/#post-2640681").

---

### Post by nm_geo on 2011-08-26
Do a complete. 

```
lsmod
```

Then 

```
sudo modprobe ath9k_htc
```

What type of computer are we dealing with?  Does it have any other wireless connection?

---

### Post by LtDarien on 2011-08-26
```

$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
vesafb                 13761  1 
arc4                   12529  2 
snd_hda_codec_hdmi     28167  4 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
usbhid                 46956  0 
nvidia              10709116  38 
usb_storage            53538  1 
uas                    17996  0 
snd_usb_audio         112426  3 
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13604  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
ath9k_htc              61400  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
mac80211              294370  1 ath9k_htc
ath9k_common           13851  1 ath9k_htc
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_hw              323077  2 ath9k_htc,ath9k_common
ath                    23773  2 ath9k_htc,ath9k_hw
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath9k_htc,mac80211,ath
uvcvideo               72195  0 
usblp                  18233  0 
hid                    91020  1 usbhid
videodev               82052  1 uvcvideo
ppdev                  17113  0 
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
psmouse                73535  0 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             36959  1 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
r8169                  48022  0 
```

sudo modprobe ath9k_htc returns nothing.

It is an Intel core 2 duo I built myself.  right now I'm dual booting windows 7 and ubuntu 11.04

I can connect to my router just fine in Windows.

---

### Post by elkaloo on 2011-09-12
I've got the same problem.

I can use the atheros driver, or pass through ndiswrapper. With both, I can show the list of available networks.
But I can just connect to unsecured networks.
With networks secured with WEP (and WPA ?), it just asks me my password undefinitely.

Thanks.

---

