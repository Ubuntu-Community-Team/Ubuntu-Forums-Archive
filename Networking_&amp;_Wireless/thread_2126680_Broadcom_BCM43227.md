---
title: "Broadcom BCM43227"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by Midoo Ousman on 2013-03-17
:(


hi there i have insalled Ubuntu 12.04 but wireless didnt work 

i re installed 11.04 although the same problem plz guys help me to  solve  the problem thanks
 
..


[SIZE=5]**ASAP**[/SIZE] plzzzz

---

### Post by wildmanne39 on 2013-03-17
Hi, recommend reinstalling 12.04 because 11.04 is not longer supported, then copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Midoo Ousman on 2013-03-17
ok thanks for ur help 

i will re install 12.04 


and i will replay you

---

### Post by Midoo Ousman on 2013-03-18
i just installed ubuntu 12.04    


i cannot access to any connection

---

### Post by Midoo Ousman on 2013-03-18
i type it in my Termial i found 


> 
.Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known.wget: unable to resolve host address `dl.dropbox.com'




---

### Post by varunendra on 2013-03-18
> **Midoo Ousman said:**
> i type it in my Termial i found

Follow the 'Wireless Script' link in my signature and follow the instruction for "No Internet Connection" method.
Run the script on the Ubuntu computer as mentioned in the linked post and post back the result file or its contents here.

---

### Post by Midoo Ousman on 2013-03-18
i got all this information 

```
*************** info trace ****************




**** uname -a ****

Linux midoo-Aspire-5742Z 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"



**** lspci ****

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0487]
	Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
	Subsystem: Foxconn International, Inc. Device [105b:e040]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)



**** lsusb ****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b2bf Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 001 Device 005: ID 0489:e033 Foxconn / Hon Hai 



**** iwconfig ****


**** rfkill ****

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



**** lsmod ****

Module                  Size  Used by
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
intel_ips              18174  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  472941  3 
mei                    41616  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
btusb                  18288  2 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  12 
bluetooth             180104  23 btusb,bnep,rfcomm
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                12979  0 
mac_hid                13253  0 
wmi                    19256  2 acer_wmi,mxm_wmi
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
ums_realtek            18248  0 
usb_storage            49198  1 ums_realtek
uas                    18180  0 
tg3                   152032  0 



**** nm-tool ****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true



**** NetworkManager.conf ****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false



**** NetworkManager.conf-10.04 ****



**** interfaces ****

auto lo
iface lo inet loopback




**** iwlist ****


**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN



**** blacklist.conf ****

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



**** dmesg ****

[    1.143393] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    3.991954] tg3.c:v3.121 (November 2, 2011)
[    3.992002] tg3 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.992016] tg3 0000:01:00.0: setting latency timer to 64
[    4.009611] tg3 mdio bus: probed
[    4.021233] tg3 0000:01:00.0: eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address <MAC address removed>
[    4.021238] tg3 0000:01:00.0: eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=100:01)
[    4.021241] tg3 0000:01:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    4.021243] tg3 0000:01:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   16.485612] wmi: Mapper loaded
[   16.534187] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.534207] acer_wmi: Function bitmap for Communication Button: 0x801
[   16.534346] acer_wmi: Brightness must be controlled by generic video driver
[   18.282232] type=1400 audit(1363619772.042:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=785 comm="apparmor_parser"
[   18.340750] tg3 0000:01:00.0: irq 43 for MSI/MSI-X
[   19.014846] tg3 0000:01:00.0: eth0: Link is down
[  103.585385] type=1400 audit(1363619857.366:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1750 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************
```

---

### Post by varunendra on 2013-03-18
> **Midoo Ousman said:**
> i got all this information 

```

02:00.0 Network controller [0280]: Broadcom Corporation** BCM43227** 802.11b/g/n [**14e4:4358**]
	Subsystem: Foxconn International, Inc. Device [105b:e040]
```

Can you get a temporary wired connection on the system? It'll make things easier.

---

### Post by Midoo Ousman on 2013-03-18
yes got it 


thanks for ur contribution

---

### Post by varunendra on 2013-03-18
Connect to it, open a terminal and do -
```
sudo apt-get update
sudo apt-get install linux-headers-generic dkms bcmwl-kernel-source
```
Unplug the cable connection, reboot and see if the wireless works.

---

### Post by Midoo Ousman on 2013-03-18
i got it and  i am online throgh the wierd connection

---

### Post by Midoo Ousman on 2013-03-18
:(

still didnt work yet ...

---

### Post by Midoo Ousman on 2013-03-18
OMG...... :P

It work's 

thank you very much for your help 


you really helped me 

god bless you ..

---

### Post by varunendra on 2013-03-18
[s]> **Midoo Ousman said:**
> :(

still didnt work yet ...

Did you follow what I suggested in post no #10 ?

If yes, please try -
```
sudo modprobe -v wl
```
..and post back if there are any errors in the terminal.

Alternatively, you can try "Additional Drivers" from Dash menu (while connected via cable), although it will do more or less the same thing that I suggested in my previous post.[/s]

disregard ^^ :P

> **Midoo Ousman said:**
> OMG...... :P

It work's 

thank you very much for your help 


you really helped me 

god bless you ..
You're welcome ! :)


**Edit 2:**
Please mark the thread as [Solved] now. (follow my signature to see how)
Thanks!

---

