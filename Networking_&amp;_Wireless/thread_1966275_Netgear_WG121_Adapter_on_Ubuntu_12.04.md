---
title: "Netgear WG121 Adapter on Ubuntu 12.04"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by Mr_Congeniality on 2012-04-26
When I went to install 12.04 it would not let me keep my existing settings from 11.10 installed on my hard drive so I had to do a fresh install, and this took out my WG121 wireless driver installed from NdisWrapper in the process. So I went to this page: [http://help.ubuntu.com/community/WifiDocs/Device/WG121]("http://help.ubuntu.com/community/WifiDocs/Device/WG121")

I could not follow these instructions because I am not able to get internet access at all since the machine solely relies on a wireless internet connection to continue the steps, and when I clicked the link that I could do it by hand instead, I was met with a page not found error. Now my system is rendered useless, and I currently have no way of installing this properly.

I need some help setting this up. I am able to migrate files across a USB stick, and I need more help on doing this. I am using the 32-bit version of 12.04.

Thanks.

---

### Post by wildmanne39 on 2012-04-27
Hi, I do not think you need ndiswrapper any more please post the output of:
> lsmod
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Mr_Congeniality on 2012-04-29
Here you are good sir.

```
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
p54usb                 17407  0 
p54common              36909  1 p54usb
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
snd_emu10k1           133257  3 snd_emu10k1_synth
snd_intel8x0           33455  2 
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        106082  2 snd_emu10k1,snd_intel8x0
snd_hwdep              13276  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25424  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
crc_ccitt              12595  1 p54common
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
mac80211              436455  2 p54usb,p54common
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
ac97_bus               12642  1 snd_ac97_codec
nouveau               712294  3 
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                80845  3 snd_emu10k1,snd_intel8x0,snd_ac97_codec
usbhid                 41906  0 
cfg80211              178679  2 p54common,mac80211
hid                    77367  1 usbhid
dcdbas                 14098  0 
snd_timer              28931  3 snd_emu10k1,snd_seq,snd_pcm
ttm                    65344  1 nouveau
psmouse                72846  0 
drm_kms_helper         45466  1 nouveau
serio_raw              13027  0 
snd                    62064  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_emu10k1,snd_intel8x0,snd_pcm
drm                   197692  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   141369  0 
usb_storage            39646  0 


```

---

### Post by wildmanne39 on 2012-04-29
Hi, I see a driver loaded please post the output of:
```
lsusb
```
Thanks

---

### Post by Mr_Congeniality on 2012-04-29
> **wildmanne39 said:**
> Hi, I see a driver loaded please post the output of:
```
lsusb
```
Thanks

Here's the lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:4210 NetGear, Inc. WG121(v2) 54 Mbps Wireless [Intersil ISL3886]
Bus 003 Device 002: ID 045e:00a4 Microsoft Corp. 
Bus 005 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
```

---

### Post by wildmanne39 on 2012-04-29
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e p54 -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by Mr_Congeniality on 2012-04-29
> **wildmanne39 said:**
> Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e p54 -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

"cat /etc/lsb-release; uname -a" returns:
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux randy-desktop 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
```
iwconfig returns:
```

lo        no wireless extensions.

eth0      no wireless extensions.


```
"rfkill list all" returns nothing.
"nm-tool" returns:
```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:11:11:4B:F2:B0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```
"sudo iwlist scan" returns:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```
"sudo cat /var/log/syslog | grep -e p54 -e firmware -e wlan -e wpa -e etork | tail -n55" returns:
```

Apr 28 16:24:36 randy-desktop kernel: [    7.925772] intel_rng: don't want to disable this in firmware setup, and if
Apr 28 16:24:36 randy-desktop kernel: [   11.856204] usb 1-8: (p54usb) cannot load firmware isl3886usb (-2)!
Apr 28 16:24:36 randy-desktop kernel: [   11.859820] p54usb: probe of 1-8:1.0 failed with error -2
Apr 28 16:24:36 randy-desktop kernel: [   11.859868] usbcore: registered new interface driver p54usb
Apr 28 16:24:44 randy-desktop NetworkManager[886]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 28 17:18:13 randy-desktop kernel: [ 3230.150602] usb 1-8: (p54usb) cannot load firmware isl3886usb (-2)!
Apr 28 17:18:13 randy-desktop kernel: [ 3230.162978] p54usb: probe of 1-8:1.0 failed with error -2
Apr 28 17:26:25 randy-desktop kernel: [ 3721.404036] usbcore: deregistering interface driver p54usb
Apr 29 08:00:38 randy-desktop kernel: [   16.492724] intel_rng: don't want to disable this in firmware setup, and if
Apr 29 08:00:38 randy-desktop NetworkManager[563]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 29 08:00:39 randy-desktop kernel: [   18.309646] usb 1-8: (p54usb) cannot load firmware isl3886usb (-2)!
Apr 29 08:00:40 randy-desktop kernel: [   18.522891] p54usb: probe of 1-8:1.0 failed with error -2
Apr 29 08:00:40 randy-desktop kernel: [   18.523168] usbcore: registered new interface driver p54usb

```

---

### Post by wildmanne39 on 2012-04-29
Hi, please do:
```
sudo apt-get install linux-firmware-nonfree
```
Then reboot.
Thanks

---

### Post by Mr_Congeniality on 2012-04-29
> **wildmanne39 said:**
> Hi, please do:
```
sudo apt-get install linux-firmware-nonfree
```
Then reboot.
Thanks

I don't have a connection without the wireless. I take this is the package I should migrate via a USB drive?

[http://www.ubuntuupdates.org/package/core/precise/multiverse/base/linux-firmware-nonfree](http://www.ubuntuupdates.org/package/core/precise/multiverse/base/linux-firmware-nonfree)

Edit: Downloaded the .deb package and migrated it over to the computer with a USB stick, and used the "sudo dpkg -i [filename]" in terminal to install it. Wireless works now. Thanks a ton!

---

### Post by wildmanne39 on 2012-05-01
Hi, that is great I am glad it is working, I am sorry I did not get back to you sooner I instlled ubuntu 12.04 and it caused issues that I have spent days fixing.
Enjoy

---

