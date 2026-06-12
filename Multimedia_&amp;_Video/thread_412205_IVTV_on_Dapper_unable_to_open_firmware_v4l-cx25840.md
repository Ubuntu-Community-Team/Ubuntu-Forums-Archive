---
title: "IVTV on Dapper: unable to open firmware v4l-cx25840.fw v4l-cx2341x-enc.fw"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by wildbillnj1975 on 2007-04-17
I am trying to get IVTV to work with a Hauppauge PVR-150 in an Ubuntu 
Dapper (2.6.15-28-386) box, but it is failing to load the drivers (dmesg output below - red lines look like errors to me):

/#.#/ pci_hotplug: PCI Hot Plug PCI Core version: 0.5
/#.#/ shpchp: HPC vendor_id 1022 device_id 700f ss_vid 0 
ss_did 0
/#.#/ shpchp: shpc_init: cannot reserve MMIO region
/#.#/ shpchp: Standard Hot Plug PCI Controller Driver 
version: 0.4
/#.#/ Linux video capture interface: v1.00
[COLOR="Red"]/#.#/ ivtv: no version for "struct_module" found: kernel 
tainted.[/COLOR]
/#.#/ ivtv:  ==================== START INIT IVTV 
====================
/#.#/ ivtv:  version 0.4.10 (tagged release) loading
/#.#/ ivtv:  Linux version: 2.6.15.7-ubuntu1 preempt 486 gcc-4.0
/#.#/ ivtv:  In case of problems please include the debug 
info between
/#.#/ ivtv:  the START INIT IVTV and END INIT IVTV lines, 
along with
/#.#/ ivtv:  any module options, when mailing the ivtv-users 
mailinglist.
/#.#/ ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
/#.#/ ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 19 (level, 
low) -> IRQ 177
/#.#/ ivtv0: Unreasonably low latency timer, setting to 64 
(was 32)
/#.#/ eth0: DSPCFG accepted after 0 usec.
/#.#/ eth0: link up.
/#.#/ eth0: Setting full-duplex based on negotiated link 
capability.
[COLOR="Red"]/#.#/ **** SET: Misaligned resource pointer: dd7fd9a2 Type 
07 Len 0[/COLOR]
/#.#/ ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
/#.#/ ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> 
GSI 10 (level, low) -> IRQ 10
/#.#/ PCI: Via IRQ fixup for 0000:00:07.5, from 11 to 10
/#.#/ PCI: Setting latency timer of device 0000:00:07.5 to 64
/#.#/ tveeprom: ivtv version
/#.#/ tveeprom: Hauppauge: model = 26132, rev = F0B2, 
serial# = 9398729
/#.#/ tveeprom: tuner = TCL M2523_5N_E (idx = 112, type = 50)
/#.#/ tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 
0x00001000)
/#.#/ tveeprom: audio processor = CX25841 (type = 23)
/#.#/ tveeprom: decoder processor = CX25841 (type = 1c)
/#.#/ ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
/#.#/ tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c 
driver #0
/#.#/ ivtv0: i2c attach to card #0 ok [client=(tuner unset), 
addr=61]
/#.#/ cx25840 1-0044: ivtv driver
/#.#/ cx25840 1-0044: cx25841-23 found @ 0x88 (ivtv i2c 
driver #0)
/#.#/ input: ImPS/2 Generic Wheel Mouse as /class/input/input2
/#.#/ ts: Compaq touchscreen protocol output
/#.#/ NET: Registered protocol family 10
/#.#/ lo: Disabled Privacy Extensions
/#.#/ IPv6 over IPv4 tunneling driver
[COLOR="Red"]/#.#/ cx25840 1-0044: unable to open firmware v4l-cx25840.fw[/COLOR]
/#.#/ ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
/#.#/ wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
/#.#/ ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
/#.#/ eth0: no IPv6 routers present
[COLOR="Red"]/#.#/ ivtv0: unable to open firmware v4l-cx2341x-enc.fw 
(must be 376836 bytes)
/#.#/ ivtv0: did you put the firmware in the hotplug 
firmware directory?
/#.#/ ivtv0 warning: failed loading encoder firmware
/#.#/ ivtv0 warning: Error loading firmware -3!
/#.#/ ivtv0: Error -3 initializing firmware.
/#.#/ ivtv0: Error -12 on initialization
/#.#/ ivtv: probe of 0000:00:0f.0 failed with error -12[/COLOR]
/#.#/ ivtv:  ====================  END INIT IVTV  
====================

(I replaced the {123456789.123456789} with /#.#/ on each line above for clarity...)

I have copies of the files in ALL the suggested locations just to be safe:

/lib/modules/v4l-cx25840.fw
/lib/modules/v4l-cx2341x-enc.fw
/lib/firmware/v4l-cx25840.fw
/lib/firmware/v4l-cx2341x-enc.fw
/lib/firmware/2.6.15-28-386/v4l-cx25840.fw
/lib/firmware/2.6.15-28-386/v4l-cx2341x-enc.fw
/usr/lib/hotplug/firmware/v4l-cx25840.fw
/usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw

Plus a couple of other locations where they appeared automagically:

/lib/modules/2.6.15-28-386/kernel/drivers/pci/hotplug/v4l-cx25840.fw
/lib/modules/2.6.15-28-386/kernel/drivers/pci/hotplug/v4l-cx2341x-enc.fw
/lib/hotplug/firmware/v4l-cx25840.fw
/lib/hotplug/firmware/v4l-cx2341x-enc.fw

Plus a couple of other locations I added just in case:

/usr/lib/firmware/hotplug/v4l-cx25840.fw
/usr/lib/firmware/hotplug/v4l-cx2341x-enc.fw

What am I missing?

I have tried rebooting, cold rebooting, shutting down for 30 seconds 
with the machine unplugged, with the same results.

I have even tried voodoo rituals and threatening hand gestures.

Why doesn't it work?
And oh, BTW, why are there N different "Howto" pages, most completely 
different?

---

### Post by superm1 on 2007-04-19
The Howto at help.ubuntu.com/community/Install_IVTV_Dapper is the one you should be using.  How did you follow doing this?  The h.u.c/community/Install_IVTV_Dapper will walk you through installing the latest firmware and all required steps.

---

### Post by wildbillnj1975 on 2007-04-19
[FONT="Arial"]Superm1, thanks, but if you read my other post [here]("http://ubuntuforums.org/showthread.php?t=406848") you'll see I tried that first with disastrous results.  Actually, here's the text of that post so you don't have to follow the link:[/FONT]

[FONT="Times New Roman"]I am installing the IVTV drivers on a very clean dapper system, for use with a Hauppauge PVR-150. I am following the "official" howto here

When I reach the step which says:

sudo modprobe ivtv

modprobe crashes, and the system is completely frozen. This is the second attempt - the first resulted in the kernel being so completely hosed that I resorted to a reinstall of ubuntu. I won't be able to boot into this kernel again.

Anybody know what might be going wrong? I followed the howto exactly!

After recoving the system (by dumping and re-installing the kernel) I tried it again, this time with :

modprobe -v ivtv

The first two lines are ok.
the third:

insmod /.../modules/2.6.15-28-386/ivtv/ivtv.ko

(I forget the part of the path in the ...)

It spits that out, and completely freezes - no error messages or anything.

Now the system will only boot to an older kernel (same as the first two failed attempts).
I can recover the system by reinstalling the 2.6.15-28-386 kernel and uninstalling the ivtv drivers.

Help!
[/FONT]

Just to make sure I'm not nuts (and in deference to your suggestion) I tried it again, however, and I saved it all in a script (attached) so I don't have to keep retyping it all.

(the script uses DEBIAN_FRONTEND=dialog... because I'm "tee"-ing all the output to a file and I don't want it diverted to another window...)

I have attached the output from my script (doivtv.log) and the output from dmesg after I rebooted (dm.txt)

The result is not the same as in my other post - I can boot the machine, but it can't load those drivers.

---

### Post by superm1 on 2007-04-22
Are you sure this card is functional?  It is sounding like all the steps are going as they should.  Could you pop this card into another PC and check?  You don't have to setup drivers or anything on the other computer.  Just download a feisty disk and do a test capture off the disk.   IVTV is included in feisty, so you can't have any other issues with module building or anything.

---

### Post by wildbillnj1975 on 2007-05-01
Superm1, I tried booting the same box with a Feisty CD, it still doesn't work, here's what I have from dmesg:

[FONT="Courier New"]
# ivtv:  ==================== START INIT IVTV ====================
# ivtv:  version 0.10.1 (tagged release) loading
# ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
# ivtv:  In case of problems please include the debug info between
# ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
# ivtv:  any module options, when mailing the ivtv-users mailinglist.
# ivtv0: Autodetected Hauppauge card (cx23416 based)
# parport_pc: VIA 686A/8231 detected
# parport_pc: probing current configuration
# parport_pc: Current parallel port base: 0x378
# parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
# ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 19 (level, low) -> IRQ 17
# ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
# input: PC Speaker as /class/input/input2
# parport_pc: VIA parallel port: io=0x378, irq=7
# input: ImPS/2 Generic Wheel Mouse as /class/input/input3
# ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[COLOR="Blue"]# ivtv0 warning: Encoder mailbox not found[/COLOR]
# ivtv0: Retry loading firmware
# ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[COLOR="Blue"]# ivtv0 warning: Encoder mailbox not found
# ivtv0: Error initializing firmware
# ivtv0: Error -19 on initialization[/COLOR]
# ivtv:  ====================  END INIT IVTV  ====================[/FONT]

I have another box, in which this card does not work at all (PC will not complete POST), but I don't know if it proves anything: The HVR-1600 I originally bought was incompatible with that mobo (a known bug at Hauppauge) and it's possible that the PVR-150 has the same problem.  I really only have the Ubuntu box to work with, and it doesn't work in Dapper or Feisty.

---

### Post by superm1 on 2007-05-01
> **wildbillnj1975 said:**
> Superm1, I tried booting the same box with a Feisty CD, it still doesn't work, here's what I have from dmesg:

[FONT=Courier New]
# ivtv:  ==================== START INIT IVTV ====================
# ivtv:  version 0.10.1 (tagged release) loading
# ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
# ivtv:  In case of problems please include the debug info between
# ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
# ivtv:  any module options, when mailing the ivtv-users mailinglist.
# ivtv0: Autodetected Hauppauge card (cx23416 based)
# parport_pc: VIA 686A/8231 detected
# parport_pc: probing current configuration
# parport_pc: Current parallel port base: 0x378
# parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
# ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 19 (level, low) -> IRQ 17
# ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
# input: PC Speaker as /class/input/input2
# parport_pc: VIA parallel port: io=0x378, irq=7
# input: ImPS/2 Generic Wheel Mouse as /class/input/input3
# ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[COLOR=Blue]# ivtv0 warning: Encoder mailbox not found[/COLOR]
# ivtv0: Retry loading firmware
# ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[COLOR=Blue]# ivtv0 warning: Encoder mailbox not found
# ivtv0: Error initializing firmware
# ivtv0: Error -19 on initialization[/COLOR]
# ivtv:  ====================  END INIT IVTV  ====================[/FONT]

I have another box, in which this card does not work at all (PC will not complete POST), but I don't know if it proves anything: The HVR-1600 I originally bought was incompatible with that mobo (a known bug at Hauppauge) and it's possible that the PVR-150 has the same problem.  I really only have the Ubuntu box to work with, and it doesn't work in Dapper or Feisty.
If things aren't working off the feisty live disk, then you have got a bad card.

---

### Post by GrammatonCleric on 2007-06-23
Better late then never....but I recently built a mythtv box for a friend and I encountered the same issue.  I just moved the PVR-150 to another PCI slot and WaLa it was working fine...

-GC

---

