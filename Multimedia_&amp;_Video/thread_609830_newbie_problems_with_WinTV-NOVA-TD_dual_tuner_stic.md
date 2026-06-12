---
title: "newbie problems with WinTV-NOVA-TD dual tuner stick"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by johnwillyums on 2007-11-11
I've just started with Ubuntu (7.10 64x) and have the WinTV-NOVA-TD dual tuner stick connected up to my pc.

Presently I'm dual booting with Vista 64x on a brand new machine and am a comparative new comer to computing in general.
I've managed to get the TV stick to work in Vista 64x but did not use Hauppauge's supplied software and am getting good quality images via Windows Media Centre (although some of the important terrestrial channels are missing)

However I'm not able to get anywhere in Ubuntu. I have installed MythTV backend setup and front end but get the same result with both of them- a screen for language setting followed by a screen saying:

Myth could not connect to database
Please verify your database settings below
Host name; localhost
Database:mythconverg
User:mythtv
Password:Zgfgc176
Database type:mySQL

I have no idea what to do next. Have tried adding my username and password but this does not seem sufficient.

The next page has 2 choices:

use custom identifier for frontend preference
At the bottom is:
If this frontends host name changes often check this box and provide a network-unique name to identify it. If undecided the frontend machine's local host name will be used to save preferences in the database.
The second choice is:

Use Wake-On-LAN to wake database
And at the bottom:
If checked,the frontend will use Wake-On-LAN parameters to reconnect to the database server.

If I choose either I get a box with:

would you like to use mythfilldatabase

If I ok this nothing seems to happen.
I'm hopelessly lost please help, John

---

### Post by johnwillyums on 2007-11-12
Am at my wits end here.
I've tried everything I can think of and I just don't get anywhere.

What with this and not being able to get my printer working I'm not sure Ubuntu is ready for people like me yet.

Shame really, John

---

### Post by wieman01 on 2007-11-12
Don't give up yet, I have a thread for you. Please post there if you need help. I'll keep an eye on the thread. :-)

[http://ubuntuforums.org/showthread.php?t=533528]("http://ubuntuforums.org/showthread.php?t=533528")

---

### Post by johnwillyums on 2007-11-12
Hello wieman, thanks for your reply

I looked at your thread and tried typing "dmesg" into terminal and pressing enter- I take it that's what you intended(?)

Anyway that got me three full screen pages of text:

[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.

[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000dfef0000 - 00000000dfef3000
[    0.000000] swsusp: Registered nosave memory region: 00000000dfef3000 - 00000000dff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000dff00000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000f2000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f2000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 1030952
[    0.000000] Kernel command line: root=UUID=bd3729dc-e776-4164-b090-b8851f54492a ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[   24.429892] time.c: Detected 2399.978 MHz processor.
[   24.430988] Console: colour VGA+ 80x25
[   24.431005] Checking aperture...
[   24.431014] Calgary: detecting Calgary via BIOS EBDA area
[   24.431015] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   24.431017] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   24.467798] Placing software IO TLB between 0x104c000 - 0x504c000
[   24.504057] Memory: 4049800k/4718592k available (2274k kernel code, 143028k reserved, 1181k data, 296k init)
[   24.504100] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   24.583988] Calibrating delay using timer specific routine.. 4803.92 BogoMIPS (lpj=9607852)
[   24.584015] Security Framework v1.0.0 initialized
[   24.584022] SELinux:  Disabled at boot.
[   24.584334] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   24.587298] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   24.588521] Mount-cache hash table entries: 256
[   24.588649] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.588652] CPU: L2 cache: 4096K
[   24.588654] CPU 0/0 -> Node 0

I have tried to paste all of it here but can't for some reason. Will try to get the last page,yes here it is:

[   39.152768] parport_pc 00:09: reported by Plug and Play ACPI
[   39.152796] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   39.222351] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   39.222359] Uniform CD-ROM driver Revision: 3.20
[   39.224605] hdd: ATAPI 48X DVD-ROM drive, 198kB Cache, UDMA(33)
[   39.269620] nvidia: module license 'NVIDIA' taints kernel.
[   39.526645] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   39.526650] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[   39.526658] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   39.526741] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   39.551706] usbcore: registered new interface driver xpad
[   39.551710] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   39.694724] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   39.694729] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[   39.696800] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   39.907629] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   40.497236] lp0: using parport0 (interrupt-driven).
[   40.609310] Linux video capture interface: v2.00
[   40.644858] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   40.646435] cx2388x dvb driver version 0.0.6 loaded
[   40.646437] cx8802_register_driver() ->registering driver type=dvb access=shared
[   40.717048] Adding 1116476k swap on /dev/sda5.  Priority:-1 extents:1 across:1116476k
[   41.114072] EXT3 FS on sda2, internal journal
[   42.220269] No dock devices found.
[   42.227809] input: Power Button (FF) as /class/input/input5
[   42.227823] ACPI: Power Button (FF) [PWRF]
[   42.227855] input: Power Button (CM) as /class/input/input6
[   42.227865] ACPI: Power Button (CM) [PWRB]
[   43.561795] ppdev: user-space parallel port driver
[   43.831538] audit(1194889006.416:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5644 profile="/usr/sbin/cupsd"
[   47.726343] NET: Registered protocol family 10
[   47.726430] lo: Disabled Privacy Extensions
[  109.274110] Failure registering capabilities with primary security module.
[  112.035082] Bluetooth: Core ver 2.11
[  112.035328] NET: Registered protocol family 31
[  112.035333] Bluetooth: HCI device and connection manager initialized
[  112.035336] Bluetooth: HCI socket layer initialized
[  112.042090] Bluetooth: L2CAP ver 2.8
[  112.042096] Bluetooth: L2CAP socket layer initialized
[  112.050216] Bluetooth: RFCOMM socket layer initialized
[  112.050237] Bluetooth: RFCOMM TTY layer initialized
[  112.050241] Bluetooth: RFCOMM ver 1.8
[  114.665024] NET: Registered protocol family 17
[  189.290116] eth0: no IPv6 routers present
johnwillyums@johnwillyums-desktop:~$ 

As you can see-no resemblance to what I expected. I read through the missing section and can't see any mention of "dvb" anywhere.
Have I I totally misunderstood?

Thanks, John Williams

---

### Post by wieman01 on 2007-11-13
What is the 'dmesg' output after inserting the stick? Just post the last 10 lines.

By the way, this web site is a great starting point:

[http://www.linuxtv.org/]("http://www.linuxtv.org/")

It should have lots of information concerning your device.

---

### Post by Scorpuk on 2007-11-13
If you are still having problems can you try the following commands:


```
dmesg | grep dvb
```

and

```
dmesg | grep DVD
```


with the device plugged in.

---

### Post by johnwillyums on 2007-11-13
Hello again wieman,

I already have the stick inserted and it was inserted when I got the above result from typing "dmesg" into terminal and pressing enter.

I am running a dual boot with Vista 64x and have the stick running in that through Windows Media Centre. I have it connected to an outside aerial and the reception is excellent.

The printout above is the first and last pages of a three page text output which I could not copy and paste in its entirety for some reason.

However I have read it all and it's all pretty much similar to the above and does not mention "dvb" or anything similar throughout.
I notice stuff about bluetooth in the final section. As far as I know I don't have bluetooth. Not even sure what it is really.

Scorpuk. Thanks for your input. Do you think I should try your suggestions given the above?

Thanks to you both for your support, John Williams

---

### Post by johnwillyums on 2007-11-14
Hi.

Sorry to keep posting about the same issue but I'm still unable to find a way to use my dvb stick.

I have managed to find what must be it in device manager. It is there but identified as NovaT 500Stick and underneath are two boxes with USB Vendor specific interface and USB raw device access written alongside.

In fact my stick is a WinTV-NOVA-TD dual tuner but surely this must be it but misidentified.

Does this throw any light on my problem?

Yours hopefully, John Williams

---

### Post by johnwillyums on 2007-11-15
hello, is there anybody out there?

---

### Post by wieman01 on 2007-11-17
John, 

I have done a bit of research and according to [this site]("http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices") your devide should work using firmware "dvb-usb-dib0700-xx.fw". Therefore you should be able to get it working using my tutorial here:

[http://ubuntuforums.org/showthread.php?t=533528]("http://ubuntuforums.org/showthread.php?t=533528")

It should work. If it doesn't, please post here or in my thread. I'll help you.

---

### Post by piroman01 on 2008-04-08
I've got the same problem than you johnwillyums. Does it ever run?

I installed the firmware and placed it in /lib/firmware/. I renamed it dvb-usb-dib0700-01.fw. Then I loaded the driver with

modprobe dvb-usb-dib0700

and I obtained...

dsmesg | grep dvb
[ 214.796000] usbcore: registered new interface driver dvb_usb_dib0700

...which doesn't show that it runs.

what should I do?
before I started to load the driver I had the same lines than johnwillyums:

grep | tail
[ 112.035082] Bluetooth: Core ver 2.11
[ 112.035328] NET: Registered protocol family 31
[ 112.035333] Bluetooth: HCI device and connection manager initialized
[ 112.035336] Bluetooth: HCI socket layer initialized
[ 112.042090] Bluetooth: L2CAP ver 2.8
[ 112.042096] Bluetooth: L2CAP socket layer initialized
[ 112.050216] Bluetooth: RFCOMM socket layer initialized
[ 112.050237] Bluetooth: RFCOMM TTY layer initialized
[ 112.050241] Bluetooth: RFCOMM ver 1.8
[ 114.665024] NET: Registered protocol family 17
[ 189.290116] eth0: no IPv6 routers present

thanks,
Romain

---

### Post by wieman01 on 2008-04-08
Is it a USB device? If so, please run:
> lsusb
After inserting it.

---

### Post by piroman01 on 2008-04-08
got this...

tetsuo@ubuntu:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. 
Bus 002 Device 002: ID 2040:9580 Hauppauge 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


thanks

---

### Post by wieman01 on 2008-04-08
When you now install & shoot up Kaffeine, what happens? To install it:
> sudo apt-get install kaffeine

---

### Post by piroman01 on 2008-04-08
I installed kaffeine but there's no dvb menu. I think my card isn't recognized, I haven't got a thing like that when I load the driver:

dvb-usb: Hauppauge Nova-TD Stick successfully initialized and connected.

I tried with kdetv too and my card seems to be absent.

any idea?

---

### Post by wieman01 on 2008-04-08
> **piroman01 said:**
> dvb-usb: Hauppauge Nova-TD Stick successfully initialized and connected.
In fact that's seems like it is working... I am confused. Could you do some Googling on this? I am sure it is alright.

---

### Post by piroman01 on 2008-04-08
I did some googling but nothing much. The only thing interesting I found is the article on linuxtv. 
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick")
It seems like it can run on linux, but how...
I don't understand all of the explanation. My English's very bad...
but I'll try!
thanks

Romain

---

### Post by wieman01 on 2008-04-08
I'll take a look at it as well and try to make sense of it myself. Let's see... :-)

---

### Post by piroman01 on 2008-04-08
ok thank you :)

---

### Post by piroman01 on 2008-04-08
I found an interesting page:
[http://www.axen.se/pages/manual110/nova-td-ubuntu.php]("http://www.axen.se/pages/manual110/nova-td-ubuntu.php")

which explain in short the article of linuxtv

'm trying...

R

---

### Post by piroman01 on 2008-04-08
ouf...

I got this now:

tetsuo@ubuntu:~$ dmesg | tail
[   49.232000] Bluetooth: RFCOMM TTY layer initialized
[   49.232000] Bluetooth: RFCOMM ver 1.8
[   55.168000] NET: Registered protocol family 17
[   63.480000] NET: Registered protocol family 10
[   63.480000] lo: Disabled Privacy Extensions
[   63.480000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3715.284000] dib0700: loaded with support for 7 different device-types
[ 3715.336000] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in cold state, will try to load a firmware
[ 3715.676000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-1.10.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[ 3715.676000] usbcore: registered new interface driver dvb_usb_dib0700


it seems to be good, but it doesn't detect my firmwares putting dvb-usb-dib0700-1.10.fw or dvb-usb-dib0700-01.fw in my /lib/firmware...

I don't understand, but I go forward!

---

### Post by wieman01 on 2008-04-08
Please try this:
> sudo cp /lib/firmware/dvb-usb-dib0700-01.fw /lib/firmware/dvb-usb-dib0700-1.10.fw 
Then unplug the device, plug it in again, and run:
> dmesg | tail
It basically renames the firmware, the correct name ought to be:
> dvb-usb-dib0700-1.10.fw

---

### Post by piroman01 on 2008-04-08
yes I don't understand...

tetsuo@ubuntu:~$ sudo cp Desktop/dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-1.10.fw 
tetsuo@ubuntu:~$ dmesg | tail
[   49.232000] Bluetooth: RFCOMM TTY layer initialized
[   49.232000] Bluetooth: RFCOMM ver 1.8
[   55.168000] NET: Registered protocol family 17
[   63.480000] NET: Registered protocol family 10
[   63.480000] lo: Disabled Privacy Extensions
[   63.480000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3715.284000] dib0700: loaded with support for 7 different device-types
[ 3715.336000] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in cold state, will try to load a firmware
[ 3715.676000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-1.10.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[ 3715.676000] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by wieman01 on 2008-04-08
Download the firmware from here:

[http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw]("http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw")

Then put it in:
> /lib/firmware/
Any better now?

---

### Post by piroman01 on 2008-04-08
I think I've got a new problem...
This card runs on usb2.0 and mine is usb1.1...

tetsuo@ubuntu:~$ dmesg | grep dvb
[   28.684000] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in cold state, will try to load a firmware
[   28.812000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   30.972000] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in warm state.
[   30.972000] dvb-usb: This USB2.0 device cannot be run on a USB1.1 port. (it lacks a hardware PID filter)
[   30.972000] dvb-usb: Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity error while loading driver (-19)
[   30.972000] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by wieman01 on 2008-04-08
Oh, this looks much better now. The stick has been recognized.

But as you said, this isn't a USB 2.0 port. Do you have another computer with USB 2.0 capabilities?

---

### Post by piroman01 on 2008-04-08
No, and that's a big problem...
I've got a usb1.1 port and a usb2.0 hub.
I have to buy new ports. Maybe there's another solution...

thank a lot for your help, I think it could run if my computer was a formula 1 and not a scooter :)

ciao
Romain

---

