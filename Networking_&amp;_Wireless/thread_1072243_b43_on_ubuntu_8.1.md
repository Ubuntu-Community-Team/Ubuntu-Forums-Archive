---
title: "b43 on ubuntu 8.1"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by lorcanf on 2009-02-17
Hi, 
can't get my broadcom wireless card to work after installing ubuntu 8.1. 
In System>Administration>Hardware Drivers I have two options: Broadcom B43 Wireless driver, which it says is activated and in use. And also Broadcom Sta Wireless Driver which is not activated. when i try to activate the broadcom sta driver it says i need a reboot and then is once again inactive. If I click on the networking icon it says "wireless is disabled". thanks,
Lorcan

here is some of the details on the computer from lshw, iwconfig, lsmod, iwlist:

 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:16:72:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.2 latency=64 module=ssb multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:67:7a:6a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:e4:5e:c4:0d:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

lorcan@lorcan-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

lorcan@lorcan-laptop:~$ lsmod
Module                  Size  Used by
isofs                  40100  0 
udf                    88356  0 
crc_itu_t              10112  1 udf
usbhid                 35840  0 
hid                    50560  1 usbhid
ipv6                  263972  10 
af_packet              25728  2 
rfkill_input           12672  0 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ndiswrapper           196380  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
b43                   131356  0 
serio_raw              13444  0 
rfkill                 17176  3 rfkill_input,b43
snd_hda_intel         384176  3 
dcdbas                 15008  0 
evdev                  17696  15 
mac80211              216820  1 b43
psmouse                45200  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
cfg80211               32392  1 mac80211
pcspkr                 10624  0 
led_class              12164  1 b43
snd_seq_dummy          10884  0 
input_polldev          11912  1 b43
snd_seq_oss            38528  0 
video                  25232  0 
fglrx                1813960  30 
output                 11008  1 video
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
mmc_core               58268  1 sdhci
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ricoh_mmc              11904  0 
battery                18436  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                     12292  0 
soundcore              15328  1 snd
button                 14224  0 
iTCO_wdt               18596  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
agpgart                42184  2 fglrx,intel_agp
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
ata_piix               24580  2 
ohci1394               37936  0 
libata                178208  3 ata_generic,pata_acpi,ata_piix
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
b44                    35984  0 
ieee1394               96324  2 sbp2,ohci1394
mii                    13440  1 b44
ehci_hcd               43788  0 
uhci_hcd               30736  0 
ssb                    40580  2 b43,b44
usbcore               149360  5 usbhid,ndiswrapper,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


lorcan@lorcan-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation

---

### Post by Ayuthia on 2009-02-17
Try the following in the Terminal and see if it works.  If it does, we can then make it permanent:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```

These commands will remove the possible conflicting modules, load the necessary modules back, restart the cards, and scan for wireless sites.  The wl module is the Broadcom STA module and the b44 is your wired ethernet card module.  We had to unload the b44 module because the ssb module (that b44 needs) conflicts with the wl module so it has to be loaded after the wl module.  

Hope that helps.

---

### Post by lorcanf on 2009-02-17
Hi, 
thanks for that. Unfortunately it didn't work, but it may have got to the crux of the problem with this blacklist on line 48. any tips on how to fix that?
here's the output from the terminal, thanks again. 
Lorcan

lorcan@lorcan-laptop:~$ sudo modprobe -r b43 b44 ssb wl
[sudo] password for lorcan: 
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with '-e'
lorcan@lorcan-laptop:~$ sudo modprobe wl
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with '-e'
lorcan@lorcan-laptop:~$ sudo modprobe b44
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with '-e'
lorcan@lorcan-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]
lorcan@lorcan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

eth0      Interface doesn't support scanning.

---

### Post by superprash2003 on 2009-02-17
something is wrong with your interfaces file.. type **sudo gedit /etc/network/interfaces** and post contents of that file..

---

### Post by lorcanf on 2009-02-17
Thanks for that, here's the post:
 
-e auto lo
iface lo inet loopback

---

### Post by Ayuthia on 2009-02-17
You can edit the file:
```
gksu gedit /etc/modprobe.d/blacklist
```
It looks like there are some additional changes in /etc/network/interfaces.  After you fix the blacklist file, you might try:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo ifconfig eth0 up
sudo ifconfig eth1 up
sudo iwlist scan

```

Hopefully you will see some wireless sites, but there have been problems with NetworkManager too that might prevent it from working.

---

### Post by lorcanf on 2009-02-17
hi, thanks for that, 
I'm not sure how to edit that file or how it should be changed, thanks

---

### Post by Ayuthia on 2009-02-17
> **lorcanf said:**
> hi, thanks for that, 
I'm not sure how to edit that file or how it should be changed, thanks

You just need to remove the -e out of the file:
```
gksu gedit /etc/network/interfaces
```

---

### Post by lorcanf on 2009-02-17
Hi thanks for that
I removed the -e in both the blacklist file, and the interface file. 
the commands you gave earlier are working now without a warning line coming up. however the iwlist scan doesn't give anything, and wireless is still disabled if I click on the network icon. 
any more tips? thanks again, 
Lorcan

lorcan@lorcan-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
lorcan@lorcan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

eth0      Interface doesn't support scanning.

---

### Post by superprash2003 on 2009-02-18
is eth1 in roaming mode??and the following lines to the /etc/network/interfaces file

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

---

### Post by lorcanf on 2009-02-18
thanks for that, 
I added those lines to the interface file. It now reads
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

And I ran through this procedure again
lorcan@lorcan-laptop:~$ sudo modprobe -r b43 b44 ssb wl
lorcan@lorcan-laptop:~$ sudo modprobe wl
lorcan@lorcan-laptop:~$ sudo modprobe b44
lorcan@lorcan-laptop:~$ sudo ifconfig eth0 up
lorcan@lorcan-laptop:~$ sudo ifconfig eth1 up
lorcan@lorcan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

eth0      Interface doesn't support scanning.

I'm not sure how to switch eth1 to roaming mode. networking icon still says wireless is disabled. 
thanks, 
Lorcan

---

### Post by lorcanf on 2009-02-18
hi, 
i just installed some updates and now the network connections icon gives different options. It gives the option 
"Wireless Network (Dell BCM4311 802.11b/g WLAN
Wireless is disabled"

the option is faded out and can't be clicked on. 
all the information comes up in duplicate.  
thanks
LF

---

### Post by danmarycap on 2009-02-18
Help!  I followed the various steps described here and now have no network devices...clicking on the icon in the top panel yields greyed-out:
 Wired Network
 device is unmanaged
 Wireless Networks
 device is unmanaged

I've pasted the text from my Terminal session below.  I hope somebody can help me get the network card back.
-Dan

~$ sudo ifconfig
 
eth0      Link encap:Ethernet  HWaddr 00:21:70:d1:05:e6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:234881010 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:46:82:55  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:11
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


~$ sudo gedit /etc/network/interfaces

>>>>added these lines in the file:

>>>>auto eth0
>>>>iface eth0 inet dhcp

>>>>auto eth1
>>>>iface eth1 inet dhcp 


~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...   
    Ignoring unknown interface eth0=eth0. [ OK ]

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
           Cell 04 - Address: 00:E0:98:F9:F7:37
                    ESSID:"CappaNet"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:5/5  Signal level:-43 dBm  Noise level:-18 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
 
~$ sudo modprobe -r b43 b44 ssb wl
~$ sudo modprobe wl
~$ sudo modprobe b44
~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...    [ OK ] 

~$ sudo modprobe -r b43 b44 ssb wl
~$ sudo modprobe wl
~$ sudo modprobe b44
~$ sudo ifconfig eth0 up
~$ sudo ifconfig eth1 up
~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 07 - Address: 00:E0:98:F9:F7:37
                    ESSID:"CappaNet"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:5/5  Signal level:-32 dBm  Noise level:-88 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

 
~$ gksu gedit /etc/network/interfaces

>>>>Panicked and deleted these lines in the file:

>>>>auto eth0
>>>>iface eth0 inet dhcp

>>>>auto eth1
>>>>iface eth1 inet dhcp 


~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:d1:05:e6
Sending on   LPF/eth0/00:21:70:d1:05:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:23:08:46:82:55
Sending on   LPF/eth1/00:23:08:46:82:55
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by lorcanf on 2009-02-19
I've had the same experience, upon reboot mine now says 
wired network 
device is unmanaged
wireless network
wireless is disabled

any tips

---

### Post by superprash2003 on 2009-02-19
arent you able to right click on the networking icon and click on "ENable networking"
try enabling the STA driver and disabling the B43 driver in system->admin->hardware drivers..

---

### Post by danmarycap on 2009-02-19
right click network icon -- network is enabled.  left click -- wired and wireless greyed out with "device is unmanaged" under each.

check hardware drivers -- B43 does not show up; only the STA -- even after doing the "sudo modprobe -r b43 b44 ssb wl" thing.

I'm thinking clean install of 8.10 unless anyone has any thoughts.

-Dan

---

### Post by lorcanf on 2009-02-20
is there no other way out of this, would rather not reinstall,
Thanks

---

### Post by sKAApGIF on 2009-03-13
If anyone else has a greyed out or unmanaged device in Network Manager its simply because you added the configuration to /etc/network/interfaces.  Network manager looks there and if there is configuration data it leaves the device alone.  If there is no configuration Network Manager will configure (¨manage¨) the device for you.

TO FIX:
remove the added lines from /etc/network/interfaces so all thats left is:
```

auto lo
iface lo inet loopback

```

Restart your computer and Network Manager will allow you to use your devices again ;)

---

