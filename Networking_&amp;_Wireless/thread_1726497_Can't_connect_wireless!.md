---
title: "Can't connect wireless!"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by JafaarNhh on 2011-04-11
Hi!

It was a long time since i used ubuntu last and now im back :)
I've got some problems connecting to the wireless network i am using wicd but it always tell me that there is no wireless networks,
so I would be pleased if you could help me im using ubuntu 9.10 pretty old but working just fine except the wireless thing.

here is some info:

```
jafar@jafar-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

### Post by JafaarNhh on 2011-04-13
I've upgraded to 10.04 now so can anyone help,
i've downloaded the drivers for my network card (broadcom) but nothing seems to work need help fast please cuz im tired of using windows i want to use ubuntu more.

---

### Post by TBABill on 2011-04-13
Need to know a bit more about what you are working with and what drivers, if any, are installed and how they are configured. 
 
With most Broadcom cards you can just plug into ethernet, do updates, then click System>>Administration>>Hardware (for 10.04). Select the right driver from the options provided, restart and enjoy. 
 
If that's not enough to get it going, please open a terminal and enter these commands, then paste their outputs back here for review:
 
```
lspci
```
```
lsmod
```
```
sudo lshw -C network
```

---

### Post by JafaarNhh on 2011-04-13
the output of lspci was:

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

```

and od lsmod:
```
Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7885  2 
fbcon                  35102  71 
tileblit                2031  1 fbcon
bridge                 45614  0 
stp                     1655  1 bridge
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
bnep                    9436  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_analog    58598  1 
lib80211_crypt_tkip     7596  0 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tpm_infineon            7745  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
radeon                676897  3 
snd_timer              19098  2 snd_pcm,snd_seq
wl                   1959598  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
ppdev                   5259  0 
joydev                  8740  0 
drm_kms_helper         29329  1 radeon
tpm_tis                 7488  0 
drm                   162345  5 radeon,ttm,drm_kms_helper
parport_pc             25962  1 
video                  17375  0 
output                  1871  1 video
tpm                    13906  2 tpm_infineon,tpm_tis
tpm_bios                5266  1 tpm
lib80211                5046  2 lib80211_crypt_tkip,wl
snd                    54180  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
ati_agp                 5094  0 
led_class               2864  1 hp_accel
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
i2c_algo_bit            5028  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
btusb                  10957  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
k8temp                  3152  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,ati_agp
i2c_piix4               8335  0 
lp                      7028  0 
shpchp                 28835  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32200  2 
tg3                   109324  0 
pata_atiixp             3148  0 

```

and of sudo lshw -C network:
```
*-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:62:51:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.09 ip=92.32.253.15 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:d0000000-d000ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:78:7d:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11a
       resources: irq:18 memory:c8000000-c8003fff

```

---

### Post by JafaarNhh on 2011-04-13
I'm using a HP Compaq 6715b if that info comes to any help...

---

### Post by TBABill on 2011-04-13
Does the device have either a physical on/off switch or a keyboard soft switch combination (such as ALT+F2)? It says network disabled, but you have the wl driver listed in lsmod, which is the STA driver for Broadcom cards, same as I use. We have the same wireless device and it appears to be setup correctly. Can you ensure it's not accidentally powered off?
 
After that, can you ```
sudo modprobe wl
``` and if there is no output in a terminal then that's normal. It just re-enables the driver.
 
Have you restarted and checked system>>administration>>hardware and made sure the STA driver choice says "activated"?

---

### Post by JafaarNhh on 2011-04-13
The power is on from the router and my laptop,and i downloaded all drivers for the broadcom card,

when I wrote sudo modprobe wl i got this output:
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```

---

### Post by TBABill on 2011-04-13
Can you add the following to the file /etc/modprobe.d/blacklist.conf then save and reboot:
 
```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
```
 
To open that file for editing, just ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
 
I didn't see any of them loading when you listed the output of lsmod, but just to be sure. You will need to restart for this to take effect.

---

### Post by JafaarNhh on 2011-04-13
I tried but i got the the same warning.

---

### Post by TBABill on 2011-04-13
I have never seen that warning before. I will try to find something via Google.
 
One thing I found....rename the file /etc/modprobe.d/blacklist to /etc/modprobe.d/blacklist.**conf**

---

### Post by TBABill on 2011-04-13
Since you have a BCM4312, try ```
sudo apt-get install --reinstall bcmwl-kernel-source
```
 
Then  ```
sudo modprobe -r wl
```
 
Then ```
sudo modprobe wl
```

---

### Post by JafaarNhh on 2011-04-15
i can't rename the file blacklist to blacklist.conf the rename options is closed!?

---

### Post by TBABill on 2011-04-17
You need to be root.

---

