---
title: "Hello! I have some troubles with WOL and suspend mode."
date: 2013-01-21
forum: Networking &amp; Wireless
---

### Post by Tae hyun on 2013-01-21
Hello, I have a problem with WOL(Wake-On-Lan) and suspend mode.

In my labatory, we use ASROCK main board B75M .
We tested on ubuntu 12.10.

However, WOL and suspend mode does not work.

For, example

When we use 'pm-suspend' , to target pc, it works well without WOL

But, when we use 'pm-suspend' after WOL, it does not work properly.
The target pc does not go into suspend mode. it rewakes.

We don't know how to solve it.

We did everything we can do.(driver update, change lancard, change graphic card, change OS , Bios update and so on..)

This problem makes us frustrated....

Thank you for reading my poor english.
Hope anyone can help me on this . :)
Thanks!!
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

[COLOR=#888888][/COLOR]

---

### Post by Tae hyun on 2013-01-22
Hello, I have a problem with WOL(Wake-On-Lan) and suspend mode.

In my labatory, we use ASROCK main board B75M .
We tested on ubuntu 12.10.

However, WOL and suspend mode does not work.

For, example

When we use 'pm-suspend' , to target pc, it works well without WOL

But, when we use 'pm-suspend' after WOL, it does not work properly.
The target pc does not go into suspend mode. it rewakes.

We don't know how to solve it.

We did everything we can do.(driver update, change lancard, change graphic card, change OS , Bios update and so on..)

This problem makes us frustrated....

Thank you for reading my poor english.
Hope anyone can help me on this . :smile:
Thanks!!

---

### Post by overdrank on 2013-01-22
Hi and welcome, please do not create multiple threads with the same issue. You may bump your thread once a day ( 24 hr) Is polite. Thanks. Threads merged

---

### Post by tgalati4 on 2013-01-22
Install acpitool

```
sudo apt-get install acpitool
```

[http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool](http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool)

---

### Post by Tae hyun on 2013-01-25
thanks for reply my problems @tgalati4 :p
 
I saw the page which you linked to me but still I can't make it..
 
As the linked page shows,
I setted up /etc/network/interfaces in my ubuntu pc like below.
[SIZE=4][ATTACH]230602[/ATTACH][/SIZE]
 
Then, I installed 'acpitool'
after, installed acpitool, I did 'acpitool -w' 
[SIZE=4][ATTACH]230603[/ATTACH][/SIZE]
 
but, I don't know which device I should wake up..
so, I disabled no.24, 25, 26
 
After that I did 'pm-suspend' to my ubuntu pc.
And then by using fedora pc, I woke up (by wol) the ubuntu pc.
However, ubuntu pc didn't go to suspend mode after wol...it rewakes again..
 
This is same symptom as before.
 
I stiil need help..:(

---

### Post by tgalati4 on 2013-01-25
You have to ENABLE devices to keep power to them after the machine is put to sleep!

Your network card is connected to a PCI or USB port on your machine.  When your machine goes to sleep, many parts of the machine will go to sleep and power will be cut off.  If the PCI bus port or USB port gets shut down (DISABLE) during sleep, then the Wake Up will not happen because the network card can't communicate with the rest of the machine.

So discover which port your network card is on and ENABLE it.  Then try again.  If your machine is having trouble going to sleep then turn ports back on until it sleeps properly.  Take notes of the original settings so you can go back to them.

Also, I think you only need one ethtool stanza and I believe it should be "pre-up".  Most ethernet ports remain in WoL mode as long as they have power.  So remove the "post-down" line and change "post-up" line to "pre-up".

Post the output of:

```
lspci
lsusb
```

---

### Post by jjanna18 on 2013-05-23
I have exactly same issue.
The system doesn't suspend only when wol used.

Here are some logs of kern.log

System fresh booted and suspended waked by keyboard.

```

May 18 18:47:25 Server kernel: [   61.229048] WARNING! power/level is deprecated; use power/control instead
May 18 18:49:29 Server kernel: [   61.973752] PM: Syncing filesystems ... done.
May 18 18:49:29 Server kernel: [   61.975276] PM: Preparing system for standby sleep
May 18 18:49:29 Server kernel: [   61.975788] Freezing user space processes ... (elapsed 0.01 seconds) done.
May 18 18:49:29 Server kernel: [   61.992088] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
May 18 18:49:29 Server kernel: [   62.008084] PM: Entering standby sleep
May 18 18:49:29 Server kernel: [   62.008119] Suspending console(s) (use no_console_suspend to debug)
May 18 18:49:29 Server kernel: [   62.008575] sd 1:0:1:0: [sdc] Synchronizing SCSI cache
May 18 18:49:29 Server kernel: [   62.008651] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May 18 18:49:29 Server kernel: [   62.008827] sd 1:0:1:0: [sdc] Stopping disk
May 18 18:49:29 Server kernel: [   62.008934] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 18 18:49:29 Server kernel: [   62.009102] sd 0:0:0:0: [sda] Stopping disk
May 18 18:49:29 Server kernel: [   62.012629] parport_pc 00:07: disabled
May 18 18:49:29 Server kernel: [   62.012846] serial 00:06: disabled
May 18 18:49:29 Server kernel: [   62.012862] serial 00:06: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.110145] sd 1:0:0:0: [sdb] Stopping disk
May 18 18:49:29 Server kernel: [   62.110316] PM: suspend of drv:sd dev:1:0:1:0 complete after 101.769 msecs
May 18 18:49:29 Server kernel: [   62.110360] PM: suspend of drv:scsi dev:target1:0:1 complete after 101.747 msecs
May 18 18:49:29 Server kernel: [   62.182891] pcieport 0000:00:1c.0: wake-up capability enabled by ACPI
May 18 18:49:29 Server kernel: [   62.196040] PM: suspend of drv:e1000e dev:0000:01:00.0 complete after 183.093 msecs
May 18 18:49:29 Server kernel: [   62.196075] PM: suspend of drv:pcieport dev:0000:00:1c.0 complete after 182.618 msecs
May 18 18:49:29 Server kernel: [   62.228893] PM: suspend of drv:sd dev:1:0:0:0 complete after 220.260 msecs
May 18 18:49:29 Server kernel: [   62.228925] PM: suspend of drv:scsi dev:target1:0:0 complete after 220.180 msecs
May 18 18:49:29 Server kernel: [   62.228984] PM: suspend of drv:scsi dev:host1 complete after 217.189 msecs
May 18 18:49:29 Server kernel: [   62.229096] PM: suspend of drv: dev:ata2 complete after 217.246 msecs
May 18 18:49:29 Server kernel: [   62.418799] PM: suspend of drv:sd dev:0:0:0:0 complete after 409.873 msecs
May 18 18:49:29 Server kernel: [   62.418829] PM: suspend of drv:scsi dev:target0:0:0 complete after 409.815 msecs
May 18 18:49:29 Server kernel: [   62.418855] PM: suspend of drv:scsi dev:host0 complete after 407.043 msecs
May 18 18:49:29 Server kernel: [   62.418947] PM: suspend of drv: dev:ata1 complete after 407.024 msecs
May 18 18:49:29 Server kernel: [   62.432041] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 418.925 msecs
May 18 18:49:29 Server kernel: [   62.432076] PM: suspend of drv: dev:pci0000:00 complete after 418.468 msecs
May 18 18:49:29 Server kernel: [   62.432099] PM: suspend of devices complete after 423.709 msecs
May 18 18:49:29 Server kernel: [   62.432104] PM: suspend devices took 0.424 seconds
May 18 18:49:29 Server kernel: [   62.432385] PM: late suspend of devices complete after 0.275 msecs
May 18 18:49:29 Server kernel: [   62.432895] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
May 18 18:49:29 Server kernel: [   62.448085] uhci_hcd 0000:00:1d.3: wake-up capability enabled by ACPI
May 18 18:49:29 Server kernel: [   62.448122] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
May 18 18:49:29 Server kernel: [   62.448159] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
May 18 18:49:29 Server kernel: [   62.448195] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
May 18 18:49:29 Server kernel: [   62.448323] PM: noirq suspend of devices complete after 15.932 msecs
May 18 18:49:29 Server kernel: [   62.448374] ACPI: Preparing to enter system sleep state S1
May 18 18:49:29 Server kernel: [   62.449042] PM: Saving platform NVS memory
May 18 18:49:29 Server kernel: [   62.449111] Disabling non-boot CPUs ...
May 18 18:49:29 Server kernel: [   62.552033] CPU 1 is now offline
May 18 18:49:29 Server kernel: [   62.554716] CPU 2 is now offline
May 18 18:49:29 Server kernel: [   62.557344] CPU 3 is now offline
May 18 18:49:29 Server kernel: [   62.560011] PM: Restoring platform NVS memory
May 18 18:49:29 Server kernel: [   62.560011] Force enabled HPET at resume
May 18 18:49:29 Server kernel: [   62.560011] Enabling non-boot CPUs ...
May 18 18:49:29 Server kernel: [   62.560011] Booting Node 0 Processor 1 APIC 0x2
May 18 18:49:29 Server kernel: [   62.453801] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:49:29 Server kernel: [   62.572269] CPU1 is up
May 18 18:49:29 Server kernel: [   62.572541] Booting Node 0 Processor 2 APIC 0x3
May 18 18:49:29 Server kernel: [   62.557166] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:49:29 Server kernel: [   62.588135] CPU2 is up
May 18 18:49:29 Server kernel: [   62.588427] Booting Node 0 Processor 3 APIC 0x1
May 18 18:49:29 Server kernel: [   62.560142] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:49:29 Server kernel: [   62.604218] CPU3 is up
May 18 18:49:29 Server kernel: [   62.606364] ACPI: Waking up from system sleep state S1
May 18 18:49:29 Server kernel: [   62.620182] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.620220] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.620258] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.620295] uhci_hcd 0000:00:1d.3: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.636085] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.668498] PM: noirq resume of devices complete after 61.589 msecs
May 18 18:49:29 Server kernel: [   62.668684] PM: early resume of devices complete after 0.136 msecs
May 18 18:49:29 Server kernel: [   62.668818] i915 0000:00:02.0: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.668873] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.668909] usb usb2: root hub lost power or was reset
May 18 18:49:29 Server kernel: [   62.668946] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.668980] usb usb3: root hub lost power or was reset
May 18 18:49:29 Server kernel: [   62.669013] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.669045] usb usb4: root hub lost power or was reset
May 18 18:49:29 Server kernel: [   62.669076] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.669107] usb usb5: root hub lost power or was reset
May 18 18:49:29 Server kernel: [   62.669147] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.669209] pci 0000:00:1e.0: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.669249] ata_piix 0000:00:1f.2: setting latency timer to 64
May 18 18:49:29 Server kernel: [   62.669395] pcieport 0000:00:1c.0: wake-up capability disabled by ACPI
May 18 18:49:29 Server kernel: [   62.669414] e1000e 0000:01:00.0: Disabling ASPM  L1
May 18 18:49:29 Server kernel: [   62.669627] e1000e 0000:01:00.0: irq 41 for MSI/MSI-X
May 18 18:49:29 Server kernel: [   62.672144] serial 00:06: activated
May 18 18:49:29 Server kernel: [   62.675018] parport_pc 00:07: activated
May 18 18:49:29 Server kernel: [   62.788094] PM: resume of drv:hub dev:4-0:1.0 complete after 117.910 msecs
May 18 18:49:29 Server kernel: [   62.788099] PM: resume of drv: dev:ep_00 complete after 117.454 msecs
May 18 18:49:29 Server kernel: [   62.788114] PM: resume of drv:hub dev:5-0:1.0 complete after 117.628 msecs
May 18 18:49:29 Server kernel: [   62.788135] PM: resume of drv: dev:ep_00 complete after 117.808 msecs
May 18 18:49:29 Server kernel: [   62.788148] PM: resume of drv:hub dev:3-0:1.0 complete after 118.282 msecs
May 18 18:49:29 Server kernel: [   62.788152] PM: resume of drv: dev:ep_81 complete after 117.900 msecs
May 18 18:49:29 Server kernel: [   62.788166] PM: resume of drv: dev:ep_00 complete after 118.148 msecs
May 18 18:49:29 Server kernel: [   62.788170] PM: resume of drv: dev:ep_81 complete after 117.607 msecs
May 18 18:49:29 Server kernel: [   62.788179] PM: resume of drv: dev:ep_81 complete after 118.238 msecs
May 18 18:49:29 Server kernel: [   62.788217] PM: resume of drv:hub dev:2-0:1.0 complete after 118.537 msecs
May 18 18:49:29 Server kernel: [   62.788222] PM: resume of drv: dev:ep_00 complete after 118.493 msecs
May 18 18:49:29 Server kernel: [   62.788236] PM: resume of drv: dev:ep_81 complete after 118.542 msecs
May 18 18:49:29 Server kernel: [   62.832174] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   62.832181] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   62.832186] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   62.836352] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   62.836358] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   62.836363] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   62.840290] ata1.00: configured for UDMA/133
May 18 18:49:29 Server kernel: [   62.840353] PM: resume of drv:scsi dev:host0 complete after 170.985 msecs
May 18 18:49:29 Server kernel: [   62.840387] PM: resume of drv:ata_port dev:ata1 complete after 164.627 msecs
May 18 18:49:29 Server kernel: [   62.840394] PM: resume of drv:scsi dev:target0:0:0 complete after 169.683 msecs
May 18 18:49:29 Server kernel: [   62.840420] PM: resume of drv:scsi_host dev:host0 complete after 170.960 msecs
May 18 18:49:29 Server kernel: [   62.840425] PM: resume of drv:sd dev:0:0:0:0 complete after 169.642 msecs
May 18 18:49:29 Server kernel: [   62.840439] sd 0:0:0:0: [sda] Starting disk
May 18 18:49:29 Server kernel: [   65.129036] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
May 18 18:49:29 Server kernel: [   65.477347] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2806.486 msecs
May 18 18:49:29 Server kernel: [   66.464345] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   66.464351] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   66.464356] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:49:29 Server kernel: [   66.481293] ata2.00: configured for UDMA/33
May 18 18:49:29 Server kernel: [   66.523235] ata2.01: configured for UDMA/33
May 18 18:49:29 Server kernel: [   66.523302] PM: resume of drv:scsi dev:host1 complete after 3853.768 msecs
May 18 18:49:29 Server kernel: [   66.523330] PM: resume of drv:ata_port dev:ata2 complete after 3682.903 msecs
May 18 18:49:29 Server kernel: [   66.523337] PM: resume of drv:scsi_host dev:host1 complete after 3853.789 msecs
May 18 18:49:29 Server kernel: [   66.523342] PM: resume of drv:scsi dev:target1:0:0 complete after 3852.403 msecs
May 18 18:49:29 Server kernel: [   66.523380] PM: resume of drv:sd dev:1:0:0:0 complete after 3852.370 msecs
May 18 18:49:29 Server kernel: [   66.523385] PM: resume of drv:scsi dev:target1:0:1 complete after 3852.222 msecs
May 18 18:49:29 Server kernel: [   66.523391] sd 1:0:0:0: [sdb] Starting disk
May 18 18:49:29 Server kernel: [   66.523408] PM: resume of drv:sd dev:1:0:1:0 complete after 3852.167 msecs
May 18 18:49:29 Server kernel: [   66.523416] sd 1:0:1:0: [sdc] Starting disk
May 18 18:49:29 Server kernel: [   70.199960] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 7528.869 msecs
May 18 18:49:29 Server kernel: [   70.199970] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 3676.360 msecs
May 18 18:49:29 Server kernel: [   70.254134] PM: resume of drv:scsi_device dev:1:0:1:0 complete after 7582.812 msecs
May 18 18:49:29 Server kernel: [   70.254253] PM: resume of devices complete after 7585.558 msecs
May 18 18:49:29 Server kernel: [   70.254534] PM: resume devices took 7.584 seconds
May 18 18:49:29 Server kernel: [   70.254815] PM: Finishing wakeup.
May 18 18:49:29 Server kernel: [   70.254821] Restarting tasks ... done.

```


Another log of kern.log

After waked by keyboard, system suspended again and waked by wol.

```

May 18 18:52:37 Server kernel: [  223.044514] PM: Syncing filesystems ... done.
May 18 18:52:37 Server kernel: [  223.046077] PM: Preparing system for standby sleep
May 18 18:52:37 Server kernel: [  223.046225] Freezing user space processes ... (elapsed 0.01 seconds) done.
May 18 18:52:37 Server kernel: [  223.060109] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
May 18 18:52:37 Server kernel: [  223.076107] PM: Entering standby sleep
May 18 18:52:37 Server kernel: [  223.076143] Suspending console(s) (use no_console_suspend to debug)
May 18 18:52:37 Server kernel: [  223.076600] sd 1:0:1:0: [sdc] Synchronizing SCSI cache
May 18 18:52:37 Server kernel: [  223.076685] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May 18 18:52:37 Server kernel: [  223.076758] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 18 18:52:37 Server kernel: [  223.076830] sd 1:0:1:0: [sdc] Stopping disk
May 18 18:52:37 Server kernel: [  223.076937] sd 0:0:0:0: [sda] Stopping disk
May 18 18:52:37 Server kernel: [  223.080599] parport_pc 00:07: disabled
May 18 18:52:37 Server kernel: [  223.080817] serial 00:06: disabled
May 18 18:52:37 Server kernel: [  223.080832] serial 00:06: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.126297] sd 1:0:0:0: [sdb] Stopping disk
May 18 18:52:37 Server kernel: [  223.236714] PM: suspend of drv:sd dev:1:0:0:0 complete after 160.040 msecs
May 18 18:52:37 Server kernel: [  223.236741] PM: suspend of drv:scsi dev:target1:0:0 complete after 160.042 msecs
May 18 18:52:37 Server kernel: [  223.236781] PM: suspend of drv:scsi dev:host1 complete after 157.097 msecs
May 18 18:52:37 Server kernel: [  223.236889] PM: suspend of drv: dev:ata2 complete after 157.205 msecs
May 18 18:52:37 Server kernel: [  223.250889] pcieport 0000:00:1c.0: wake-up capability enabled by ACPI
May 18 18:52:37 Server kernel: [  223.264040] PM: suspend of drv:e1000e dev:0000:01:00.0 complete after 183.122 msecs
May 18 18:52:37 Server kernel: [  223.264076] PM: suspend of drv:pcieport dev:0000:00:1c.0 complete after 183.043 msecs
May 18 18:52:37 Server kernel: [  223.486509] PM: suspend of drv:sd dev:0:0:0:0 complete after 409.768 msecs
May 18 18:52:37 Server kernel: [  223.486540] PM: suspend of drv:scsi dev:target0:0:0 complete after 409.791 msecs
May 18 18:52:37 Server kernel: [  223.486565] PM: suspend of drv:scsi dev:host0 complete after 406.885 msecs
May 18 18:52:37 Server kernel: [  223.486658] PM: suspend of drv: dev:ata1 complete after 406.889 msecs
May 18 18:52:37 Server kernel: [  223.500040] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 419.086 msecs
May 18 18:52:37 Server kernel: [  223.500066] PM: suspend of drv: dev:pci0000:00 complete after 419.009 msecs
May 18 18:52:37 Server kernel: [  223.500076] PM: suspend of devices complete after 423.662 msecs
May 18 18:52:37 Server kernel: [  223.500081] PM: suspend devices took 0.424 seconds
May 18 18:52:37 Server kernel: [  223.500362] PM: late suspend of devices complete after 0.275 msecs
May 18 18:52:37 Server kernel: [  223.500871] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
May 18 18:52:37 Server kernel: [  223.516086] uhci_hcd 0000:00:1d.3: wake-up capability enabled by ACPI
May 18 18:52:37 Server kernel: [  223.516123] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
May 18 18:52:37 Server kernel: [  223.516160] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
May 18 18:52:37 Server kernel: [  223.516196] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
May 18 18:52:37 Server kernel: [  223.516359] PM: noirq suspend of devices complete after 15.990 msecs
May 18 18:52:37 Server kernel: [  223.516406] ACPI: Preparing to enter system sleep state S1
May 18 18:52:37 Server kernel: [  223.516988] PM: Saving platform NVS memory
May 18 18:52:37 Server kernel: [  223.517059] Disabling non-boot CPUs ...
May 18 18:52:37 Server kernel: [  223.620033] CPU 1 is now offline
May 18 18:52:37 Server kernel: [  223.724036] CPU 2 is now offline
May 18 18:52:37 Server kernel: [  223.828026] CPU 3 is now offline
May 18 18:52:37 Server kernel: [  223.832007] PM: Restoring platform NVS memory
May 18 18:52:37 Server kernel: [  223.832007] Force enabled HPET at resume
May 18 18:52:37 Server kernel: [  223.832007] Enabling non-boot CPUs ...
May 18 18:52:37 Server kernel: [  223.832007] Booting Node 0 Processor 1 APIC 0x2
May 18 18:52:37 Server kernel: [  223.521748] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:52:37 Server kernel: [  223.844192] CPU1 is up
May 18 18:52:37 Server kernel: [  223.844445] Booting Node 0 Processor 2 APIC 0x3
May 18 18:52:37 Server kernel: [  223.625447] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:52:37 Server kernel: [  223.860134] CPU2 is up
May 18 18:52:37 Server kernel: [  223.860433] Booting Node 0 Processor 3 APIC 0x1
May 18 18:52:37 Server kernel: [  223.729062] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:52:37 Server kernel: [  223.876168] CPU3 is up
May 18 18:52:37 Server kernel: [  223.878354] ACPI: Waking up from system sleep state S1
May 18 18:52:37 Server kernel: [  223.892175] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.892213] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.892250] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.892287] uhci_hcd 0000:00:1d.3: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.908082] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.940494] PM: noirq resume of devices complete after 61.617 msecs
May 18 18:52:37 Server kernel: [  223.940680] PM: early resume of devices complete after 0.136 msecs
May 18 18:52:37 Server kernel: [  223.940799] i915 0000:00:02.0: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.940853] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.940884] usb usb2: root hub lost power or was reset
May 18 18:52:37 Server kernel: [  223.940912] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.940939] usb usb3: root hub lost power or was reset
May 18 18:52:37 Server kernel: [  223.940965] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.940991] usb usb4: root hub lost power or was reset
May 18 18:52:37 Server kernel: [  223.941017] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.941042] usb usb5: root hub lost power or was reset
May 18 18:52:37 Server kernel: [  223.941070] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.941114] pci 0000:00:1e.0: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.941145] ata_piix 0000:00:1f.2: setting latency timer to 64
May 18 18:52:37 Server kernel: [  223.941183] pcieport 0000:00:1c.0: wake-up capability disabled by ACPI
May 18 18:52:37 Server kernel: [  223.941196] e1000e 0000:01:00.0: Disabling ASPM  L1
May 18 18:52:37 Server kernel: [  223.941371] e1000e 0000:01:00.0: irq 41 for MSI/MSI-X
May 18 18:52:37 Server kernel: [  223.948720] serial 00:06: activated
May 18 18:52:37 Server kernel: [  223.949708] parport_pc 00:07: activated
May 18 18:52:37 Server kernel: [  224.064085] PM: resume of drv:hub dev:2-0:1.0 complete after 118.229 msecs
May 18 18:52:37 Server kernel: [  224.064092] PM: resume of drv: dev:ep_00 complete after 118.118 msecs
May 18 18:52:37 Server kernel: [  224.064101] PM: resume of drv:hub dev:5-0:1.0 complete after 117.708 msecs
May 18 18:52:37 Server kernel: [  224.064106] PM: resume of drv:hub dev:4-0:1.0 complete after 117.799 msecs
May 18 18:52:37 Server kernel: [  224.064113] PM: resume of drv: dev:ep_81 complete after 118.228 msecs
May 18 18:52:37 Server kernel: [  224.064129] PM: resume of drv: dev:ep_00 complete after 117.775 msecs
May 18 18:52:37 Server kernel: [  224.064145] PM: resume of drv: dev:ep_81 complete after 117.823 msecs
May 18 18:52:37 Server kernel: [  224.064162] PM: resume of drv: dev:ep_81 complete after 117.745 msecs
May 18 18:52:37 Server kernel: [  224.064207] PM: resume of drv:hub dev:3-0:1.0 complete after 117.989 msecs
May 18 18:52:37 Server kernel: [  224.064211] PM: resume of drv: dev:ep_00 complete after 117.778 msecs
May 18 18:52:37 Server kernel: [  224.064232] PM: resume of drv: dev:ep_00 complete after 117.990 msecs
May 18 18:52:37 Server kernel: [  224.064241] PM: resume of drv: dev:ep_81 complete after 118.010 msecs
May 18 18:52:37 Server kernel: [  224.070309] e1000e 0000:01:00.0: eth0: MAC Wakeup cause - Magic Packet
May 18 18:52:37 Server kernel: [  224.108179] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  224.108185] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  224.108190] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  224.112343] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  224.112348] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  224.112354] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  224.116296] ata1.00: configured for UDMA/133
May 18 18:52:37 Server kernel: [  224.116367] PM: resume of drv:scsi dev:host0 complete after 170.768 msecs
May 18 18:52:37 Server kernel: [  224.116371] PM: resume of drv:ata_port dev:ata1 complete after 166.074 msecs
May 18 18:52:37 Server kernel: [  224.116395] PM: resume of drv:scsi_host dev:host0 complete after 170.783 msecs
May 18 18:52:37 Server kernel: [  224.116411] PM: resume of drv:scsi dev:target0:0:0 complete after 169.950 msecs
May 18 18:52:37 Server kernel: [  224.116444] PM: resume of drv:sd dev:0:0:0:0 complete after 169.971 msecs
May 18 18:52:37 Server kernel: [  224.116456] sd 0:0:0:0: [sda] Starting disk
May 18 18:52:37 Server kernel: [  226.389031] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
May 18 18:52:37 Server kernel: [  226.755108] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2808.600 msecs
May 18 18:52:37 Server kernel: [  227.812350] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  227.812357] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  227.812362] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:52:37 Server kernel: [  227.829316] ata2.00: configured for UDMA/33
May 18 18:52:37 Server kernel: [  227.873829] ata2.01: configured for UDMA/33
May 18 18:52:37 Server kernel: [  227.873894] PM: resume of drv:scsi dev:host1 complete after 3928.264 msecs
May 18 18:52:37 Server kernel: [  227.873899] PM: resume of drv:ata_port dev:ata2 complete after 3757.493 msecs
May 18 18:52:37 Server kernel: [  227.873925] PM: resume of drv:scsi dev:target1:0:1 complete after 3927.279 msecs
May 18 18:52:37 Server kernel: [  227.873937] PM: resume of drv:scsi dev:target1:0:0 complete after 3927.418 msecs
May 18 18:52:37 Server kernel: [  227.873950] PM: resume of drv:scsi_host dev:host1 complete after 3928.284 msecs
May 18 18:52:37 Server kernel: [  227.873970] PM: resume of drv:sd dev:1:0:1:0 complete after 3927.303 msecs
May 18 18:52:37 Server kernel: [  227.873978] PM: resume of drv:sd dev:1:0:0:0 complete after 3927.414 msecs
May 18 18:52:37 Server kernel: [  227.873984] sd 1:0:1:0: [sdc] Starting disk
May 18 18:52:37 Server kernel: [  227.873993] sd 1:0:0:0: [sdb] Starting disk
May 18 18:52:37 Server kernel: [  227.955027] PM: resume of drv:scsi_device dev:1:0:1:0 complete after 4008.328 msecs
May 18 18:52:37 Server kernel: [  231.580402] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 7633.798 msecs
May 18 18:52:37 Server kernel: [  231.580421] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 3706.298 msecs
May 18 18:52:37 Server kernel: [  231.580568] PM: resume of devices complete after 7639.879 msecs
May 18 18:52:37 Server kernel: [  231.580851] PM: resume devices took 7.640 seconds
May 18 18:52:37 Server kernel: [  231.581137] PM: Finishing wakeup.
May 18 18:52:37 Server kernel: [  231.581143] Restarting tasks ... done.

```


Finally tried to suspend system but wake right back.

```

May 18 18:54:18 Server kernel: [  325.413945] PM: Syncing filesystems ... done.
May 18 18:54:18 Server kernel: [  325.415516] PM: Preparing system for standby sleep
May 18 18:54:18 Server kernel: [  325.415675] Freezing user space processes ... (elapsed 0.01 seconds) done.
May 18 18:54:18 Server kernel: [  325.432101] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
May 18 18:54:18 Server kernel: [  325.448099] PM: Entering standby sleep
May 18 18:54:18 Server kernel: [  325.448134] Suspending console(s) (use no_console_suspend to debug)
May 18 18:54:18 Server kernel: [  325.448591] sd 1:0:1:0: [sdc] Synchronizing SCSI cache
May 18 18:54:18 Server kernel: [  325.448682] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May 18 18:54:18 Server kernel: [  325.448715] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 18 18:54:18 Server kernel: [  325.448895] sd 0:0:0:0: [sda] Stopping disk
May 18 18:54:18 Server kernel: [  325.452857] parport_pc 00:07: disabled
May 18 18:54:18 Server kernel: [  325.453076] serial 00:06: disabled
May 18 18:54:18 Server kernel: [  325.453091] serial 00:06: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  325.472370] sd 1:0:1:0: [sdc] Stopping disk
May 18 18:54:18 Server kernel: [  325.490513] sd 1:0:0:0: [sdb] Stopping disk
May 18 18:54:18 Server kernel: [  325.622892] pcieport 0000:00:1c.0: wake-up capability enabled by ACPI
May 18 18:54:18 Server kernel: [  325.636044] PM: suspend of drv:e1000e dev:0000:01:00.0 complete after 182.871 msecs
May 18 18:54:18 Server kernel: [  325.636089] PM: suspend of drv:pcieport dev:0000:00:1c.0 complete after 182.765 msecs
May 18 18:54:18 Server kernel: [  325.659024] PM: suspend of drv:sd dev:1:0:0:0 complete after 210.369 msecs
May 18 18:54:18 Server kernel: [  325.659048] PM: suspend of drv:scsi dev:target1:0:0 complete after 210.391 msecs
May 18 18:54:18 Server kernel: [  325.659073] PM: suspend of drv:scsi dev:host1 complete after 207.110 msecs
May 18 18:54:18 Server kernel: [  325.659156] PM: suspend of drv: dev:ata2 complete after 207.164 msecs
May 18 18:54:18 Server kernel: [  325.859022] PM: suspend of drv:sd dev:0:0:0:0 complete after 410.323 msecs
May 18 18:54:18 Server kernel: [  325.859048] PM: suspend of drv:scsi dev:target0:0:0 complete after 410.307 msecs
May 18 18:54:18 Server kernel: [  325.859070] PM: suspend of drv:scsi dev:host0 complete after 407.087 msecs
May 18 18:54:18 Server kernel: [  325.859174] PM: suspend of drv: dev:ata1 complete after 407.115 msecs
May 18 18:54:18 Server kernel: [  325.872040] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 418.833 msecs
May 18 18:54:18 Server kernel: [  325.872105] PM: suspend of drv: dev:pci0000:00 complete after 418.762 msecs
May 18 18:54:18 Server kernel: [  325.872137] PM: suspend of devices complete after 423.732 msecs
May 18 18:54:18 Server kernel: [  325.872141] PM: suspend devices took 0.424 seconds
May 18 18:54:18 Server kernel: [  325.872426] PM: late suspend of devices complete after 0.279 msecs
May 18 18:54:18 Server kernel: [  325.872937] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
May 18 18:54:18 Server kernel: [  325.888103] uhci_hcd 0000:00:1d.3: wake-up capability enabled by ACPI
May 18 18:54:18 Server kernel: [  325.888141] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
May 18 18:54:18 Server kernel: [  325.888178] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
May 18 18:54:18 Server kernel: [  325.888214] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
May 18 18:54:18 Server kernel: [  325.888377] PM: noirq suspend of devices complete after 15.944 msecs
May 18 18:54:18 Server kernel: [  325.888426] ACPI: Preparing to enter system sleep state S1
May 18 18:54:18 Server kernel: [  325.889007] PM: Saving platform NVS memory
May 18 18:54:18 Server kernel: [  325.889079] Disabling non-boot CPUs ...
May 18 18:54:18 Server kernel: [  325.992036] CPU 1 is now offline
May 18 18:54:18 Server kernel: [  326.096035] CPU 2 is now offline
May 18 18:54:18 Server kernel: [  326.200026] CPU 3 is now offline
May 18 18:54:18 Server kernel: [  326.204007] PM: Restoring platform NVS memory
May 18 18:54:18 Server kernel: [  326.204007] Force enabled HPET at resume
May 18 18:54:18 Server kernel: [  326.204007] Enabling non-boot CPUs ...
May 18 18:54:18 Server kernel: [  326.204007] Booting Node 0 Processor 1 APIC 0x2
May 18 18:54:18 Server kernel: [  325.893698] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:54:18 Server kernel: [  326.216252] CPU1 is up
May 18 18:54:18 Server kernel: [  326.216506] Booting Node 0 Processor 2 APIC 0x3
May 18 18:54:18 Server kernel: [  325.997103] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:54:18 Server kernel: [  326.232184] CPU2 is up
May 18 18:54:18 Server kernel: [  326.232444] Booting Node 0 Processor 3 APIC 0x1
May 18 18:54:18 Server kernel: [  326.101293] Atom PSE erratum detected, BIOS microcode update recommended
May 18 18:54:18 Server kernel: [  326.248192] CPU3 is up
May 18 18:54:18 Server kernel: [  326.250332] ACPI: Waking up from system sleep state S1
May 18 18:54:18 Server kernel: [  326.264170] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  326.264209] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  326.264246] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  326.264283] uhci_hcd 0000:00:1d.3: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  326.280090] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  326.312501] PM: noirq resume of devices complete after 61.563 msecs
May 18 18:54:18 Server kernel: [  326.312691] PM: early resume of devices complete after 0.140 msecs
May 18 18:54:18 Server kernel: [  326.312820] i915 0000:00:02.0: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313030] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313035] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313078] usb usb3: root hub lost power or was reset
May 18 18:54:18 Server kernel: [  326.313081] usb usb2: root hub lost power or was reset
May 18 18:54:18 Server kernel: [  326.313175] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313208] usb usb4: root hub lost power or was reset
May 18 18:54:18 Server kernel: [  326.313275] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313310] usb usb5: root hub lost power or was reset
May 18 18:54:18 Server kernel: [  326.313382] pci 0000:00:1e.0: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313396] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.313543] pcieport 0000:00:1c.0: wake-up capability disabled by ACPI
May 18 18:54:18 Server kernel: [  326.313559] e1000e 0000:01:00.0: Disabling ASPM  L1
May 18 18:54:18 Server kernel: [  326.313758] e1000e 0000:01:00.0: irq 41 for MSI/MSI-X
May 18 18:54:18 Server kernel: [  326.316207] ata_piix 0000:00:1f.2: setting latency timer to 64
May 18 18:54:18 Server kernel: [  326.317369] serial 00:06: activated
May 18 18:54:18 Server kernel: [  326.319567] parport_pc 00:07: activated
May 18 18:54:18 Server kernel: [  326.432083] PM: resume of drv: dev:ep_00 complete after 118.078 msecs
May 18 18:54:18 Server kernel: [  326.432091] PM: resume of drv:hub dev:5-0:1.0 complete after 118.122 msecs
May 18 18:54:18 Server kernel: [  326.432126] PM: resume of drv: dev:ep_00 complete after 118.305 msecs
May 18 18:54:18 Server kernel: [  326.432134] PM: resume of drv: dev:ep_00 complete after 118.621 msecs
May 18 18:54:18 Server kernel: [  326.432138] PM: resume of drv: dev:ep_81 complete after 118.172 msecs
May 18 18:54:18 Server kernel: [  326.432148] PM: resume of drv:hub dev:3-0:1.0 complete after 118.575 msecs
May 18 18:54:18 Server kernel: [  326.432155] PM: resume of drv:hub dev:2-0:1.0 complete after 118.694 msecs
May 18 18:54:18 Server kernel: [  326.432161] PM: resume of drv:hub dev:4-0:1.0 complete after 118.286 msecs
May 18 18:54:18 Server kernel: [  326.432174] PM: resume of drv: dev:ep_81 complete after 118.592 msecs
May 18 18:54:18 Server kernel: [  326.432182] PM: resume of drv: dev:ep_81 complete after 118.718 msecs
May 18 18:54:18 Server kernel: [  326.432187] PM: resume of drv: dev:ep_00 complete after 118.265 msecs
May 18 18:54:18 Server kernel: [  326.432193] PM: resume of drv: dev:ep_81 complete after 118.306 msecs
May 18 18:54:18 Server kernel: [  326.484431] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  326.484439] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  326.484446] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  326.484523] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  326.484530] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  326.484536] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  326.492290] ata1.00: configured for UDMA/133
May 18 18:54:18 Server kernel: [  326.492367] PM: resume of drv:ata_port dev:ata1 complete after 172.017 msecs
May 18 18:54:18 Server kernel: [  326.492376] PM: resume of drv:scsi dev:host0 complete after 179.120 msecs
May 18 18:54:18 Server kernel: [  326.492419] PM: resume of drv:scsi_host dev:host0 complete after 179.141 msecs
May 18 18:54:18 Server kernel: [  326.492424] PM: resume of drv:scsi dev:target0:0:0 complete after 178.410 msecs
May 18 18:54:18 Server kernel: [  326.492446] PM: resume of drv:sd dev:0:0:0:0 complete after 178.429 msecs
May 18 18:54:18 Server kernel: [  326.492459] sd 0:0:0:0: [sda] Starting disk
May 18 18:54:18 Server kernel: [  327.762307] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1448.251 msecs
May 18 18:54:18 Server kernel: [  328.328344] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  328.328350] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  328.328356] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 18 18:54:18 Server kernel: [  328.345324] ata2.00: configured for UDMA/33
May 18 18:54:18 Server kernel: [  328.394987] ata2.01: configured for UDMA/33
May 18 18:54:18 Server kernel: [  328.395048] PM: resume of drv:scsi dev:host1 complete after 2081.740 msecs
May 18 18:54:18 Server kernel: [  328.395063] PM: resume of drv:ata_port dev:ata2 complete after 1902.660 msecs
May 18 18:54:18 Server kernel: [  328.395096] PM: resume of drv:scsi dev:target1:0:1 complete after 2080.919 msecs
May 18 18:54:18 Server kernel: [  328.395101] PM: resume of drv:scsi_host dev:host1 complete after 2081.763 msecs
May 18 18:54:18 Server kernel: [  328.395120] PM: resume of drv:scsi dev:target1:0:0 complete after 2081.061 msecs
May 18 18:54:18 Server kernel: [  328.395129] PM: resume of drv:sd dev:1:0:1:0 complete after 2080.919 msecs
May 18 18:54:18 Server kernel: [  328.395140] sd 1:0:1:0: [sdc] Starting disk
May 18 18:54:18 Server kernel: [  328.395144] PM: resume of drv:sd dev:1:0:0:0 complete after 2081.013 msecs
May 18 18:54:18 Server kernel: [  328.395152] sd 1:0:0:0: [sdb] Starting disk
May 18 18:54:18 Server kernel: [  328.773064] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
May 18 18:54:18 Server kernel: [  331.891172] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 5577.021 msecs
May 18 18:54:18 Server kernel: [  331.891178] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 3495.764 msecs
May 18 18:54:18 Server kernel: [  331.942820] PM: resume of drv:scsi_device dev:1:0:1:0 complete after 5626.637 msecs
May 18 18:54:18 Server kernel: [  331.942924] PM: resume of devices complete after 5630.226 msecs
May 18 18:54:18 Server kernel: [  331.943184] PM: resume devices took 5.628 seconds
May 18 18:54:18 Server kernel: [  331.943387] PM: Finishing wakeup.
May 18 18:54:18 Server kernel: [  331.943391] Restarting tasks ... done.

```

---

### Post by davidsheppard293 on 2013-05-23
Did you try this?

Maybe it's a solution for you.

- assuming that **eth0** is your LAN connection.
- You need the following utilities to be installed: **ethtool** and **wakeonlan**
- You need to know the MAC address of the LAN card in the PC you want to wake up. You can find the MAC address like this:
**ifconfig eth0 | grep HW**
- You may need to check that WOL is enabled in that PCs BIOS
- You need to check that that LAN card supports WOL (not all do) with
**ethtool eth0**

You'll need to be root to make these changes:
Create a very small script called **activateWOL**
It looks like this 
 	Code:
 	
#!/bin/bash ethtool -s eth0 wol g 
make it executable and move it into **/usr/bin/**
Now [COLOR=Red]add a line[/COLOR] to the **/etc/network/interfaces** file, in the part relevant to **eth0** to call that script, like this 	Code:
 	
auto lo iface lo inet loopback address 127.0.0.1 netmask 255.0.0.0  auto eth0 iface eth0 inet static address 10.0.0.4 netmask 255.255.255.0 gateway 10.0.0.2 [COLOR=Red]post-down /usr/bin/activateWOL[/COLOR] 
Restart networking to make sure this change is noticed:
**/etc/init.d/networking restart**

What this does is re-enable the WOL capability of the card after it has  been shut down. It seems stupid to have to have a script with only one  command in it, but when I tried just putting **post-down ethtool -s eth0 wol g** in the interfaces file, it didn't work.

When the PC has shut down and has kept WOL activated, I notice a little  green light by the ethernet connector, even though the PC is "powered  off".

Now you can now wake that pc from another PC on your LAN  with the command
**wakeonlan *macaddress*** like this
 	Code:
 	
wakeonlan 00:11:2E:A0:0B:55 
With a bit of port-forwarding, I can now wake up, and shut down my  home server from anywhere connected to the internet. Linux is awesome  sometimes.

---

### Post by jjanna18 on 2013-05-24
Thank you for your reply davidsheppard293.

I did followed your recomendation, but still doesn't work.
The WOL works fine, but the problem is the system does not suspend after once it waked by WOL from my window laptop.
If the system waked by server's local keyboard, then it suspend again fine.
Since suspend does not work properly, I rather poweroff the system and WOL from my laptop but boot up takes more time than suspend.
I think it is some network configuration but I have no idea.

Any other solutions?

---

