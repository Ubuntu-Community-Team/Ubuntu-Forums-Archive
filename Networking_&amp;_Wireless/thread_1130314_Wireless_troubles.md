---
title: "Wireless troubles"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by pyrofoam on 2009-04-19
I recently installed ubuntu for the first time and I'm having quite a bit of trouble getting an internet connection.  For some reason it wont even pick up the signal from my router.  I am using a linksys pci adaptor with broadcom corp. BCM4318 [AirForce One 54g] 802.11g wireless LAN controller chipset.  Any help is greatly appreciated.

---

### Post by pyrofoam on 2009-04-19
adding info:

pyrofoam@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:01:c5:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12068 (12.0 KB)  TX bytes:12068 (12.0 KB)

pyrofoam@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


pyrofoam@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  263972  22 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
bridge                 56980  0 
rfcomm                 44432  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
psmouse                45200  0 
dcdbas                 15008  0 
serio_raw              13444  0 
pcspkr                 10624  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_usb_audio          89728  2 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
evdev                  17696  16 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
xpad                   18440  0 
snd_mixer_oss          22784  1 snd_pcm_oss
led_class              12164  1 xpad
ff_memless             13320  1 xpad
snd_pcm                83204  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  21 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 drm,intel_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
usb_storage            81728  1 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
libusual               27156  1 usb_storage
ahci                   37132  1 
libata                177312  1 ahci
scsi_mod              155212  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ssb                    40580  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
e1000e                112680  0 
usbcore               148848  9 snd_usb_audio,snd_usb_lib,xpad,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 


pyrofoam@ubuntu:~$ sudo lshw -C network
[sudo] password for pyrofoam: 
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:01:c5:47
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-0 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:0f:5e:59:12:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


pyrofoam@ubuntu:~$ uname -mr
2.6.27-7-generic i686

---

### Post by coffeeaddict22 on 2009-04-19
Hi,
You've got a driver loaded, so it should be OK.  
Try ```
sudo iwlist scan
``` and see what the output is.  If you can see your network, and the signal is OK, it may well be an encryptation problem.  Have you got any encryptation on the network?  Can you turn it off for a bit to check if you can pick up an unencrypted network?

---

### Post by pyrofoam on 2009-04-19
```
pyrofoam@ubuntu:~$ sudo iwlist scan
[sudo] password for pyrofoam: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

Also, i unencrypted my network but there was still no signal being picked up.

---

### Post by RedSingularity on 2009-04-19
Type "lspci" in terminal and post output.

---

### Post by pyrofoam on 2009-04-19
**lspci**
```
pyrofoam@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)
04:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by coffeeaddict22 on 2009-04-19
Hmmm... I lied.  The wireless network driver- looks like b43-pci-bridge - isn't being loaded looking through lsmod.  Googling, looks like Ubuntu 8.04 did OK with your card, and the driver was on the CD.  So what does lspci (or ```
lspci |grep -i Broadcom
``` for brevity) return?

---

### Post by RedSingularity on 2009-04-19
Have you installed drivers with NDISwrapper?

---

### Post by pyrofoam on 2009-04-19
i tried to, but the instructions i was using were sort of vague so im not sure if it was successful, but didnt the other guy above you say i had a driver installed already?

---

### Post by RedSingularity on 2009-04-19
Well he said he lied......

> **coffeeaddict22 said:**
> Hmmm... I lied.


You should probably get those drivers installed via NDISwrapper.  Try using this fruitcakes guide located [HERE](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/)

Let us know if you have any difficulty.

---

### Post by pyrofoam on 2009-04-19
sorry thats my bad, i guess i didnt see his second post, ill try the guide and post results.

---

### Post by pyrofoam on 2009-04-19
i followed that guide and it still wont recognize that there is a wireless signal, but i did get this far at least.

```
pyrofoam@ubuntu:~$ ndiswrapper -l
WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with '-e'
bcmwl5a : driver installed
	device (14E4:4318) present (alternate driver: ssb)

```

---

### Post by pyrofoam on 2009-04-21
**lspci | grep -i Broadcom**
```
pyrofoam@ubuntu:~$ lspci | grep -i Broadcom
04:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by RedSingularity on 2009-04-21
In terminal type sudo apt-get install ndisgtk.

That is the graphical interface for ndiswrapper.

Then in terminal type ndisgtk.

---

### Post by pyrofoam on 2009-04-23
when i used ndisgtk before and now, it first pops up with an - unable to see if hardware is present.  Then on the main screen of ndisgtk, there is the driver bcmwl5a - hardware present:yes

---

### Post by pyrofoam on 2009-04-25
anyone else have an i dea of what to do?  Would upgrading to 9.04 help or hurt this situation?  Any help is appreciated.

---

### Post by SeePU on 2009-04-25
Is 'b43-fwcutter' installed?

Look it up in the repositories.

I think you need it if you don't use ndiswrapper.

---

### Post by coffeeaddict22 on 2009-04-26
It might be worth upgrading to 9.04, although you'd be best to run it off a live CD to start with; you'll be able to test the network card off that without changing your setup irreversibly.  Networking with wireless has got a lot more ironed out over the last year, so you may well get good results.  I've got a Broadcom 4322 that took a couple of days of messing with on 8.04, and "just works" now (on the 64bit version of 9.04).

It sounds like your problem is possibly that you're running at least two drivers.  Once again, my apology for misreading your lsmod; on that list you had no wireless drivers
There's a good wiki page for wireless: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")
that steps you through it.  
Having said that, it should be possible to get the card you've got working if you don't want to upgrade that way.  At the moment I'm not sure what drivers you have and haven't got running.  try ```
sudo lshw -C network 
``` again.  Mine comes out with:
```
 description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:bb:0c:55
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.2.4 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

```
The bottom line- configuration- lists the driver; in my case it's wl0.  Yours should have ndiswrapper, with the module being the driver you've loaded into it.

Have you looked in System/Administration/Hardware Drivers?  The proprietary drivers are kept in there and not enabled automatically, so it might be as simple as activating that.

---

### Post by pyrofoam on 2009-05-03
Hey, i havent really ahd a chance to wrok on this due to school lately, but i've upgraded to 9.04 now and i think im close to getting my signal, im just unsure what to do still.  

```
sudo lshw -C network
```

```
*-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:01:c5:47
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-0 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:85:21:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:15:11:e0:3f:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Also here is my iwconfig, before i was getting no wireless extensions on wlan0 too, so i hope this is a good sign.

```
greg@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

