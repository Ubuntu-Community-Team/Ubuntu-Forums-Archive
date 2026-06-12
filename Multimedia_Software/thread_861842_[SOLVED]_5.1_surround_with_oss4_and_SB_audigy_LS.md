---
title: "[SOLVED] 5.1 surround with oss4 and SB audigy LS"
date: 2008-07-17
forum: Multimedia Software
---

### Post by gummygod on 2008-07-17
so ive gotten sick of alsa not being able to play 2 sounds simultaneously. i searched all over for solutions, but found only that it is a bug.  i heard that oss4 can play multiple sounds so i installed that via this very helpful guide: [http://ubuntuforums.org/showthread.php?p=4874981](http://ubuntuforums.org/showthread.php?p=4874981)   
this got oss4 up and running, but i only have 2 speakers working (front right and front left).  multiple sound sources work, which is awesome. but i cant find a way to get all 6 channels/speakers working.  i also tried oss 4.1 to see if that had a difference but i have the same problems.  

heres info i suspect is useful

ossdetect -v
```
Detected Sound Blaster Audigy LS / Live7.1
Detected Generic USB audio/MIDI device (BETA)
```

ossinfo
```
Version info: OSS 4.1 (b 080705/200807162043) (0x00040090) GPL
Platform: Linux/x86_64 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 (andrew-desktop)

Number of audio devices:	4
Number of audio engines:	9
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_audigyls0 AudigyLS interrupts=1126935 (1126935)
 2: oss_usb0 USB audio core services


Mixer devices
 0: AudigyLS Mixer (Mixer 0 of device object 1)

Audio devices
AudigyLS front                    /dev/oss/oss_audigyls0/pcm0  (device index 0)
AudigyLS center/lfe               /dev/oss/oss_audigyls0/pcm1  (device index 1)
AudigyLS surround                 /dev/oss/oss_audigyls0/pcm2  (device index 2)
AudigyLS 5.1 output               /dev/oss/oss_audigyls0/pcm3  (device index 3)

```

osstest
```
Sound subsystem and version: OSS 4.1 (b 080705/200807162043) (0x00040090)
Platform: Linux/x86_64 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_audigyls0/pcm0 (audio engine 0): AudigyLS front
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_audigyls0/pcm1 (audio engine 2): AudigyLS center/lfe
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_audigyls0/pcm2 (audio engine 3): AudigyLS surround
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_audigyls0/pcm3 (audio engine 4): AudigyLS 5.1 output
- Skipping multi channel device

*** Some errors were detected during the tests ***

```

funny thing happens w/ 'osstest' it gives the above message normally, but if im playing music with say amarok, it successfully completes the left, right, and stereo portions, but then fails:

```
Sound subsystem and version: OSS 4.1 (b 080705/200807162043) (0x00040090)
Platform: Linux/x86_64 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_audigyls0/pcm0 (audio engine 0): AudigyLS front
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47946.00 Hz (-0.11%)> 
/dev/oss/oss_audigyls0/pcm1 (audio engine 2): AudigyLS center/lfe
- Performing audio playback test... /dev/oss/oss_audigyls0/pcm1: Device or resource busy
The device is busy. There is some other application
using it.
Can't open the device
/dev/oss/oss_audigyls0/pcm2 (audio engine 3): AudigyLS surround
- Performing audio playback test... /dev/oss/oss_audigyls0/pcm2: Device or resource busy
The device is busy. There is some other application
using it.
Can't open the device
/dev/oss/oss_audigyls0/pcm3 (audio engine 4): AudigyLS 5.1 output
- Skipping multi channel device

*** Some errors were detected during the tests ***

```



does anyone have ideas how i can get all my speakers working normally in oss?  or a fix to the alsa bug so it can play multiple sounds simultaneously?  ive been searching but havent found what im looking for yet

---

### Post by gummygod on 2008-07-17
do i just go back to alsa and forget about playing multiple sounds at the same time?

---

### Post by Derviansoul on 2008-07-17
Hello

Glad to hear someone with the same problem, i've got a Intel Corporation 82801G (ICH7 Family, and besides this when i use ossxmix it doesn't saves the changes:S, and with some movies the sound seems really low, does anyone knows why?
Besides that Ekiga seems to not detect oss4:(, and i really need it, does anyone knows a replacement for ekiga to use with voipbuster, 
regards

---

### Post by Derviansoul on 2008-07-17
gone back to alsa:(, hopping to hear better news from oss4 and their drivers:(
regards

---

### Post by gummygod on 2008-07-18
yea ill proly take that route shortly. hopefully its not too much of a pain to go back and get everythin set up

---

### Post by gummygod on 2008-07-18
well then, turns out it IS a pain. does someone know how i can get alsa working again after installing oss4?  i know kinda shot myself in the foot, but hey, it would be nice to have sound working as it should
thanks

---

### Post by Derviansoul on 2008-07-19
Hello

this is a big problem, to put alsa working again, apparently oss and alsa write some of their own "stuff" within the kernel or something i don't really know what the hell it was,besides that i had to reinstall my ati drivers back again.

so basically try to do the fresh kernel step installation that it's shown at the forum here, but it didn't work for me! i would recommend you to try it.

here it is the link:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=install+alsa]("http://ubuntuforums.org/showthread.php?t=205449&highlight=install+alsa")

Now what i've done, first i used qgrubeditor from synaptic to boot from another kernel version: ex i was using 2.24.16 and i used 2.24.19-rt.

Now before you restart you have to remove from the boot process the oss drivers:
```
sudo gzip /etc/init.d/oss
sudo rm -v /etc/init.d/oss

```
now you have to remove all the alsa blacklisted drivers, removing all the lines at the end of the file that have "blacklist snd-"
from here:

```
gksu gedit /etc/modprobe.d/blacklist
```

now you should reboot

once u rebooted you should remove the kernel that u were using in the first place:

```

sudo apt-get purge linux-headers-2.6.24-[the version that you were using] linux-headers-2.6.24-[the version that you were using] linux-image-2.6.24-[the version that you were using]-generic linux-restricted-modules-2.6.24-[the version that you were using]-generic

```

now you should remove what's left from this directory
```
rm -Rv /lib/modules/2.6.24-[the version that you were using]-generic/
```


```

sudo apt-get install linux-headers-2.6.24-[the version that you were using] linux-headers-2.6.24-[the version that you were using] linux-image-2.6.24-[the version that you were using]-generic linux-restricted-modules-2.6.24-[the version that you were using]-generic

```

go to the qgrubeditor and put the kernel version that u first had at the beginning.

reboot

now it's time to install the alsa drivers

first we have to find out which model you got, just go to a terminal and write:

```
 lspci | grep Audio 
```


now go to the alsa [webpage]("http://www.alsa-project.org/main/index.php/Matrix:Main") that will tell you which driver you will be using, check your brand acording to lspci and check which drivers they tell you to use.

now download the drivers from [here]("ftp://ftp.alsa-project.org/pub/driver/cc"):

now type
```
sudo -s
mkdir /usr/src/alsa

```

now go to the directory where you download those drivers and type:

```
cp alsa-driver-* /usr/src/alsa 
```
then:
```

bunzip2 alsa-driver-xxx
tar -xf alsa-driver-xxx
cd alsa-driver-xxx

```

now:

```
 apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

dpkg-reconfigure alsa-source 

```

> 
# You now have a big blue dialog box (left and right keys to choose 'Yes' and 'No', Enter key proceed). Answer yes (for ISA-PNP - recommended by package maintainers), then yes again (for debugging - recommended by package maintainers).
# Now you must pick which driver you want to install. Use space to select and deselect modules, and up and down to navigate.
# From General Help step 3, you should know the name of your driver. Deselect 'all' (the * will go away), and select your driver. In my case, I deselected 'all' then selected 'via82xx'. Hit Enter. Almost home free! 

now the very final step to compile it
```
./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<insert driver> --with-oss=yes 

```
```

make 

```
```

make install

```

If you get no error messages, you will have installed the drivers successfully. 

now reboot

```
alsamixer
```

to save your changes do this

```
sudo alsactl store 0
```

hopefully this will works for you too, hope this helps
regards

---

### Post by gummygod on 2008-07-21
thanks for the response, but, unfortunately that didnt work.

i dont know whats going on, but when i type 'alsamixer' i get

```


alsamixer: function snd_ctl_open failed for default: No such file or directory
```

im fairly certain that shouldnt happen. any ideas?

---

### Post by Derviansoul on 2008-07-21
What drivers are you using for you sound card?
whats the output for:

```

dmesg
and,
sudo /etc/init.d/alsasound start

if you don't get any output then type:

sudo /etc/init.d/alsasound status

```



did you compiled the drivers into the new installed kernel?did you removed oss from init.d?

whats the name of the drivers that you are using it?
whats the output of:

```
lspci | grep Audio
```



regards

---

### Post by gummygod on 2008-07-21
i should be using ca0106

dmesg:
```
[   16.039279] NET: Registered protocol family 20
[   16.039307] PCI-GART: No AMD northbridge found.
[   16.039311] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   16.039315] hpet0: 4 64-bit timers, 14318180 Hz
[   16.040340] AppArmor: AppArmor Filesystem Enabled
[   16.043237] Time: tsc clocksource has been installed.
[   16.043243] Switched to high resolution mode on CPU 0
[   16.043706] Switched to high resolution mode on CPU 1
[   16.051238] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   16.051241] system 00:01: ioport range 0x290-0x29f has been reserved
[   16.051244] system 00:01: ioport range 0x800-0x87f has been reserved
[   16.051246] system 00:01: ioport range 0x290-0x294 has been reserved
[   16.051249] system 00:01: ioport range 0x880-0x88f has been reserved
[   16.051257] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[   16.051262] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   16.051268] system 00:0c: iomem range 0xce000-0xcffff has been reserved
[   16.051271] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   16.051273] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   16.051276] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   16.051279] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
[   16.051281] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   16.051284] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
[   16.051287] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   16.051289] system 00:0c: iomem range 0xfed10000-0xfed1dfff has been reserved
[   16.051292] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[   16.051295] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   16.051297] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[   16.051610] PCI: Bridge: 0000:00:01.0
[   16.051611]   IO window: b000-bfff
[   16.051614]   MEM window: f4000000-f6ffffff
[   16.051616]   PREFETCH window: e0000000-efffffff
[   16.051618] PCI: Bridge: 0000:00:1c.0
[   16.051620]   IO window: a000-afff
[   16.051623]   MEM window: disabled.
[   16.051625]   PREFETCH window: disabled.
[   16.051628] PCI: Bridge: 0000:00:1c.3
[   16.051630]   IO window: 9000-9fff
[   16.051633]   MEM window: disabled.
[   16.051635]   PREFETCH window: disabled.
[   16.051638] PCI: Bridge: 0000:00:1c.4
[   16.051640]   IO window: c000-cfff
[   16.051643]   MEM window: f7000000-f8ffffff
[   16.051646]   PREFETCH window: 80000000-800fffff
[   16.051649] PCI: Bridge: 0000:00:1e.0
[   16.051650]   IO window: d000-dfff
[   16.051653]   MEM window: disabled.
[   16.051656]   PREFETCH window: disabled.
[   16.051665] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.051669] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.051682] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.051685] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.051698] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   16.051702] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.051714] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   16.051717] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   16.051725] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.051731] NET: Registered protocol family 2
[   16.087221] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   16.087705] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   16.088794] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.089181] TCP: Hash tables configured (established 262144 bind 65536)
[   16.089183] TCP reno registered
[   16.099255] checking if image is initramfs... it is
[   16.705025] Freeing initrd memory: 7987k freed
[   16.707962] audit: initializing netlink socket (disabled)
[   16.707977] audit(1216647650.252:1): initialized
[   16.709461] VFS: Disk quotas dquot_6.5.1
[   16.709509] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.709597] io scheduler noop registered
[   16.709598] io scheduler anticipatory registered
[   16.709599] io scheduler deadline registered
[   16.709674] io scheduler cfq registered (default)
[   16.712803] Boot video device is 0000:01:00.0
[   16.712916] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.712939] assign_interrupt_mode Found MSI capability
[   16.712958] Allocate Port Service[0000:00:01.0:pcie00]
[   16.713012] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.713042] assign_interrupt_mode Found MSI capability
[   16.713066] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.713089] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.713146] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.713176] assign_interrupt_mode Found MSI capability
[   16.713200] Allocate Port Service[0000:00:1c.3:pcie00]
[   16.713223] Allocate Port Service[0000:00:1c.3:pcie02]
[   16.713281] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   16.713311] assign_interrupt_mode Found MSI capability
[   16.713335] Allocate Port Service[0000:00:1c.4:pcie00]
[   16.713358] Allocate Port Service[0000:00:1c.4:pcie02]
[   16.730775] Real Time Clock Driver v1.12ac
[   16.730850] Linux agpgart interface v0.102
[   16.730852] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.730949] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.731325] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.731851] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.731894] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.731958] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.732229] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.732232] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.746388] mice: PS/2 mouse device common for all mice
[   16.746417] cpuidle: using governor ladder
[   16.746419] cpuidle: using governor menu
[   16.746523] NET: Registered protocol family 1
[   16.746597] registered taskstats version 1
[   16.746676]   Magic number: 0:96:686
[   16.746723] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.746725] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.746727] EDD information not available.
[   16.746733] Freeing unused kernel memory: 320k freed
[   16.762639] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.886105] fuse init (API version 7.9)
[   17.899764] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.899856] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   17.899965] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.899975] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.899983] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.985705] usbcore: registered new interface driver usbfs
[   17.985721] usbcore: registered new interface driver hub
[   17.985739] usbcore: registered new device driver usb
[   17.986328] USB Universal Host Controller Interface driver v3.0
[   17.986365] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.986373] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   17.986375] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   17.986540] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   17.986564] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[   17.986643] usb usb1: configuration #1 chosen from 1 choice
[   17.986658] hub 1-0:1.0: USB hub found
[   17.986662] hub 1-0:1.0: 2 ports detected
[   18.087690] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   18.087700] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   18.087703] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   18.087720] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   18.087743] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e500
[   18.087816] usb usb2: configuration #1 chosen from 1 choice
[   18.087833] hub 2-0:1.0: USB hub found
[   18.087840] hub 2-0:1.0: 2 ports detected
[   18.149056] SCSI subsystem initialized
[   18.170365] libata version 3.00 loaded.
[   18.191491] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   18.191501] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   18.191504] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   18.191521] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   18.191543] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[   18.191618] usb usb3: configuration #1 chosen from 1 choice
[   18.191634] hub 3-0:1.0: USB hub found
[   18.191638] hub 3-0:1.0: 2 ports detected
[   18.295277] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   18.295286] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.295288] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.295304] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   18.295325] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[   18.295397] usb usb4: configuration #1 chosen from 1 choice
[   18.295413] hub 4-0:1.0: USB hub found
[   18.295416] hub 4-0:1.0: 2 ports detected
[   18.399060] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   18.399069] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.399072] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.399089] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   18.399111] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[   18.399190] usb usb5: configuration #1 chosen from 1 choice
[   18.399205] hub 5-0:1.0: USB hub found
[   18.399209] hub 5-0:1.0: 2 ports detected
[   18.502865] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   18.502873] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.502876] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.502892] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   18.502913] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[   18.502992] usb usb6: configuration #1 chosen from 1 choice
[   18.503013] hub 6-0:1.0: USB hub found
[   18.503017] hub 6-0:1.0: 2 ports detected
[   18.606307] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   18.607117] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   18.607122] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   18.607158] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   18.611054] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   18.611060] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9000000
[   18.630031] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.630112] usb usb7: configuration #1 chosen from 1 choice
[   18.630128] hub 7-0:1.0: USB hub found
[   18.630133] hub 7-0:1.0: 6 ports detected
[   18.729926] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   18.730726] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.730730] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.730780] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   18.734686] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.734690] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9001000
[   18.749805] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.749885] usb usb8: configuration #1 chosen from 1 choice
[   18.749904] hub 8-0:1.0: USB hub found
[   18.749908] hub 8-0:1.0: 6 ports detected
[   18.857884] ata_piix 0000:00:1f.2: version 2.12
[   18.857889] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   18.857910] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   18.857934] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.858009] scsi0 : ata_piix
[   18.858038] scsi1 : ata_piix
[   18.858420] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   18.858422] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   19.029394] ata1.00: HPA unlocked: 488130922 -> 488397168, native 488397168
[   19.029398] ata1.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   19.029400] ata1.00: 488397168 sectors, multi 16: LBA48 
[   19.037493] ata1.00: configured for UDMA/133
[   19.207630] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   19.207676] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   19.207696] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   19.207717] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.207746] scsi2 : ata_piix
[   19.207774] scsi3 : ata_piix
[   19.208113] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[   19.208115] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[   19.524403] ata3.00: ATAPI: ASUS    DRW-1814BLT, 1.04, max UDMA/66
[   19.696072] ata3.00: configured for UDMA/66
[   19.866692] scsi 2:0:0:0: CD-ROM            ASUS     DRW-1814BLT      1.04 PQ: 0 ANSI: 5
[   19.866767] r8169 Gigabit Ethernet driver 2.2LK loaded
[   19.866784] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.866796] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   19.867009] eth0: RTL8168b/8111b at 0xffffc200008b2000, 00:1a:4d:50:1d:14, XID 38000000 IRQ 507
[   19.874353] Driver 'sd' needs updating - please use bus_type methods
[   19.874401] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   19.874409] sd 0:0:0:0: [sda] Write Protect is off
[   19.874410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.874422] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.874452] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   19.874458] sd 0:0:0:0: [sda] Write Protect is off
[   19.874460] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.874471] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.874473]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.890996]  sda1 sda2 sda3 < sda5 >
[   19.914938] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.918112] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.918125] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   19.919691] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.919694] Uniform CD-ROM driver Revision: 3.20
[   19.919722] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   20.202150] Attempting manual resume
[   20.202152] swsusp: Resume From Partition 8:5
[   20.202153] PM: Checking swsusp image.
[   20.202285] PM: Resume from disk failed.
[   20.240867] kjournald starting.  Commit interval 5 seconds
[   20.240874] EXT3-fs: mounted filesystem with ordered data mode.
[   29.891367] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   30.231874] iTCO_vendor_support: vendor-support=0
[   30.250684] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.282783] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.306582] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.333250] logips2pp: Detected unknown logitech mouse model 101
[   30.526689] input: Power Button (FF) as /devices/virtual/input/input3
[   30.578507] ACPI: Power Button (FF) [PWRF]
[   30.578547] input: Power Button (CM) as /devices/virtual/input/input4
[   30.584900] snd: Unknown symbol unregister_sound_special
[   30.584977] snd: Unknown symbol register_sound_special_device
[   30.585198] snd: Unknown symbol sound_class
[   30.598158] snd_timer: Unknown symbol snd_verbose_printd
[   30.598181] snd_timer: Unknown symbol snd_hidden_kzalloc
[   30.598203] snd_timer: Unknown symbol snd_info_register
[   30.598226] snd_timer: Unknown symbol snd_info_create_module_entry
[   30.598252] snd_timer: Unknown symbol snd_info_free_entry
[   30.598278] snd_timer: Unknown symbol snd_hidden_kfree
[   30.598317] snd_timer: Unknown symbol snd_verbose_printk
[   30.598343] snd_timer: Unknown symbol snd_iprintf
[   30.598378] snd_timer: Unknown symbol snd_ecards_limit
[   30.598404] snd_timer: Unknown symbol snd_oss_info_register
[   30.598426] snd_timer: Unknown symbol snd_unregister_device
[   30.598454] snd_timer: Unknown symbol snd_hidden_kstrdup
[   30.598476] snd_timer: Unknown symbol snd_device_new
[   30.598529] snd_timer: Unknown symbol snd_hidden_kmalloc
[   30.598551] snd_timer: Unknown symbol snd_register_device_for_dev
[   30.618594] snd: Unknown symbol unregister_sound_special
[   30.618672] snd: Unknown symbol register_sound_special_device
[   30.618892] snd: Unknown symbol sound_class
[   30.638375] ACPI: Power Button (CM) [PWRB]
[   30.639143] snd_timer: Unknown symbol snd_verbose_printd
[   30.639167] snd_timer: Unknown symbol snd_hidden_kzalloc
[   30.639189] snd_timer: Unknown symbol snd_info_register
[   30.639212] snd_timer: Unknown symbol snd_info_create_module_entry
[   30.639238] snd_timer: Unknown symbol snd_info_free_entry
[   30.639264] snd_timer: Unknown symbol snd_hidden_kfree
[   30.639302] snd_timer: Unknown symbol snd_verbose_printk
[   30.639329] snd_timer: Unknown symbol snd_iprintf
[   30.639363] snd_timer: Unknown symbol snd_ecards_limit
[   30.639389] snd_timer: Unknown symbol snd_oss_info_register
[   30.639411] snd_timer: Unknown symbol snd_unregister_device
[   30.639439] snd_timer: Unknown symbol snd_hidden_kstrdup
[   30.639461] snd_timer: Unknown symbol snd_device_new
[   30.639513] snd_timer: Unknown symbol snd_hidden_kmalloc
[   30.639535] snd_timer: Unknown symbol snd_register_device_for_dev
[   30.808286] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   30.852202] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0460)
[   30.852232] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.852272] parport_pc 00:07: reported by Plug and Play ACPI
[   30.852313] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   30.903957] snd_pcm: Unknown symbol snd_verbose_printd
[   30.903982] snd_pcm: Unknown symbol snd_hidden_kzalloc
[   30.904004] snd_pcm: Unknown symbol snd_info_register
[   30.904027] snd_pcm: Unknown symbol snd_info_create_module_entry
[   30.904049] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[   30.904093] snd_pcm: Unknown symbol snd_timer_notify
[   30.904122] snd_pcm: Unknown symbol snd_timer_interrupt
[   30.904145] snd_pcm: Unknown symbol snd_info_free_entry
[   30.904167] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[   30.904193] snd_pcm: Unknown symbol snd_info_get_str
[   30.904215] snd_pcm: Unknown symbol snd_hidden_kcalloc
[   30.904239] snd_pcm: Unknown symbol snd_hidden_kfree
[   30.904297] snd_pcm: Unknown symbol snd_verbose_printk
[   30.904348] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[   30.904370] snd_pcm: Unknown symbol snd_card_file_add
[   30.904396] snd_pcm: Unknown symbol snd_iprintf
[   30.904432] snd_pcm: Unknown symbol snd_major
[   30.904485] snd_pcm: Unknown symbol snd_unregister_device
[   30.904511] snd_pcm: Unknown symbol snd_timer_new
[   30.904534] snd_pcm: Unknown symbol snd_device_new
[   30.904579] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[   30.904617] snd_pcm: Unknown symbol snd_lookup_minor_data
[   30.904639] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[   30.904670] snd_pcm: Unknown symbol snd_info_create_card_entry
[   30.904693] snd_pcm: Unknown symbol snd_power_wait
[   30.904718] snd_pcm: Unknown symbol snd_hidden_kmalloc
[   30.904740] snd_pcm: Unknown symbol snd_device_free
[   30.904780] snd_pcm: Unknown symbol snd_card_file_remove
[   30.904802] snd_pcm: Unknown symbol snd_register_device_for_dev
[   30.904857] snd_pcm: Unknown symbol snd_device_register
[   30.904881] snd_pcm: Unknown symbol snd_info_get_line
[   30.947918] snd_ac97_codec: Unknown symbol snd_hidden_kzalloc
[   30.947942] snd_ac97_codec: Unknown symbol snd_info_register
[   30.947965] snd_ac97_codec: Unknown symbol snd_ctl_add
[   30.948011] snd_ac97_codec: Unknown symbol snd_info_free_entry
[   30.948035] snd_ac97_codec: Unknown symbol snd_hidden_kcalloc
[   30.948058] snd_ac97_codec: Unknown symbol snd_interval_refine
[   30.948081] snd_ac97_codec: Unknown symbol snd_hidden_kfree
[   30.948105] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[   30.948127] snd_ac97_codec: Unknown symbol snd_verbose_printk
[   30.948150] snd_ac97_codec: Unknown symbol snd_ctl_new1
[   30.948176] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[   30.948206] snd_ac97_codec: Unknown symbol snd_component_add
[   30.948228] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[   30.948257] snd_ac97_codec: Unknown symbol snd_iprintf
[   30.948279] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[   30.948347] snd_ac97_codec: Unknown symbol snd_device_new
[   30.948402] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[   30.948433] snd_ac97_codec: Unknown symbol snd_info_get_line
[   30.983810] snd_seq_device: Unknown symbol snd_hidden_kzalloc
[   30.983834] snd_seq_device: Unknown symbol snd_info_register
[   30.983857] snd_seq_device: Unknown symbol snd_info_create_module_entry
[   30.983880] snd_seq_device: Unknown symbol snd_info_free_entry
[   30.983904] snd_seq_device: Unknown symbol snd_seq_root
[   30.983926] snd_seq_device: Unknown symbol snd_hidden_kfree
[   30.983949] snd_seq_device: Unknown symbol snd_verbose_printk
[   30.983971] snd_seq_device: Unknown symbol snd_iprintf
[   30.984004] snd_seq_device: Unknown symbol snd_device_new
[   31.006841] nvidia: module license 'NVIDIA' taints kernel.
[   31.271534] snd: Unknown symbol unregister_sound_special
[   31.271612] snd: Unknown symbol register_sound_special_device
[   31.271833] snd: Unknown symbol sound_class
[   31.274118] snd_seq_device: Unknown symbol snd_hidden_kzalloc
[   31.274142] snd_seq_device: Unknown symbol snd_info_register
[   31.274165] snd_seq_device: Unknown symbol snd_info_create_module_entry
[   31.274187] snd_seq_device: Unknown symbol snd_info_free_entry
[   31.274211] snd_seq_device: Unknown symbol snd_seq_root
[   31.274234] snd_seq_device: Unknown symbol snd_hidden_kfree
[   31.274256] snd_seq_device: Unknown symbol snd_verbose_printk
[   31.274279] snd_seq_device: Unknown symbol snd_iprintf
[   31.274312] snd_seq_device: Unknown symbol snd_device_new
[   31.274606] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.274613] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   31.274662] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   31.282569] snd_rawmidi: Unknown symbol snd_verbose_printd
[   31.282594] snd_rawmidi: Unknown symbol snd_hidden_kzalloc
[   31.282617] snd_rawmidi: Unknown symbol snd_info_register
[   31.282640] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl_compat
[   31.282662] snd_rawmidi: Unknown symbol snd_seq_device_new
[   31.282689] snd_rawmidi: Unknown symbol snd_info_free_entry
[   31.282714] snd_rawmidi: Unknown symbol snd_hidden_kfree
[   31.282736] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[   31.282762] snd_rawmidi: Unknown symbol snd_verbose_printk
[   31.282785] snd_rawmidi: Unknown symbol snd_register_oss_device
[   31.282811] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[   31.282833] snd_rawmidi: Unknown symbol snd_card_file_add
[   31.282860] snd_rawmidi: Unknown symbol snd_iprintf
[   31.282886] snd_rawmidi: Unknown symbol snd_major
[   31.282917] snd_rawmidi: Unknown symbol snd_oss_info_register
[   31.282940] snd_rawmidi: Unknown symbol snd_unregister_device
[   31.282967] snd_rawmidi: Unknown symbol snd_device_new
[   31.282991] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[   31.283027] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[   31.283054] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[   31.283076] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl_compat
[   31.283100] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[   31.283126] snd_rawmidi: Unknown symbol snd_hidden_kmalloc
[   31.283149] snd_rawmidi: Unknown symbol snd_card_file_remove
[   31.283173] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[   31.283198] snd_rawmidi: Unknown symbol snd_device_register
[   31.302946] snd_ca0106: Unknown symbol snd_rawmidi_receive
[   31.302970] snd_ca0106: Unknown symbol snd_hidden_kzalloc
[   31.303009] snd_ca0106: Unknown symbol snd_rawmidi_transmit
[   31.303032] snd_ca0106: Unknown symbol snd_ctl_add
[   31.303054] snd_ca0106: Unknown symbol snd_pcm_new
[   31.303079] snd_ca0106: Unknown symbol snd_card_register
[   31.303102] snd_ca0106: Unknown symbol snd_card_free
[   31.303124] snd_ca0106: Unknown symbol snd_card_proc_new
[   31.303158] snd_ca0106: Unknown symbol snd_hidden_kfree
[   31.303181] snd_ca0106: Unknown symbol snd_ac97_mixer
[   31.303206] snd_ca0106: Unknown symbol snd_ac97_bus
[   31.303228] snd_ca0106: Unknown symbol snd_ctl_find_id
[   31.303250] snd_ca0106: Unknown symbol snd_pcm_set_sync
[   31.303281] snd_ca0106: Unknown symbol snd_verbose_printk
[   31.303322] snd_ca0106: Unknown symbol snd_ctl_new1
[   31.303350] snd_ca0106: Unknown symbol snd_ctl_remove_id
[   31.303387] snd_ca0106: Unknown symbol snd_card_new
[   31.303409] snd_ca0106: Unknown symbol snd_iprintf
[   31.303432] snd_ca0106: Unknown symbol snd_pcm_lib_malloc_pages
[   31.303454] snd_ca0106: Unknown symbol snd_ctl_boolean_mono_info
[   31.303477] snd_ca0106: Unknown symbol snd_pcm_lib_ioctl
[   31.303497] snd_ca0106: Unknown symbol release_and_free_resource
[   31.303522] snd_ca0106: Unknown symbol snd_pcm_lib_free_pages
[   31.303547] snd_ca0106: Unknown symbol snd_pcm_set_ops
[   31.303585] snd_ca0106: Unknown symbol snd_device_new
[   31.303619] snd_ca0106: Unknown symbol snd_rawmidi_new
[   31.303641] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_integer
[   31.303672] snd_ca0106: Unknown symbol snd_rawmidi_set_ops
[   31.303699] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_pages
[   31.303758] snd_ca0106: Unknown symbol snd_pcm_period_elapsed
[   31.303781] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_step
[   31.303805] snd_ca0106: Unknown symbol snd_info_get_line
[   32.217442] lp0: using parport0 (interrupt-driven).
[   32.291251] Adding 2080376k swap on /dev/sda5.  Priority:-1 extents:1 across:2080376k
[  340.523328] EXT3 FS on sda2, internal journal
[  340.691977] device-mapper: uevent: version 1.0.3
[  340.691997] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[  342.465236] ip_tables: (C) 2000-2006 Netfilter Core Team
[  344.467394] No dock devices found.
[  346.709617] NET: Registered protocol family 10
[  346.709794] lo: Disabled Privacy Extensions
[  347.169275] ppdev: user-space parallel port driver
[  347.576684] audit(1216665982.047:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=7582 profile="/usr/sbin/cupsd" namespace="default"
[  349.495313] RPC: Registered udp transport module.
[  349.495316] RPC: Registered tcp transport module.
[  349.607532] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  349.695692] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  349.695715] NFSD: starting 90-second grace period
[  353.171431] r8169: eth0: link up
[  353.171437] r8169: eth0: link up
[  358.188471] NET: Registered protocol family 17
[  372.462366] eth0: no IPv6 routers present
[20309.654189] keytouchd[8704]: segfault at 8 rip 7f8f83c88dc2 rsp 7fff8c48d5e8 error 4

```

sudo /etc/init.d/alsasound start
no output

sudo /etc/init.d/alsasound status
```
ALSA sound driver not loaded.
```

and how do i compile the drivers into the new installed kernel? i booted from another version and installed the alsa drivers.

yes, oss is no longer in init.d

lspci | grep audio:
```
05:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
```

im not sure what i did, but guess messing around with sound is not a good idea. thanks for the help so far.

---

### Post by Derviansoul on 2008-07-21
Just to clear something have you installed the new kernel?? if yes you will have to select it back again on your qgrubeditor, so you can start over again.

if you haven't done that please do it and once you reboot it, please type:

```
dmesg | grep "snd_"
```

basically when i was getting all the errors that you can see with snd_ it was or either coz oss had a chance to put it self into the kernel and boot up, or coz i was using a kernel that had traces of oss.

please just to make it clear tell if you have boot up with the new installed kernel because that it's the most important step to install the alsa back again.


regards

---

### Post by gummygod on 2008-07-21
so where should i get another kernel version from thats ubuntufied?

---

### Post by Derviansoul on 2008-07-22
> **Derviansoul said:**
> Hello
...Now what i've done, first i used qgrubeditor from synaptic to boot from another kernel version: ex i was using 2.24.16 and i used 2.24.19-rt.

Now before you restart you have to remove from the boot process the oss drivers:
```
sudo gzip /etc/init.d/oss
sudo rm -v /etc/init.d/oss

```

You will have to do this before any reboot because otherwise it will load the oss system into your kernel everytime that you boot up.

> **Derviansoul said:**
> 

now you have to remove all the alsa blacklisted drivers, removing all the lines at the end of the file that have "blacklist snd-"
from here:

```
gksu gedit /etc/modprobe.d/blacklist
```

now you should reboot

once u rebooted you should remove the kernel that u were using in the first place:

```

sudo apt-get purge linux-headers-2.6.24-[the version that you were using] linux-headers-2.6.24-[the version that you were using] linux-image-2.6.24-[the version that you were using]-generic linux-restricted-modules-2.6.24-[the version that you were using]-generic

```

now you should remove what's left from this directory
```
rm -Rv /lib/modules/2.6.24-[the version that you were using]-generic/
```




Have you done this step, basically with this step u are removing the kernel that had the oss drivers into it,and you are deleting any possible traces of rubbish left
> **Derviansoul said:**
> 

```

sudo apt-get install linux-headers-2.6.24-[the version that you were using] linux-headers-2.6.24-[the version that you were using] linux-image-2.6.24-[the version that you were using]-generic linux-restricted-modules-2.6.24-[the version that you were using]-generic

```

go to the qgrubeditor and put the kernel version that u first had at the beginning.

reboot


here you are installing it again this should provide you a kernel free of those errors with in dmesg with "snd_" but it's very important that you go back to qgrubeditor and choose the kernel version that you just installed before you rebooted if you haven't done it please do it so you can compile the alsa drivers.


If you followed this steps precisely i really think that they should give you your sound card working. because i recreated this situation a few times before i posted it.

you can also try this:
```

cd /usr/src/alsa/
cd alsa-drivers-xxx
sudo ./sndevices

```

```

modprobe snd-ca0106 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss


```

your alsa page recommends to do this but i never needed to do it.

regards

---

### Post by fogelfink on 2008-07-22
I followed the steps of this thread,trying to recover from a failed OSS install, but still have no sound back!  
ALSA seems to be installed according to ```
 alsactl -v
``` I have the latest version.  I removed the kernel I used before, and reinstalled it.  

What I wasn't sure about was when I used this command ```
rm -Rv /lib/modules/2.6.24-[the version that you were using]-generic/
``` I was asked about lots of subdirectories that were moved into.  There was no indication in the terminal as what to do, so I simply typed y and enter, and after a few lines I was back to user@user.  

Still the same problem in the System/Preferences/Sound tab: When I select alsa and test it, I get this > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. error message.

Where do I turn next?

---

### Post by Derviansoul on 2008-07-22
> **fogelfink said:**
> 
What I wasn't sure about was when I used this command ```
rm -Rv /lib/modules/2.6.24-[the version that you were using]-generic/
``` I was asked about lots of subdirectories that were moved into.  There was no indication in the terminal as what to do, so I simply typed y and enter, and after a few lines I was back to user@user.  


hello

basically older installations of oss and alsa keep their some files there, the only way to do it, it's to remove it before you start using the new installed kernel

ex:

when i type on uname -r

i get:

```
2.6.24-16-generic
```

so on that line that i mentioned i would type 
```
rm -Rv /lib/modules/2.6.24-16-generic/
```

this line just removes all traces of the old kernel before you installing the new one because apt-get wont remove them, this line it's quite important because if you have old alsa settings or oss settings it will remove them.

the big problem with the alsa drivers it's if there is traces of old drivers or other oss drivers and whenever you will try to do 
```

modprobe [your drivers] ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```
most likely you will get errors and wont let you register those drivers.

basicaly all the steps that i mentioned here were taken from [here]("https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation")

there are there a few other steps that actually didn't worked out for me,so i didnt put them here, but they're worth a go. but please don't forget that whenever you are trying to put alsa back again you have to make sure that there is no traces of oss.

regards

---

### Post by Derviansoul on 2008-07-23
i'm really sorry if this wont work for any of us, since i've posted everything that i've done, and i told us everything that i know about it.
regards

---

### Post by gummygod on 2008-07-24
alright i finally realized what u were asking me to do. so i reinstalled the kernel i was using and that causes the loging/logout sounds to play as they should, but most other sounds dont work. amarok gives an error saying it is unable to initialize audio drivers, sys>pref>sound pressing test gives errors in alsa.  ESD works fine, but things using alsa dont.  but i installed alsa with my fresh kernel, so that is good.  any thoughts?

thank you much

---

### Post by Derviansoul on 2008-07-24
humm thats weird is alsamixer working? which driver are you using is it a laptop? there is some problems with sound cards in laptops. can you show me the output of

```
 lspci | grep "Audio"
```
and
```
dmesg
```
```
aplay -l
```

regards

---

### Post by gummygod on 2008-07-25
lspci | grep audio:

```
05:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
```

dmesg

```
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1208 pages reserved
[    0.000000]   DMA zone: 2735 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515531
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=2ceb3a8d-feb1-443d-84d3-453316236c88
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   18.841825] time.c: Detected 2333.333 MHz processor.
[   18.842762] Console: colour VGA+ 80x25
[   18.842765] console [tty0] enabled
[   18.845148] Checking aperture...
[   18.845188] Calgary: detecting Calgary via BIOS EBDA area
[   18.845190] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   18.860741] Memory: 2053896k/2096000k available (2466k kernel code, 41716k reserved, 1309k data, 316k init)
[   18.860814] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   18.939623] Calibrating delay using timer specific routine.. 4669.84 BogoMIPS (lpj=9339685)
[   18.939716] Security Framework initialized
[   18.939755] SELinux:  Disabled at boot.
[   18.939797] AppArmor: AppArmor initialized
[   18.939834] Failure registering capabilities with primary security module.
[   18.940039] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.940974] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.941409] Mount-cache hash table entries: 256
[   18.941547] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.941607] CPU: L2 cache: 4096K
[   18.941642] CPU 0/0 -> Node 0
[   18.941676] using mwait in idle threads.
[   18.941711] CPU: Physical Processor ID: 0
[   18.941746] CPU: Processor Core ID: 0
[   18.941784] CPU0: Thermal monitoring enabled (TM2)
[   18.941829] SMP alternatives: switching to UP code
[   18.942499] Early unpacking initramfs... done
[   19.248465] ACPI: Core revision 20070126
[   19.248530] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.291131] Using local APIC timer interrupts.
[   19.333944] APIC timer calibration result 20833343
[   19.333946] Detected 20.833 MHz APIC timer.
[   19.334040] SMP alternatives: switching to SMP code
[   19.334635] Booting processor 1/2 APIC 0x1
[   19.345012] Initializing CPU#1
[   19.421811] Calibrating delay using timer specific routine.. 4666.68 BogoMIPS (lpj=9333375)
[   19.421816] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.421817] CPU: L2 cache: 4096K
[   19.421819] CPU 1/1 -> Node 0
[   19.421820] CPU: Physical Processor ID: 0
[   19.421821] CPU: Processor Core ID: 1
[   19.421825] CPU1: Thermal monitoring enabled (TM2)
[   19.422251] Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[   19.422314] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.442666] Brought up 2 CPUs
[   19.442761] CPU0 attaching sched-domain:
[   19.442763]  domain 0: span 03
[   19.442764]   groups: 01 02
[   19.442766]   domain 1: span 03
[   19.442767]    groups: 03
[   19.442769] CPU1 attaching sched-domain:
[   19.442770]  domain 0: span 03
[   19.442771]   groups: 02 01
[   19.442773]   domain 1: span 03
[   19.442774]    groups: 03
[   19.442941] net_namespace: 120 bytes
[   19.443272] Time: 20:23:03  Date: 07/25/08
[   19.443324] NET: Registered protocol family 16
[   19.443497] ACPI: bus type pci registered
[   19.443586] PCI: Using configuration type 1
[   19.443621] mtrr: your CPUs had inconsistent variable MTRR settings
[   19.443658] mtrr: probably your BIOS does not setup all CPUs.
[   19.443694] mtrr: corrected configuration.
[   19.444685] ACPI: EC: Look up EC in DSDT
[   19.447991] ACPI: Interpreter enabled
[   19.448030] ACPI: (supports S0 S3 S4 S5)
[   19.448169] ACPI: Using IOAPIC for interrupt routing
[   19.452053] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.452655] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   19.452694] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   19.453255] PCI: Transparent bridge - 0000:00:1e.0
[   19.453314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.453430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   19.453490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   19.453549] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   19.453607] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   19.465350] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   19.465781] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   19.466255] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   19.466679] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   19.467104] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   19.467528] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   19.467952] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   19.468425] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   19.468867] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.468924] pnp: PnP ACPI init
[   19.468963] ACPI: bus type pnp registered
[   19.470800] pnpacpi: exceeded the max number of mem resources: 12
[   19.470936] pnp: PnP ACPI: found 14 devices
[   19.470971] ACPI: ACPI bus type pnp unregistered
[   19.471171] PCI: Using ACPI for IRQ routing
[   19.471207] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.485777] NET: Registered protocol family 8
[   19.485814] NET: Registered protocol family 20
[   19.485876] PCI-GART: No AMD northbridge found.
[   19.485915] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   19.486077] hpet0: 4 64-bit timers, 14318180 Hz
[   19.487136] AppArmor: AppArmor Filesystem Enabled
[   19.489756] Time: tsc clocksource has been installed.
[   19.489797] Switched to high resolution mode on CPU 0
[   19.490655] Switched to high resolution mode on CPU 1
[   19.497756] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   19.497795] system 00:01: ioport range 0x290-0x29f has been reserved
[   19.497833] system 00:01: ioport range 0x800-0x87f has been reserved
[   19.497871] system 00:01: ioport range 0x290-0x294 has been reserved
[   19.497909] system 00:01: ioport range 0x880-0x88f has been reserved
[   19.497958] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[   19.497998] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   19.498046] system 00:0c: iomem range 0xce000-0xcffff has been reserved
[   19.498083] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   19.498121] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   19.498159] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   19.498197] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
[   19.498242] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   19.498280] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
[   19.498325] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   19.498363] system 00:0c: iomem range 0xfed10000-0xfed1dfff has been reserved
[   19.498401] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[   19.498439] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.498484] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[   19.498807] PCI: Bridge: 0000:00:01.0
[   19.498842]   IO window: b000-bfff
[   19.498878]   MEM window: f4000000-f6ffffff
[   19.498913]   PREFETCH window: e0000000-efffffff
[   19.498949] PCI: Bridge: 0000:00:1c.0
[   19.498985]   IO window: a000-afff
[   19.499513]   MEM window: disabled.
[   19.499548]   PREFETCH window: disabled.
[   19.499585] PCI: Bridge: 0000:00:1c.3
[   19.499620]   IO window: 9000-9fff
[   19.499656]   MEM window: disabled.
[   19.499691]   PREFETCH window: disabled.
[   19.499728] PCI: Bridge: 0000:00:1c.4
[   19.499763]   IO window: c000-cfff
[   19.499799]   MEM window: f7000000-f8ffffff
[   19.499835]   PREFETCH window: 80000000-800fffff
[   19.499873] PCI: Bridge: 0000:00:1e.0
[   19.499908]   IO window: d000-dfff
[   19.499944]   MEM window: disabled.
[   19.499979]   PREFETCH window: disabled.
[   19.500022] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.500092] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.500109] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.500179] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.500192] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   19.500262] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   19.500275] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   19.500345] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   19.500353] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.500359] NET: Registered protocol family 2
[   19.533742] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   19.534284] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   19.535418] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.535847] TCP: Hash tables configured (established 262144 bind 65536)
[   19.535885] TCP reno registered
[   19.545775] checking if image is initramfs... it is
[   20.148732] Freeing initrd memory: 7948k freed
[   20.151663] audit: initializing netlink socket (disabled)
[   20.151717] audit(1217017383.260:1): initialized
[   20.153257] VFS: Disk quotas dquot_6.5.1
[   20.153344] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   20.153464] io scheduler noop registered
[   20.153499] io scheduler anticipatory registered
[   20.153535] io scheduler deadline registered
[   20.153639] io scheduler cfq registered (default)
[   20.156785] Boot video device is 0000:01:00.0
[   20.156898] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.156927] assign_interrupt_mode Found MSI capability
[   20.156983] Allocate Port Service[0000:00:01.0:pcie00]
[   20.157036] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.157065] assign_interrupt_mode Found MSI capability
[   20.157124] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.157145] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.157202] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   20.157232] assign_interrupt_mode Found MSI capability
[   20.157291] Allocate Port Service[0000:00:1c.3:pcie00]
[   20.157314] Allocate Port Service[0000:00:1c.3:pcie02]
[   20.157369] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   20.157399] assign_interrupt_mode Found MSI capability
[   20.157458] Allocate Port Service[0000:00:1c.4:pcie00]
[   20.157480] Allocate Port Service[0000:00:1c.4:pcie02]
[   20.174608] Real Time Clock Driver v1.12ac
[   20.174720] Linux agpgart interface v0.102
[   20.174755] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.174894] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.175298] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.175852] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.175941] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.176048] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.176367] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.176406] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.188912] mice: PS/2 mouse device common for all mice
[   20.188977] cpuidle: using governor ladder
[   20.189016] cpuidle: using governor menu
[   20.189149] NET: Registered protocol family 1
[   20.189218] registered taskstats version 1
[   20.189331]   Magic number: 0:829:397
[   20.189404]   hash matches device random
[   20.189447] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   20.189493] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.189530] EDD information not available.
[   20.189569] Freeing unused kernel memory: 316k freed
[   20.222961] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.314447] fuse init (API version 7.9)
[   20.327782] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.327959] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   20.328179] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.328271] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.328372] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.460672] usbcore: registered new interface driver usbfs
[   20.460727] usbcore: registered new interface driver hub
[   20.460812] r8169 Gigabit Ethernet driver 2.2LK loaded
[   20.460869] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.460953] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   20.461175] eth0: RTL8168b/8111b at 0xffffc200008ac000, 00:1a:4d:50:1d:14, XID 38000000 IRQ 507
[   20.462746] usbcore: registered new device driver usb
[   20.468871] USB Universal Host Controller Interface driver v3.0
[   20.468941] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.469017] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   20.469020] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   20.469226] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   20.469294] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[   20.469419] usb usb1: configuration #1 chosen from 1 choice
[   20.469470] hub 1-0:1.0: USB hub found
[   20.469509] hub 1-0:1.0: 2 ports detected
[   20.572155] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   20.572235] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   20.572238] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   20.572289] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   20.572354] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e500
[   20.572462] usb usb2: configuration #1 chosen from 1 choice
[   20.572512] hub 2-0:1.0: USB hub found
[   20.572549] hub 2-0:1.0: 2 ports detected
[   20.588136] SCSI subsystem initialized
[   20.602700] libata version 3.00 loaded.
[   20.675972] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.676050] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   20.676052] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   20.676103] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   20.676169] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[   20.676275] usb usb3: configuration #1 chosen from 1 choice
[   20.676325] hub 3-0:1.0: USB hub found
[   20.676363] hub 3-0:1.0: 2 ports detected
[   20.779727] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   20.779803] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.779806] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.779857] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   20.779922] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[   20.780033] usb usb4: configuration #1 chosen from 1 choice
[   20.780084] hub 4-0:1.0: USB hub found
[   20.780121] hub 4-0:1.0: 2 ports detected
[   20.883533] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   20.883610] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.883613] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.883675] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   20.883740] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[   20.883851] usb usb5: configuration #1 chosen from 1 choice
[   20.883901] hub 5-0:1.0: USB hub found
[   20.883938] hub 5-0:1.0: 2 ports detected
[   20.986812] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.986888] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.986890] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.986942] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   20.987010] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[   20.987112] usb usb6: configuration #1 chosen from 1 choice
[   20.987162] hub 6-0:1.0: USB hub found
[   20.987198] hub 6-0:1.0: 2 ports detected
[   21.090765] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   21.091645] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   21.091650] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.091725] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   21.095663] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   21.095668] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9000000
[   21.114485] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.114613] usb usb7: configuration #1 chosen from 1 choice
[   21.114665] hub 7-0:1.0: USB hub found
[   21.114704] hub 7-0:1.0: 6 ports detected
[   21.214373] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   21.215226] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.215231] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.215315] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   21.219265] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   21.219269] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9001000
[   21.234259] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.234386] usb usb8: configuration #1 chosen from 1 choice
[   21.234442] hub 8-0:1.0: USB hub found
[   21.234486] hub 8-0:1.0: 6 ports detected
[   21.342182] ata_piix 0000:00:1f.2: version 2.12
[   21.342187] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   21.342379] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   21.342471] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.342542] scsi0 : ata_piix
[   21.342610] scsi1 : ata_piix
[   21.343525] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   21.343564] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   21.513848] ata1.00: HPA unlocked: 488130922 -> 488397168, native 488397168
[   21.513895] ata1.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   21.513933] ata1.00: 488397168 sectors, multi 16: LBA48 
[   21.521945] ata1.00: configured for UDMA/133
[   21.688080] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   21.688169] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   21.688344] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   21.688430] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.688459] scsi2 : ata_piix
[   21.688520] scsi3 : ata_piix
[   21.688893] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[   21.688931] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[   22.004865] ata3.00: ATAPI: ASUS    DRW-1814BLT, 1.04, max UDMA/66
[   22.176524] ata3.00: configured for UDMA/66
[   22.343158] scsi 2:0:0:0: CD-ROM            ASUS     DRW-1814BLT      1.04 PQ: 0 ANSI: 5
[   22.349255] Driver 'sd' needs updating - please use bus_type methods
[   22.349339] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   22.349384] sd 0:0:0:0: [sda] Write Protect is off
[   22.349420] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.349432] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.349506] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   22.349549] sd 0:0:0:0: [sda] Write Protect is off
[   22.349587] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.349599] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.349647]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.364026]  sda1 sda2 sda3 < sda5 >
[   22.388051] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.390696] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.390745] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   22.392793] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   22.392840] Uniform CD-ROM driver Revision: 3.20
[   22.392901] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   22.649664] Attempting manual resume
[   22.649700] swsusp: Resume From Partition 8:5
[   22.649701] PM: Checking swsusp image.
[   22.649830] PM: Resume from disk failed.
[   22.688960] kjournald starting.  Commit interval 5 seconds
[   22.688966] EXT3-fs: mounted filesystem with ordered data mode.
[   31.075208] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.226685] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.231251] logips2pp: Detected unknown logitech mouse model 101
[   31.250609] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.266761] iTCO_vendor_support: vendor-support=0
[   31.276676] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.493658] input: Power Button (FF) as /devices/virtual/input/input3
[   31.549998] ACPI: Power Button (FF) [PWRF]
[   31.550077] input: Power Button (CM) as /devices/virtual/input/input4
[   31.597891] ACPI: Power Button (CM) [PWRB]
[   31.714321] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   31.739711] nvidia: module license 'NVIDIA' taints kernel.
[   31.976304] parport_pc 00:07: reported by Plug and Play ACPI
[   31.976383] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   31.978081] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0460)
[   31.978146] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.054356] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.054436] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   32.054508] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   32.219732] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[   32.219819] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   33.261787] lp0: using parport0 (interrupt-driven).
[   33.334986] Adding 2080376k swap on /dev/sda5.  Priority:-1 extents:1 across:2080376k
[   33.756559] EXT3 FS on sda2, internal journal
[   33.852912] device-mapper: uevent: version 1.0.3
[   33.852931] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   34.909764] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.565714] No dock devices found.
[   38.015988] NET: Registered protocol family 10
[   38.016148] lo: Disabled Privacy Extensions
[   38.349224] ppdev: user-space parallel port driver
[   38.601387] audit(1217035402.402:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5457 profile="/usr/sbin/cupsd" namespace="default"
[   41.342391] RPC: Registered udp transport module.
[   41.342394] RPC: Registered tcp transport module.
[   41.408679] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   41.481535] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   41.506964] NFSD: starting 90-second grace period
[   49.912706] r8169: eth0: link up
[   49.912712] r8169: eth0: link up
[   54.719313] NET: Registered protocol family 17
[   66.886034] eth0: no IPv6 routers present
[   75.970724] keytouchd[6619]: segfault at 8 rip 7f55da205dc2 rsp 7fffe2a0a878 error 4

```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


so reinstalling the kernel, i dont know what it did, but somehow thats not working. altho the version i booted from to delete that version DOES have semi-working sound. so these results are from that, which works fine w/ me (except sound). any ideas now?
thanks for all the help

---

### Post by Derviansoul on 2008-07-26
hello

really don't understand much of whats going on now, i can't find nothing wrong with your setup,please try:

```

speaker-test -Dplug:front -c2

speaker-test -Dplug:surround51 -c6

```

you should have output from at least your front left and right

have you unmuted all the your channels with your alsamixer?
have you also tried other devices with on gnome sound configuration?
regards

---

### Post by gummygod on 2008-07-26
speaker-test -Dplug:front -c2:

```

speaker-test 1.0.15

Playback device is plug:front
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy

```

yea, i unmuted everything and turned the channels up. but i get errors w/ amarok and the sound test in sys>pref>sound still.  any ideas?

---

### Post by Yellow Pasque on 2008-07-26
It's too late now, but when you had OSS4, did you set vmix to multich instead of stereo? The latest OSS4.1 has this setting right in a drop-down menu in ossxmix.

---

### Post by Derviansoul on 2008-07-27
> **Temüjin said:**
> It's too late now, but when you had OSS4, did you set vmix to multich instead of stereo? The latest OSS4.1 has this setting right in a drop-down menu in ossxmix.

I did change the option of the ossxmixer to multichannel and it never worked,if you make a quick search through oss forums it seems that the surround sound doesn't work for anyone, and besides that in some movies the sound volume was really low, ekiga refused to detect oss drivers:S, i think OSS could be better than alsa, but at the moment they are not there yet maybe for developers...

> **gummygod said:**
> speaker-test -Dplug:front -c2:

```

speaker-test 1.0.15

Playback device is plug:front
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy

```

yea, i unmuted everything and turned the channels up. but i get errors w/ amarok and the sound test in sys>pref>sound still.  any ideas?

i'm sorry but i really don't know what it could be i googled your error and i could only find this [link]("http://www.linuxquestions.org/questions/linux-hardware-18/fix-for-aoalsa-playback-open-error-device-or-resource-busy.-no-coding-624869/")

besides that i'ven't got a clue since that never happen to me:(
sorry

regards

---

### Post by gummygod on 2008-07-27
alright, so i followed that guide in the link to stop audio previews. but ESD was still running so i killed it. and now i got fully working sound (at least in this kernel).  all 6 channels are up and working prefectly.  thank you Derviansoul for all the help

and temujin, i did have vmix=1 in ossxmix checked. something like that i remember.  

last time i **** around with sound in ubuntu. but that was unnecessarily problematic for trying to get multiple sounds to play simultaneously.

---

### Post by Derviansoul on 2008-07-28
> **gummygod said:**
> alright, so i followed that guide in the link to stop audio previews. but ESD was still running so i killed it. and now i got fully working sound (at least in this kernel).  all 6 channels are up and working prefectly.  thank you Derviansoul for all the help

and temujin, i did have vmix=1 in ossxmix checked. something like that i remember.  

last time i **** around with sound in ubuntu. but that was unnecessarily problematic for trying to get multiple sounds to play simultaneously.

No problems glad i could i help, regards, how is your alsamixer everytime that u restart?i have to do

```
sudo alsactl restore 0
```

because my settings wont be saved by sudo alsactl store 0, hope u don't have this problem.
regards

---

