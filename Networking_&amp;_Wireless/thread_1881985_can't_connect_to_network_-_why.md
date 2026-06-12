---
title: "can't connect to network - why?"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by mark1977 on 2011-11-16
Hi,

I can't connect to the network anymore. previously I was able to connect with eth0 but not with my wireless, so I know eth0 works in principle. I have no idea why this has happened, but here is a load of info that may be of help in working out why:

```


mark@kapu: ~mark@kapu:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ppdev                   6375  0 
snd_hda_codec_realtek   279040  1 
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
i915                  325095  3 
drm_kms_helper         30742  1 i915
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   200288  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
uvcvideo               62883  0 
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               40550  1 uvcvideo
soundcore               8052  1 snd
video                  20623  1 i915
v4l1_compat            15495  2 uvcvideo,videodev
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    11892  1 videodev
output                  2503  1 video
intel_agp              29319  2 i915
psmouse                65040  0 
serio_raw               4918  0 
joydev                 11104  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38030  2 





]0;mark@kapu: ~mark@kapu:~$  lspci|grep -i ethernet
01:00.0 [01;31m[KEthernet[m[K controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast [01;31m[KEthernet[m[K controller (rev 05)
]0;mark@kapu: ~mark@kapu:~$ dmesg|grep -i ethernet
[    1.412706] r8169 Gigabit [01;31m[KEthernet[m[K driver 2.3LK-NAPI loaded
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:70:F4:66:0A:01

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ lshw -C network
WARNING: you should run this program as super-user.


DMI

   
SMP

   
PA-RISC

       
device-tree

           
SPD

   
memory

      
/proc/cpuinfo

             
CPUID

     
PCI (sysfs)

           
ISA PnP

       
PCMCIA

      
PCMCIA

      
kernel device tree (sysfs)

                          
USB

   
IDE

   
SCSI

    
Network interfaces

                  
Framebuffer devices

                   
Display

       
CPUFreq

       
ABI

   

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:66:0a:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:3000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d1500000-d151ffff memory:d0d00000-d0d0ffff(prefetchable)
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ 
]0;mark@kapu: ~mark@kapu:~$ sudo dhclient eth0
[sudo] password for mark: 
There is already a pid file /var/run/dhclient.pid with pid 2330
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/b8:70:f4:66:0a:01
Sending on   LPF/eth0/b8:70:f4:66:0a:01
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
]0;mark@kapu: ~mark@kapu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```Any ideas of why?

Thanks :p

Mark

---

### Post by jonobr on 2011-11-16
Looking at your logs it seems as if the router/gateway is not responding to DHCP request from your machine.

If DHCP to your router is fine, maybe its a cabling issue.

You can double check your dhcp requests by using
```
sudo tcpdump -i eth0 -vvv port bootps
```

see whats going out the interface hopefully

---

### Post by dandnsmith on 2011-11-16
Just a thought- try googling 'ubuntu problems r8169 driver', and look at some of the results.
I have recently had trouble with a system dual-booted with Windows 7, using a RTL 8111 ethernet - symptom sounds a bit like yours.
I realise you've a different card/chipset, which is why I suggest some reading, rather than a possible fix. Some found they needed to use a different driver (r8168?), but, for me, the fix came in changing Win7 settings.

HTH

---

### Post by praseodym on 2011-11-16
Please show explicitly:

```
lspci -nnk | grep -iA2 net
lsusb
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/resolv.conf
route -n
```

---

### Post by mark1977 on 2011-11-16
> **jonobr said:**
> Looking at your logs it seems as if the router/gateway is not responding to DHCP request from your machine.

If DHCP to your router is fine, maybe its a cabling issue.

You can double check your dhcp requests by using
```
sudo tcpdump -i eth0 -vvv port bootps
```see whats going out the interface hopefully

Thanks jonobr - you got it. I tried another cable and it works fine! :D

Thanks to everyone else too.

mark

---

### Post by jonobr on 2011-11-16
Rock and roll baby,
Rock and roll..............:guitar:

---

