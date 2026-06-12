---
title: "No wireless connection after upgrade to 10.04"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by poisoneggs on 2010-05-05
NOTE: My upgrade wasn't smooth. Now everything is extremely slow. However if I boot from the disc to try without installing, the connection problem is still there.

There is an exclamation mark on the connection applet, right clicking shows that Enable Wireless is unchecked and unclickable.

I've included outputs of common network commands which might prove to be useful.

```
[~] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:60:f0:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4432 (4.4 KB)  TX bytes:4432 (4.4 KB)
```
```
[~] iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.
```
```
[~] lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```
```
[~] lsmod | grep rtl
rtl8187                50680  0 
mac80211              204922  1 rtl8187
led_class               2864  1 rtl8187
cfg80211              126485  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
```

I should mention that the wireless connectivity has been working flawlessly before the upgrade.

Thanks

---

### Post by GSF1200S on 2010-05-05
In your lspci output, I dont even SEE your wireless card. I see your ethernet card:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```
This poster has the SAME ethernet card as you (different revision though), but he also has a wireless adapter listed directly below.
[http://ubuntuforums.org/showthread.php?t=1472795]("http://ubuntuforums.org/showthread.php?t=1472795")

It would help for us to know what kind of wireless card it is. If you give us the computer model (what kind of computer is it?), we might be able to figure out what wireless chipset it uses and why it isnt listed. That seems very odd to me, as lspci usually never fails in this respect. Please run the following commands as a precaution to your failed upgrade. It might fix the slowness, and perhaps after a reboot your wireless card will work, or at least show in lspci:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade
sudo depmod -a
```
Please save the terminal output in a text file so you can post the results here after you reboot and try it out. Hopefully someone else will chime in with some ideas..

---

### Post by poisoneggs on 2010-05-05
Hmm I don't really know... the laptop is a Toshiba Satellite Pro L300.

I have made a karmic partition, where I am replying from. Bearing in mind that I have a wireless connection, this is the lspci output from Karmic

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

I cannot run the commands you offered, since I have no internet connection.

EDIT: Could that Realtek card do ethernet and wireless? this is the output of lshw -C net:
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:60:f0:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:12:61:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg
```

---

### Post by eltonw on 2010-05-05
> **poisoneggs said:**
> Hmm I don't really know... the laptop is a Toshiba Satellite Pro L300.

I have made a karmic partition, where I am replying from. Bearing in mind that I have a wireless connection, this is the lspci output from Karmic

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

I cannot run the commands you offered, since I have no internet connection.

EDIT: Could that Realtek card do ethernet and wireless? this is the output of lshw -C net:
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:60:f0:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:12:61:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg
```

Perhaps this would be of help? SEE:[http://ubuntuforums.org/showthread.php?t=1473629]("http://ubuntuforums.org/showthread.php?t=1473629")

---

### Post by poisoneggs on 2010-05-05
> **eltonw said:**
> Perhaps this would be of help? SEE:[http://ubuntuforums.org/showthread.php?t=1473629]("http://ubuntuforums.org/showthread.php?t=1473629")

Thanks. I tried the new kernel, didn't work.
I also tried making a clean install of Lucid on the partition I made for Karmic. It was very smooth, like it should be, but still no wireless adapter.

---

### Post by GSF1200S on 2010-05-05
Man, I wish you would have posted the results of lsmod from Karmic :( Does anyone in this forum know how to tell what devices are using what modules? 

If we can find out what package you used on Karmic where it worked, we should be able to just grab that deb. I suppose that realtek could be both. I hope someone comes along with additional information.

If you end up installing Karmic again, please post the entire results of:
```
lsmod
```
here.

If you havent done so already, I would post a bug report:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by poisoneggs on 2010-05-06
I installed Karmic again, else I didn't have an internet connection. Here is the output for lsmod:

```
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
arc4                    1660  2 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ecb                     2524  2 
lp                      8964  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
rtl8187                50624  0 
mac80211              181236  1 rtl8187
led_class               4096  1 rtl8187
parport                35340  2 ppdev,lp
serio_raw               5280  0 
joydev                 10272  0 
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
```

---

### Post by poisoneggs on 2010-05-06
Oh man!! I feel so stupid. To think I doubted the amazing Ubuntu team for a second..

This is what happened. My Karmic installation didn't recognise the manual wireless switch on the laptop.. so I kept it off. Lucid went and fixed that, so I simply had it off!!

I am so sorry about this, thanks everyone so much for your help.

---

### Post by GSF1200S on 2010-05-06
> **poisoneggs said:**
> Oh man!! I feel so stupid. To think I doubted the amazing Ubuntu team for a second..

This is what happened. My Karmic installation didn't recognise the manual wireless switch on the laptop.. so I kept it off. Lucid went and fixed that, so I simply had it off!!

I am so sorry about this, thanks everyone so much for your help.

You must be kidding me.. Oh man :lolflag: Happens man- we all do something like that... let me know if it gives you issues..

---

