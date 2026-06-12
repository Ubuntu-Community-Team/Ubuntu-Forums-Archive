---
title: "strange ipod mounting problems PLEASE HELP"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by Mooie on 2006-08-11
Earlier today I decided to check if my ipod would work with this kernel (it didnt with an earlier one, but its updated some in the last few months).  I plugged my ipod into my computer via the usb cable, and to my suprise within seconds it came up on my desktop and i was able to transfer 4 cds to it with gtkpod!  I was very happy with this and hit "safely remove device" (or somthing to that effect) on the ipods right click menu thing.  it disconnected and i was able to listen to my music.  Later I found a cd I wanted to add to my ipod, so i plugged my ipod back into my computer the same way as I had earlier that day (the only thing i had done since the last time i plugged it in was restart my computer, i had not installed any packages or changed any hardware) and nothing happened.  The ipod didnt even tell me not to disconnect it.  Somtimes now it does tell me "Do not disconnect" but its not mounting onto my computer.  I have checked all through the /dev file, as it normally mounts as /dev/sdb2 all that is there is /dev/sda1 which is my windows partition...   could anybody please tell me what is going on here?  I would really like to get my ipod working in linux again, and i dont like having to boot to windos just for my ipod...

:confused: :confused: :confused: please help! :confused: :confused: :confused:

---

### Post by huygens on 2006-08-11
Hi,

If you open a terminal just after pluging in your iPod and type the following command:
```
dmesg | tail -32
``` Could you post here the output?

Or perhaps you find out by yourself what is the problem ;)

Huygens

---

### Post by Mooie on 2006-08-11
my output from dmesg | tail -32 is:

```
[   56.235063] NTFS driver 2.1.25 [Flags: R/O MODULE].
[   56.326888] NTFS volume version 3.1.
[   57.150483] NET: Registered protocol family 10
[   57.150612] lo: Disabled Privacy Extensions
[   57.150978] IPv6 over IPv4 tunneling driver
[   63.134775] ACPI: Power Button (FF) [PWRF]
[   63.134808] ACPI: Power Button (CM) [PWRB]
[   63.211329] ibm_acpi: ec object not found
[   63.254699] pcc_acpi: loading...
[   63.672135] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   63.672163] powernow-k8: MP systems not supported by PSB BIOS structure
[   63.672187] powernow-k8: MP systems not supported by PSB BIOS structure
[   65.085806] ppdev: user-space parallel port driver
[   67.861863] eth0: no IPv6 routers present
[   68.805779] Bluetooth: Core ver 2.8
[   68.805786] NET: Registered protocol family 31
[   68.805788] Bluetooth: HCI device and connection manager initialized
[   68.805809] Bluetooth: HCI socket layer initialized
[   68.850917] Bluetooth: L2CAP ver 2.8
[   68.850922] Bluetooth: L2CAP socket layer initialized
[   68.858337] Bluetooth: RFCOMM socket layer initialized
[   68.858362] Bluetooth: RFCOMM TTY layer initialized
[   68.858364] Bluetooth: RFCOMM ver 1.7
[  317.797984] cdrom: dropping to old style cdda (sense=4)
[  388.135124] usb 2-6: new high speed USB device using ehci_hcd and address 3
[  398.559037] Initializing USB Mass Storage driver...
[  398.559129] scsi6 : SCSI emulation for USB Mass Storage devices
[  398.559211] usb-storage: device found at 3
[  398.559212] usb-storage: waiting for device to settle before scanning
[  398.559224] usbcore: registered new driver usb-storage
[  398.559227] USB Mass Storage support registered.
[  409.165212] usb 2-6: reset high speed USB device using ehci_hcd and address 3

```

a few seconds after I did this, my ipod beeped a few times then ejected itself so it was just charging, I dont think its ever done that before...
I also made sure it wasnt an ipod problem by trying it on a windows machine, and it mounted there flawlessly.

---

### Post by Mooie on 2006-08-14
anybody? please help me!

---

### Post by huygens on 2006-08-14
Sorry not to have answer quicker, but I was not in front of my PC this week-end :)

So, the output of your problem did not help me much. But google-ing a bit with parts of this output, I have found [this thread]("http://www.ubuntuforums.org/showthread.php?t=47805") which talks about a similar-ish problem. The solution of the person was to change of USB connector, as it seems that he had a power issue (the USB port is not giving enough power to the device)

I have found another [thread on Fedora]("http://www.fedoraforum.org/forum/showthread.php?t=103776"), which gives a dmesg output that I would qualilfy as similar. Could you try the solution at the end to see if with the USB1.x driver it is working or not? It might help making a diagnostic of your own problem. On Ubuntu, you will have to do in a terminal:
```
sudo  modprobe -r ehci_hcd
``` Then, once done. Plug your iPod and check if it is working. It should be much slower :(

Huygens

---

### Post by huygens on 2006-08-14
Still some more information that could help you, if you want to dig around by yourself ;)
A how-to about iPod (people have been writing problems and solutions, I did not find something that could be related to yours, but you could try to write there your problem...): [http://www.ubuntuforums.org/showthread.php?t=103071&highlight=mount+usb](http://www.ubuntuforums.org/showthread.php?t=103071&highlight=mount+usb)
Then on the wonderful Gentoo-Wiki, I have found this: [http://gentoo-wiki.com/HARDWARE_iPod](http://gentoo-wiki.com/HARDWARE_iPod)

All this made me think of one thing:
Could you put in your CD tray the Ubuntu CD or DVD and boot on it?
Once the desktop is displayed, plug-in your iPod and see if it does still work. If it is working from the Live version of Ubuntu, then you should try to verify if there is not a discrepency for the Kernel or USB driver (ehci) between these two versions.
You could also try to compare the outputs of dmesg...

Huygens

---

### Post by Mooie on 2006-08-14
My ipod works on the 32-bit live cd and automounts, but its not happening on the 64-bit version, here is the dmesg | tail -32 from the 64-bit:
```
[  133.272987] Bluetooth: L2CAP socket layer initialized
[  133.733476] Bluetooth: RFCOMM socket layer initialized
[  133.733512] Bluetooth: RFCOMM TTY layer initialized
[  133.733514] Bluetooth: RFCOMM ver 1.7
[  249.941276] usb 2-6: USB disconnect, address 3
[  266.384197] usb 2-6: new high speed USB device using ehci_hcd and address 4
[  271.497561] usb 2-6: unable to read config index 0 descriptor/start
[  271.497570] usb 2-6: can't read configurations, error -110
[  271.599373] usb 2-6: new high speed USB device using ehci_hcd and address 5
[  276.708654] usb 2-6: unable to read config index 0 descriptor/start
[  276.708663] usb 2-6: can't read configurations, error -110
[  276.810567] usb 2-6: new high speed USB device using ehci_hcd and address 6
[  281.817946] usb 2-6: unable to read config index 0 descriptor/start
[  281.817954] usb 2-6: can't read configurations, error -110
[  281.919819] usb 2-6: new high speed USB device using ehci_hcd and address 7
[  286.928239] usb 2-6: unable to read config index 0 descriptor/start
[  286.928248] usb 2-6: can't read configurations, error -110
[  309.345704] usb 2-6: new high speed USB device using ehci_hcd and address 8
[  314.456013] usb 2-6: unable to read config index 0 descriptor/all
[  314.456024] usb 2-6: can't read configurations, error -110
[  314.559880] usb 2-6: new high speed USB device using ehci_hcd and address 9
[  319.674702] scsi7 : SCSI emulation for USB Mass Storage devices
[  319.674854] usb-storage: device found at 9
[  319.674856] usb-storage: waiting for device to settle before scanning
[  324.671732]   Vendor: Apple     Model: iPod              Rev: 1.62
[  324.671743]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  354.748426] usb 2-6: reset high speed USB device using ehci_hcd and address 9[  364.958940] usb 2-6: reset high speed USB device using ehci_hcd and address 9[  381.263989] usb 2-6: reset high speed USB device using ehci_hcd and address 9[  391.758294] usb 2-6: device not accepting address 9, error -110
[  391.860222] usb 2-6: reset high speed USB device using ehci_hcd and address 9[  398.073663] usb 2-6: reset high speed USB device using ehci_hcd and address 9
```
I will post the dmesg from the 32-bit in a few minutes

---

### Post by Mooie on 2006-08-14
(still on the 64-bit live cd)
my ipod says "OK to disconnect." so it probably COULD work on the live cd w/ some tweaking...

---

### Post by Mooie on 2006-08-14
on the 32-bit live cd (on which the ipod works) my dmesg is:
```
[4294747.496000] apm: overridden by ACPI.
[4294754.129000] Bluetooth: Core ver 2.8
[4294754.129000] NET: Registered protocol family 31
[4294754.129000] Bluetooth: HCI device and connection manager initialized
[4294754.129000] Bluetooth: HCI socket layer initialized
[4294754.213000] Bluetooth: L2CAP ver 2.8
[4294754.213000] Bluetooth: L2CAP socket layer initialized
[4294755.342000] Bluetooth: RFCOMM socket layer initialized
[4294755.342000] Bluetooth: RFCOMM TTY layer initialized
[4294755.342000] Bluetooth: RFCOMM ver 1.7
[4294820.486000] usb 1-6: new high speed USB device using ehci_hcd and address 3[4294822.219000] Initializing USB Mass Storage driver...
[4294822.219000] scsi6 : SCSI emulation for USB Mass Storage devices
[4294822.219000] usb-storage: device found at 3
[4294822.219000] usb-storage: waiting for device to settle before scanning
[4294822.219000] usbcore: registered new driver usb-storage
[4294822.219000] USB Mass Storage support registered.
[4294827.220000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4294827.220000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294827.222000] SCSI device sdb: 78126047 512-byte hdwr sectors (40001 MB)
[4294827.225000] sdb: Write Protect is off
[4294827.225000] sdb: Mode Sense: 64 00 00 08
[4294827.225000] sdb: assuming drive cache: write through
[4294827.229000] SCSI device sdb: 78126047 512-byte hdwr sectors (40001 MB)
[4294827.232000] sdb: Write Protect is off
[4294827.232000] sdb: Mode Sense: 64 00 00 08
[4294827.232000] sdb: assuming drive cache: write through
[4294827.232000]  sdb: sdb1 sdb2
[4294827.570000] sd 6:0:0:0: Attached scsi removable disk sdb
[4294827.570000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[4294827.570000] usb-storage: device scan complete
[4294828.412000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```
I hope the problem isn't a 64-bit driver issue. Also, I use the latest amd64-K8-smp kernel from the repos, I dont really know anything (at all) about compiling my own kernel.

---

### Post by Mooie on 2006-08-14
my ipod works w/ usb 1.0! I have dial-up because i live in the middle of nowhere, so I have learned to be patient w/ my computer...  at least it works now! thanks

What exactly is the effect of ```
sudo  modprobe -r ehci_hcd
```
do I have to run it every time I want to use my ipod?

---

### Post by huygens on 2006-08-14
Hi Mooi,

It seems that the EHCI driver in 64bits has some problems with your external device. Perhaps, you should file a bug about it.

In short EHCI is the "code name" (shall I say) of the USB2 Linux driver. It is a module, meaning it is loaded by the Kernel to operate USB2 devices.
By performing after the boot: ```
sudo modprobe -r ehci_hcd
``` You ask the system to remove (-r option) the ehci_hcd driver. Thus, it is forcing the kernel to use the USB1 driver as a USB2 device can be operated either by the USB2 or USB1 driver.

You do not need to execute this command each time you plug your iPod onto your computer. But you would need to do it after each reboot, unless you specify that you don't want this driver to ever load again.... :( however I am sorry, because I forgot where (I mean in which configuration file) this can be set and thus I don't know how to achieve this goal...

Perhaps, somebody else could give you a hint...

Huygens

---

### Post by Mooie on 2006-08-15
ok, I will look around, and mabey in the next version of ubuntu they will include a newer version, thanks for all your help! Now I can put music on my ipod again!

---

### Post by Kosmonaut on 2006-08-15
Hi there!

I´ve got the same problem with that nasty "ehci_hcd".
I have to "sudo rmmod ehci_hcd" so that my MP3 Player and(!) my Sony picture camera will connect with ubuntu.
The very anoying point is that USB2 plug&play devices worked with elder kernel-versions (>=Kernel 2.6.15.23).

A workaround could look like this
sudo gedit /etc/modprobe.d/blacklist
And add a new blacklist-element called ehci_hcd.
Well this is a way to "solve" the problem, but this is not very nice.
Let us hope&pray[-o< that the next kernelupdate will solve this problem
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53813](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53813)

---

### Post by Mooie on 2006-08-16
yeah, I hope they fix that.  I might try some diff kernels untill they do...  oh well.

---

### Post by huygens on 2006-08-16
> **Kosmonaut said:**
> Let us hope&pray[-o< that the next kernelupdate will solve this problem
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53813](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53813)


It would be good that you report to the above mentionned bug report your troubles (I mean both of you). Just explain which devices have been involved. You just need to add a comment for that.

---

### Post by edrappin on 2006-08-31
Mooie,

I experienced the same exact problem you reported in post #7 of this thread on my 64 bit machine. Enable memory hole in the BIOS did the trick for me.

---

### Post by Sentinel on 2006-08-31
[17181351.100000] VFS: Can't find a valid FAT filesystem on dev sda3.

can someone explain this?

---

### Post by huygens on 2006-08-31
> **Sentinel said:**
> [17181351.100000] VFS: Can't find a valid FAT filesystem on dev sda3.

can someone explain this?

I know that iPod can be formatted using the Apple HFS+ filesystem. Are you able to view from a Windows PC your iPod as an external drive?

Huygens

---

