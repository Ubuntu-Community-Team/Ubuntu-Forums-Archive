---
title: "what commands to run for help with WiFi."
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by hockeyshifter on 2008-12-20
i have been trying for 3 weeks now and searching and installing and reading all that i can trying to set up the home WiFi. i get a wired connection all the time no issues there but the wifi will not connect no mater what i do . 
all essid and other security has been disabled the drivers are installed and working but i am unable to obtain a ip address and when WICD cycles it times out then defaults back to a wired connection . when i command line lspci it see the pci card when i plug in  a usb thumber and run lsusb it see it also but nojoy will not connect...  

can any one tell me what commands to run and post so that i can try and fix this issue. please

---

### Post by LostMagix on 2008-12-20
Please list the outputs for the following commands


```
$ lsmod

$ lspci

$ iwconfig


```

And what all have you tried?

---

### Post by hockeyshifter on 2008-12-21
ok new dilemia... i have a linksys gaming wifi router. set it up throught winXP and pluged it into the nic card on my laptop. ok got Internet no issues. however i put in a trendnet tew-424ub into the usb port and what hapened is that i have a working connection throught the usb dongle. ( have installed ndiswrapper)  i am using WICD in place of the network manager installed by Gnome. 

side note if i unplug the usb adapter then reinsert it 1 min later have lost my connection until i hook back up the nic card. 

with the above post and total confusion.. can some one explain what is happening and why. Can i also get more instruction as to what settings need to be adjusted so that i can connect with out using the gaming router.

---

### Post by cdtech on 2008-12-21
As LostMagix posted above, we would need to see the outputs of:
```

dmesg | grep -e ndis -e wlan
lshw -C Network
lsmod

```

---

### Post by hockeyshifter on 2008-12-21
garth@gatetop:~$ sudo **lshw -C network **
sudo: unable to resolve host gatetop
[sudo] password for garth: 
  *-network               [C
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:83:b4:68
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: e2:16:e5:42:b7:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 00:14:d1:5a:6a:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.53+Realtek Semiconductor Corp. ip=192.168.1.200 link=yes multicast=yes wireless=IEEE 802.11g

---------------------------------------------------------------------------
**dmesg code:**

garth@gatetop:~$ dmesg | grep -e ndis -e wlan
[   33.559281] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   35.133636] ndiswrapper: driver lsrtnds (Linksys,04/10/2003,5.135.410.2003) loaded
[   35.134302] ndiswrapper 0000:06:00.0: enabling device (0000 -> 0003)
[   35.134332] ndiswrapper 0000:06:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   35.134802] ndiswrapper 0000:06:00.0: setting latency timer to 64
[   35.288634] ndiswrapper: using IRQ 10
[   35.957765] wlan0: ethernet device 00:0c:41:40:02:9b using NDIS driver: lsrtnds, version: 0x100, NDIS version: 0x500, vendor: 'Realtek RTL8180 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8180.5.conf
[   35.957822] wlan0: encryption modes supported: WEP
[   35.961387] usbcore: registered new interface driver ndiswrapper
[   35.970187] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   35.970356] udev: renamed network interface wlan0 to wlan1
[ 2839.006812] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[ 2839.080100] wlan1: no IPv6 routers present
[ 2843.901777] wlan0: ethernet device 00:14:d1:5a:6a:93 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0BDA:8189.F.conf
[ 2843.903096] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 2845.007123] wlan0: duplicate address detected!
[12919.232051] wlan1: no IPv6 routers present
[13136.044043] wlan1: no IPv6 routers present
[13314.844049] wlan1: no IPv6 routers present
[13615.416046] wlan1: no IPv6 routers present
[13919.840041] wlan1: no IPv6 routers present
[14220.644044] wlan1: no IPv6 routers present
[14515.636051] wlan1: no IPv6 routers present
[14822.508075] wlan1: no IPv6 routers present
[15120.476052] wlan1: no IPv6 routers present
[15415.584044] wlan1: no IPv6 routers present
[15716.672054] wlan1: no IPv6 routers present
[16032.308046] wlan1: no IPv6 routers present
[16101.480728] ndiswrapper: device wlan1 removed
[16101.482489] ndiswrapper 0000:06:00.0: PCI INT A disabled
-------------------------------------------------------------------
**lsmod**


Module                  Size  Used by
ipv6                  263972  8 
binfmt_misc            16904  1 
savage                 39424  2 
drm                    86056  3 savage
af_packet              25728  4 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
wmi                    14504  0 
sbs                    19464  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
joydev                 18368  0 
ndiswrapper           196380  0 
pcmcia                 43052  0 
snd_maestro3           27524  3 
snd_ac97_codec        111652  1 snd_maestro3
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
evdev                  17696  6 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_pcm                83204  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
serio_raw              13444  0 
psmouse                45200  0 
snd_seq_dummy          10884  0 
container              11520  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
button                 14224  0 
battery                18436  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ac                     12292  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
pcspkr                 10624  0 
i2c_piix4              16144  0 
intel_agp              33724  1 
snd                    63268  16 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               31892  1 i2c_piix4
soundcore              15328  1 snd
agpgart                42184  2 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
uhci_hcd               30736  0 
ata_generic            12932  0 
usbcore               148848  3 ndiswrapper,uhci_hcd
e100                   41356  0 
mii                    13440  1 e100
libata                177312  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
garth@gatetop:~$ 
--------------------------------------------------------------------------------


God i sure would like to know how to read this stuff... the amount of info displayed by these commands is mind bending... make me humble and appreicate the guys that write this stuff...:)


note this was posted with the usb dongle inplace and working no wire nic hook up

---

### Post by hockeyshifter on 2008-12-21
bump bump bump

---

### Post by hockeyshifter on 2008-12-21
don' the hustle----- don' the bump.

---

### Post by hockeyshifter on 2008-12-21
new issue.. i had to reboot and when i did i selected the current kernal but in recovery mode.. then selected normal boot from recovery screen. the boot went as normal. In stead of hooking up the game adapter i just started firefox and the pop up asked for the home network router log-in and passkey. well it worked and now have the internet. 

can any anyone give the command line code to check the connection and configuration set up. BTW. WICD dose not show the connection but is working. 

thanks and 
Happy Holidays.

---

### Post by cdtech on 2008-12-22
```

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4660 (4.6 KB)  TX bytes:4660 (4.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:b5:7e:d1  
          inet addr:192.168.1.211  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17096791 (17.0 MB)  TX bytes:2618136 (2.6 MB)
          Interrupt:19 Memory:f6000000-f6004000
```
And for your routing table:
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```
Also check your "/etc/network/interfaces" file for configuration settings.

---

### Post by kevdog on 2008-12-22
Check the guide about Manual Command Use in My Signature.  That will give you a good walk through of the commands used to connect to wifi.

---

### Post by hockeyshifter on 2008-12-23
to cdtech and kevdog... thanks will run with it

---

### Post by hockeyshifter on 2008-12-25
kevdog.. i read your tutorial and followed it. the info was geat.. but what i do not understand why did it just work all of a sudden and now its working every time i power up and down the OS. i have screen shots of before when the WiFI was not working and can now look to find changes.

but Why i must know i must feel the force or be corrupted by the windows side... twisted and dysfunctional..

---

