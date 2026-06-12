---
title: "No wifi on battery power"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by hermannelson on 2010-11-18
Hello,

I have no Wifi on Battery Power?

My wifi quits when power cord is  pulled? I plug in  the  power cord and wifi works again?

Dell XPS 16   1645  Ubuntu 10.10

Much appreciated for a link to solve the problem or  instructions.

Thanks,

Herman.

---

### Post by grahammechanical on 2010-11-19
I would examine the power saving settings both in the Operating System and in the Bios. What does the machine's user guide say about wireless networking? Is there a key press that you have to press to activate the wireless device. The more power a portable machine uses the shorter the battery life. It makes sense to give the user some control over the use of wireless so that battery power is not used when the machine is not connected to a wireless network.

Regards.

---

### Post by hermannelson on 2010-11-19
Thanks for the reply,

I have tried all that, and no joy. Actually when on battery, I do remain connected, but no Internet????



Carl

---

### Post by xarxiusxiii on 2010-12-03
Try running "sudo iwconfig wlan0 power off" (replace wlan0 with the name of your wireless connection - could be eth1). Make sure you run this when your laptop is unplugged. If that works, try doing what I suggested [here]("http://ubuntuforums.org/showpost.php?p=10193828&postcount=18") to disable the wifi power management.

---

### Post by hermannelson on 2010-12-03
Hello Xarxiusxiii

Thanks  for your  input. I tried your command:

IEEE 802.11  ESSID:"augustine"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:D1:DE:66:3A   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-29 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

  
 but no joy,I show connected, but no internet????

However, in a cyber cafe, I did work on battery?? But  when I am on battery my  whole computer will freeze up in a matter of minutes. Could this be related?

I appreciate your try,

Herman

---

### Post by northd_tech on 2010-12-03
Hi Herman,

If you have verified that this is NOT a power management problem (which I suspect from what you describe), there might be something peculiar with your specific WiFi chipset.  Will you post the output when running the following commands in a terminal? 

```
lspci 
sudo lshw -C network
lsmod
lsusb
ndiswrapper -l
ifconfig
iwconfig

ping www.ucla.edu

```**NOTE:  You will need to press CTRL-C in the terminal window to kill that "ping" command above.**

There might be some helpful threads around the forum about your particular WiFi interface (maybe there is a power management module that is missing or corrupted or something similar).

Also, I have heard that it sometimes helps to use the laptop's switch or key combination to turn off the wireless and then turn it back on to force a "hardware reset" of sorts.  

I'm assuming that your WiFi just goes dead when unplugging the AC power, either with or without restarting the computer (if your battery is healthy enough to restart and log in completely), but this might be worth testing out too.

Edit:  There might be a power problem with that particular laptop, too (from a quick internet search):

> DELL Studio XPS 16 1645 i7 power problem

Dell is finally listening, they are replacing the 90 watt charger with a 130 watt slim charger with a promise of a BIOS fix version A07 that is promised to fix the problem.
 Will update upon the testing of the BIOS.
 here is how to place a replacement request in USA and Canada
 [http://en.community.dell.com/forums/t/19320784.aspx](http://en.community.dell.com/forums/t/19320784.aspx)
...

[http://en.community.dell.com/support-forums/laptop/f/3518/t/19306277.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/t/19306277.aspx)

---

### Post by hermannelson on 2010-12-05
Hello northd_tech,

Thanks for your tiips.

I looked at yoru posts for Dell and it's community. My conputer does not have the over heating or throttleing problems. It was built over 6 months from this problem> I did update the bios while there.

The windows side runs perfect, that is a perfect as windows can get.

Heree are some read outs.

carl@carl-Studio-XPS-1645:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
09:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
09:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
09:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
09:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
0b:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
carl@carl-Studio-XPS-1645:~$ 



carl@carl-Studio-XPS-1645:~$ sudo lshw -C network
[sudo] password for carl: 
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: c4:46:19:05:a5:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.64 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0900000-f0903fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 10
       serial: b8:ac:6f:74:81:9e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:f0d00000-f0d0ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
carl@carl-Studio-XPS-1645:~$ 



carl@carl-Studio-XPS-1645:~$ lsmod
Module                  Size  Used by
fglrx                2566382  166 
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792888  2 vboxnetadp,vboxnetflt
joydev                 11363  0 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_idt      64667  1 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               62379  0 
snd_hwdep               6660  1 snd_hda_codec
lib80211_crypt_tkip     8732  0 
videodev               49359  1 uvcvideo
i7core_edac            18090  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
wl                   1965231  0 
video                  22176  0 
output                  2527  1 video
dell_laptop             6722  0 
psmouse                62080  0 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
snd_timer              23850  2 snd_seq,snd_pcm
dell_wmi                3372  0 
dcdbas                  6910  1 dell_laptop
serio_raw               4910  0 
snd                    64117  13 snd_hda_codec_idt,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
edac_core              46822  1 i7core_edac
lib80211                6175  2 lib80211_crypt_tkip,wl
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
firewire_ohci          24679  0 
sdhci_pci               7765  0 
ahci                   21857  0 
tg3                   135768  0 
libahci                26199  4 ahci
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
carl@carl-Studio-XPS-1645:~$ 


carl@carl-Studio-XPS-1645:~$ lsusb
Bus 002 Device 006: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 002 Device 005: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:640f Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carl@carl-Studio-XPS-1645:~$ 



carl@carl-Studio-XPS-1645:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common                                                                            ==+++++++++++++++++++++++++++++++++++++++++++++++++
carl@carl-Studio-XPS-1645:~$                                                                                                Will run the:   sudo apt-get install ndiswrapper-common   
                                                                                                                                                 ++++++++++++++++++++++++++++++++++++++++++++


                                                                                                                                                       and report below.

carl@carl-Studio-XPS-1645:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:74:81:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr c4:46:19:05:a5:71  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe05:a571/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1459 errors:0 dropped:0 overruns:0 frame:51948
          TX packets:1566 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:986476 (986.4 KB)  TX bytes:347202 (347.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1590 (1.5 KB)  TX bytes:1590 (1.5 KB)

carl@carl-Studio-XPS-1645:~$ 



carl@carl-Studio-XPS-1645:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:241  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

carl@carl-Studio-XPS-1645:~$ ping [www.ucla.edu](www.ucla.edu)
PING [www.ucla.edu](www.ucla.edu) (169.232.56.224) 56(84) bytes of data.
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=1 ttl=48 time=46.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=2 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=3 ttl=48 time=44.7 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=4 ttl=48 time=44.5 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=5 ttl=48 time=44.7 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=6 ttl=48 time=44.0 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=7 ttl=48 time=45.1 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=8 ttl=48 time=51.5 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=9 ttl=48 time=44.8 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=10 ttl=48 time=44.1 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=11 ttl=48 time=44.5 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=12 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=13 ttl=48 time=44.7 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=14 ttl=48 time=44.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=15 ttl=48 time=44.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=16 ttl=48 time=44.7 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=17 ttl=48 time=45.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=18 ttl=48 time=358 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=19 ttl=48 time=44.9 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=20 ttl=48 time=8367 ms++++++++++++++++++++++++++++++++++++++++++++
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=21 ttl=48 time=7365 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=22 ttl=48 time=6365 ms  somewhere here I pulled the battery for about 5 - seconds.
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=23 ttl=48 time=5366 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=24 ttl=48 time=4366 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=25 ttl=48 time=3366 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=26 ttl=48 time=2366 ms+++++++++++++++++++++++++++++++++++++++++++++++++
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=27 ttl=48 time=1367 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=28 ttl=48 time=367 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=29 ttl=48 time=45.0 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=30 ttl=48 time=44.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=31 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=32 ttl=48 time=44.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=33 ttl=48 time=44.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=34 ttl=48 time=44.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=35 ttl=48 time=45.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=36 ttl=48 time=45.1 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=37 ttl=48 time=44.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=38 ttl=48 time=43.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=39 ttl=48 time=44.9 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=40 ttl=48 time=44.8 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=41 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=42 ttl=48 time=44.6 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=43 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=44 ttl=48 time=44.8 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=45 ttl=48 time=44.8 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=46 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=47 ttl=48 time=44.9 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=48 ttl=48 time=44.5 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=49 ttl=48 time=44.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=50 ttl=48 time=44.3 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=51 ttl=48 time=46.7 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=52 ttl=48 time=46.0 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=53 ttl=48 time=44.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=54 ttl=48 time=45.1 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=55 ttl=48 time=54.4 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=56 ttl=48 time=44.7 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=57 ttl=48 time=46.5 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=58 ttl=48 time=44.9 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=59 ttl=48 time=46.5 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=60 ttl=48 time=44.9 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=61 ttl=48 time=45.1 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=62 ttl=48 time=45.2 ms
64 bytes from [www.ucla.edu](www.ucla.edu) (169.232.56.224): icmp_req=63 ttl=48 time=44.8 ms
^C


carl@carl-Studio-XPS-1645:~$ sudo apt-get install ndiswrapper-common       
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.6kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main ndiswrapper-common all 1.56-3 [21.6kB]
Fetched 21.6kB in 0s (25.2kB/s)           
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 177865 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.56-3_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.56-3) ...
carl@carl-Studio-XPS-1645:~$ 


After the above instilation and reboot, no change.
All data above is with the power cord plugged in, except the ping where the power cord was pulled for about 5 - 10 sec.

Thanks again Herman            [ carl ]

---

### Post by northd_tech on 2010-12-05
> **hermannelson said:**
> ** lspci **
05:00.0 Network controller: [COLOR=Red]**Broadcom** Corporation BCM**4313** 802.11b/g LP-PHY (rev 01)[/COLOR]
0b:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

**sudo lshw -C network**
  *-network               
       description: Wireless interface
       product:[COLOR=Red] BCM4313[/COLOR] 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: [COLOR=Red]eth1[/COLOR]
       version: 01
       serial: c4:46:19:05:a5:71
       width:[COLOR=Red] 64 bits[/COLOR]
       clock: 33MHz
       capabilities:[COLOR=Red] pm[/COLOR] msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: **broadcast=yes** [COLOR=Red]driver=wl0[/COLOR] [COLOR=Red]driverversion=5.60.48.36[/COLOR] ip=192.168.1.64 **latency=0** multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0900000-f0903fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 10
       serial: b8:ac:6f:74:81:9e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:f0d00000-f0d0ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  [B]
lsmod[/B]
Module                  Size  Used by
[COLOR=Red]lib80211_crypt_tkip     8732  0 [/COLOR]
[COLOR=Red]**wl**                   1965231  0 
lib80211                6175  2 lib80211_crypt_tkip,**wl**[/COLOR]

**  lsusb**
[B]
  ndiswrapper -l[/B]
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common                                                                            ==+++++++++++++++++++++++++++++++++++++++++++++++++
carl@carl-Studio-XPS-1645:~$                                                                                                Will run the:   sudo apt-get install ndiswrapper-common   
                                                                                                                                                 ++++++++++++++++++++++++++++++++++++++++++++

**ifconfig**
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:74:81:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

[COLOR=Red]eth1      Link encap:Ethernet  HWaddr c4:46:19:05:a5:71  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe05:a571/64 Scope:Link
          **UP BROADCAST** RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1459 errors:0 dropped:0 overruns:0 frame:51948
          **TX packets:1566 errors:11** dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:986476 (986.4 KB)  TX bytes:347202 (347.2 KB)**
          Interrupt:17 [/COLOR]
[B]
  iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR=Red]eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:241  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0[/COLOR]

vboxnet0  no wireless extensions.

*[COLOR=Green]  sudo apt-get install ndiswrapper-common       [/COLOR]*
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.6kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main ndiswrapper-common all 1.56-3 [21.6kB]
Fetched 21.6kB in 0s (25.2kB/s)           
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 177865 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.56-3_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.56-3) ...

Hi Carl- I highlighted the wireless-specific output above in [COLOR=Red]red[/COLOR], and it looks like you have a Broadcom 4313 wireless interface.  That "[COLOR=Red]**wl**[/COLOR]" should be the proprietary "Broadcom STA wireless driver" module.  It should show as "Active" (with the green LED-like icon "lit") when you go into System > Administration > Hardware Drivers.

You appear to have the proper modules already loaded into the Linux kernel.  I'm using a[COLOR=Blue] working Broadcom "STA" 4321AG wireless in my laptop[/COLOR] to type this, and it also currently shows these same modules and is also called "eth1":

> 
**lsmod **
[COLOR=Blue]**wl **                  1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
lib80211_crypt_tkip     8676  0 [/COLOR]

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR=Blue]eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:218  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0[/COLOR]
I see something interesting in that **ping** command, but I'll quote that in another post later to keep this thread shorter.  You really did not need to install [COLOR=Green]ndiswrapper[/COLOR] yet (the [COLOR=Green]green [/COLOR]command above), but it really shouldn't hurt anything yet either- I was just curious whether it was installed or not.  We can always uninstall it later, too.

I've seen a few issues with the Broadcom 4313 lately- I don't know if Broadcom made some minor changes or if it is something in the Ubuntu 10.xx kernels, but several other people have also had similar trouble.

Does your "STA" driver currently show "Active" under System > Administration > Hardware Drivers?  Can you also post the output from the following terminal commands, just to make sure what version of Linux you are running:

> uname -a
lsb_release -d
Edit:  I just disconnected my AC power to see whether I have a similar problem- so if I take a while to respond- that is probably why.

---

### Post by hermannelson on 2010-12-05
Hello Northd_tech

Thanks again for looking at my post.

Yes, I have the green button on the STA driver, and I did install the driver modules , all with no change.



carl@carl-Studio-XPS-1645:~$ uname -a
Linux carl-Studio-XPS-1645 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux
carl@carl-Studio-XPS-1645:~$ 



carl@carl-Studio-XPS-1645:~$ lsb_release -d 
Description:	Ubuntu 10.10
carl@carl-Studio-XPS-1645:~$ 



Herman  [ Carl ]

---

### Post by northd_tech on 2010-12-05
Hi again Carl,

Yours is a 64 bit Ubuntu 10.10 "Meerkat" version.  Let's try the fix found here for a 64-bit Ubuntu 10.04 "Lucid Lynx" version, also with Broadcom 4313 wireless:

[http://ubuntuforums.org/showthread.php?t=1562076](http://ubuntuforums.org/showthread.php?t=1562076)

Enter the following terminal command and then restart and see if your connection speed/stability is any better (you might need to re-"Activate" the STA driver under Sytem > Admin > Hardware Drivers after the restart though):

```
sudo apt-get --reinstall install bcmwl-kernel-source
```If the above doesn't help, we will probably want to look at "b43" Broadcom driver solutions instead of "STA" driver for that 4313- that has been a common problem lately.

Edit:  I also ran my battery down to 51% last night with no AC power, and the STA driver didn't disconnect or slow down one single time for my Broadcom 4328 wireless- this took about 2 hours I would say.

---

### Post by hermannelson on 2010-12-06
I did the reinstall, but no joy.

Also, I have an excellent connection except with when on battery. So, I am sure the driver is working ok.

Thanks again,

Herman.

---

### Post by hermannelson on 2010-12-07
[Hello northd_tech]("http://ubuntuforums.org/member.php?u=938429")

I tried the reinstall and no joy. Also your link of for a troubled connection. My connection is perfect................ with the power pugged in.



Herman [ Carl ]

---

### Post by hermannelson on 2010-12-16
Thanks to alexpennos  I solved my problem.

I will report this package problem.

[http://ubuntuforums.org/showpost.php?p=10185265&postcount=12](http://ubuntuforums.org/showpost.php?p=10185265&postcount=12)


Herman

---

### Post by papu40000 on 2011-01-02
Thank you hermannelson and alexpennos, works.

Also didn't work for me: remote desktop + discharge battery. I think is a serious problem for laptops. It's important to report it to pmitools and ubuntu updating.

Sorry the empty-brain and bad english

---

