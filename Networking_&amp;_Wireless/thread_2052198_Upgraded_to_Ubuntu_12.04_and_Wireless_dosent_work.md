---
title: "Upgraded to Ubuntu 12.04 and Wireless dosent work"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by dkb12 on 2012-09-02
Hello Everyone, I recently Upgraded to Ubuntu 12.04 and Im not able to get my wireless to work. Heres what I get when I put the commands in. Can anyone help? thanks

---

### Post by dkb12 on 2012-09-02
katelynsmommy@katelynsmommy-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS100 AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS100 [Radeon IGP320M]

katelynsmommy@katelynsmommy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

snd_page_alloc         14115  1 snd_pcm
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
shpchp                 32325  0 
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
radeon                733687  2 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
floppy                 60310  0 
natsemi                31943  0 
pata_ali               13562  2 
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13199  1 radeon
video                  19068  0 
ati_agp                13242  1 
usbhid                 41906  0 
hid                    77367  1 usbhid

 sudo lshw -C Network
[sudo] password for katelynsmommy: 
PCI (sysfs)  

  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0004000-d0005fff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:7a:54:39
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.99.100 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 ioport:8c00(size=256) memory:d000a000-d000afff memory:1c000000-1c00ffff

katelynsmommy@katelynsmommy-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by chili555 on 2012-09-03
> 00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)We need just a bit more information. Please run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Tell Katelyn that Grandpa Chili says hello.

Thanks.

---

### Post by dkb12 on 2012-09-03
> **chili555 said:**
> We need just a bit more information. Please run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Tell Katelyn that Grandpa Chili says hello.

Thanks.

katelynsmommy@katelynsmommy-laptop:~$ lspci -nn | grep 0280
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
 

I will tell her :) and this Says Kubuntu at the top and its supposed to be Ubuntu. I didnt know how to change it if I could.

---

### Post by chili555 on 2012-09-03
Please hook up the ethernet temporarily and do this: [http://ubuntuforums.org/showthread.php?t=1979650](http://ubuntuforums.org/showthread.php?t=1979650)

Reboot, detach the ethernet and enjoy your wireless!

---

### Post by dkb12 on 2012-09-03
I tried it and it installed it but when I rebooted I still had nothing. Its not even detecting my wireless network.

---

### Post by chili555 on 2012-09-03
Let's see if the message logs give us an answer. Please open a terminal and run and post:```
dmesg | grep b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by dkb12 on 2012-09-03
This is all I get when I run that command 

katelynsmommy@katelynsmommy-laptop:~$ dmesg | grep b43
katelynsmommy@katelynsmommy-laptop:~$

---

### Post by chili555 on 2012-09-03
Please try:```
sudo modprobe b43
dmesg | grep b43
iwconfig
rfkill list all
```I wonder if b43 just failed to load automatically.

---

### Post by dkb12 on 2012-09-03
heres what I got this time. 

katelynsmommy@katelynsmommy-laptop:~$ sudo modprobe b43
katelynsmommy@katelynsmommy-laptop:~$ dmesg | grep b43
[ 6764.837578] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
katelynsmommy@katelynsmommy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

katelynsmommy@katelynsmommy-laptop:~$ rfkill list all
katelynsmommy@katelynsmommy-laptop:~$

---

### Post by chili555 on 2012-09-04
Something is wrong. Loading the correct module for your device ought to marry the device and the driver and create a wireless interface, wlan0, ideally, and kick Network Manager to life and connect. In your case, it just sits there and does nothing.

Your rfkill is mysterious as well. It doesn't seem to recognize a wireless radio at all. Here is a normal reading from my laptop:```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```'phy0' refers to, roughly, the first physical device. 

Let's dig deeper. Please go into the BIOS and look around for any settings that may enable or disable the wireless radio. Make sure it's enabled. You might also set the BIOS to defaults; often F9. 

Next, let's look at the logs for any information about the PCI bus your wireless connects to:> [COLOR="Red"]00:09.0[/COLOR] Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
Please run and post:```
dmesg | grep 09.0
```Let's see if there are any interesting warnings or errors:```
dmesg | grep -i warn
dmesg | grep -i err
```Hi, Katelyn!!

---

### Post by dkb12 on 2012-09-04
katelynsmommy@katelynsmommy-laptop:~$ dmesg | grep 09.0
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.036804] RTC time: 14:10:24, date: 09/04/12
[    0.069629] pci 0000:00:09.0: [14e4:4320] type 0 class 0x000280
[    0.069643] pci 0000:00:09.0: reg 10: [mem 0xd0004000-0xd0005fff]
[    0.069692] pci 0000:00:09.0: supports D1 D2
[    0.072008] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.072013] pci 0000:00:09.0: PME# disabled
[    0.072113] pci 0000:00:0c.0: reg 10: [mem 0xd0009000-0xd00097ff]
[    0.091078] AppArmor: AppArmor Filesystem Enabled
[    0.092004] pnp 00:02: [irq 8]
[    0.092051] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.092065] pnp 00:03: [io  0x00f0-0x00fe]
[    0.092069] pnp 00:03: [irq 13]
[    0.093002] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.094023] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.094027] pnp 00:0a: [irq 4]
[    0.509406] ERST: Table is not found!
[    0.509409] GHES: HEST is not enabled!
[    1.533528] rtc_cmos 00:02: setting system clock to 2012-09-04 14:10:28 UTC (1346767828)
[   30.509005] psmouse serio1: synaptics: Touchpad model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0

---

### Post by dkb12 on 2012-09-04
Heres the other command I ran. I agree its like its sitting there. When I had the 10.04 It hooked right up then I upgraded to the 12.04 and it connected 2 times and I had the telephone company come out to replace my dsl and it hasnt connected since. I dont know if that could be a problem or what but it seems like it stopped working all at once. 

katelynsmommy@katelynsmommy-laptop:~$ dmesg | grep -i warn
[    2.408376] ata2.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    2.408380] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
katelynsmommy@katelynsmommy-laptop:~$ dmesg | grep -i err
[    0.032251] no hardware sampling interrupt available.
[    0.060565] ACPI: Using PIC for interrupt routing
[    0.072630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.072717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.075475] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.075577] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.075674] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 *10)
[    0.075772] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *9
[    0.075871] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[    0.075970] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 *11)
[    0.076090] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.076205] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.076303] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[    0.132784] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.134586] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[    0.644687] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    1.847663] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    1.960590] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   28.995572] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   29.048967] lp0: using parport0 (interrupt-driven).
[   30.596774] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   33.704052] ali mixer 1 creating error.

---

### Post by chili555 on 2012-09-04
The only thing interesting we see is here:> [ 0.069629] pci 0000:00:[COLOR="Red"]09.0[/COLOR]: [[COLOR="Red"]14e4:4320[/COLOR]] type 0 class 0x000280We see the bus and the hardware unite and, evidently, nothing else. 

Anything interesting in the BIOS? Did you reset it?

---

### Post by dkb12 on 2012-09-04
Im sorry Im still learning all of this. How do I get to the Bios? I hit f9 but it did nothing

---

### Post by chili555 on 2012-09-04
When you first boot your computer, before the operation system even starts, you should see an option to press F1 or ESC or DEL or some such to enter the setup pages. The first picture I attached shows an example of 'Press DEL to enter setup.' The second shows a BIOS page and this particular version shows F6 for failsafe defaults.

Please don't be intimidated; all we need to do is enter the BIOS, reset to defaults, save and close. Save and close is F10 in the example. These may be different in your computer.

Then the computer will boot and, hopefully, your wireless will wake up and do some work.

---

### Post by dkb12 on 2012-09-07
ok. I entered the Bios. do I reset to defaults on there? Im really hoping to get this fixed :)

---

### Post by dkb12 on 2012-09-07
I just went back and looked. I didnt see anything about resetting defaults.

---

### Post by chili555 on 2012-09-07
Often, there is a menu of available options at the bottom of the BIOS page. Please see attached. Although this is an IBM BIOS page, you can see at the bottom is F9 to reset to defaults and F10 to save and exit. Your exact F-whatever will probably be different, but many BIOS pages are similar.

---

### Post by dkb12 on 2012-09-07
When I go to the Bios. My f9 says Setup Defaults and I hit the f9 it says Setup Configuration Now and I says yes it restarts it and I still get nothing.  Do you have to set anything up in the terminal for the b43 cutter?

---

### Post by chili555 on 2012-09-08
> When I go to the Bios. My f9 says Setup Defaults and I hit the f9 it says Setup Configuration Now and I says yes it restarts it Is there no F10 to save and exit?>  Do you have to set anything up in the terminal for the b43 cutter? You only need b43-fwcutter if you are missing firmware for your card. We see no evidence of that in dmesg. Just to double-check, do you see firmware here?```
ls /lib/firmware/b43
```Do you see 'file not found' or do you see dozens of installed firmware files? We don't need to see the whole list, just tell us if it exists.

---

### Post by dkb12 on 2012-09-11
> **chili555 said:**
> Is there no F10 to save and exit?You only need b43-fwcutter if you are missing firmware for your card. We see no evidence of that in dmesg. Just to double-check, do you see firmware here?```
ls /lib/firmware/b43
```Do you see 'file not found' or do you see dozens of installed firmware files? We don't need to see the whole list, just tell us if it exists.


I did do the f10 and when  I put the code in it showed dozens of firmware files.

---

### Post by chili555 on 2012-09-11
I wish I could find an easy problem!

Please try, with the ethernet hooked up and connected:```
sudo apt-get install firmware-b43legacy-installer
sudo modprobe -r b43
sudo modprobe b43legacy
```Any improvement?

---

