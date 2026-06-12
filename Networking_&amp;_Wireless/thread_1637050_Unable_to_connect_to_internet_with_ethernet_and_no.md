---
title: "Unable to connect to internet with ethernet and no idea what to do about it in 10.04"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by jarednielsen on 2010-12-03
I'm rather new to Linux/Ubuntu and about to lose my religion figuring this one out.  

I am unable to connect to the internet with ethernet in 10.04 64bit.  Everything was working fine this morning, but when I booted up this evening, no connection. 

In Network Connections, under the Wired tab, Auto eth0 reads Last Used: never.  Also, Network Manager had created a new network, Wired Connection 1.  I deleted Wired Connection 1.  

This morning the system attempted to run a check, which I cancelled.  So I rebooted and allowed the check to run.  

Now, no connections appear in the Wired Network box when I click the icon in the tool bar.   

I am able to connect via ethernet with my laptop, running 9.10.  

Also, the icon in the tool bar is wireless waves and not broken/connected cable.  
And the LED on the ethernet port does not light up.  

I don't have a Live CD to boot off.  

Any help will be greatly appreciated.

---

### Post by northd_tech on 2010-12-04
Hi Jared,

It sounds like you might have gotten a new kernel update (which wiped out your network modules for the new kernel- but that probably isn't anywhere near as terrible as it sounds ;) ).

To figure out what kind of hardware you've got on the 10.04 computer, can you post the results of the following terminal commands (under Ubuntu, go to Applications > Accessories > Terminal):

```
lspci 
sudo lshw -C network
lsusb
lsmod
ifconfig
iwconfig
ndiswrapper -l
```You probably want to copy & paste those commands to make sure there aren't any typos.  If you get error messages, post those here too.

---

### Post by jarednielsen on 2010-12-04
Thanks for your response.  Here's what I've got:
The first command, lspci | grep Network returned nothing.

```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 90:e6:ba:cb:8b:fa
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:b800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6ff8000-f6ffbfff(prefetchable) memory:fbdf0000-fbdfffff(prefetchable)

lsusb:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 03f0:2c12 Hewlett-Packard Officejet J4680
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod:

Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
usb_storage            49961  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_via      33207  1 
snd_ice1712            66309  0 
snd_ice17xx_ak4xxx      3123  1 snd_ice1712
snd_ak4xxx_adda         8572  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7946  1 snd_ice1712
snd_ac97_codec        125394  1 snd_ice1712
ac97_bus                1450  1 snd_ac97_codec
snd_i2c                 5550  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6857  1 snd_ice1712
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  5 snd_ice1712,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71251  21 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               515227  2 
asus_atk0110           10033  0 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
usblp                  12407  0 
psmouse                64576  0 
soundcore               8052  1 snd
serio_raw               4918  0 
i2c_piix4               9639  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_core              45423  0 
edac_mce_amd            9278  0 
drm                   198948  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
lp                      9336  0 
parport                37160  2 ppdev,lp
pata_marvell            3225  0 
usbhid                 41116  0 
hid                    83472  1 usbhid
ohci1394               30260  0 
r8169                  39682  0 
pata_atiixp             4209  0 
mii                     5237  1 r8169
ahci                   37870  4 
ieee1394               94771  1 ohci1394

ifconfig:

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:cb:8b:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10124 (10.1 KB)  TX bytes:10124 (10.1 KB)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

ndiswrapper -l:

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

```

---

### Post by northd_tech on 2010-12-04
> **jarednielsen said:**
> sudo lshw -C network
*-network               
       description: Ethernet interface
       product: **RTL8111/8168B **PCI Express Gigabit Ethernet controller
       vendor:** Realtek** Semiconductor Co., Ltd.

**lsmod**:
Module                  Size  Used by
**r8169**                  39682  0 
mii                     5237  1** r8169**

**ifconfig**:
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:cb:8b:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)**
          Interrupt:30 Base address:0xa000 

That looks to be a Realtek 8111/8168B/8169 ethernet controller which I believe was more stable with the older Ubuntu kernels.  Apparently there is a problem with the 10.x Ubuntu versions from the threads that I just found here in a search:

[http://ubuntuforums.org/showthread.php?t=1465703](http://ubuntuforums.org/showthread.php?t=1465703)

[http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667)

[http://ubuntuforums.org/showthread.php?t=1591756](http://ubuntuforums.org/showthread.php?t=1591756)

Also, I should have had you run the following** lspci **command (I typed a minor typo), but we probably have enough hardware info with what you just posted above:

```
lspci
```I'm assuming this is an onboard (motherboard) Network Interface Card (NIC) and the only interface available then?

Edit: there does look to be an "r8169" Realtek module and one accompanying module loaded, but I'm not sure what that particular NIC needs to work properly- you might want to bump one of those older threads and hopefully someone has a working Realtek 8168/8169 card under Ubuntu 10.xx.

---

### Post by jarednielsen on 2010-12-04
Thanks for pointing me in the right direction northd_tech.  I found the solution on this thread: [http://ubuntuforums.org/showthread.php?t=1436667&page=3](http://ubuntuforums.org/showthread.php?t=1436667&page=3)

For anyone else who Googles this, this is what worked for me: simply unplug your computer, let it sit for a spell, then plug it back in.  I let mine sit over night.

---

