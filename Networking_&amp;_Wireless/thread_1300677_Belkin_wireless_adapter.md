---
title: "Belkin wireless adapter"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by sk8trf on 2009-10-25
I downloaded the older version of ubuntu the 8.04 because the 9.04 version wouldnt boot on my pc for some reason, not really worried about it cause the 8.04 version does work. The only thing is i dont have a wired connection going to my computer so i had to go out and buy a wireless card. So i got a Belkin wireless usb card for my computer. Is there anyway i can get it to work, and if so can someone walk me through it. Im guessing i need drivers for it.

---

### Post by bkratz on 2009-10-25
> **sk8trf said:**
> I downloaded the older version of ubuntu the 8.04 because the 9.04 version wouldnt boot on my pc for some reason, not really worried about it cause the 8.04 version does work. The only thing is i dont have a wired connection going to my computer so i had to go out and buy a wireless card. So i got a Belkin wireless usb card for my computer. Is there anyway i can get it to work, and if so can someone walk me through it. Im guessing i need drivers for it.



Please see the following to see what everyone will need to know to help you.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by sk8trf on 2009-10-25
**Machine Brand:** 
Emachines

**Wireless Model and Chipset:**
```
Bus 005 Device 002: Device 050d:815f Belkin Components
```

**Interface:**
```
lo   no wireless extensions
eht1   no wireless extensions
eht0   no wireless extensions
```

[B]Ubuntu Version:
[/B]8.04.3 LTS[B]

Kernel/Architecture:
[/B]```
2.6.24-24-generic i686
```

That is about the most i could get, my computer is detecting that its plugged in but the card wont detect any netoworks, like i said i think it needs the drivers

---

### Post by coffeecat on 2009-10-25
I think you've got two problems.

I tried googling the ID number (050d:815f) for your wireless device which usually brings up useful information, but this time the results were sparse. The only one which was of use is [this forum thread for Puppy linux]("http://www.murga-linux.com/puppy/viewtopic.php?p=354167"). If I'm reading that right, you've got a very recent Realtek chipset which may or may not have Linux drivers available. Explanation - wireless drivers are contained in the kernel and it takes time for new devices to have drivers written, to be incorporated into the kernel and then for that version of the kernel to be used in a Linux distro.

Which leads to your second problem in that Ubuntu 8.04 is now 18 months old and is using a more-than 18-months old version of the kernel. It is very unlikely that 8.04 will have a suitable driver.

I have two suggestions.

Ubuntu 9.10 is about to be released. Why not download the RC version [from here]("http://www.ubuntu.com/getubuntu/releasenotes/910overview")? Run it live from the CD and see if the wireless device works. If it does, you might as well install it because the few updates and bugfixes that will be available over the next few days will turn a RC install into a final release install. No need to reinstall once it's gone final.

The other suggestion is to use ndiswrapper. I have no experience of this but I believe it's now much simpler that it once was, but if you're using Hardy (8.04) you might only be able to get an earlier less-friendly version of ndiswrapper. With ndiswrapper you use the Windows driver from the CD that came with the device.

---

### Post by sk8trf on 2009-10-25
Thanks i would download the the 9.10 beta, but how easy would it be to upgrade it to the full version? cause if its going to be hard and complicated ill just wait till it comes out in 4 days and do it then, i would like to do it asap and see if i can get my adapter to work i really dont want to use windows anymore

---

### Post by coffeecat on 2009-10-25
> **sk8trf said:**
> Thanks i would download the the 9.10 beta, but how easy would it be to upgrade it to the full version?

Sorry I didn't make myself clear. The answer is: very easy indeed.

If you go to the link I provided, there are links on there to a number of servers from which you can get the **Release Candidate**, not the Beta. Between now and this coming Thursday, when the final version becomes available, (four days only) there will be a few bug-fixes and updates. If you install the RC version to your hard disc (assuming it works for you) now and install all the updates as they become available, you will have the final version by Thursday. The only difference between the RC and the final is  those few updates and bugfixes.

In fact if you do this you'll have the final version up and running a couple of days before all the people who wait for the final to be released. This is because the package list has to be frozen 36-48 hours before release so that the final ISOs can be prepared, QC'd and distributed to the various servers. And, of course, on release day the servers get hammered by all the downloads and become very slow, so it can be difficult getting the final before Friday.

---

### Post by sk8trf on 2009-10-25
So it would be in my best intrest to download the beta and install it now so i dont have to wait if it works i can just upgrade, seeing my adapter works with the new install?

---

### Post by sk8trf on 2009-10-25
sorry for posting again but if i do get it to work, how hard would it be to update from 8.04 to the new 9.10 version once i get my card to work?

---

### Post by coffeecat on 2009-10-26
> **sk8trf said:**
> So it would be in my best intrest to download the beta and install it now so i dont have to wait if it works i can just upgrade, seeing my adapter works with the new install?

Yes. That's more or less what I said. Except - as I've already said - it's not the Beta anymore: it's the Release Candidate at the time of posting. Actually, what I was trying to say was download the **[SIZE=4]Release Candidate[/SIZE]** :wink: , run it live, **if** your network device works then install, keep it updated and by the end of the week you'll have to the final.

But if the live CD doesn't detect and use your network device, I'm afraid you'll be stuck with ndiswrapper - which may not be as difficult as it may appear. All ndiswrapper does it put a "wrapper" around the Windows driver (the one that comes on the Belkin CD) to make your Ubuntu system think it's using a Linux driver. Apparently, the installation is all quite straightforward - it's just that I have never needed to do this myself so I can't advise you on the actual installation process.

> **sk8trf said:**
> sorry for posting again but if i do get it to work, how hard would it be to update from 8.04 to the new 9.10 version once i get my card to work?

To do dist-upgrades you must upgrade from one version to the next. In your case 8.04 > 8.10 > 9.04 > 9.10. You musn't skip a version. In your situation you're probably better off doing a fresh install, but you must decide. In any event, try the **[SIZE=4]Release Candidate[/SIZE]** :wink: version of 9.10 from the live CD first (without installing to the HD) to see whether your wireless device works or not with 9.10. Then decide what to do.

Unless you wait until Thursday when the final version will become available, but the download servers will be slow or unavailable for at least a day because of the rush.

---

### Post by sk8trf on 2009-10-26
ok i ran the live cd of the RC with ubuntu 9.10 and it still didnt work so im going to have to use ndiswrapper, my question is how do i install it without internet connection?

also can i upgrade from my 8.04 to 9.10 in a couple days when it comes out, once i get my adapter working? i know you said i can do it from the RC to the full version

---

### Post by coffeecat on 2009-10-26
> **sk8trf said:**
> ok i ran the live cd of the RC with ubuntu 9.10 and it still didnt work so im going to have to use ndiswrapper, my question is how do i install it without internet connection?

Yes, that is a problem when you have no wired connection. The best and easiest guide I've found is [this one]("http://ubuntuforums.org/showthread.php?t=1266908"). The principle is the same whether you're running 8.04 or 9.10. For 9.10, the packages you need are firstly ndisgtk which is a GUI frontend to ndiswrapper proper. Then its  2 dependencies, ndiswrapper-common and ndiswrapper-utils-1.9. You need to download all three packages and my guess is you need to install them in the order utils, common, gtk, otherwise you'll get errors about unmet dependencies. If you prefer, instead of using the dpkg command from the terminal, you can just copy the files onto the desktop and double-click on them and the GUI app GDebi will install them for you.

I'm fairly sure that the ndisgtk frontend was available for version 8.04 but, if not, you've got some forum searching and terminal work ahead of you. And ndiswrapper-utils in 8.04 will have a different version number. Once you've got ndiswrapper installed, I can't help you any further although I've read that the gtk GUI frontend makes it very easy.

> **sk8trf said:**
> also can i upgrade from my 8.04 to 9.10 in a couple days when it comes out, once i get my adapter working?

Have a look at my previous post, #9, again. I've already answered this. :wink:

---

### Post by bkratz on 2009-10-26
> **sk8trf said:**
> ok i ran the live cd of the RC with ubuntu 9.10 and it still didnt work so im going to have to use ndiswrapper, my question is how do i install it without internet connection?

also can i upgrade from my 8.04 to 9.10 in a couple days when it comes out, once i get my adapter working? i know you said i can do it from the RC to the full version


I don't know about 8.04 for sure, but I used 8.10 and 9.04 and did the ndisgtk thing from the installation cd. I believe it automatically loaded all the dependancies (ndiswrapper--).

go to : (put the installation disk in the drive!)

 system--administration--software sources and tick cd rom at the bottom.  Then search for ndisgtk

Using ndisgtk couldn't be much simpler- I don't think you would need much if any help.
It will be in the menus.

---

### Post by sk8trf on 2009-10-26
so basically i would want to do a new install with the RC of 9.10 instead up upgrading from 8.04->8.10 etc. and then get my ndiswrapper working? which ive been reading a lot on and it really shouldnt be that hard

---

### Post by sk8trf on 2009-10-27
ok, i finally got ndiswrapper installed and i also installed a driver off my disk i got with my adapter, problem is i still cant pick up any networks, when i type
```
ndiswrapper -l
```
i get this readout
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
       device (050d:815F) present
```
So from what i understand the driver is installed and it still detects my hardware, but for some reason when i go to connect to a network im still getting nothing to choose from. Maybe i have the wrong driver installed?

---

### Post by bkratz on 2009-10-27
> **sk8trf said:**
> ok, i finally got ndiswrapper installed and i also installed a driver off my disk i got with my adapter, problem is i still cant pick up any networks, when i type
```
ndiswrapper -l
```
i get this readout
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
       device (050d:815F) present
```
So from what i understand the driver is installed and it still detects my hardware, but for some reason when i go to connect to a network im still getting nothing to choose from. Maybe i have the wrong driver installed?



Don't worry about the Warning, but can you post the output of 
(from the terminal)

sudo iwlist scan           (scan for wireless networks)

and also

sudo lshw -C network       (network configuration)

---

### Post by sk8trf on 2009-10-27
sudo iwlist scan i get
```
lo    Interface doesnt support scanning.
 i get the same readout for eht0 and eht1
```

for the sudo lshw -C network i get
```
   	 	 	 	 	 	   *-network:0              
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 1  
        bus info: pci@0000:05:01.0  
        logical name: eth1  
        version: 10  
        serial: 00:1d:0f:c3:79:07  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s  
        resources: irq:22 ioport:1000(size=256) memory:50002000-500020ff memory:fffe0000-ffffffff(prefetchable)  
   *-network:1  
        description: Ethernet interface  
        product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller  
        vendor: Intel Corporation  
        physical id: 8  
        bus info: pci@0000:05:08.0  
        logical name: eth0  
        version: 04  
        serial: 00:11:11:c1:b0:fa  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s  
        resources: irq:20 memory:50000000-50000fff ioport:1100(size=64)  
 
```

---

### Post by logari81 on 2009-12-22
Hi I am looking for someone who has the following device:
> Bus 005 Device 002: Device 050d:815f Belkin Components
and can try the karmic kernel 2.6.31-17.54+ppak4 from here:
[https://launchpad.net/~logari81/+archive/ppa/+packages](https://launchpad.net/~logari81/+archive/ppa/+packages)

Please test it in an enviroment where ndiswrapper has never been installed. The kernel should load the rt2870 driver. Please after installing this kernel post the results from:

```
lsusb
lsmod
ifconfig
iwconfig
dmesg
```

---

### Post by deeptingler on 2010-01-16
if ive done this right.... lsusb gives me on my belkin 3015uk wireless n adapter...

Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2040:9950 Hauppauge 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




lsmod gives me....

Module                  Size  Used by
binfmt_misc            10220  1 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
iptable_filter          3872  0 
snd_pcm_oss            44704  0 
ip_tables              21200  1 iptable_filter
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_dummy           3460  0 
x_tables               25832  1 ip_tables
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
rt2870sta             552712  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
arc4                    2144  2 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mt2060                  5796  2 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
ecb                     3296  2 
rt2800usb              40800  0 
rt2x00usb              13600  1 rt2800usb
rt2x00lib              34624  2 rt2800usb,rt2x00usb
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210008  2 rt2x00usb,rt2x00lib
i2c_piix4              11728  0 
ppdev                   8232  0 
dvb_usb_dib0700        58184  0 
dib7000p               19272  1 dvb_usb_dib0700
dib7000m               16836  1 dvb_usb_dib0700
dvb_usb                19276  1 dvb_usb_dib0700
dvb_core              104528  1 dvb_usb
dib3000mc              14344  3 dvb_usb_dib0700
dibx000_common          4196  3 dib7000p,dib7000m,dib3000mc
dib0070                 8868  1 dvb_usb_dib0700
parport_pc             37352  1 
psmouse                57124  0 
serio_raw               6596  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
asus_atk0110            9472  0 
cfg80211              109144  2 rt2x00lib,mac80211
crc_ccitt               2336  1 rt2800usb
joydev                 13088  0 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
hid_logitech           10112  0 
ff_memless              6504  1 hid_logitech
usbhid                 43968  1 hid_logitech
floppy                 65192  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
radeon                684512  1 
ttm                    43056  1 radeon
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon
r8169                  38884  0 
mii                     6368  1 r8169



ifconfig gives me....

eth0      Link encap:Ethernet  HWaddr 00:24:8c:0a:60:3d  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe0a:603d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1010022 (1.0 MB)  TX bytes:164725 (164.7 KB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:8f:ae:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-75-8F-AE-59-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig gives me....

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



dmesg gives me....

[    1.090560] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.090561] ACPI: Power Button [PWRB]
[    1.091143] processor LNXCPU:00: registered as cooling_device0
[    1.091145] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.091471] processor LNXCPU:01: registered as cooling_device1
[    1.091794] processor LNXCPU:02: registered as cooling_device2
[    1.092118] processor LNXCPU:03: registered as cooling_device3
[    1.095570] Linux agpgart interface v0.103
[    1.095576] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.096244] brd: module loaded
[    1.096487] loop: module loaded
[    1.096527] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.096625] ahci 0000:00:11.0: version 3.0
[    1.096637]   alloc irq_desc for 22 on node 0
[    1.096638]   alloc kstat_irqs on node 0
[    1.096642] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.096740] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.096742] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.096990] scsi0 : ahci
[    1.097046] scsi1 : ahci
[    1.097080] scsi2 : ahci
[    1.097112] scsi3 : ahci
[    1.097176] ata1: SATA max UDMA/133 irq_stat 0x00400000 irq 22, PHY RDY changed
[    1.097179] ata2: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbff980 irq 22
[    1.097181] ata3: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbffa00 irq 22
[    1.097184] ata4: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbffa80 irq 22
[    1.097380]   alloc irq_desc for 16 on node 0
[    1.097382]   alloc kstat_irqs on node 0
[    1.097385] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.097404] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.097465] scsi4 : pata_atiixp
[    1.097502] scsi5 : pata_atiixp
[    1.098435] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.098437] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.098567]   alloc irq_desc for 20 on node 0
[    1.098568]   alloc kstat_irqs on node 0
[    1.098571] pata_it821x 0000:04:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.098575] pata_it821x: controller in smart mode.
[    1.098598] pata_it821x 0000:04:06.0: setting latency timer to 64
[    1.108659] it821x_firmware_command: timeout
[    1.108722] scsi6 : pata_it821x
[    1.108758] scsi7 : pata_it821x
[    1.108777] ata7: PATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 20
[    1.108778] ata8: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 20
[    1.109097] Fixed MDIO Bus: probed
[    1.109116] PPP generic driver version 2.4.2
[    1.109170] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.109216] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.109228] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.109256] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.109274] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.109291] ehci_hcd 0000:00:12.2: debug port 1
[    1.109303] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbbff000
[    1.120019] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.120074] usb usb1: configuration #1 chosen from 1 choice
[    1.120094] hub 1-0:1.0: USB hub found
[    1.120099] hub 1-0:1.0: 6 ports detected
[    1.120188]   alloc irq_desc for 19 on node 0
[    1.120189]   alloc kstat_irqs on node 0
[    1.120192] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.120203] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.120222] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.120238] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.120254] ehci_hcd 0000:00:13.2: debug port 1
[    1.120266] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbbfa800
[    1.140016] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.140061] usb usb2: configuration #1 chosen from 1 choice
[    1.140076] hub 2-0:1.0: USB hub found
[    1.140080] hub 2-0:1.0: 6 ports detected
[    1.140168]   alloc irq_desc for 23 on node 0
[    1.140169]   alloc kstat_irqs on node 0
[    1.140172] ehci_hcd 0000:04:07.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    1.140183] ehci_hcd 0000:04:07.2: EHCI Host Controller
[    1.140203] ehci_hcd 0000:04:07.2: new USB bus registered, assigned bus number 3
[    1.140242] ehci_hcd 0000:04:07.2: irq 23, io mem 0xfbfdfc00
[    1.160018] ehci_hcd 0000:04:07.2: USB 2.0 started, EHCI 1.00
[    1.160062] usb usb3: configuration #1 chosen from 1 choice
[    1.160080] hub 3-0:1.0: USB hub found
[    1.160084] hub 3-0:1.0: 4 ports detected
[    1.160136] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.160177] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.160188] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.160207] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.160227] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbbfe000
[    1.224081] usb usb4: configuration #1 chosen from 1 choice
[    1.224099] hub 4-0:1.0: USB hub found
[    1.224109] hub 4-0:1.0: 3 ports detected
[    1.224186] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.224196] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.224213] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 5
[    1.224227] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbbfd000
[    1.284064] usb usb5: configuration #1 chosen from 1 choice
[    1.284079] hub 5-0:1.0: USB hub found
[    1.284089] hub 5-0:1.0: 3 ports detected
[    1.284168] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.284180] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.284198] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 6
[    1.284217] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbbfc000
[    1.312939] ata5.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    1.312943] ata5.00: ATA-7: SAMSUNG SP2514N, VF100-50, max UDMA/100
[    1.312944] ata5.00: 488397168 sectors, multi 16: LBA48 
[    1.313116] ata5.01: ATA-6: WDC WD3200JB-00KFA0, 08.05J08, max UDMA/100
[    1.313118] ata5.01: 625142448 sectors, multi 16: LBA48 
[    1.344066] usb usb6: configuration #1 chosen from 1 choice
[    1.344082] hub 6-0:1.0: USB hub found
[    1.344092] hub 6-0:1.0: 3 ports detected
[    1.344169] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.344179] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.344199] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 7
[    1.344212] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbbfb000
[    1.353024] ata5.00: configured for UDMA/100
[    1.393029] ata5.01: configured for UDMA/100
[    1.404067] usb usb7: configuration #1 chosen from 1 choice
[    1.404082] hub 7-0:1.0: USB hub found
[    1.404092] hub 7-0:1.0: 3 ports detected
[    1.404169] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.404180] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.404202] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 8
[    1.404215] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbbf9000
[    1.440878] ata4: SATA link down (SStatus 0 SControl 300)
[    1.464066] usb usb8: configuration #1 chosen from 1 choice
[    1.464081] hub 8-0:1.0: USB hub found
[    1.464091] hub 8-0:1.0: 2 ports detected
[    1.464133] uhci_hcd: USB Universal Host Controller Interface driver
[    1.464204]   alloc irq_desc for 21 on node 0
[    1.464205]   alloc kstat_irqs on node 0
[    1.464208] uhci_hcd 0000:04:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.464214] uhci_hcd 0000:04:07.0: UHCI Host Controller
[    1.464234] uhci_hcd 0000:04:07.0: new USB bus registered, assigned bus number 9
[    1.464266] uhci_hcd 0000:04:07.0: irq 21, io base 0x0000e080
[    1.464313] usb usb9: configuration #1 chosen from 1 choice
[    1.464327] hub 9-0:1.0: USB hub found
[    1.464331] hub 9-0:1.0: 2 ports detected
[    1.464384] uhci_hcd 0000:04:07.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.464389] uhci_hcd 0000:04:07.1: UHCI Host Controller
[    1.464406] uhci_hcd 0000:04:07.1: new USB bus registered, assigned bus number 10
[    1.464431] uhci_hcd 0000:04:07.1: irq 22, io base 0x0000e000
[    1.464482] usb usb10: configuration #1 chosen from 1 choice
[    1.464496] hub 10-0:1.0: USB hub found
[    1.464500] hub 10-0:1.0: 2 ports detected
[    1.464560] PNP: No PS/2 controller found. Probing ports directly.
[    1.464870] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.464884] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.464953] mice: PS/2 mouse device common for all mice
[    1.465020] rtc_cmos 00:03: RTC can wake from S4
[    1.465040] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.465062] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.465142] device-mapper: uevent: version 1.0.3
[    1.465193] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.465278] device-mapper: multipath: version 1.1.0 loaded
[    1.465281] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.465452] cpuidle: using governor ladder
[    1.465453] cpuidle: using governor menu
[    1.465706] TCP cubic registered
[    1.465776] NET: Registered protocol family 10
[    1.466061] lo: Disabled Privacy Extensions
[    1.466236] NET: Registered protocol family 17
[    1.466248] Bluetooth: L2CAP ver 2.13
[    1.466249] Bluetooth: L2CAP socket layer initialized
[    1.466251] Bluetooth: SCO (Voice Link) ver 0.6
[    1.466252] Bluetooth: SCO socket layer initialized
[    1.466295] Bluetooth: RFCOMM TTY layer initialized
[    1.466297] Bluetooth: RFCOMM socket layer initialized
[    1.466298] Bluetooth: RFCOMM ver 1.11
[    1.466322] powernow-k8: Found 1 AMD Phenom(tm) II X4 940 Processor processors (4 cpu cores) (version 2.20.00)
[    1.466348] powernow-k8:    0 : pstate 0 (3000 MHz)
[    1.466349] powernow-k8:    1 : pstate 1 (2300 MHz)
[    1.466350] powernow-k8:    2 : pstate 2 (1800 MHz)
[    1.466352] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.466895] PM: Resume from disk failed.
[    1.466901] registered taskstats version 1
[    1.467002]   Magic number: 10:503:226
[    1.467061] rtc_cmos 00:03: setting system clock to 2010-01-16 11:12:10 UTC (1263640330)
[    1.467063] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.467064] EDD information not available.
[    1.500849] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.620020] ata3: softreset failed (device not ready)
[    1.620022] ata3: applying SB600 PMP SRST workaround and retrying
[    1.620039] ata2: softreset failed (device not ready)
[    1.620041] ata2: applying SB600 PMP SRST workaround and retrying
[    1.673063] usb 1-2: configuration #1 chosen from 1 choice
[    1.800026] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.800046] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.802462] ata2.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    1.802464] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.804142] ata2.00: configured for UDMA/133
[    1.812126] ata3.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.812128] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.813026] ata3.00: configured for UDMA/133
[    1.980015] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    2.020016] ata1: softreset failed (device not ready)
[    2.020019] ata1: applying SB600 PMP SRST workaround and retrying
[    2.161865] usb 4-1: configuration #1 chosen from 1 choice
[    2.200022] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.213684] ata1.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.213686] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.214592] ata1.00: configured for UDMA/133
[    2.232589] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.232664] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.232693] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.232715] sd 0:0:0:0: [sda] Write Protect is off
[    2.232717] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.232729] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.232796]  sda:
[    2.232843] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    2.232903] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.232924] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.232945] sd 1:0:0:0: [sdb] Write Protect is off
[    2.232947] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.232959] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.232980] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.233011]  sdb:
[    2.233059] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.233075] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.233095] sd 2:0:0:0: [sdc] Write Protect is off
[    2.233097] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.233107] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.233157]  sdc:
[    2.233198] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG SP2514N  VF10 PQ: 0 ANSI: 5
[    2.233256] sd 4:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.233259] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.233282] sd 4:0:0:0: [sdd] Write Protect is off
[    2.233284] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.233290] scsi 4:0:1:0: Direct-Access     ATA      WDC WD3200JB-00K 08.0 PQ: 0 ANSI: 5
[    2.233296] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.233357] sd 4:0:1:0: Attached scsi generic sg4 type 0
[    2.233375]  sdd:
[    2.233378] sd 4:0:1:0: [sde] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.241455]  sdd1
[    2.241457] sd 4:0:1:0: [sde] Write Protect is off
[    2.241461] sd 4:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    2.241463]  sdd2 < sda1 < sda5 >
[    2.246452] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.250878]  sdd5
[    2.250881] sd 4:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.251851]  sdc1 < sdc5 >
[    2.252177] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.252977]  sdb1 < sdb5 >
[    2.253697] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.259086]  sdd6 >
[    2.259202]  sde: sde1 <
[    2.271405] sd 4:0:0:0: [sdd] Attached SCSI disk
[    2.271415]  sde5 >
[    2.271537] sd 4:0:1:0: [sde] Attached SCSI disk
[    2.282515] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    2.410342] ata6.00: ATAPI: LITE-ON DVDRW LH-20A1L, BL05, max UDMA/100
[    2.434270] usb 3-1: configuration #1 chosen from 1 choice
[    2.461185] ata6.00: configured for UDMA/100
[    2.463091] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1L   BL05 PQ: 0 ANSI: 5
[    2.468641] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.468644] Uniform CD-ROM driver Revision: 3.20
[    2.468693] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.468719] sr 5:0:0:0: Attached scsi generic sg5 type 5
[    2.620085] Freeing unused kernel memory: 660k freed
[    2.620217] Write protecting the kernel read-only data: 7584k
[    2.686893] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.686913] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.686955] r8169 0000:03:00.0: setting latency timer to 64
[    2.686986]   alloc irq_desc for 28 on node 0
[    2.686988]   alloc kstat_irqs on node 0
[    2.686998] r8169 0000:03:00.0: irq 28 for MSI/MSI-X
[    2.687412] eth0: RTL8168c/8111c at 0xffffc9000067e000, 00:24:8c:0a:60:3d, XID 3c4000c0 IRQ 28
[    2.696726] [drm] Initialized drm 1.1.0 20060810
[    2.715335] [drm] radeon default to kernel modesetting DISABLED.
[    2.715724] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.715729] pci 0000:01:00.0: setting latency timer to 64
[    2.715852] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    2.722760] ohci1394 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.722765] ohci1394 0000:02:00.0: setting latency timer to 64
[    2.725458] Floppy drive(s): fd0 is 1.44M
[    2.729776] usbcore: registered new interface driver hiddev
[    2.729850] usbcore: registered new interface driver usbhid
[    2.729852] usbhid: v2.6:USB HID core driver
[    2.735620] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input3
[    2.735663] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-1/input0
[    2.743434] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    2.743860] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.1/input/input4
[    2.743945] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-1/input1
[    2.753846] FDC 0 is a post-1991 82077
[    2.791062] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fbdff800-fbdfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.672342] PM: Starting manual resume from disk
[    3.672344] PM: Resume from partition 8:53
[    3.672346] PM: Checking hibernation image.
[    3.672550] PM: Resume from disk failed.
[    3.695189] kjournald starting.  Commit interval 5 seconds
[    3.695196] EXT3-fs: mounted filesystem with writeback data mode.
[    4.112625] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001b6d190]
[    4.165538] type=1505 audit(1263640333.195:2): operation="profile_load" pid=517 name=/usr/share/gdm/guest-session/Xsession
[    4.171586] type=1505 audit(1263640333.195:3): operation="profile_load" pid=518 name=/sbin/dhclient3
[    4.171777] type=1505 audit(1263640333.195:4): operation="profile_load" pid=518 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.171886] type=1505 audit(1263640333.195:5): operation="profile_load" pid=518 name=/usr/lib/connman/scripts/dhclient-script
[    4.221862] type=1505 audit(1263640333.252:6): operation="profile_load" pid=519 name=/usr/bin/evince
[    4.224800] type=1505 audit(1263640333.252:7): operation="profile_load" pid=519 name=/usr/bin/evince-previewer
[    4.226570] type=1505 audit(1263640333.252:8): operation="profile_load" pid=519 name=/usr/bin/evince-thumbnailer
[    4.237628] type=1505 audit(1263640333.265:9): operation="profile_load" pid=521 name=/usr/lib/cups/backend/cups-pdf
[    4.237860] type=1505 audit(1263640333.265:10): operation="profile_load" pid=521 name=/usr/sbin/cupsd
[    4.995348] Adding 2000052k swap on /dev/sdd5.  Priority:-1 extents:1 across:2000052k 
[    5.115227] udev: starting version 147
[    5.508498] EXT3 FS on sdd1, internal journal
[    6.155895] lp: driver loaded but no devices found
[    6.322628] cfg80211: Calling CRDA to update world regulatory domain
[    6.409449] EDAC MC: Ver: 2.1.0 Dec 10 2009
[    6.411424] EDAC amd64_edac:  Ver: 3.2.0 Dec 10 2009
[    6.411499] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    6.411502] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    6.411504] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    6.411505]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    6.411506]     Might be a BIOS bug, if BIOS says ECC is enabled
[    6.411507]     Use of the override can cause unknown side effects.
[    6.411517] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    6.506296] parport_pc 00:07: reported by Plug and Play ACPI
[    6.506364] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    6.582610] lp0: using parport0 (interrupt-driven).
[    6.659383] dib0700: loaded with support for 9 different device-types
[    6.659529] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[    6.659557] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    6.659705] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    6.789995] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[    7.058955] ppdev: user-space parallel port driver
[    7.064064] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    7.064067] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.149865] cfg80211: World regulatory domain updated:
[    7.149867] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.149869] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.149871] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.149873] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.149874] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.149876] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.518489] MT2060: successfully identified (IF1 = 1230)
[    7.571245] phy0: Selected rate control algorithm 'minstrel'
[    7.571673] Registered led device: rt2800usb-phy0::radio
[    7.571685] Registered led device: rt2800usb-phy0::assoc
[    7.571698] Registered led device: rt2800usb-phy0::quality
[    7.571951] usbcore: registered new interface driver rt2800usb
[    7.621395] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    7.623405] rtusb init --->
[    7.623430] usbcore: registered new interface driver rt2870
[    8.084692] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.141796] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.149201] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.149368] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    8.154816] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[    8.159428] MT2060: successfully identified (IF1 = 1236)
[    8.301098] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[    8.304084] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    8.304116] HDA Intel 0000:01:00.1: setting latency timer to 64
[    8.761884] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:04:07.2/usb3/3-1/input/input6
[    8.761912] dvb-usb: schedule remote query interval to 50 msecs.
[    8.761915] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[    8.762082] usbcore: registered new interface driver dvb_usb_dib0700
[   17.126634] EXT4-fs (sdd6): barriers enabled
[   17.146515] kjournald2 starting: pid 1012, dev sdd6:8, commit interval 5 seconds
[   17.146799] EXT4-fs (sdd6): internal journal on sdd6:8
[   17.146802] EXT4-fs (sdd6): delayed allocation enabled
[   17.146805] EXT4-fs: file extents enabled
[   17.147192] EXT4-fs: mballoc enabled
[   17.147203] EXT4-fs (sdd6): mounted filesystem with ordered data mode
[   19.219445] __ratelimit: 3 callbacks suppressed
[   19.219447] type=1505 audit(1263640348.245:12): operation="profile_replace" pid=1178 name=/usr/share/gdm/guest-session/Xsession
[   19.220336] type=1505 audit(1263640348.245:13): operation="profile_replace" pid=1179 name=/sbin/dhclient3
[   19.220528] type=1505 audit(1263640348.245:14): operation="profile_replace" pid=1179 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.220638] type=1505 audit(1263640348.245:15): operation="profile_replace" pid=1179 name=/usr/lib/connman/scripts/dhclient-script
[   19.222633] type=1505 audit(1263640348.255:16): operation="profile_replace" pid=1180 name=/usr/bin/evince
[   19.225567] type=1505 audit(1263640348.255:17): operation="profile_replace" pid=1180 name=/usr/bin/evince-previewer
[   19.227339] type=1505 audit(1263640348.255:18): operation="profile_replace" pid=1180 name=/usr/bin/evince-thumbnailer
[   19.230522] type=1505 audit(1263640348.255:19): operation="profile_replace" pid=1182 name=/usr/lib/cups/backend/cups-pdf
[   19.230756] type=1505 audit(1263640348.255:20): operation="profile_replace" pid=1182 name=/usr/sbin/cupsd
[   19.231882] type=1505 audit(1263640348.255:21): operation="profile_replace" pid=1183 name=/usr/sbin/tcpdump
[   19.378001] r8169: eth0: link up
[   19.378006] r8169: eth0: link up
[   19.393080] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
[   19.446973] usplash:457 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   19.723718] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.298327] [drm] Setting GART location based on new memory map
[   21.313415] [drm] Loading RV730/RV740 PFP Microcode
[   21.313426] [drm] Loading RV730/RV740 CP Microcode
[   21.328413] [drm] Resetting GPU
[   21.328469] [drm] writeback test succeeded in 1 usecs
[   22.848338] CPU0 attaching NULL sched-domain.
[   22.848342] CPU1 attaching NULL sched-domain.
[   22.848344] CPU2 attaching NULL sched-domain.
[   22.848346] CPU3 attaching NULL sched-domain.
[   22.881721] CPU0 attaching sched-domain:
[   22.881725]  domain 0: span 0-3 level MC
[   22.881726]   groups: 0 1 2 3
[   22.881729]   domain 1: span 0-3 level CPU
[   22.881731]    groups: 0-3 (__cpu_power = 4096)
[   22.881734] CPU1 attaching sched-domain:
[   22.881736]  domain 0: span 0-3 level MC
[   22.881737]   groups: 1 2 3 0
[   22.881739]   domain 1: span 0-3 level CPU
[   22.881740]    groups: 0-3 (__cpu_power = 4096)
[   22.881743] CPU2 attaching sched-domain:
[   22.881744]  domain 0: span 0-3 level MC
[   22.881745]   groups: 2 3 0 1
[   22.881747]   domain 1: span 0-3 level CPU
[   22.881749]    groups: 0-3 (__cpu_power = 4096)
[   22.881751] CPU3 attaching sched-domain:
[   22.881752]  domain 0: span 0-3 level MC
[   22.881753]   groups: 3 0 1 2
[   22.881755]   domain 1: span 0-3 level CPU
[   22.881756]    groups: 0-3 (__cpu_power = 4096)
[   24.880879] CPU0 attaching NULL sched-domain.
[   24.880884] CPU1 attaching NULL sched-domain.
[   24.880886] CPU2 attaching NULL sched-domain.
[   24.880887] CPU3 attaching NULL sched-domain.
[   24.921723] CPU0 attaching sched-domain:
[   24.921727]  domain 0: span 0-3 level MC
[   24.921729]   groups: 0 1 2 3
[   24.921733] CPU1 attaching sched-domain:
[   24.921734]  domain 0: span 0-3 level MC
[   24.921735]   groups: 1 2 3 0
[   24.921738] CPU2 attaching sched-domain:
[   24.921739]  domain 0: span 0-3 level MC
[   24.921740]   groups: 2 3 0 1
[   24.921743] CPU3 attaching sched-domain:
[   24.921744]  domain 0: span 0-3 level MC
[   24.921745]   groups: 3 0 1 2
[   27.165093] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   30.032505] eth0: no IPv6 routers present
[   36.320008] ehci_hcd 0000:04:07.2: force halt; handhake ffffc90000650c14 00004000 00000000 -> -110

---

### Post by logari81 on 2010-01-16
thanks for the feed back. Now your system loads two drivers, rt2800usb and rt2870. The second one is the one I would like to know if it works with this hardware or not. So it has not a lot of chances to work. I have some further questions:

1) I suppose your hardware doesn't work with the original karmic kernel. Is that right? It would be helpful to have a dmesg result with the standard kernel.

2) In order to test rt2870 you need to blacklist the rt2800usb module and provide us the same results as before.

Please post your results formated as ```
code
```
edit your last post too, to make it easier readable.

---

