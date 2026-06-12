---
title: "Network Manager shows &quot;Wired Networks disconnected&quot; and disabled"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by Radar4002 on 2011-09-04
This issue is related to my issue I posted here:

[http://ubuntuforums.org/showthread.php?t=1838904]("http://ubuntuforums.org/showthread.php?t=1838904")

After searching/googling for most of the day, it seems there are a lot of network issues with this upgrade. 

One thing I noticed in trying to solve the issue is that when I open the Network Manager menu in the task bar, it shows both of my network interfaces disconnected and disabled and I have no idea how to enable them or to solve this issue.

Every since I upgraded to 11.04, I have not been able to enable my wired network connection. I don't know too much about networking of Ubuntu and was hoping to get some guidance on trouble-shooting this issue.

---

### Post by Vakman on 2011-09-04
Please post the outputs of:
```
sudo lshw -C network
```
```
ifconfig eth0
```

---

### Post by Radar4002 on 2011-09-04
Here's my output from sudo lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:e7:72:e8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:9e00(size=256) memory:fceff000-fcefffff memory:fcef8000-fcefbfff memory:fce00000-fce1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 03
       serial: 6c:f0:49:e7:72:ea
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:8e00(size=256) memory:fddff000-fddfffff memory:fddf8000-fddfbfff memory:fdd00000-fdd1ffff

```

And here's the ifconfig eth0:

```

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e7:72:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x6000 

```

---

### Post by Vakman on 2011-09-04
Okay. Now: ```
ifconfig
```

---

### Post by Radar4002 on 2011-09-04
ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e7:72:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 6c:f0:49:e7:72:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 6c:f0:49:e7:72:e8  
          inet addr:169.254.11.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3084 (3.0 KB)  TX bytes:3084 (3.0 KB)


```

---

### Post by Vakman on 2011-09-04
Okay, so we can try a few things.
But first do you have multiple ethernet cards or just the one?

---

### Post by Radar4002 on 2011-09-04
My motherboard has a built in dual LAN support, so I assume that I do have multiple cards.

---

### Post by Vakman on 2011-09-04
Ah, all right.

Attempt to run:
```
sudo dhclient eth0
``` and ```
sudo dhclient eth1
``` as I am not sure which it is connected to.
Does this solve anything?

If not:
Open up "Network Connections" (System Settings > Network Connections).
Add a new connection, right hand side, "Add".
Under the IPv4 Settings tab when adding this new connection, change the method to "Automatic (DHCP) addresses only" and then where it says "DNS servers", put 8.8.8.8, which is one of the public DNS servers that Google has and do this without the quotes. Then click Save. "Edit" the Auto Eth0 connection and do the same.
Does this help in any way?

---

### Post by Radar4002 on 2011-09-04
Doesn't look like those help.

When I run the dhclient, it just sits in the prompt for about 10-20 seconds then continues on in terminal like normal. 

Added the Google's DNS server doesn't seem to help either. I thought maybe it was a DNS issue, but I've tried pinging a Google IP, and that doesn't work either.

---

### Post by Vakman on 2011-09-05
Well, this is interesting.
I assume you have trying simply using the other ethernet port on your motherboard?
Hmm, what else...

---

### Post by Radar4002 on 2011-09-05
Yeah, and I know the current port that I am using is good because if I boot to Win7, my network/internet connection is fine.

I am clueless on what is going on...

---

### Post by Vakman on 2011-09-05
> **Radar4002 said:**
> Yeah, and I know the current port that I am using is good because if I boot to Win7, my network/internet connection is fine.

I am clueless on what is going on...

Did you try your other one though?

---

### Post by fdrake on 2011-09-05
can you post the results for:
```

lsmod
less /etc/modprobe.d/blacklist.conf | grep r8169
nm-tool
rfkill list all
```

edit: the fact that this happened after an update shows that you did not install backports mudules.

---

### Post by Radar4002 on 2011-09-05
Yes, I did try the other port.

---

### Post by Radar4002 on 2011-09-05
Here's my lsmod output:

```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
usb_storage            53538  1 
uas                    17996  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
radeon                982152  3 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
drm                   227534  5 radeon,ttm,drm_kms_helper
ppdev                  17113  0 
serio_raw              13166  0 
k10temp                13119  0 
edac_core              53845  0 
i2c_algo_bit           13400  1 radeon
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_mce_amd           23464  0 
sp5100_tco             13744  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             36959  1 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
firewire_ohci          40370  0 
usbhid                 46956  0 
ahci                   25951  1 
hid                    91020  1 usbhid
floppy                 74120  0 
firewire_core          62646  1 firewire_ohci
libahci                26642  1 ahci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13165  0 
pata_jmicron           12747  0 
r8169                  48022  0 
xhci_hcd               77643  0 

```

Here's the nm-tool output:

```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:F0:49:E7:72:E8

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:F0:49:E7:72:EA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```

The other 2 commands didn't output anything to terminal. And I am rather new to Ubuntu so I am not familiar with backports mudules.

---

### Post by nm_geo on 2011-09-05
This is interesting:

[http://ubuntuforums.org/showthread.php?t=1805271#6](http://ubuntuforums.org/showthread.php?t=1805271#6)

in the same top ten threads

---

### Post by fdrake on 2011-09-05
> **nm_geo said:**
> This is interesting:

[http://ubuntuforums.org/showthread.php?t=1805271#6](http://ubuntuforums.org/showthread.php?t=1805271#6)

in the same top ten threads

good catch! Since he doesn't a have connection that will be a little bit hard to achieve. I hope he has another computer available or a win partition available. 
He also should have the right driver already in the kernel. Probably blacklisted.

```
less /etc/modprobe.d/blacklist.conf | grep r816
```

---

### Post by nm_geo on 2011-09-05
> Yeah, and I know the current port that I am using is good because if I boot to Win7, my network/internet connection is fine.

He has a windoze option..but said fairly new to Ubuntu..

---

### Post by Radar4002 on 2011-09-05
@nm_geo Thanks a ton! That was definitely it! Made the changes in the post you linked to and then re-booted and it picked up it instantly! 

I am glad that is solved.

---

### Post by fdrake on 2011-09-05
> **Radar4002 said:**
> @nm_geo Thanks a ton! That was definitely it! Made the changes in the post you linked to and then re-booted and it picked up it instantly! 

I am glad that is solved.

make sure you install backports otherwise you will run again in the same problem in case of another updates of a new driver.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Radar4002 on 2011-09-05
@fdrake - Thanks, I will definitely take a look into backports.

---

### Post by nm_geo on 2011-09-05
> **Radar4002 said:**
> @fdrake - Thanks, I will definitely take a look into backports.
Please marked Solved I have a feeling we will see this again.. Thread tools

---

