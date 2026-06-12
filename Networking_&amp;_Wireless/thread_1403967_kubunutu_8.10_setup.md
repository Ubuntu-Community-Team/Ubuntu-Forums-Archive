---
title: "kubunutu 8.10 setup"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by rich_montana on 2010-02-10
I have kubuntu 8.10 up and running however I am not able to get internet configured. this is on a laptop i re-purposed. I have ubuntu on a desktop that works just fine. however w/ kubuntu no such luck. i realize its just kde vs gnome and am connected to the same router and such so all should work just fine, but alas it doesn't. 

the desktop is configured using dhcp, not static IPs.

the laptop w/ kubuntu isn't recognizing eth0

>cat /etc/network/interfaces displays:

auto eth0
iface eth0 inet dhcp

(this was edited by me)

after restarting and running /etc/init.d/network restart
there is no resolv.conf... i understand dhcp should auto-create this?

furthermore running ifconfig desplays no results ?????

i could definitely appreciate some help and any and all comments would be greatly appreciated!!!

---

### Post by johnson.d on 2010-02-11
As there was no eth0 entry in the /etc/network/interfaces file you can check whether the Ethernet is recognized by the kubuntu.This can be done by using the following command

$ lshw -c network

This will list all the network devices connected to the OS.

If it is listing the ethernet adapter you can use the following command to check whether link is available for the particular adapter.

$ mii-tool

If the device is not listed then you need to install the drivers for the device.

Can you also post the output of the following command

$ lsmod

---

### Post by rich_montana on 2010-02-11
as you can see there is sorta 2 issues. 1 eth0 isnt recognized as Ethernet controller is unclaimed and that the wireless interface isnt connecting to any wireless networks. thoughts?


**rich@media-center:**~$ [COLOR=Red]lshw -c network[/COLOR]
WARNING: you should run this program as super-user.
  *-network                                        
       description: Wireless interface             
       product: Wireless WiFi Link 5100            
       vendor: Intel Corporation                   
       physical id: 0                              
       bus info: pci@0000:05:00.0                  
       logical name: wmaster0                      
       version: 00                                 
       serial: 00:22:fa:72:eb:6c                   
       width: 64 bits                              
       clock: 33MHz                                
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network UNCLAIMED                                                                                           
       description: Ethernet controller                                                                         
       product: Attansic Technology Corp.                                                                       
       vendor: Attansic Technology Corp.                                                                        
       physical id: 0                                                                                           
       bus info: pci@0000:09:00.0                                                                               
       version: c0                                                                                              
       width: 64 bits                                                                                           
       clock: 33MHz                                                                                             
       capabilities: cap_list                                                                                   
       configuration: latency=0                                                                                 
  *-network DISABLED                                                                                            
       description: Ethernet interface                                                                          
       physical id: 1                                                                                           
       logical name: pan0                                                                                       
       serial: e6:71:f8:80:a1:d8                                                                                
       capabilities: ethernet physical                                                                          
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes                  
**rich@media-center:~$ **[COLOR=Red]mii-tool                                                                                   [/COLOR]
SIOCGMIIPHY on 'eth0' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth1' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth2' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth3' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth4' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth5' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth6' failed: Operation not permitted                                                           
SIOCGMIIPHY on 'eth7' failed: Operation not permitted                                                           
no MII interfaces found                                                                                         
**rich@media-center:~$** [COLOR=Red]sudo mii-tool                                                                              [/COLOR]
[sudo] password for rich:                                                                                       
no MII interfaces found                                                                                         
**rich@media-center:~$** [COLOR=Red]lsmod                                                                                      [/COLOR]
Module                  Size  Used by                                                                           
usb_storage            81728  0                                                                                 
libusual               27156  1 usb_storage                                                                     
ipv6                  263972  10                                                                                
af_packet              25728  2                                                                                 
rfcomm                 44432  0                                                                                 
sco                    18308  2                                                                                 
bridge                 56980  0                                                                                 
stp                    10628  1 bridge                                                                          
bnep                   20480  2                                                                                 
l2cap                  30464  6 rfcomm,bnep                                                                     
bluetooth              61924  6 rfcomm,sco,bnep,l2cap                                                           
ppdev                  15620  0                                                                                 
acpi_cpufreq           15500  1                                                                                 
cpufreq_ondemand       14988  1                                                                                 
cpufreq_powersave       9856  0                                                                                 
cpufreq_userspace      11396  0                                                                                 
cpufreq_conservative    14600  0                                                                                
cpufreq_stats          13188  0                                                                                 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats                                     
pci_slot               12552  0                                                                                 
container              11520  0                                                                                 
sbs                    19464  0                                                                                 
sbshc                  13440  1 sbs                                                                             
iptable_filter         10752  0                                                                                 
ip_tables              19600  1 iptable_filter                                                                  
x_tables               22916  1 ip_tables                                                                       
parport_pc             39204  0                                                                                 
lp                     17156  0                                                                                 
parport                42604  3 ppdev,parport_pc,lp                                                             
joydev                 18368  0                                                                                 
acer_wmi               18880  0                                                                                 
arc4                    9984  2                                                                                 
ecb                    10880  2                                                                                 
crypto_blkcipher       25476  1 ecb                                                                             
uvcvideo               62728  0                                                                                 
psmouse                45200  0                                                                                 
iwlagn                 99588  0                                                                                 
pcspkr                 10624  0                                                                                 
serio_raw              13444  0                                                                                 
iwlcore                92740  1 iwlagn                                                                          
evdev                  17696  12                                                                                
compat_ioctl32          9344  1 uvcvideo                                                                        
videodev               41344  1 uvcvideo                                                                        
rfkill                 17176  2 iwlcore                                                                         
v4l1_compat            22404  2 uvcvideo,videodev                                                               
led_class              12164  2 acer_wmi,iwlcore                                                                
mac80211              216820  2 iwlagn,iwlcore                                                                  
cfg80211               32392  3 iwlagn,iwlcore,mac80211                                                         
snd_hda_intel         381488  1                                                                                 
snd_pcm_oss            46848  0                                                                                 
snd_mixer_oss          22784  1 snd_pcm_oss                                                                     
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss                                                       
snd_seq_dummy          10884  0                                                                                 
snd_seq_oss            38528  0                                                                                 
snd_seq_midi           14336  0                                                                                 
snd_rawmidi            29824  1 snd_seq_midi                                                                    
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi                                                        
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                       
snd_timer              29960  2 snd_pcm,snd_seq                                                                 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq                      
video                  25104  0                                                                                 
output                 11008  1 video                                                                           
snd                    63268  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd                                                                                                      
wmi                    14504  1 acer_wmi                                                                                                 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0
battery                18436  0
button                 14224  0
ac                     12292  0
pci_hotplug            35236  1 shpchp
intel_agp              33724  0
agpgart                42184  1 intel_agp
ext3                  133256  1
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0
sd_mod                 42264  3
sr_mod                 22212  0
hid                    50560  1 usbhid
cdrom                  43168  1 sr_mod
crc_t10dif              9984  1 sd_mod
sg                     39732  0
ahci                   37132  2
libata                177312  1 ahci
scsi_mod              155212  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0
ehci_hcd               43276  0
usbcore               148848  7 usb_storage,libusual,uvcvideo,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0
fbcon                  47648  0
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1
rich@media-center:~$

---

### Post by johnson.d on 2010-02-12
From lsmod output, I don't see MII specific module loaded.
In order to load the mii module, can you issue the follwoing command:

```
$ sudo modprobe mii
```

Also from the lsmod output, it looks like no network specific driver is loaded.
You need to install the driver module specific to your kernel.
If you already have a module present in the following path: /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko, issue:

```
$ modprobe atl.ko
```

If it is not present in the kernel modules path, then you need to compile the driver from source.
Please check the following thread about loading the required driver module for your network card
[http://ubuntuforums.org/showthread.php?t=429845](http://ubuntuforums.org/showthread.php?t=429845)
The source code for the driver is attached in the thread. Before compiling from source, you need to have the kernel headers specific to your kernel version and build-essential tools.

```
$ sudo apt-get install build-essential
```

```
$ sudo apt-get install <kernel-headers-specific-to-your-kernel-version>
```

In case if you face any issue, during loading the module (i.e., modprobe), please post the output of the following command:

```
$ dmesg
```

If you are not able to compile the driver code, please post the error log of the compilation process.

---

### Post by martin.lawrence on 2010-02-12
Hello..

I'm XP savvy but very very new to linux, installed Ubuntu and under duress of a buddy switched to Kubuntu 8.10 today. PROBLEM 1, on the 1st boot up (I have it on its own HD, no partition) it had a line that said "rejecting I/O to dead device" and a bunch of lines that says "usb 5-2 device description read/64, error -110" and "device not accepting address 6 and 7 error 110". After about 3 minutes of this it finally boots and goes to the desktop. PROBLEM 2, in the toolbar in the bottom right corner there is a globe that is black and white, I click on it (wlan 0 disconnected) and it shows my wireless connection (2WIRE153) but it says its not connected. I clicked on it and clicked "connect and save" but I still have no connection. PROBLEM 3, I copied my MP3's from XP Pro to Kubuntu and AmaroK won't play them, it says that I need to install libxine1-ffmpeg, how do I do that and where is it? Is it on the CD? How do I install it? I know how to open Konsole but what should I type in as I am not code savvy. and PROBLEM 4 how do I stop it from asking me for a password to cut the computer off? My machine... ASUS p5gc-mx motherboard Intel 1.6 mhz dual core pentium 4 gig memory D-Link DWA-552 wireless PCI card 3 Western Digital SATA hard drives AOpen DVD-RW burner Logitech wireless keyboard & mouse I use audio and video off the board.

---

### Post by rich_montana on 2010-03-09
sorry for the delayed response(personal).

anyways ive loaded mii-tool and the atl2.ko driver im fairly certain but the eth0 is still 'unclaimed' ?? ideas? i feel like im really close as i have the driver loaded ... still no internet however


                                       [COLOR=Red]**rich@media-center**[/COLOR]:/lib/modules/2.6.27-7-generic/kernel/drivers/net$ lshw -c networkWARNING: you should run this program as super-user.                                
    [LEFT]  *-network                                                                        [/LEFT]
    [LEFT]       description: Wireless interface                                             [/LEFT]
    [LEFT]       product: Wireless WiFi Link 5100                                            [/LEFT]
    [LEFT]       vendor: Intel Corporation                                                   [/LEFT]
    [LEFT]       physical id: 0                                                              [/LEFT]
    [LEFT]       bus info: pci@0000:05:00.0                                                  [/LEFT]
    [LEFT]       logical name: wmaster0                                                      [/LEFT]
    [LEFT]       version: 00                                                                 [/LEFT]
    [LEFT]       serial: 00:22:fa:72:eb:6c                                                   [/LEFT]
    [LEFT]       width: 64 bits                                                              [/LEFT]
    [LEFT]       clock: 33MHz                                                                [/LEFT]
    [LEFT]       capabilities: bus_master cap_list logical ethernet physical wireless        [/LEFT]
    [LEFT]       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn                                                                    [/LEFT]
    [LEFT]  *-network UNCLAIMED                                                                     [/LEFT]
    [LEFT]       description: Ethernet controller[/LEFT]
    [LEFT]       product: Attansic Technology Corp.[/LEFT]
    [LEFT]       vendor: Attansic Technology Corp.[/LEFT]
    [LEFT]       physical id: 0[/LEFT]
    [LEFT]       bus info: pci@0000:09:00.0[/LEFT]
    [LEFT]       version: c0[/LEFT]
    [LEFT]       width: 64 bits[/LEFT]
    [LEFT]       clock: 33MHz[/LEFT]
    [LEFT]       capabilities: cap_list[/LEFT]
    [LEFT]       configuration: latency=0[/LEFT]
    [LEFT]  *-network DISABLED[/LEFT]
    [LEFT]       description: Ethernet interface[/LEFT]
    [LEFT]       physical id: 2[/LEFT]
    [LEFT]       logical name: pan0[/LEFT]
    [LEFT]       serial: ca:9b:3e:d7:0e:85[/LEFT]
    [LEFT]       capabilities: ethernet physical[/LEFT]
    [LEFT]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/LEFT]
    [LEFT]**[COLOR=Red]rich@media-cente[/COLOR]**r:/lib/modules/2.6.27-7-generic/kernel/drivers/net$ sudo mii-tool[/LEFT]
    [LEFT]no MII interfaces found[/LEFT]
    [LEFT][COLOR=Red]**rich@media-cente**[/COLOR]r:/lib/modules/2.6.27-7-generic/kernel/drivers/net$ /sbin/modinfo atl2.ko[/LEFT]
    [LEFT]filename:       atl2.ko[/LEFT]
    [LEFT]version:        1.0.40.2[/LEFT]
    [LEFT]license:        GPL[/LEFT]
    [LEFT]description:    Attansic 100M Ethernet Network Driver[/LEFT]
    [LEFT]author:         Attansic Corporation, <xiong_huang@attansic.com>[/LEFT]
    [LEFT]srcversion:     60600F6B087D9769ABDF7E4[/LEFT]
    [LEFT]alias:          pci:v00001969d00002048sv*sd*bc*sc*i*[/LEFT]
    [LEFT]depends:[/LEFT]
    [LEFT]vermagic:       2.6.20-15-generic SMP mod_unload 586[/LEFT]
    [LEFT]parm:           TxMemSize:Bytes of Transmit Memory (array of int)[/LEFT]
    [LEFT]parm:           RxMemBlock:Number of receive memory block (array of int)[/LEFT]
    [LEFT]parm:           MediaType:MediaType Select (array of int)[/LEFT]
    [LEFT]parm:           IntModTimer:Interrupt Moderator Timer (array of int)[/LEFT]
    [LEFT]parm:           FlashVendor:SPI Flash Vendor (array of int)[/LEFT]
    [LEFT]parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)[/LEFT]
    [LEFT]**[COLOR=Red]rich@media-cente[/COLOR]**r:/lib/modules/2.6.27-7-generic/kernel/drivers/net$ lsmod | grep atl2[/LEFT]
    [LEFT]atl2                   34072  0[/LEFT]
    [LEFT]**[COLOR=Red]rich@media-center[/COLOR]**:/lib/modules/2.6.27-7-generic/kernel/drivers/net$ lsmod | grep mii[/LEFT]
    [LEFT]mii                    13440  0[/LEFT]
    [LEFT]**[COLOR=Red]rich@media-center:[/COLOR]**/lib/modules/2.6.27-7-generic/kernel/drivers/net$[/LEFT]

---

