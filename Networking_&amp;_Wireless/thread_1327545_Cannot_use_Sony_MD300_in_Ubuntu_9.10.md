---
title: "Cannot use Sony MD300 in Ubuntu 9.10"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by ventura36 on 2009-11-15
Hi!

I just upgraded from 9.04 to 9.10. Everything seems to be ok, but my MD300 Sony Ericsson modem does not work anymore. It is recognized only as a pendrive.

I've tried a couple of things found on google, like editing the file /etc/udev/rules.d/50-md300modem.rules and unmounting the device, but nothing seems to work.

I've been told to look at the logs but I don't know what to look for.

I hope someone can help me.

Thanks a lot.

---

### Post by pdc on 2009-11-15
plu it in 

type

> lsusb in a terminal and then

> sudo tail -f /var/log/messages

and copy and paste the results back;

If it appears as an icon on your desktop;

right-click on the icon;

select "Eject";

again type

> lsusb

and check the messages as above, and see if anything changes

(and post it back here)

---

### Post by ventura36 on 2009-11-16
Hi pdc,

I did as you said. The command "lsusb" after and before ejecting gives the same output:

> ventura@seropedica:~$ lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0fce:d0cf Sony Ericsson Mobile Communications AB 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Then, I typed the command the "sudo tail -f /var/log/messages"and the output was

> Nov 16 16:14:08 seropedica kernel: [   69.416559] sd 3:0:0:0: Attached scsi generic sg3 type 0
Nov 16 16:14:08 seropedica kernel: [   69.422258] sd 3:0:0:0: [sdc] 348161 512-byte logical blocks: (178 MB/170 MiB)
Nov 16 16:14:08 seropedica kernel: [   69.429253] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
Nov 16 16:14:08 seropedica kernel: [   69.445251] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
Nov 16 16:14:08 seropedica kernel: [   69.445259]  sdc: sdc1
Nov 16 16:14:08 seropedica kernel: [   69.464272] sdc: p1 size 348161 exceeds device capacity, limited to end of disk
Nov 16 16:14:08 seropedica kernel: [   69.481258] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
Nov 16 16:14:08 seropedica kernel: [   69.481267] sd 3:0:0:0: [sdc] Attached SCSI removable disk
Nov 16 16:14:39 seropedica kernel: [  100.932529] usb 4-1: reset full speed USB device using uhci_hcd and address 2
Nov 16 16:15:10 seropedica kernel: [  131.916011] usb 4-1: reset full speed USB device using uhci_hcd and address 2After ejecting, as far as I can see, nothing changed. I tried unmounting too, but again, nothing happened.

Thanks a lot.

---

