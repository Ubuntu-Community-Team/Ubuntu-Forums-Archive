---
title: "Madwifi, WG511T, modprobe ath_pci"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by versteckt on 2006-01-02
First off, I must say hello to the forum since I've not yet posted here.

Secondly, I have a problem (don't we all as beginners?).  I've searched around on the forum and elsewhere on the Internet, but can't seem to find an answer anywhere so I figured I'd post here to see if perhaps a more knowledgeable person could help me out.

I spent a good part of yesterday trying to figure out how to install MadWiFi for my Netgear WG511T card on the Breezy system on my laptop.  Although this brought about much frustration, as I encountered countless errors that I had to work through with each step, I was successful in installing the card and accessing the Internet wirelessly.  But now after a reboot, I'm stuck back at the beginning.  No wireless.  When booting Ubuntu, my system just hangs when it attempts to configure the network connection.  My wireless card has power to it, as one light is on and blinks occasionally, but after about 3 minutes, my system will start without wireless connectivity.  So I figure I'll just reconfigure the network.  I first checked the GUI network utility, but only eth0 and ppp0 are listed.  So I turn back to the [madwifi newbie howto]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") for some help.

I begin at the step where it says to type the command

```
modprobe ath_pci
```

in order to load the madwifi driver module into the system, but in doing so, I'm introduced to more errors:

```
root@odin:~# modprobe ath_pci
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.12-10-386/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.12-10-386/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

So I take a look through dmesg as it says, and find this BIG mess:

```
root@odin:~# dmesg
 ath_pci: Unknown symbol ath_hal_getwirelessmodes
[4294705.608000] Real Time Clock Driver v1.12
[4294705.803000] input: PC Speaker
[4294706.570000] NET: Registered protocol family 17
[4294716.561000] r8169: eth0: PHY reset until link up
[4294726.561000] r8169: eth0: PHY reset until link up
[4294736.561000] r8169: eth0: PHY reset until link up
[4294746.561000] r8169: eth0: PHY reset until link up
[4294756.561000] r8169: eth0: PHY reset until link up
[4294766.561000] r8169: eth0: PHY reset until link up
[4294773.583000] ACPI: AC Adapter [AC0] (on-line)
[4294773.635000] ACPI: Battery Slot [BAT0] (battery present)
[4294773.653000] ACPI: Power Button (FF) [PWRF]
[4294773.653000] ACPI: Lid Switch [LID]
[4294773.653000] ACPI: Sleep Button (CM) [SLPB]
[4294773.653000] ACPI: Power Button (CM) [PWRB]
[4294773.746000] ibm_acpi: ec object not found
[4294773.852000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294776.561000] r8169: eth0: PHY reset until link up
[4294780.410000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294780.410000] apm: overridden by ACPI.
[4294781.352000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[4294781.354000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[4294781.357000] cs: IO port probe 0xc00-0xcf7: clean.
[4294781.358000] cs: IO port probe 0xc00-0xcf7: clean.
[4294781.358000] cs: IO port probe 0xa00-0xaff: clean.
[4294781.359000] cs: IO port probe 0xa00-0xaff: clean.
[4294782.224000] usb 3-1: new low speed USB device using ohci_hcd and address 2
[4294782.358000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:03.2-1
[4294782.892000] Bluetooth: Core ver 2.7
[4294782.892000] NET: Registered protocol family 31
[4294782.892000] Bluetooth: HCI device and connection manager initialized
[4294782.892000] Bluetooth: HCI socket layer initialized
[4294782.921000] Bluetooth: L2CAP ver 2.7
[4294782.921000] Bluetooth: L2CAP socket layer initialized
[4294782.948000] Bluetooth: RFCOMM ver 1.5
[4294782.948000] Bluetooth: RFCOMM socket layer initialized
[4294782.948000] Bluetooth: RFCOMM TTY layer initialized
[4294786.561000] r8169: eth0: PHY reset until link up
[4294792.181000] NET: Registered protocol family 10
[4294792.181000] Disabled Privacy Extensions on device c02eb280(lo)
[4294792.181000] IPv6 over IPv4 tunneling driver
[4294796.561000] r8169: eth0: PHY reset until link up
[4294802.995000] eth0: no IPv6 routers present
[4294806.561000] r8169: eth0: PHY reset until link up
[4294816.561000] r8169: eth0: PHY reset until link up
[4294826.561000] r8169: eth0: PHY reset until link up
[4294836.561000] r8169: eth0: PHY reset until link up
[4294846.561000] r8169: eth0: PHY reset until link up
[4294856.561000] r8169: eth0: PHY reset until link up
[4294866.561000] r8169: eth0: PHY reset until link up
[4294876.561000] r8169: eth0: PHY reset until link up
[4294883.065000] ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
[4294883.065000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[4294883.065000] ath_pci: Unknown symbol ath_rate_tx_complete
[4294883.066000] ath_pci: disagrees about version of symbol _ath_hal_attach
[4294883.066000] ath_pci: Unknown symbol _ath_hal_attach
[4294883.066000] ath_pci: Unknown symbol ath_rate_attach
[4294883.066000] ath_pci: Unknown symbol ath_rate_newassoc
[4294883.066000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[4294883.066000] ath_pci: Unknown symbol ath_hal_computetxtime
[4294883.066000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[4294883.066000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[4294883.066000] ath_pci: disagrees about version of symbol ath_hal_detach
[4294883.066000] ath_pci: Unknown symbol ath_hal_detach
[4294883.067000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4294883.067000] ath_pci: Unknown symbol ath_rate_detach
[4294883.067000] ath_pci: Unknown symbol ath_rate_node_init
[4294883.067000] ath_pci: Unknown symbol ath_rate_findrate
[4294883.067000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[4294883.067000] ath_pci: Unknown symbol ath_hal_init_channels
[4294883.067000] ath_pci: Unknown symbol ath_rate_newstate
[4294883.067000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4294883.068000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[4294883.068000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[4294886.561000] r8169: eth0: PHY reset until link up
[4294896.561000] r8169: eth0: PHY reset until link up
[4294901.297000] usb 3-1: USB disconnect, address 2
[4294906.561000] r8169: eth0: PHY reset until link up
[4294914.637000] ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
[4294914.637000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[4294914.637000] ath_pci: Unknown symbol ath_rate_tx_complete
[4294914.637000] ath_pci: disagrees about version of symbol _ath_hal_attach
[4294914.637000] ath_pci: Unknown symbol _ath_hal_attach
[4294914.638000] ath_pci: Unknown symbol ath_rate_attach
[4294914.638000] ath_pci: Unknown symbol ath_rate_newassoc
[4294914.638000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[4294914.638000] ath_pci: Unknown symbol ath_hal_computetxtime
[4294914.638000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[4294914.638000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[4294914.638000] ath_pci: disagrees about version of symbol ath_hal_detach
[4294914.638000] ath_pci: Unknown symbol ath_hal_detach
[4294914.639000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4294914.639000] ath_pci: Unknown symbol ath_rate_detach
[4294914.639000] ath_pci: Unknown symbol ath_rate_node_init
[4294914.639000] ath_pci: Unknown symbol ath_rate_findrate
[4294914.639000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[4294914.639000] ath_pci: Unknown symbol ath_hal_init_channels
[4294914.639000] ath_pci: Unknown symbol ath_rate_newstate
[4294914.639000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4294914.639000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[4294914.639000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[4294916.561000] r8169: eth0: PHY reset until link up
[4294926.561000] r8169: eth0: PHY reset until link up
[4294936.561000] r8169: eth0: PHY reset until link up
[4294946.561000] r8169: eth0: PHY reset until link up
[4294956.561000] r8169: eth0: PHY reset until link up
[4294966.561000] r8169: eth0: PHY reset until link up
[4294976.561000] r8169: eth0: PHY reset until link up
[4294986.561000] r8169: eth0: PHY reset until link up
[4294996.561000] r8169: eth0: PHY reset until link up
[4295006.561000] r8169: eth0: PHY reset until link up
[4295016.561000] r8169: eth0: PHY reset until link up
[4295026.561000] r8169: eth0: PHY reset until link up
[4295036.561000] r8169: eth0: PHY reset until link up
[4295046.561000] r8169: eth0: PHY reset until link up
[4295056.561000] r8169: eth0: PHY reset until link up
[4295057.237000] ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
[4295057.237000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[4295057.237000] ath_pci: Unknown symbol ath_rate_tx_complete
[4295057.238000] ath_pci: disagrees about version of symbol _ath_hal_attach
[4295057.238000] ath_pci: Unknown symbol _ath_hal_attach
[4295057.238000] ath_pci: Unknown symbol ath_rate_attach
[4295057.238000] ath_pci: Unknown symbol ath_rate_newassoc
[4295057.238000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[4295057.238000] ath_pci: Unknown symbol ath_hal_computetxtime
[4295057.238000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[4295057.238000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[4295057.238000] ath_pci: disagrees about version of symbol ath_hal_detach
[4295057.238000] ath_pci: Unknown symbol ath_hal_detach
[4295057.239000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4295057.239000] ath_pci: Unknown symbol ath_rate_detach
[4295057.239000] ath_pci: Unknown symbol ath_rate_node_init
[4295057.239000] ath_pci: Unknown symbol ath_rate_findrate
[4295057.239000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[4295057.239000] ath_pci: Unknown symbol ath_hal_init_channels
[4295057.239000] ath_pci: Unknown symbol ath_rate_newstate
[4295057.239000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4295057.240000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[4295057.240000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[4295066.561000] r8169: eth0: PHY reset until link up
[4295076.561000] r8169: eth0: PHY reset until link up
[4295086.561000] r8169: eth0: PHY reset until link up
[4295096.561000] r8169: eth0: PHY reset until link up
[4295106.561000] r8169: eth0: PHY reset until link up
[4295116.561000] r8169: eth0: PHY reset until link up
[4295126.561000] r8169: eth0: PHY reset until link up
[4295136.561000] r8169: eth0: PHY reset until link up
[4295146.561000] r8169: eth0: PHY reset until link up
[4295156.561000] r8169: eth0: PHY reset until link up
[4295166.561000] r8169: eth0: PHY reset until link up
[4295176.561000] r8169: eth0: PHY reset until link up
[4295186.561000] r8169: eth0: PHY reset until link up
[4295196.561000] r8169: eth0: PHY reset until link up
[4295206.561000] r8169: eth0: PHY reset until link up
[4295216.151000] ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
[4295216.151000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[4295216.151000] ath_pci: Unknown symbol ath_rate_tx_complete
[4295216.152000] ath_pci: disagrees about version of symbol _ath_hal_attach
[4295216.152000] ath_pci: Unknown symbol _ath_hal_attach
[4295216.152000] ath_pci: Unknown symbol ath_rate_attach
[4295216.152000] ath_pci: Unknown symbol ath_rate_newassoc
[4295216.152000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[4295216.152000] ath_pci: Unknown symbol ath_hal_computetxtime
[4295216.152000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[4295216.152000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[4295216.152000] ath_pci: disagrees about version of symbol ath_hal_detach
[4295216.152000] ath_pci: Unknown symbol ath_hal_detach
[4295216.153000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4295216.153000] ath_pci: Unknown symbol ath_rate_detach
[4295216.153000] ath_pci: Unknown symbol ath_rate_node_init
[4295216.153000] ath_pci: Unknown symbol ath_rate_findrate
[4295216.153000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[4295216.153000] ath_pci: Unknown symbol ath_hal_init_channels
[4295216.153000] ath_pci: Unknown symbol ath_rate_newstate
[4295216.153000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4295216.153000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[4295216.153000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[4295216.561000] r8169: eth0: PHY reset until link up
[4295226.561000] r8169: eth0: PHY reset until link up
[4295236.561000] r8169: eth0: PHY reset until link up
[4295246.561000] r8169: eth0: PHY reset until link up
[4295256.561000] r8169: eth0: PHY reset until link up
[4295266.561000] r8169: eth0: PHY reset until link up
[4295276.561000] r8169: eth0: PHY reset until link up
[4295286.561000] r8169: eth0: PHY reset until link up
[4295296.561000] r8169: eth0: PHY reset until link up
[4295306.561000] r8169: eth0: PHY reset until link up
[4295316.561000] r8169: eth0: PHY reset until link up
[4295326.561000] r8169: eth0: PHY reset until link up
[4295336.561000] r8169: eth0: PHY reset until link up
[4295346.561000] r8169: eth0: PHY reset until link up
[4295356.561000] r8169: eth0: PHY reset until link up
[4295366.561000] r8169: eth0: PHY reset until link up
[4295376.561000] r8169: eth0: PHY reset until link up
[4295386.561000] r8169: eth0: PHY reset until link up
[4295396.561000] r8169: eth0: PHY reset until link up
[4295406.561000] r8169: eth0: PHY reset until link up
[4295416.561000] r8169: eth0: PHY reset until link up
[4295426.561000] r8169: eth0: PHY reset until link up
[4295436.561000] r8169: eth0: PHY reset until link up
[4295446.561000] r8169: eth0: PHY reset until link up
[4295456.561000] r8169: eth0: PHY reset until link up
[4295466.561000] r8169: eth0: PHY reset until link up
[4295476.561000] r8169: eth0: PHY reset until link up
[4295486.561000] r8169: eth0: PHY reset until link up
[4295496.561000] r8169: eth0: PHY reset until link up
[4295506.561000] r8169: eth0: PHY reset until link up
[4295516.561000] r8169: eth0: PHY reset until link up
[4295526.561000] r8169: eth0: PHY reset until link up
[4295536.561000] r8169: eth0: PHY reset until link up
[4295546.561000] r8169: eth0: PHY reset until link up
[4295556.561000] r8169: eth0: PHY reset until link up
[4295566.561000] r8169: eth0: PHY reset until link up
[4295576.561000] r8169: eth0: PHY reset until link up
[4295586.561000] r8169: eth0: PHY reset until link up
[4295596.561000] r8169: eth0: PHY reset until link up
[4295606.561000] r8169: eth0: PHY reset until link up
[4295616.561000] r8169: eth0: PHY reset until link up
[4295626.561000] r8169: eth0: PHY reset until link up
[4295636.561000] r8169: eth0: PHY reset until link up
[4295646.561000] r8169: eth0: PHY reset until link up
[4295656.561000] r8169: eth0: PHY reset until link up
[4295666.561000] r8169: eth0: PHY reset until link up
[4295676.561000] r8169: eth0: PHY reset until link up
[4295686.561000] r8169: eth0: PHY reset until link up
[4295696.561000] r8169: eth0: PHY reset until link up
[4295706.561000] r8169: eth0: PHY reset until link up
[4295716.561000] r8169: eth0: PHY reset until link up
[4295726.561000] r8169: eth0: PHY reset until link up
[4295728.286000] usb 4-2: new high speed USB device using ehci_hcd and address 4
[4295728.644000] Initializing USB Mass Storage driver...
[4295728.649000] scsi0 : SCSI emulation for USB Mass Storage devices
[4295728.650000] usb-storage: device found at 4
[4295728.650000] usb-storage: waiting for device to settle before scanning
[4295728.650000] usbcore: registered new driver usb-storage
[4295728.650000] USB Mass Storage support registered.
[4295733.651000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 2033
[4295733.651000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4295733.657000] usb-storage: device scan complete
[4295733.715000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[4295733.716000] sda: Write Protect is off
[4295733.716000] sda: Mode Sense: 02 00 00 00
[4295733.716000] sda: assuming drive cache: write through
[4295733.720000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[4295733.722000] sda: Write Protect is off
[4295733.722000] sda: Mode Sense: 02 00 00 00
[4295733.722000] sda: assuming drive cache: write through
[4295733.722000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4295733.724000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4295734.195000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295736.561000] r8169: eth0: PHY reset until link up
[4295746.561000] r8169: eth0: PHY reset until link up
[4295751.974000] usb 3-1: new low speed USB device using ohci_hcd and address 3
[4295752.125000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:03.2-1
[4295756.561000] r8169: eth0: PHY reset until link up
[4295766.561000] r8169: eth0: PHY reset until link up
[4295776.561000] r8169: eth0: PHY reset until link up
[4295786.561000] r8169: eth0: PHY reset until link up
[4295796.561000] r8169: eth0: PHY reset until link up
```

Now I've only been using Ubuntu for about a month now and this is the first time I've ever had to use **dmesg** so that huge list looks like a lot of gibberish to me.  What is it saying?  I see plenty of entries for **ath_pci** and plenty of **unknown symbol**s.  What is going on here?  Why did I not have this problem last night while configuring my wireless card, yet today I now have it?  How can I progress in setting up my wireless card again if I can't even get the madwifi driver module to load?  Any suggestions would be greatly appreciated.

---

### Post by Lambert on 2006-01-02
A couple questions.

I take it you downloaded and compiled the driver. true? which version did you download?

copy this command in terminal and post output?

```
sudo dpkg -s linx-restricted-modules-`uname -r`
```

---

### Post by versteckt on 2006-01-02
Yes, I downloaded and compiled the driver, version madwifi-ng-current from [http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)

As for the output of the command, I have:

```
versteckt@odin:~$ sudo dpkg -s linx-restricted-modules-`uname -r`
Paket &#187;linx-restricted-modules-2.6.12-10-386&#171; ist nicht installiert und keine Info ist vorhanden.

Benutze dpkg --info (= dpkg-deb --info) zum Untersuchen von Archiven,
und     dpkg --contents (= dpkg-deb --contents) zum Auflisten ihres Inhalts.
versteckt@odin:~$
```

Quick translation:

Packet &#187;linux-restricted-modules-2.6.12-10-386&#171; isn't installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to explore archives and dpkg --contents (= dpkg-deb --contents) to list the contents.

I suppose I will need to install this?

---

### Post by Lambert on 2006-01-02
Sounded like there was a conflict between two installed drivers but not the case.

There's something wrong with the install and I can't help resolve it.

1. try the madwifi irc channel or their website for other support options.

2. uninstall and reinstall. I would suggest just installing the linux restricted modules package as that has a precompile madwifi driver in it.

to uninstall you should just go to the directory you built the driver in and type this

```
sudo make uninstall
```

If you have another way to connect while booted into ubuntu

```
sudo apt-get install linux-restricted-modules-`uname -r`
```

3. If you want to install madwifi-ng see this howto

[http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi)


I know there is a problem with madwifi-ng after Dec 28th where there was an incompatability with hal and madwifi. You may want to try a snap shot from the 28th or older. I didn't think this affected breezy but it is possible.

---

### Post by versteckt on 2006-01-02
Thanks for the help.  I'll try what you just outlined above tonight.  I just thought it was odd since I had it working (seemingly) flawlessly last night, but had no luck today.

---

### Post by goombah88 on 2006-01-03
[QUOTE=Lambert]Sounded like there was a conflict between two installed drivers but not the case.

There's something wrong with the install and I can't help resolve it.

1. try the madwifi irc channel or their website for other support options.

2. uninstall and reinstall. I would suggest just installing the linux restricted modules package as that has a precompile madwifi driver in it.

to uninstall you should just go to the directory you built the driver in and type this

```
sudo make uninstall
```

If you have another way to connect while booted into ubuntu

```
sudo apt-get install linux-restricted-modules-`uname -r`
```

3. If you want to install madwifi-ng see this howto

[http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi)


I know there is a problem with madwifi-ng after Dec 28th where there was an incompatability with hal and madwifi. You may want to try a snap shot from the 28th or older. I didn't think this affected breezy but it is possible.[/QUOTE]


versteckt - i went through the same thing with my WG511t.  

1.  remove the linux-restricted-modules package...as it will only get in the way.  
2.  install the latest madwifi snapshot (not the madwifi-ng)
     use this post.  go to the 3rd entry (the one by iceman) and following the instructions down to the 'sudo mv' stuff.
     [http://www.ubuntuforums.org/showthread.php?t=38972&highlight=madwifi-ng](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=madwifi-ng)
3.  reboot.  everything should work fine after a reboot.

NOTE - if you're using the -386 kernel then the WG511t will work fine out of the box.  for the -686-smp kernel use the above steps and it should be working in no time.

hope this helps.

---

### Post by versteckt on 2006-01-03
Several problems with this:

1. I don't have the the linux-restricted modules installed.

2.  I am using a 386 kernel and my card does NOT work out of the box.

3.  I followed the tutorial from the post you linked to (before I even bothered with the madwifi.org tutorial), and had no success.  I honestly don't even remember how I got the card working correctly the first time.  I pieced together parts of several tutorials and somehow it just worked, but like I said, after the reboot, nothing.

I still haven't had a chance to try what Lambert had suggested, so I'll still do that and if it doesn't work, will try what you just outlined above even though I'm not sure how that will work.  But it's still worth a try.

---

