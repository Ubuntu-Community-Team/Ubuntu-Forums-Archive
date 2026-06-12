---
title: "Logitech quickcam Pro 9000 --&gt; Could not connect to video device"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by teak0413 on 2008-01-08
Could someone pleas post a cookbook method of connecting a Logitech PRO 9000 webcam. I have found posts that go all over and a new user like myself would appreciate having everything in one place with a checklist. I have tried multiple times without success.

Thank you

---

### Post by Nevell on 2008-01-09
I have the same problems.
Camorama and Skype don't see this camera, but lucview see /dev/video0 with no problems... I trying many ways, but all of this ways dont work for me...
> caminfo
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "UVC Camera (046d:0990)"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 960x720
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

Someone help us?

---

### Post by wjston on 2008-01-09
> **Nevell said:**
> I have the same problems.
Camorama and Skype don't see this camera, but lucview see /dev/video0 with no problems... I trying many ways, but all of this ways dont work for me...

Someone help us?

have you tried typing **luvcview** into a terminal to see whether your camera works with Luvcview? If so, and the camera turns on and you see yourself, post the results of** luvcview -L**. You should see a number of different frame rates and video screen sizes that your camera can support. The part you should look for and post (everything from this line down)t is - pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }. I am on my way to work and will not be able to help until later this evening, but I will try to help both of you resolve your Skype issues. I was able to get my camera finally working on the weekend.

---

### Post by Nevell on 2008-01-09
Yes, _luvcview_ work correcly.
**luvcview -L**
> $ luvcview -L
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
        Time interval between frame: 1/5,  

**$ caminfo**
> CVideoDeviceInput: Warning: no channel info available.
CVideoDevice::ResetImagesRGB()
CVideoDevice::ResetImagesYUV()
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "UVC Camera (046d:0990)"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 960x720
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0


**$ lsmod | grep uvcvideo**
> uvcvideo               54788  0
compat_ioctl32          2304  1 uvcvideo
videodev               29312  2 quickcam,uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
usbcore               138632  10 quickcam,uvcvideo,snd_usb_audio,snd_usb_lib,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd


**$ lsusb**
> Bus 003 Device 007: ID 046d:0990 Logitech, Inc.


luvcview, Kopete and Cheese see my camera and i see myself... But in the Skype after press TEST button i see black image and TEST call to videoecho123 not work, he say "i could not get your video".

P.S. quickcam driver i installed after many test with 7.10 ubuntu, i thought this help for me, but no

---

### Post by wjston on 2008-01-09
> luvcview, Kopete and Cheese see my camera and i see myself... But in the Skype after press TEST button i see black image and TEST call to videoecho123 not work, he say "i could not get your video".

P.S. quickcam driver i installed after many test with 7.10 ubuntu, i thought this help for me, but no

Can you see the camera when you go to >Options>Video? 

Also, my camera would freeze about 10 seconds after starting a call. I had to enter information in the config file. I will let you know tonight what it was.

OK, here is the information I added to my config.xml file from my .Skype folder (located in /my_home_folder/.Skype/my_username/config.xml):
<Video>
      <AutoSend>1</AutoSend>
     [COLOR="Red"] <CaptureHeight>600</CaptureHeight>
      <CaptureWidth>800</CaptureWidth>
      <Device>/dev/video0</Device>
      <Fps>25</Fps>[/COLOR]
    </Video>

Go to your home folder>press Ctrl_H and this should show all hidden folders in your home folder. Navigate to the .Skype folder and then the folder with the config.xml file in it. Right click on the file and choose>open with> then choose either a text editor or Bluefish editor or some other editor that will allow you to add information. Add the part that I highlighted in red or a Height and Width that works for you. This hopefully will help.

---

### Post by teak0413 on 2008-01-10
These are my results:
 luvcview -L
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
        Time interval between frame: 1/5,

---

### Post by teak0413 on 2008-01-10
lsmod | grep uvcvideo
uvcvideo               52228  0 
compat_ioctl32         11136  1 uvcvideo
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
usbcore               161584  7 snd_usb_audio,snd_usb_lib,uvcvideo,usblp,ohci_hcd,ehci_hcd

---

### Post by teak0413 on 2008-01-11
dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=2293d861-a090-4455-8c31-4603e72eb4c3 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F76C0 checksum 0
[    0.000000] ACPI: RSDP 000F76C0, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT 7FEE3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEEC440, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3280, 917B (r1 NVIDIA AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEEC640, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEEC6C0, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEEC580, 007C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515614
[    0.000000] Kernel command line: root=UUID=2293d861-a090-4455-8c31-4603e72eb4c3 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   14.794417] time.c: Detected 2812.960 MHz processor.
[   14.795786] Console: colour VGA+ 80x25
[   14.795798] Checking aperture...
[   14.795800] CPU 0: aperture @ 7a82000000 size 32 MB
[   14.795801] Aperture too small (32 MB)
[   14.800230] No AGP bridge found
[   14.813135] Memory: 2055072k/2096000k available (2274k kernel code, 40540k reserved, 1181k data, 296k init)
[   14.813168] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.890856] Calibrating delay using timer specific routine.. 5630.16 BogoMIPS (lpj=11260338)
[   14.890878] Security Framework v1.0.0 initialized
[   14.890883] SELinux:  Disabled at boot.
[   14.890992] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   14.891782] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.892214] Mount-cache hash table entries: 256
[   14.892303] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.892305] CPU: L2 Cache: 1024K (64 bytes/line)
[   14.892307] CPU 0/0 -> Node 0
[   14.892308] CPU: Physical Processor ID: 0
[   14.892310] CPU: Processor Core ID: 0
[   14.892322] SMP alternatives: switching to UP code
[   14.892491] Early unpacking initramfs... done
[   15.098667] ACPI: Core revision 20070126
[   15.098719] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.143003] Using local APIC timer interrupts.
[   15.178554] result 12557838
[   15.178555] Detected 12.557 MHz APIC timer.
[   15.178874] SMP alternatives: switching to SMP code
[   15.178925] Booting processor 1/2 APIC 0x1
[   15.189114] Initializing CPU#1
[   15.266935] Calibrating delay using timer specific routine.. 5626.09 BogoMIPS (lpj=11252191)
[   15.266940] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.266941] CPU: L2 Cache: 1024K (64 bytes/line)
[   15.266943] CPU 1/1 -> Node 0
[   15.266945] CPU: Physical Processor ID: 0
[   15.266946] CPU: Processor Core ID: 1
[   15.267028] AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 03
[   15.270828] Brought up 2 CPUs
[   15.833727] migration_cost=303
[   15.833752] NET: Registered protocol family 16
[   15.833816] ACPI: bus type pci registered
[   15.833820] PCI: Using configuration type 1
[   15.835011] ACPI: EC: Look up EC in DSDT
[   15.841234] ACPI: Interpreter enabled
[   15.841238] ACPI: (supports S0 S1 S3 S4 S5)
[   15.841255] ACPI: Using IOAPIC for interrupt routing
[   15.850018] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.850024] PCI: Probing PCI hardware (bus 00)
[   15.850492] PCI: Transparent bridge - 0000:00:06.0
[   15.850573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.850828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   15.887078] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[   15.887236] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.887395] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   15.887552] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[   15.887708] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.887866] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 *11 14 15)
[   15.888022] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.888179] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.888336] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.888494] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   15.888652] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   15.888813] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   15.888971] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.889129] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   15.889286] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   15.889443] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.889601] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[   15.889759] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   15.889916] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[   15.890101] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   15.890279] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   15.890456] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   15.890632] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   15.890811] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   15.890988] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[   15.891165] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   15.891342] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   15.891520] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   15.891698] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   15.891876] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   15.892054] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   15.892231] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   15.892408] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   15.892585] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   15.892763] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   15.892943] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   15.893121] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   15.893299] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[   15.893381] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.893388] pnp: PnP ACPI init
[   15.893394] ACPI: bus type pnp registered
[   15.897940] pnp: PnP ACPI: found 15 devices
[   15.897942] ACPI: ACPI bus type pnp unregistered
[   15.897980] PCI: Using ACPI for IRQ routing
[   15.897983] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.898032] NET: Registered protocol family 8
[   15.898033] NET: Registered protocol family 20
[   15.898079] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   15.898082] hpet0: 3 32-bit timers, 25000000 Hz
[   15.899126] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   15.899128] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   15.899130] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   15.899132] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   15.899133] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   15.899135] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   15.899142] pnp: 00:0d: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   15.899145] pnp: 00:0e: iomem range 0xcca00-0xcffff has been reserved
[   15.899147] pnp: 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   15.899149] pnp: 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   15.899151] pnp: 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   15.899356] PCI: Bridge: 0000:00:06.0
[   15.899357]   IO window: disabled.
[   15.899359]   MEM window: fde00000-fdefffff
[   15.899361]   PREFETCH window: disabled.
[   15.899363] PCI: Bridge: 0000:00:0f.0
[   15.899364]   IO window: a000-afff
[   15.899366]   MEM window: f8000000-fbffffff
[   15.899368]   PREFETCH window: e0000000-efffffff
[   15.899374] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   15.899379] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   15.899387] NET: Registered protocol family 2
[   15.902887] Time: hpet clocksource has been installed.
[   15.946815] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.947344] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   15.949471] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.949854] TCP: Hash tables configured (established 262144 bind 65536)
[   15.949856] TCP reno registered
[   15.962854] checking if image is initramfs... it is
[   16.367351] Freeing initrd memory: 7184k freed
[   16.370697] audit: initializing netlink socket (disabled)
[   16.370708] audit(1200079060.544:1): initialized
[   16.372081] VFS: Disk quotas dquot_6.5.1
[   16.372116] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.372173] io scheduler noop registered
[   16.372175] io scheduler anticipatory registered
[   16.372176] io scheduler deadline registered
[   16.372238] io scheduler cfq registered (default)
[   16.399979] Boot video device is 0000:02:00.0
[   16.400078] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   16.400094] assign_interrupt_mode Found MSI capability
[   16.400096] Allocate Port Service[0000:00:0f.0:pcie00]
[   16.415722] Real Time Clock Driver v1.12ac
[   16.415876] hpet_resources: 0xfefff000 is busy
[   16.415900] Linux agpgart interface v0.102 (c) Dave Jones
[   16.415902] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.415988] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.416389] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.416824] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.416974] input: Macintosh mouse button emulation as /class/input/input0
[   16.417022] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.417546] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.417550] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.417630] mice: PS/2 mouse device common for all mice
[   16.417718] TCP cubic registered
[   16.417763] NET: Registered protocol family 1
[   16.417907] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.417913] Freeing unused kernel memory: 296k freed
[   16.443607] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.543614] AppArmor: AppArmor initialized<5>audit(1200079061.724:2):  type=1505 info="AppArmor initialized" pid=1279
[   17.548197] fuse init (API version 7.8)
[   17.550955] Failure registering capabilities with primary security module.
[   17.577279] ACPI: Fan [FAN] (on)
[   17.581153] ACPI: Thermal Zone [THRM] (40 C)
[   17.914110] usbcore: registered new interface driver usbfs
[   17.914132] usbcore: registered new interface driver hub
[   17.914149] usbcore: registered new device driver usb
[   17.915187] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   17.915196] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   17.915449] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   17.915455] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   17.915585] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   17.915608] ehci_hcd 0000:00:02.1: debug port 1
[   17.915611] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   17.915620] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
[   17.915626] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.915700] usb usb1: configuration #1 chosen from 1 choice
[   17.915718] hub 1-0:1.0: USB hub found
[   17.915722] hub 1-0:1.0: 10 ports detected
[   17.918710] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.926577] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   17.944900] SCSI subsystem initialized
[   17.948310] libata version 2.21 loaded.
[   17.982989] Floppy drive(s): fd0 is 1.44M
[   18.006160] FDC 0 is a post-1991 82077
[   18.022983] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   18.022992] ACPI: PCI Interrupt 0000:01:08.2[C] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   18.023197] ehci_hcd 0000:01:08.2: EHCI Host Controller
[   18.023242] ehci_hcd 0000:01:08.2: new USB bus registered, assigned bus number 2
[   18.023279] ehci_hcd 0000:01:08.2: irq 16, io mem 0xfdefd000
[   18.023285] ehci_hcd 0000:01:08.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   18.023356] usb usb2: configuration #1 chosen from 1 choice
[   18.023375] hub 2-0:1.0: USB hub found
[   18.023380] hub 2-0:1.0: 5 ports detected
[   18.131246] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   18.131255] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 22
[   18.131260] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   18.131266] forcedeth: using HIGHDMA
[   18.270566] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   18.423274] usb 1-1: configuration #1 chosen from 1 choice
[   18.654950] eth0: forcedeth.c: subsystem: 01043:8239 bound to 0000:00:08.0
[   18.655161] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   18.655170] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
[   18.655341] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.655346] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   18.655388] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   18.655407] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[   18.716601] usb usb3: configuration #1 chosen from 1 choice
[   18.716623] hub 3-0:1.0: USB hub found
[   18.716629] hub 3-0:1.0: 10 ports detected
[   18.822890] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   18.822898] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   18.823047] ohci_hcd 0000:01:08.0: OHCI Host Controller
[   18.823099] ohci_hcd 0000:01:08.0: new USB bus registered, assigned bus number 4
[   18.823116] ohci_hcd 0000:01:08.0: irq 18, io mem 0xfdeff000
[   18.914632] usb 2-3: new high speed USB device using ehci_hcd and address 2
[   19.187292] usb 2-3: configuration #1 chosen from 1 choice
[   19.392946] usb usb4: configuration #1 chosen from 1 choice
[   19.392968] hub 4-0:1.0: USB hub found
[   19.392973] hub 4-0:1.0: 3 ports detected
[   19.494587] usb 3-3: new full speed USB device using ohci_hcd and address 2
[   19.736646] usb 3-3: configuration #1 chosen from 1 choice
[   19.910778] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   19.910785] ACPI: PCI Interrupt 0000:01:08.1[B] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   19.910949] ohci_hcd 0000:01:08.1: OHCI Host Controller
[   19.911002] ohci_hcd 0000:01:08.1: new USB bus registered, assigned bus number 5
[   19.911020] ohci_hcd 0000:01:08.1: irq 19, io mem 0xfdefe000
[   20.481212] usb usb5: configuration #1 chosen from 1 choice
[   20.481348] hub 5-0:1.0: USB hub found
[   20.481354] hub 5-0:1.0: 2 ports detected
[   20.999984] sata_nv 0000:00:05.0: version 3.4
[   21.000285] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   21.000292] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   21.000518] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   21.000634] scsi0 : sata_nv
[   21.000669] scsi1 : sata_nv
[   21.000725] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001dc00 irq 20
[   21.000727] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001dc08 irq 20
[   21.004541] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.004545] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.470293] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   21.502598] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-11, max UDMA7
[   21.502602] ata1.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   21.514586] ata1.00: configured for UDMA/133
[   21.986247] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.154314] ata2.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66
[   22.334299] ata2.00: configured for UDMA/66
[   22.334366] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   22.334999] scsi 1:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.00 PQ: 0 ANSI: 5
[   22.335529] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   22.335532] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   22.335720] PCI: Setting latency timer of device 0000:00:05.1 to 64
[   22.335776] scsi2 : sata_nv
[   22.335997] scsi3 : sata_nv
[   22.336136] ata3: SATA max UDMA/133 cmd 0x00000000000109e0 ctl 0x0000000000010be2 bmdma 0x000000000001c800 irq 23
[   22.336139] ata4: SATA max UDMA/133 cmd 0x0000000000010960 ctl 0x0000000000010b62 bmdma 0x000000000001c808 irq 23
[   22.650185] ata3: SATA link down (SStatus 0 SControl 300)
[   22.974155] ata4: SATA link down (SStatus 0 SControl 300)
[   22.984843] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 22
[   22.984846] ACPI: PCI Interrupt 0000:00:05.2[C] -> Link [ASA2] -> GSI 22 (level, low) -> IRQ 22
[   22.985015] PCI: Setting latency timer of device 0000:00:05.2 to 64
[   22.985079] scsi4 : sata_nv
[   22.985299] scsi5 : sata_nv
[   22.985446] ata5: SATA max UDMA/133 cmd 0x000000000001c400 ctl 0x000000000001c002 bmdma 0x000000000001b400 irq 22
[   22.985449] ata6: SATA max UDMA/133 cmd 0x000000000001bc00 ctl 0x000000000001b802 bmdma 0x000000000001b408 irq 22
[   23.298128] ata5: SATA link down (SStatus 0 SControl 300)
[   23.622098] ata6: SATA link down (SStatus 0 SControl 300)
[   23.632375] NFORCE-MCP55: IDE controller at PCI slot 0000:00:04.0
[   23.632390] NFORCE-MCP55: chipset revision 161
[   23.632392] NFORCE-MCP55: not 100% native mode: will probe irqs later
[   23.632395] NFORCE-MCP55: BIOS didn't set cable bits correctly. Enabling workaround.
[   23.632398] NFORCE-MCP55: 0000:00:04.0 (rev a1) UDMA133 controller
[   23.632404]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   23.632411] Probing IDE interface ide0...
[   23.645666] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   23.645676] sd 0:0:0:0: [sda] Write Protect is off
[   23.645678] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.645687] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.645725] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   23.645730] sd 0:0:0:0: [sda] Write Protect is off
[   23.645731] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.645739] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.645742]  sda: sda1
[   23.673480] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.676188] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.676294] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   23.680404] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.680408] Uniform CD-ROM driver Revision: 3.20
[   23.680446] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.370106] hda: DVD RW DRU-820A, ATAPI CD/DVD-ROM drive
[   24.654079] hdb: MAXTOR STM3160812A, ATA DISK drive
[   24.716146] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   24.722609] hdb: max request size: 512KiB
[   24.765395] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   24.789800] hdb: cache flushes supported
[   24.789825]  hdb: hdb1 hdb2 < hdb5 >
[   24.843701] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   25.124859] Attempting manual resume
[   25.124862] swsusp: Resume From Partition 3:69
[   25.124863] PM: Checking swsusp image.
[   25.125011] PM: Resume from disk failed.
[   25.152780] kjournald starting.  Commit interval 5 seconds
[   25.152789] EXT3-fs: mounted filesystem with ordered data mode.
[   30.112728] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.130416] Netfilter messages via NETLINK v0.30.
[   30.139661] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   31.745560] input: PC Speaker as /class/input/input2
[   31.802812] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.805333] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.826247] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   31.826391] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   32.032626] input: PS2++ Logitech MX Mouse as /class/input/input3
[   32.035600] parport_pc 00:0a: reported by Plug and Play ACPI
[   32.035625] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   32.144830] nvidia: module license 'NVIDIA' taints kernel.
[   32.399329] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   32.399334] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 16
[   32.399340] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   32.399435] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.07  Thu Dec 13 18:34:01 PST 2007
[   32.489079] Linux video capture interface: v2.00
[   32.513656] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x1604
[   32.513671] usbcore: registered new interface driver usblp
[   32.513673] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   32.590504] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[   32.621208] usbcore: registered new interface driver uvcvideo
[   32.621212] USB Video Class driver (v0.1.0)
[   32.715135] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   32.715140] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [AAZA] -> GSI 21 (level, low) -> IRQ 21
[   32.715357] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   32.722933] usbcore: registered new interface driver snd-usb-audio
[   33.977542] lp0: using parport0 (interrupt-driven).
[   34.036997] Adding 6040400k swap on /dev/hdb5.  Priority:-1 extents:1 across:6040400k
[   34.371729] EXT3 FS on hdb1, internal journal
[   36.767826] No dock devices found.
[   36.812619] input: Power Button (FF) as /class/input/input4
[   36.812633] ACPI: Power Button (FF) [PWRF]
[   36.812662] input: Power Button (CM) as /class/input/input5
[   36.812672] ACPI: Power Button (CM) [PWRB]
[   37.135422] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ processors (version 2.00.00)
[   37.135311] powernow-k8: MP systems not supported by PSB BIOS structure
[   37.135450] powernow-k8: MP systems not supported by PSB BIOS structure
[   38.219983] ppdev: user-space parallel port driver
[   38.348425] NET: Registered protocol family 10
[   38.348540] lo: Disabled Privacy Extensions
[   38.508700] audit(1200097083.624:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5613 profile="/usr/sbin/cupsd"
[   40.978315] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   41.033651] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   41.047854] NFSD: starting 90-second grace period
[   41.819278] Failure registering capabilities with primary security module.
[   46.603585] NET: Registered protocol family 17
[   59.427211] eth0: no IPv6 routers present

---

### Post by wjston on 2008-01-12
> **teak0413 said:**
> dmesg
[   15.178925] Booting processor 1/2 APIC 0x1
[   15.189114] Initializing CPU#1
[   15.266935] Calibrating delay using timer specific routine.. 5626.09 BogoMIPS (lpj=11252191)
[   15.266940] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.266941] CPU: L2 Cache: 1024K (64 bytes/line)
[   15.266943] CPU 1/1 -> Node 0
[   15.266945] CPU: Physical Processor ID: 0
[   15.266946] CPU: Processor Core ID: 1
[   15.267028] AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 03
[   15.270828] Brought up 2 CPUs
[   32.590504] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[   32.621208] usbcore: registered new interface driver uvcvideo
[   32.621212] USB Video Class driver (v0.1.0)

I see that you are running a 64 bit processor. You haven't said whether you tried inputting the information I posted into your .Skype confi.xml file. If you have and are still not able to view video you may need to build the uvc driver for your 64 bit system. There are specific directions for doing so here: [http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393)
Also, make sure that your logitech camera isn't located on something other than dev/video0. It may be that it is located at /dev/video1 if you have other video devices enabled (TV capture cards). You can find out by going into Skype options>video and check the video device in the drop down box.

---

### Post by teak0413 on 2008-01-12
I am not using Skype

---

### Post by wjston on 2008-01-12
> **teak0413 said:**
> I am not using Skype

The fastest way to get help is to provide as many details as you can so that forum members no what it is you are having a problem with. It would help to know what program you are using. Other members using the same program may be able to help you.

---

### Post by ridgeland on 2008-04-01
Hi wjston,
I have a Pro9000 that I cannot get to work on a Dell-Ubuntu PC.  With my old Gateway PC and 8.04 Alpha 6 it worked fine.  I used Skype for a couple of calls.  I tried again on the Dell PC with 7.04, 7.10 and 8.04 Beta and it won't work.  With 8.04 in Skype video-> test I get an image for about 10 seconds then it breaks up in horizontal lines and stuck replay of two second on image on the bottom half of the video window.
I tried post #5 edit to ~/.skype/me/config.xml  Same 10 seconds and crash.
On this Dell I can get Skype to work with SuSE 10.3.  Works fine.
This is a dual core but I'm using i386 Linux installs because Skype wants i386.

I copied the ...config.xml from the working SuSE to the not working Ubuntu but that did not help.

What files might I copy from SuSE that would get Ubuntu working?

ED: I just tired luvcview and it looks great.  Image is stable and good quality.  Why not with Sype etc?

---

