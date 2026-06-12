---
title: "NOVA T 500 remote control"
date: 2008-11-22
forum: Mythbuntu
---

### Post by NegativeSpace on 2008-11-22
Hello,

I have setup Mythbuntu with an Hauppauge Nova-TD-500 (the diversity model) and everything seems to be working nicely except for the remote control.

*cat /proc/bus/input/devices* yields:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=0005 Version=0051
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```
No sign of the remote control...

However, *dmesg | grep ir* gives:
```

simon@adaephon:/dev/input$ dmesg | grep ir
[    0.000000] kernel direct mapping tables up to 1ffd0000 @ 7000-d000
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.004000] virtual kernel memory layout:
[    0.512268] Booting paravirtualized kernel on bare hardware
[    0.536541] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.536546] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    1.388469] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.819547] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.819786] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.822676] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.822686] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.824586] rtc0: alarms up to one month, hpet irqs
[    2.846714] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e400
[    2.973133] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
[    3.077099] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[    3.184911] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[    3.305975] uhci_hcd 0000:02:09.0: irq 21, io base 0x0000b800
[    3.537188] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:0c:6e:71:d8:a0
[    3.537553] ehci_hcd 0000:02:09.2: irq 23, io mem 0xfeafec00
[    3.922674] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    3.922682] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    4.292558] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BB-22D 65.1 PQ: 0 ANSI: 5
[   10.257969] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   10.875507] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   10.875516] firmware: requesting dvb-usb-dib0700-1.20.fw
[   12.699864] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   12.902026] dib0700: firmware started successfully.
[   33.236328] Bridge firewalling registered
[ 1236.639393] lirc_dev: IR Remote Control driver registered, major 61 
[ 1236.902239] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 1236.902254] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[ 1346.202420] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 1346.202434] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[ 1381.152905] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 1381.152926] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[ 1480.880378] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 1480.880388] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[ 8997.974132] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 8997.974144] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[ 9738.604454] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 9738.604465] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[ 9989.126117] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[ 9989.126129] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[10462.208074] lirc_dev: IR Remote Control driver registered, major 61 
[10462.312823] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[10462.312836] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[10480.481169] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[10480.481182] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio
[11108.542298] lirc_dev: IR Remote Control driver registered, major 61 
[11108.622709] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[11108.622725] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio

```
I notice the line:
```

[ 1236.639393] lirc_dev: IR Remote Control driver registered, major 61 

```
Suggests that LIRC at least sees something...

I have also tried */etc/init.d/lirc start*

But get the following:
```

simon@adaephon:/dev/input$ /etc/init.d/lirc start
 * Loading LIRC modules                                                                      [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```
irw also gives me a *Connection refused* error.

Basically I'm stuck.  I **think** LIRC is recognising that something exists, but beyond that nothing seems to work.  Unfortunately, as I'm sure is evident, my Linux skills are limited...

Any help would be appreciated.

---

### Post by TheConsultant on 2008-11-23
Hi,

I had the same problem, If I had used irw to check my remote control, there are cryptic symbols on my screen.

I have downladed the latest firmware from the hauppauge webpage to fix this. Now my remote control for a NOVA T-500 is working well.

It's seems, that a corrupted dib0700 firmware is inside the mythbuntu 8.10.

Hope tis will fix your problem.

A sample short description of my /etc/lirc/hardware.conf:

[I]#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
# REMODE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DRIVER""
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""[/I]

Best regards

Martin

---

### Post by NegativeSpace on 2008-11-23
TheConsultant,

Thanks for your help.  I am running dvb-usb-dib0700-1.20 of the firmware, which I downloaded, rather than using Mythbuntu's default.  Should I revert back to 1.10?

I have tried Hauppauge's website but can't find anything Linux related -- perhaps you have a direct link?

Many thanks.

---

### Post by NegativeSpace on 2008-11-24
I tried running dvb-usb-dib0700-1.10.fw but this prevents the card from playing any TV at all.

I'm still at a loss -- can anyone else help?

---

### Post by NegativeSpace on 2008-11-25
bump

---

### Post by SteveGodfrey on 2008-12-14
Thanks for the helpful posts.

I have a slightly different take on this problem. Every time I unplug the reconnect my USB tuner the 'input' number changes.

Currently it's 
Sysfs=/devices/pci0000:00/0000:00:13.2/usb1/1-5/input/input9

I have now unplugged then reconnected the USB stick and the input number has changed
S: Sysfs=/devices/pci0000:00/0000:00:13.2/usb1/1-5/input/input10

Any suggestions on how to make this 'stick'?

Thanks

---

### Post by uMuppet on 2008-12-14
You will need to make the input event static,
see this site

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver)

But basically you create a shortcut to your device and refer to that as an input device.  Its been a while since I did this so if you have trouble let me know and I'll have a better look.  I've been meaning to do a nice "how to" for this and put it on my Wiki for some time.

If you have the newer all black Hauppauge remote I have some preconfigured files on my site [here]("http://mythkiwi.com/index.php/remository?func=select&id=5")

---

