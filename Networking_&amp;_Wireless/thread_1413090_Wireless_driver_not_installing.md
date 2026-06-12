---
title: "Wireless driver not installing"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by ren3dar on 2010-02-22
I am using an HP dv6 series laptop

the wireless works fine in Ubuntu 9.10 (must install the Broadcom STA wireless driver)

When i try to use Kubuntu 9.10 my computer crashes when i try to install the driver.  Is there any particular reason why it works in one and not the other?  Anyone know of a fix?

---

### Post by northd_tech on 2010-02-22
Well the "fix" for me has been not to update to Karmic 9.10 (I'm still running Jaunty 9.04, and I prefer both that and 8.10 to version 9.10 in all honesty).  I have a Broadcom "4328" in my HP DV98xx laptop that seems to like the Broadcom STA driver.

I have also heard that you need to Remove, then re-Activate the STA driver (and you might have to unplug your ethernet cable first), then restart the computer.  Others have said that they needed to uninstall the linux kernel backports in order to get the proprietary Hardware Drivers to re-appear.

There was discussion about proprietary drivers (both Broadcom and NVIDIA, which we probably both need and use for HP laptops) on this thread:

[http://ubuntuforums.org/showthread.php?t=1411847](http://ubuntuforums.org/showthread.php?t=1411847)

I'm not sure about kubuntu (I only tried it briefly and didn't like KDE version 4) and I'm currently running Ultimate Ubuntu 2.3 (based upon Jaunty 9.04).  I also don't know your exact model of hardware so let's figure that out first.  Can you post the results of the following terminal commands:

```
lspci 

lsmod

lsusb

sudo lshw -C network

ifconfig

iwconfig 
 
sudo iwlist scan 
 
nm-tool
```

The output of some of those will be pretty long, so you will probably want to cut/paste the responses.

---

### Post by ren3dar on 2010-02-22
A little more information on what happens:

After a clean install of Kubuntu 9.10 and installing all available updates, I went into the hardware drivers and attempted to install the Broadcom STA wireless driver.  Installation completed but before i could restart the system crashed.  Other attempts have yeilded similar results and all of them either fail or crash.

here is the system info you requested:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                   
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)                                            
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)                                                   
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

```
Module                  Size  Used by                                           
cbc                     4224  70                                                
cryptd                  8008  0                                                 
aes_x86_64              8992  71                                                
aes_generic            28480  1 aes_x86_64                                      
ecb                     3296  1                                                 
dm_crypt               14888  0                                                 
ppdev                   8232  0                                                 
b43                   136584  0                                                 
mac80211              210008  1 b43                                             
snd_hda_codec_intelhdmi    14880  1                                             
snd_hda_codec_idt      72976  1                                                 
snd_hda_intel          31880  2                                                 
cfg80211              109144  2 b43,mac80211                                    
snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel                                                                         
snd_hwdep               9352  1 snd_hda_codec                                   
snd_pcm_oss            44704  0                                                 
wl                   1277380  0                                                 
iptable_filter          3872  0                                                 
lib80211                7812  1 wl                                              
ip_tables              21200  1 iptable_filter                                  
snd_mixer_oss          18976  1 snd_pcm_oss                                     
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss         
snd_seq_dummy           3460  0                                                 
x_tables               25832  1 ip_tables                                       
snd_seq_oss            33440  0                                                 
lp                     11908  0                                                 
snd_seq_midi            8192  0                                                 
snd_rawmidi            27360  1 snd_seq_midi                                    
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi                        
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                                                                       
parport                40528  2 ppdev,lp                                        
snd_timer              26992  2 snd_pcm,snd_seq                                 
hp_accel               12480  0                                                 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lis3lv02d               9312  1 hp_accel
uvcvideo               65260  0
snd                    77096  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 13088  0
lirc_ene0100            9444  0
soundcore               9088  1 snd
input_polldev           4720  1 lis3lv02d
lirc_dev               13928  1 lirc_ene0100
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0
led_class               5256  2 b43,hp_accel
ssb                    40944  1 b43
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
serio_raw               6596  0
v4l2_compat_ioctl32    13344  1 videodev
fbcon                  41344  72
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
usb_storage            66016  0
usbhid                 43968  0
i915                  247304  2
drm                   193856  2 i915
i2c_algo_bit            7076  1 i915
r8169                  38884  0
mii                     6368  1 r8169
intel_agp              32816  2 i915
video                  23612  1 i915
output                  3680  1 video
```

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:03f1 Quanta Computer, Inc.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c526 Logitech, Inc.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
 *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:12:85:10
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.197 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:5000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
```

```
eth0      Link encap:Ethernet  HWaddr 00:26:9e:12:85:10
          inet addr:192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:fe12:8510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:946764 (946.7 KB)  TX bytes:172088 (172.0 KB)
          Interrupt:30 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1240 (1.2 KB)  TX bytes:1240 (1.2 KB)

```

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:9E:12:85:10

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.197
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```

---

### Post by northd_tech on 2010-02-22
> **ren3dar said:**
> 
**lspci**
02:00.0 Network controller: **Broadcom** Corporation BCM**4312** 802.11b/g (rev 01)
03:00.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd. **RTL8101E/RTL8102E** PCI Express Fast Ethernet controller (rev 02)[/CODE]```


**lsmod**
Module                  Size  Used by                                                                                **b43 **                  136584  0                                                 
mac80211              210008  1 **b43**                                                                              cfg80211              109144  2 **b43**,mac80211                                                                [COLOR=Blue][B]
wl [/B]                  1277380  0                                                                                         
lib80211                7812  1 **wl ** [/COLOR]                                            
led_class               5256  2 **b43**,hp_accel
ssb                    40944  1 **b43**

[COLOR=DarkGreen]r8169                  38884  0
mii                     6368  1 r8169[/COLOR]

**sudo lshw -C network**
*-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=b43-pci-bridge** latency=0
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:12:85:10
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 **driverversion=2.3LK-NAPI duplex=full ip=192.168.1.197 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:5000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:26:9e:12:85:10
          inet addr:192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:fe12:8510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:946764 (946.7 KB)  TX bytes:172088 (172.0 KB)
          Interrupt:30 Base address:0x6000

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**nm-tool**
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:9E:12:85:10

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.197
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

OK- that's a Broadcom 4312 wireless which should work with either the Broadcom "STA" driver or else the older "b43" driver.

Problem is- you have both installed but there are some easy fixes for that, and they should be pretty well documented around here.

I believe that kubuntu 9.10 will need you to modify a different blacklist file than the older method that my system used, but let's see how you are configured right now under kubuntu before we make the changes.

Can you post the results of this terminal command (one of them will probably be empty set):

[CODE]cat /etc/modprobe.d/blacklist

cat /etc/modprobe.d/blacklist.conf

```edit: the blue "wl" stuff is for the "STA" driver, and the green modules are for your cabled Realtek **RTL8101E/RTL8102E** ethernet connection.

---

### Post by ren3dar on 2010-02-22
The first returns "no such file or directory"

The second returns the following:
```
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
```

what is showing that both drivers are installed?
[INDENT]*in the hardware drivers menu it lists both as neither being installed nor in use*[/INDENT]

---

### Post by northd_tech on 2010-02-22
Sorry- I was busy at work today, and then I was working on a furnace and a water heater.  It looks like I only gave you half of the terminal commands earlier that we need to look at.  If you can also post the results of:

```
cat /etc/modules

cat /etc/modules.conf
```

Only one of those should return results, but I'm not sure when the "crossover" point was for the different setups (9.10 should be the "new" way), so let's look at/for both.

The 2-driver thing is highlighted in my post #4, but we can pull up the fresh status with these 2 terminal commands:

```
lsmod | grep b43

lsmod | grep wl
```

---

### Post by ren3dar on 2010-02-22
I actually found some other issues that my laptop was having with kubuntu, and it was acting very unstable, so i decided to install ubuntu and then add plasma to gnome (plasma is the only reason i wanted kubuntu anyway)  Since i got that working im all set to go.

Thanks for the help though

---

