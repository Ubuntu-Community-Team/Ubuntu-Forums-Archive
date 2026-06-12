---
title: "RealTek 8192e and 64 bit amd not working"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by warmastr on 2011-01-01
Hello,

     I have looked through several posts and have tried many many  different things to get my wireless card working all to no avail. I am  new to ubuntu and linux in general but have a pretty good understanding  of computers.

     I have tried ndiswrapper using 32 bit and 64 bit winxp drivers and  the 32 bit driver just doesn't work period (as expected.) The 64 bit  driver locked the system up completely and I ended up reinstalling  ubunto. I have now reinstalled and updated and upgraded ubunto 10 times  in the last 3 days of trying to get this to work and need some external  help!

     using ```
lshw -C network
``` I do see my network card and driver. 

Where I am at currently: I have a fresh install of ubunto 10.04 with it  upgraded and updated. I do not have ndiswrapper gtk installed and I have  not downloaded any drivers for the wireless card. Would someone please  help me? Thank you!

JJ

---

### Post by PatchesTheCaveman on 2011-01-01
Hi warmastr.  Happy New Year!

Please run this command and copy/paste what appears:
```
lspci -v
```

---

### Post by warmastr on 2011-01-01
Hi Patches, Happy New Year to you too! Thanks for offering to help!

warmaster@warmaster-laptop:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64
    Capabilities: <access denied>

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: cfd00000-cfefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c8000000-c81fffff
    Prefetchable memory behind bridge: 00000000c8200000-00000000c83fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c8400000-c85fffff
    Prefetchable memory behind bridge: 00000000c8600000-00000000c87fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f0300000-f03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c8800000-c89fffff
    Prefetchable memory behind bridge: 00000000c8a00000-00000000c8bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Memory behind bridge: f0500000-f05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8430 [size=8]
    I/O ports at 8424 [size=4]
    I/O ports at 8428 [size=8]
    I/O ports at 8420 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f0208000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0004000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0005000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0208400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0006000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0007000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f0208800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, slow devsel, latency 64, IRQ 17
    Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=09, subordinate=0d, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
    Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 1000 [size=256]
    Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl819xE
    Kernel modules: r8192_pci

04:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f0300000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at b000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

0a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01) (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0501000 (32-bit, non-prefetchable) [size=4K]
    Memory at f0500000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

0a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0503800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

0a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f0502000 (32-bit, non-prefetchable) [size=4K]
    Memory at f0503000 (32-bit, non-prefetchable) [size=2K]
    Memory at f0500800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>

warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-01
Run this command and copy/paste it back here:
```
dmesg | grep -i rtl
```

---

### Post by warmastr on 2011-01-01
warmaster@warmaster-laptop:~$ dmesg | grep -i rtl
[    7.767880] Linux kernel driver for RTL8192 based WLAN cards
[    7.767936] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.767943] rtl819xE 0000:02:00.0: setting latency timer to 64
[   14.269212] rtl819xE: PlatformInitFirmware()==>
[   14.269251] rtl819xE 0000:02:00.0: firmware: requesting RTL8192E/boot.img
[   14.775657] rtl819xE 0000:02:00.0: firmware: requesting RTL8192E/main.img
[   14.950025] rtl819xE:Download Firmware: Put code fail!
[   14.950032] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   14.950035] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   14.950037] rtl819xE:ERR in init_firmware()
[   14.950041] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-01
There is an update for your card's firmware that should fix this problem.  To download it, you must plug in to a wired Ethernet connection and run the following commands:
```
sudo apt-get update
sudo apt-get install linux-firmware
```

Reboot afterward to let the changes take effect.

---

### Post by warmastr on 2011-01-01
I will try that and post back, thank you!

JJ

---

### Post by warmastr on 2011-01-01
Ok it still does not work here is the ```
dmesg | grep -i rtldmesg | grep -i rtl 
```

warmaster@warmaster-laptop:~$ dmesg | grep -i rtl
[   13.539850] Linux kernel driver for RTL8192 based WLAN cards
[   13.539898] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.539905] rtl819xE 0000:02:00.0: setting latency timer to 64
[   14.300939] rtl819xE: PlatformInitFirmware()==>
[   14.300962] rtl819xE 0000:02:00.0: firmware: requesting RTL8192E/boot.img
[   14.326460] rtl819xE 0000:02:00.0: firmware: requesting RTL8192E/main.img
[   14.350089] rtl819xE:Download Firmware: Put code fail!
[   14.350094] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   14.350097] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   14.350099] rtl819xE:ERR in init_firmware()
[   14.350103] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by chili555 on 2011-01-01
> firmware: requesting RTL8192E/boot.imgDo you have a directory RTL8192E?```
ls /lib/firmware | grep RTL
```Does it contain the firmware files?```
ls /lib/firmware/RTL8192E
```

---

### Post by PatchesTheCaveman on 2011-01-01
Try updating your drivers.  Run:
```
sudo apt-get install linux-backports-modules-wireless-`lsb_release -cs`-generic
```

Please note that the ` character is an accent grave, not a apostrophe/single quote.  It is located to the left of the 1 key and underneath Escape on most US keyboards.

---

### Post by warmastr on 2011-01-01
@ Chili555

warmaster@warmaster-laptop:~$ ls /lib/firmware | grep RTL
RTL8192E
RTL8192SE
warmaster@warmaster-laptop:~$ 

and

warmaster@warmaster-laptop:~$ ls /lib/firmware/RTL8192E
boot.img  data.img  main.img
warmaster@warmaster-laptop:~$ 



@patches

Im updating now and will post back with results

thanks to all

---

### Post by warmastr on 2011-01-01
Ok, still not working after updating the drivers...

---

### Post by warmastr on 2011-01-02
Ok, so after the very last thing you had me do (update the drivers) I did nothing more besides restart the computer at that time. So i turned on the computer today and now I don't have a wired connection either. This is very frustrating.

How can I undo what was last done?

---

### Post by PatchesTheCaveman on 2011-01-02
```
sudo apt-get purge linux-backports-modules-wireless-`lsb_release -cs`-generic
```

But it's very unlikely that broke your wired connection because the wired network drivers come in a completely different package. (linux-backports-modules-net-*[maverick|lucid]*-generic)

---

### Post by warmastr on 2011-01-02
well, I was actually just getting back on to say that it must have been a fluke because I just restarted and now I am back online with a wired connection.

---

### Post by PatchesTheCaveman on 2011-01-02
Try running this:
```
sudo modprobe -r rtl819xE 
sudo modprobe r8192_pci
```

---

### Post by warmastr on 2011-01-02
neither one worked:

warmaster@warmaster-laptop:~$ sudo modprobe -r rtl819xE 
[sudo] password for warmaster: 
FATAL: Module rtl819xE not found.
warmaster@warmaster-laptop:~$ sudo modprobe r8192se_pci
warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-02
Run ```
lsmod
``` and copy/paste please.

---

### Post by warmastr on 2011-01-02
warmaster@warmaster-laptop:~$ lsmod
Module                  Size  Used by
r8192se_pci           489163  0 
binfmt_misc             7960  1 
joydev                 11104  0 
ppdev                   6375  0 
snd_hda_intel          25741  2 
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62595  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71251  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
fglrx                2353486  31 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
i2c_piix4               9639  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_core              45423  0 
atl1c                  33232  0 
edac_mce_amd            9278  0 
shpchp                 33711  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3764  1 sdhci
r8192_pci             269210  0 
psmouse                64576  0 
serio_raw               4918  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
video                  20623  0 
output                  2503  1 video
usbhid                 41116  0 
ohci1394               30260  0 
hid                    83472  1 usbhid
pata_atiixp             4209  0 
ieee1394               94771  1 ohci1394
ahci                   37870  2 
warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-02
That looks good.  Try ```
sudo iwconfig
```

---

### Post by warmastr on 2011-01-02
warmaster@warmaster-laptop:~$ sudo iwconfig
[sudo] password for warmaster: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-02
Okay, now do ```
sudo iwlist wlan0 scan
```

---

### Post by warmastr on 2011-01-02
warmaster@warmaster-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-02
Of course not.

Okay, lets check something simple since the complicated isn't working out very well for us.  Download the rfkill package:
```
sudo apt-get install rfkill
```

Then, run it:
```
sudo rfkill list
```

Is anything showing as hard or soft blocked?

---

### Post by warmastr on 2011-01-02
warmaster@warmaster-laptop:~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,990B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe rfkill 0.3-3 [7,990B]
Fetched 7,990B in 0s (15.5kB/s) 
Selecting previously deselected package rfkill.
(Reading database ... 145849 files and directories currently installed.)
Unpacking rfkill (from .../rfkill_0.3-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.3-3) ...
warmaster@warmaster-laptop:~$ sudo rfkill list
warmaster@warmaster-laptop:~$ 


nothing showed for rfkill list

---

### Post by PatchesTheCaveman on 2011-01-02
What's the manufacturer/model of your laptop?

---

### Post by warmastr on 2011-01-02
It is a Toshiba Satellite P505D-S8935

---

### Post by PatchesTheCaveman on 2011-01-02
Try running:
```
sudo modprobe toshiba_acpi
```

and see if your wireless card then shows up when you run ```
sudo rfkill list
```

---

### Post by warmastr on 2011-01-02
warmaster@warmaster-laptop:~$ sudo modprobe toshiba_acpi
[sudo] password for warmaster: 
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.32-27-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device
warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-02
Try ```
sudo modprobe omnibook
```

---

### Post by warmastr on 2011-01-02
nothing happened :(

---

### Post by PatchesTheCaveman on 2011-01-02
Nothing happened as in it didn't output anything )it wasn't supposed to) or your wireless still doesn't work?

Did the output of rfkill change at all?

Try flipping your wireless switch (which is probably a Fn key combo) and running ```
sudo iwlist wlan0 scan
``` again.  Sometime the kernel needs some coaxing to turn your wireless card on.

---

### Post by warmastr on 2011-01-02
I have an external physical switch and I did as you asked and these are the results.

warmaster@warmaster-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for warmaster: 
wlan0     No scan results

warmaster@warmaster-laptop:~$ 


In response to my previous post, nothing happened as in:

warmaster@warmaster-laptop:~$ sudo modprobe omnibook
warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-02
The only other thing you can try is downloading, compiling, and installing the official Realtek drivers.

Someone in [this thread](http://ubuntuforums.org/showthread.php?t=1464448) had trouble with a Realtek card on Toshiba hardware and got it fixed that way.

To do that, you'll need the Linux kernel headers and build-essential package:
```
sudo apt-get build-essential linux-headers-`uname -r`
```

Then download them from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

They're the "Unix (Linux) drivers under RTL8192SE.  There should be a README file in the package with instructions on how to install.

If you have any trouble, let me know.

---

### Post by warmastr on 2011-01-02
im about to step away for dinner and I will try it when I get back. Thank you so much for helping.

JJ

---

### Post by warmastr on 2011-01-02
I have looked through that post and the problem is, that post relates to the 8192SE model and I have the 8192E so those drivers will not work for me.

I think I found the right driver on one of the posts I sifted through so may give it a shot if I can find the right driver again. Ill post back with results..may have to reinstall this AGAIN :( if it gets screwed up like last time I tried that driver... it locked my desktop up and I couldn't click on anything.

---

### Post by warmastr on 2011-01-03
This command: 

sudo apt-get build-essential linux-headers-`uname -r`
does not work for me, I get:

warmaster@warmaster-laptop:~$ sudo apt-get build-essential linux-headers-`uname -r`
[sudo] password for warmaster: 
E: Invalid operation build-essential
warmaster@warmaster-laptop:~$

---

### Post by PatchesTheCaveman on 2011-01-03
My bad!  Forgot "install":
```
sudo apt-get build-essential linux-headers-`uname -r`
```

Something about the "get" in *apt-get* makes me always forget the "install" portion, because I never forget it with yum on Fedora.  :-(

---

### Post by warmastr on 2011-01-03
ok so would I need to get the build essential and kernal headers prior to doing what is on this site?

[http://sunnavy.net/entry/5DD29546DF1511DFA60FA23B96352BA3](http://sunnavy.net/entry/5DD29546DF1511DFA60FA23B96352BA3)

and at what point does install go in there? lol before or after build essential ?

---

### Post by PatchesTheCaveman on 2011-01-03
Wow.  I'm batting 1000 today.  It's:
```
sudo apt-get **install** build-essential linux-headers-`uname -r`
```

Good grief!

I would be leery of downloading drivers from non-official sources.  But then again I wear a tinfoil hat when I go out into public to stop the government from reading my mind with their brainwaves... :-D

That being said, I might have pointed you at the wrong driver so I'll double-check to be sure.

---

### Post by PatchesTheCaveman on 2011-01-03
I can't find that download on Realtek's site either so I guess you'll have to trust that guy.

And yes you'll need build-essential and the kernel headers to do that.

---

### Post by warmastr on 2011-01-03
yeah im positive you pointed me to the wrong driver. I found the driver name from this ubuntoforums post:

[http://ubuntuforums.org/showpost.php?p=9146770&postcount=44](http://ubuntuforums.org/showpost.php?p=9146770&postcount=44)

since the link for that driver was broken I googled rtl8192e_linux_2.6.0014.0401.2010 and found that site.

---

### Post by warmastr on 2011-01-03
grrrrr STILL not working I am sooo frustrated. I almost wish I had not dbanned my hard drive. If I had known linux would not support realtek network cards I wouldn't have done this.

---

### Post by PatchesTheCaveman on 2011-01-03
Give the compat-wireless drivers from the Linux kernel wireless team a shot:

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

---

### Post by warmastr on 2011-01-03
warmaster@warmaster-laptop:~$ sudo apt-get install linux-backports-modules-wireless-lucid-generic
[sudo] password for warmaster: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-wireless-lucid-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
warmaster@warmaster-laptop:~$

how can I get the drivers and everything back to its original state after first installing ubunto? The reason I ask is, what if something I tried 20 steps ago is affecting what I just did?

---

### Post by PatchesTheCaveman on 2011-01-03
You can reboot to make sure your kernel modules state is default.

I would just give the compat-wireless drivers a shot because:
A.  they're the latest, greatest, and most sure to work drivers the Linux kernel team has to offer
B.  they do a good job of getting all other drivers out of the way so they'll clear out any old cruft you have going

They've also been updated 20 times or so since Ubuntu last made their package of them.

---

### Post by warmastr on 2011-01-03
I have a viable solution for myself. This may not work for everyone. I didn't buy the computer because it was 64 Bit, I bought the computer rather because it was the best bang for the buck so to speak. So I installed a 32 bit version of 10.04.1 and now the video doesn't work after upgrading to 10.10 so I am off to figure that one out lol. But, the wireless works out of the box on the 32 bit so it is just the fact that it is a 64 bit OS that is giving the realtek the trouble.  Thanks for the help Patches.

JJ

---

### Post by PatchesTheCaveman on 2011-01-03
If you have 3 GB of RAM or less, there really isn't a reason to run a 64-bit OS.  I'm running 32-bit Ubuntu right now simply because my netbook doesn't have a 64-bit processor and I was too lazy to download two ISOs.

Glad to hear everything is working okay now.  :-D

---

### Post by eldergs on 2011-02-23
Using Ubuntu 10.10 64bits

Hi. I have the same problem. But, readying so many forum and post, I resolved the problem.

Sorry for my bad english.

First, open your terminal.

Run the code:

**lsmod | grep 819**

I think will show:

r8192e_pci
r8192se_pci

This is the conflicting drivers.

Now, run this code (to add r8192se_pci in blacklist):

[B]sudo su
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
exit[/B]

**Reboot**

Now, Download the newest driver from realtek, they mail me with instructions and file (I post in some servers)

[http://eldergs.4shared.com](http://eldergs.4shared.com)
[http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html](http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html)
[http://www.megaupload.com/?d=F2R0S36T](http://www.megaupload.com/?d=F2R0S36T)

Now do what the support from realtek say:

[B]Hi Sir,               
 
Thanks for your email.
 
Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the updated one different from the one you used.
 
Just kindly remind, please install by the below steps.
The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
 
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).
 
If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delet it first before install:
 
 
    1) cd /lib/modules/2.6.3x.xx.xx/
    2) find -name "r8192e_pci.ko"
    3) delet all the r8192e_pci.ko
    4) install our RTL8192E driver
    5) reboot.
 
 
if there’s still any other problem, please let us know.
   Thanks a lot
 
Regards,
Kidman[/B]

Reboot

Now, You can use your Wireless and have fun.

:)

---

