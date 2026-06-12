---
title: "SMC EZ Connect g adapter!"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by Rampo on 2011-01-09
Hi,
 
I am new to Ubuntu. I just installed Ubuntu Netbook on my Dell Latitude D610. I need a wireless USB adapter to use the internet. I decided to make use of the SMC EZ Connect g 802.11g Wireless USB 2.0 Adapter, which I used on Windows XP. Unfortunately Ubuntu recognizes the adapter (lsusb in the terminal). But that's it. No connection to the internet whatsoever or searching for available networks. 
Help me, guys. What should I do to make this adapter work. Drivers? I looked for drivers on the SMC website, couldn't find any.
 
Model: SMC2862W-G
Part No: 99-012084-449

---

### Post by PatchesTheCaveman on 2011-01-10
That wireless adapter uses a "prism" chipset and should be supported out of the box with Ubuntu.

Since it's not working, follow the instructions in this thread to provide us with diagnostic information we can use to see what's going on with it:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Rampo on 2011-01-10
Thanks man! I'll try your suggestion.

---

### Post by Rampo on 2011-01-10
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller

```
 
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:14:22:c4:ba:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15840 (15.8 KB)  TX bytes:15840 (15.8 KB)

```

iwconfig
```

lo        no wireless extensions.
eth0     no wireless extensions.

```

lsmod
```

Module                  Size  Used by
p54usb                 11206  0 
p54common              25426  1 p54usb
led_class               2633  1 p54common
mac80211              231541  2 p54usb,p54common
cfg80211              144470  2 p54common,mac80211
binfmt_misc             6599  1 
joydev                  8735  0 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
i915                  290938  4 
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168054  5 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
yenta_socket           21518  0 
dell_laptop             5730  0 
parport_pc             26058  1 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
intel_agp              26360  2 i915
dcdbas                  5402  1 dell_laptop
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
video                  18712  1 i915
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
tg3                   123310  0
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: eth0
       version: 01
       serial: 00:14:22:c4:ba:c9
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfdf0000-dfdfffff

```

iwlist scan
```

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

```

lsb_release -d
```

Description: Ubuntu 10.10

```

uname -mr
```

2.6.35-22-generic i686

```

---

### Post by PatchesTheCaveman on 2011-01-11
Hmm.  The driver is loading but it's not creating a network interface for your adapter.

Copy/paste the results from this command:
```
dmesg | grep -i p54
```
That will show us any errors the driver might be reporting.

---

### Post by Rampo on 2011-01-11
```

[    762.625446] usb 1-8: (p54usb) cannot load firmware isl3887usb (-2)!
[    762.634219] p54usb: probe of 1-8: 1.0 failed with error -2
[    762.634267] usbcore: registered new interface driver p54usb

```

---

### Post by PatchesTheCaveman on 2011-01-11
Plug into a wired Ethernet connection, and run the following command on the terminal to install some missing files needed by your wireless USB device:
```
sudo apt-get install linux-firmware-nonfree
```

Then, run the following commands to restart your wireless driver:
```
sudo modprobe -r p54usb
sudo modprobe p54usb
```

Now, you should be able to unplug the wired connection and click on the wireless icon on your top panel and connect to wireless networks.

---

### Post by Rampo on 2011-01-12
Thanks it worked!

---

### Post by Rampo on 2011-01-12
Thanks it worked!

---

### Post by Rampo on 2011-01-12
Thanks it worked!

---

