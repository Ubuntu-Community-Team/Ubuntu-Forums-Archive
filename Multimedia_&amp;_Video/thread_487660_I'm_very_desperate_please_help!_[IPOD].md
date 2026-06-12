---
title: "I'm very desperate please help! [IPOD]"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Opeth115 on 2007-06-29
Ok well i have tried almost every program with no avail to put my music onto my ipod... i have 2160 songs on my computer and none of them on my ipod.  I have tried amarok, doesn't do anything it just sits there,  rythem box freezes all the time, banshee gives me so error saying that banshee has failed or something, gtk pod  can only recognize like 100 of my songs..., yam pod, also freezes like rythem box.  what can i do?  i would really like my music on my ipod...

---

### Post by Skeorx13 on 2007-06-29
Amarok can do it, you just have to set up the ipod in the options. Connect the ipod to your computer. Wait for it to mount. Then go into amarok options and go to the media devices tab. You have to sort of create a profile for your ipod (give the name, mount spot, what-not) and make sure it recognizes it. If you set it up right you should be good to go. When you want amarok to access the ipod you have to go to the media devices tab on the playlist editor thing and there should be an icon to "connect to media device" just below the menu bar. Click that and wait. It may take a few seconds to fully load. Then you just go to your collection, highlight what you want, right click and send to media device. Make sure you go back to the media device tab and right click then click on "start transfer." I can do a step by step guide with screenshots if you need.

---

### Post by Opeth115 on 2007-06-29
im pretty sure that is the exact same process iw ent through but it just didn't work i dunno ill try it again and see what happens then repost

---

### Post by Opeth115 on 2007-06-29
i just tried it and it went well for about 1000 songs then my ipod jsut seemed to unoumnt and remount its sefl screwing the entire thing up

---

### Post by tgalati4 on 2007-06-29
You might have a cable problem or a file system problem on the iPod.  

Find another cable, or a slower computer with the existing cable.  Sounds like a USB data transfer problem.

In a terminal post the output of:

dmesg | tail -n 50

It should look something like:

tgalati4@tubuntu2:~$ dmesg | tail -n 30
[20267592.968000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[20267592.984000] sda: Write Protect is off
[20267592.984000] sda: Mode Sense: 64 00 00 08
[20267592.984000] sda: assuming drive cache: write through
[20267592.984000]  sda: [mac] sda1 sda2 sda3
[20267593.032000] sd 3:0:0:0: Attached scsi removable disk sda
[20267593.032000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[20267593.032000] usb-storage: device scan complete
[20268841.524000] usb 1-1.4: USB disconnect, address 6
[20369923.476000] usb 1-1.4: new full speed USB device using ohci_hcd and address 7
[20369923.592000] scsi4 : SCSI emulation for USB Mass Storage devices
[20369923.592000] usb 1-1.4: 400mA over 100mA budget!
[20369923.592000] hub 1-1:1.0: 64mA over power budget!
[20369923.592000] usb-storage: device found at 7
[20369923.592000] usb-storage: waiting for device to settle before scanning
[20369928.600000]   Vendor: Apple     Model: iPod              Rev: 1.62
[20369928.600000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[20369928.612000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[20369928.624000] sda: Write Protect is off
[20369928.624000] sda: Mode Sense: 64 00 00 08
[20369928.624000] sda: assuming drive cache: write through
[20369928.640000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[20369928.656000] sda: Write Protect is off
[20369928.656000] sda: Mode Sense: 64 00 00 08
[20369928.656000] sda: assuming drive cache: write through
[20369928.656000]  sda: [mac] sda1 sda2 sda3
[20369928.972000] sd 4:0:0:0: Attached scsi removable disk sda
[20369928.972000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[20369928.972000] usb-storage: device scan complete
[20372115.576000] usb 1-1.4: USB disconnect, address 7


Any write errors will normally show up here.

---

### Post by Opeth115 on 2007-06-29
matt@matt-desktop:~$ dmesg | tail -n 50
[   13.117484] parport: PnPBIOS parport detected.
[   13.117535] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   13.165279] nvidia: module license 'NVIDIA' taints kernel.
[   13.415810] NET: Registered protocol family 17
[   13.415908] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.415915] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   13.416010] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   13.467138] logips2pp: Detected unknown logitech mouse model 1
[   13.561246] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   13.561262] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   13.641182] input: PS/2 Logitech Mouse as /class/input/input3
[   14.118371] fuse init (API version 7.8)
[   14.144400] lp0: using parport0 (interrupt-driven).
[   14.233329] Adding 6024332k swap on /dev/disk/by-uuid/9e149e3b-abbe-432b-80d9-0894876c2d71.  Priority:-1 extents:1 across:6024332k
[   14.392790] EXT3 FS on sda1, internal journal
[   14.586235] NET: Registered protocol family 10
[   14.586350] lo: Disabled Privacy Extensions
[   25.318053] eth0: no IPv6 routers present
[   37.459560] kjournald starting.  Commit interval 5 seconds
[   37.459869] EXT3 FS on sda3, internal journal
[   37.459873] EXT3-fs: mounted filesystem with ordered data mode.
[   37.505197] ReiserFS: sda4: found reiserfs format "3.6" with standard journal
[   37.505208] ReiserFS: sda4: using ordered data mode
[   37.505423] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   37.505617] ReiserFS: sda4: checking transaction log (sda4)
[   37.513438] ReiserFS: sda4: Using r5 hash to sort names
[   42.614144] ibm_acpi: ec object not found
[   42.701371] No dock devices found.
[   42.708577] Using specific hotkey driver
[   42.756793] input: Power Button (FF) as /class/input/input4
[   42.756813] ACPI: Power Button (FF) [PWRF]
[   42.756846] input: Sleep Button (CM) as /class/input/input5
[   42.756863] ACPI: Sleep Button (CM) [SLPB]
[   42.830234] pcc_acpi: loading...
[   45.413517] ppdev: user-space parallel port driver
[   46.402738] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   46.402742] apm: disabled - APM is not SMP safe.
[   48.940707] Bluetooth: Core ver 2.11
[   48.940753] NET: Registered protocol family 31
[   48.940755] Bluetooth: HCI device and connection manager initialized
[   48.940758] Bluetooth: HCI socket layer initialized
[   48.963822] Bluetooth: L2CAP ver 2.8
[   48.963826] Bluetooth: L2CAP socket layer initialized
[   49.108404] Bluetooth: RFCOMM socket layer initialized
[   49.108413] Bluetooth: RFCOMM TTY layer initialized
[   49.108414] Bluetooth: RFCOMM ver 1.8
[   58.702316] eth0: no IPv6 routers present
[   92.855070] FAT: Filesystem panic (dev sdb2)
[   92.855076]     fat_free_clusters: deleting FAT entry beyond EOF
[   92.855079]     File system has been set read-only

that's the out put of dmesg | tail -n 50

---

### Post by Opeth115 on 2007-06-29
YAY! all fixed i plugged my ipod into a different USB port and it allw orked fin im guessing it's just my 2 USB ports ont he front of my computer cuz the one i tried on the back worked perfect...  any ideas as to what's wrong with them?

---

### Post by tseliot on 2007-06-29
I have edited the title of this thread.

Please, try to use a more explicative title (e.g. "my Ipod is not detected") next time

---

### Post by Opeth115 on 2007-06-29
tanks for the title edit but it's not fixed... i thought it was but now my ipod does not see any of the music it says all of the space is taken up but only 699 songs are available... any ideas?

---

### Post by Opeth115 on 2007-06-29
anyone know why?  i can see all of my music under rockbox but i really don't like the GUI of it on a 4th generation color ipod...it's ugly  why can is ee my music there but not in the Appl firmware?

---

### Post by Skeorx13 on 2007-06-29
Might be how you transferred it over. Sometimes when I'm in windows winamp doesn't transfer my video over to my ipod properly and takes up space but isn't listed in the video section when disconnected from the computer. I'd say delete the files that aren't listed and try to transfer them over again. (do a few only and check it so you don't have to wait so long to test it out) That tends to do the trick for me. Try it through amarok (if you finally got that working right) and it should work ok. Amarok might ask you about a locked file and if it should delete it. Just click yes, it won't hurt your ipod at all.

---

### Post by tgalati4 on 2007-07-01
Try deleting files in your .Trash directory on the iPod.  This is best done using the command line.  When files get deleted under Linux, they are moved to .Trash on that drive, so you will need to delete them from .Trash to free up space.

As far as the USB ports, sometimes the front ports don't supply enough power for certain devices.  The back ports usually do have more power.  I don't know why but I've had the same experience with HP/Compaq computers with ports on the front and back.  Weird but true.  Also using the USB ports on some printers will work with some devices but not others.  It's a crap shoot.

---

