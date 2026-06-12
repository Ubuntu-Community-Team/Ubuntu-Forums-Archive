---
title: "Wifi rt2800usb works during install but not after"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by stoltzmr on 2013-04-26
Hi, having battled to get my WiFi to work (on LENOVO ThinkPad R61i) with 12.04 LTS, I booted the latest Ubuntu v 13 from DVD and the wifi worked immediately when prompted for the password by the installation wizard. But after the installation and reboot, the wifi is dead!!! The configuration still reflects the SSID and password supplied at installation, but the Network configuration tool at the top right-hand corner of the screen reports WiFi Network (RALINK 802.11 n WLAN) "WiFi is disabled by hardware switch". But this is a USB wifi and has no hw switch.

Troubleshooting outputs as follows;

markus@markus-ThinkPad-R61e:~$ rfkill list all
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Notice how the menu interface reports to me that WiFi is disabled by hardware switch, but that rfkill does not indicate hw blocked...!

Can someone please help? I'm an ubuntu novice but from google I can see that Ubunutu is a pain with wireless. The light on the usb wifi is on. The network configuration gui shows that the wifi is "off" and says "out of reach" ?

Further outputs below:

markus@markus-ThinkPad-R61e:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             unavailable
  Default:           no
  HW Address:        C8:3A:35:CF:55:10

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

markus@markus-ThinkPad-R61e:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:25:91:e6:33
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=sb v2.11 ip=10.0.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe000000-fe00ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1
       logical name: wlan1
       serial: c8:3a:35:cf:55:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.8.0-19-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn

markus@markus-ThinkPad-R61e:~$ lsusb
Bus 002 Device 002: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 004 Device 002: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

markus@markus-ThinkPad-R61e:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_conexant    52256  1 
pcmcia                 39544  0 
rt2800usb              22366  0 
rt2x00usb              19979  1 rt2800usb
rt2800lib              60947  1 rt2800usb
rt2x00lib              48522  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12627  1 rt2800lib
arc4                   12543  4 
thinkpad_acpi          69384  0 
nvram                  13986  1 thinkpad_acpi
snd_hda_intel          38307  3 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_hda_codec         117580  2 snd_hda_codec_conexant,snd_hda_intel
iwl3945                63619  0 
snd_hwdep              13272  1 snd_hda_codec
iwlegacy               87575  1 iwl3945
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
i915                  535507  3 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
coretemp               13131  0 
drm_kms_helper         47545  1 i915
mac80211              526519  5 iwl3945,iwlegacy,rt2x00lib,rt2x00usb,rt2800lib
snd                    56485  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
video                  18894  1 i915
mac_hid                13037  0 
drm                   228750  4 i915,drm_kms_helper
cfg80211              436177  4 iwl3945,iwlegacy,mac80211,rt2x00lib
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
microcode              18286  0 
lpc_ich                16925  0 
psmouse                81038  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
serio_raw              13031  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
tg3                   143666  0 
ptp                    18189  1 tg3
ahci                   25507  2 
libahci                26108  1 ahci
pps_core               13736  1 ptp

---

### Post by kurt18947 on 2013-04-26
Even though it's a USB device, the wireless slide switch has to be on.  At least it does on mine.  I have a generic 5370 that's being weird.  I have two wireless routers, an Actiontec from Verizon and a Linksys WRT-300N with DD-WRT installed to play with.  Running 13.04 on the T61, the 5370 USB will connect to the Actiontec device but not the Linksys/DD-WRT.  If I plug the 5370 into a homebuilt desktop running 13.04, it will connect to the Linksys/DD-WRT machine no problem.  I have the same issue with a live USB on the Thinkpad so I'm wondering if I got a daily build with some issues.  I'm going to download a new 13.04 .iso once the rush slows down.

Edit:  I guess the Linksys just need a kick (reboot).  The reception on the generic device is weaker than other devices but it functions fine, no disconnects or other unpleasantness.

---

### Post by praseodym on 2013-04-26
Try these options:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by stoltzmr on 2013-04-29
Hi,

I fixed it! It was NOT the hw switch as so many threads seem to claim.

I found that another wireless module iwl3945 is also loaded for an internal wifi card which is broken and hence not used. But when I rmmod iwl3945, the USB wireless comes up immediately.

:)

---

### Post by kurt18947 on 2013-04-29
> **stoltzmr said:**
> Hi,

I fixed it! It was NOT the hw switch as so many threads seem to claim.

I found that another wireless module iwl3945 is also loaded for an internal wifi card which is broken and hence not used. But when I rmmod iwl3945, the USB wireless comes up immediately.

:)

Good job!  I have that adapter on a Thinkpad.  I find it *really* hard to discourage, it wants to run no matter what.   Have you blacklisted the module?  If you don't, you'll have to run the rmmod command each time you restart.

---

### Post by stoltzmr on 2013-04-29
Yes, blacklisted. 

Now I have to figure out how to mark this thread as 'SOLVED'. Can't seem to see where I need to tag it.... ;-)

---

