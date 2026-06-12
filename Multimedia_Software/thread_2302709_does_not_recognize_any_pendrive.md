---
title: "does not recognize any pendrive"
date: 2015-11-12
forum: Multimedia Software
---

### Post by kevin191 on 2015-11-12
```

lsusb:
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 020: ID 0e8d:0002 MediaTek Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
fdisk -l:
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a99ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1452773375   726385664   83  Linux
/dev/sda2      1452775422  1465147391     6185985    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1452775424  1465147391     6185984   82  Linux swap / Solaris
```

My computer is a Dell inspiron 14.







 
 
 I appreciate any help. Thank you :o.

---

### Post by matt_symes on 2015-11-12
Hi

Open a terminal and type 

```
tail -f /var/log/syslog
```

Plug in a USB pendrive. Wait 10 seconds and post any output from the terminal into your next post.

That may give some clues as to what is going on.

Kind regards

---

### Post by kevin191 on 2015-11-12
Hi matt, thanks for your answer and recommendation, i will take into account.

to enter tail -f /var/log/syslog was output:
```

Nov 12 14:04:48 Inspiron-3421 kernel: [ 3892.524930] usb 1-3: device not accepting address 23, error -71
Nov 12 14:04:48 Inspiron-3421 kernel: [ 3892.636901] usb 1-3: new full-speed USB device number 24 using xhci_hcd
Nov 12 14:04:48 Inspiron-3421 kernel: [ 3892.637120] usb 1-3: Device not responding to setup address.
Nov 12 14:04:48 Inspiron-3421 kernel: [ 3892.841051] usb 1-3: Device not responding to setup address.
Nov 12 14:04:49 Inspiron-3421 kernel: [ 3893.044767] usb 1-3: device not accepting address 24, error -71
Nov 12 14:04:49 Inspiron-3421 kernel: [ 3893.044806] usb usb1-port3: unable to enumerate USB device
Nov 12 14:13:18 Inspiron-3421 AptDaemon: INFO: Quitting due to inactivity
Nov 12 14:13:18 Inspiron-3421 AptDaemon: INFO: Quitting was requested
Nov 12 14:17:01 Inspiron-3421 CRON[20173]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 14:17:16 Inspiron-3421 kernel: [ 4640.547593] usb 1-2: USB disconnect, device number 20
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.611965] usb 1-1: new high-speed USB device number 25 using xhci_hcd
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.741417] usb 1-1: New USB device found, idVendor=0e8d, idProduct=0002
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.741427] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.741432] usb 1-1: Product: MT6225 
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.741436] usb 1-1: Manufacturer: MediaTek Inc
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.741440] usb 1-1: SerialNumber: 103212006660470
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.742495] usb-storage 1-1:1.0: USB Mass Storage device detected
Nov 12 15:01:59 Inspiron-3421 kernel: [ 7322.744002] scsi host22: usb-storage 1-1:1.0
Nov 12 15:01:59 Inspiron-3421 mtp-probe: checking bus 1, device 25: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1"
Nov 12 15:01:59 Inspiron-3421 mtp-probe: bus: 1, device: 25 was not an MTP device
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.745352] scsi 22:0:0:0: Direct-Access     MEDIATEK  FLASH DISK      6225 PQ: 0 ANSI: 0 CCS
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.746624] sd 22:0:0:0: Attached scsi generic sg2 type 0
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.747818] sd 22:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.748543] sd 22:0:0:0: [sdb] Write Protect is off
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.748551] sd 22:0:0:0: [sdb] Mode Sense: 03 00 00 00
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.749414] sd 22:0:0:0: [sdb] No Caching mode page found
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.749426] sd 22:0:0:0: [sdb] Assuming drive cache: write through
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.766317]  sdb: sdb1
Nov 12 15:02:00 Inspiron-3421 kernel: [ 7323.770240] sd 22:0:0:0: [sdb] Attached SCSI removable disk
Nov 12 15:02:00 Inspiron-3421 usb_modeswitch: switch device 0e8d:0002 on 001/025
Nov 12 15:17:01 Inspiron-3421 CRON[26768]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

I also try
```
**modprobe usb-storage**
``` 


 
 
 but nothing happened and gparted also detected.



Thanks for your help, kind regards.

---

### Post by matt_symes on 2015-11-12
Hi

```
.... Product: MT6225 
.... Manufacturer: MediaTek Inc
```

From your log file this is the device. What actually is this device ? A search on the vendor and product id...

```
New USB device found, idVendor=0e8d, idProduct=0002
```

seems to suggest that the device might be a phone or modem with storage support.

It seems to be detecting it

```
sd 22:0:0:0: [sdb] Assuming drive cache: write through
sdb: sdb1
```

so it may just not be auto-mounting it.

It is a multi  state device as it's calling usb_modeswitch

```
usb_modeswitch: switch device 0e8d:0002 on 001/025
```

So what exactly is the device ?

Is a standard USB stick not detected as well ?

Kind regards

---

### Post by kevin191 on 2015-11-12
Hi again matt,
The device is a phone with storage media. Currently I think that solves the problem going into  BIOS and changing some settings, then refresh the system with sudo apt-get update and apt-get upgrade and rebooting. Connect a mouse and usb that had not worked and now worked perfectly, the phone still with the same problem, so I thought that it was auto-assembling and i try mounting it manually, i search and i find that running ls -l /dev/sd* the output is:
```
brw-rw---- 1 root disk 8, 0 nov 12 19:23 /dev/sda
brw-rw---- 1 root disk 8, 1 nov 12 19:23 /dev/sda1
brw-rw---- 1 root disk 8, 2 nov 12 19:23 /dev/sda2
brw-rw---- 1 root disk 8, 5 nov 12 19:23 /dev/sda5
```

I am so confused because it's like if detected and while not, 
and now I have no idea what the problem.

Thanks for you help and patience :p.

---

### Post by matt_symes on 2015-11-13
Hi

> **kevin191 said:**
> Hi again matt,
The device is a phone with storage media. Currently I think that solves the problem going into  BIOS and changing some settings, then refresh the system with sudo apt-get update and apt-get upgrade and rebooting. Connect a mouse and usb that had not worked and now worked perfectly, the phone still with the same problem, so I thought that it was auto-assembling and i try mounting it manually, i search and i find that running ls -l /dev/sd* the output is:
```
brw-rw---- 1 root disk 8, 0 nov 12 19:23 /dev/sda
brw-rw---- 1 root disk 8, 1 nov 12 19:23 /dev/sda1
brw-rw---- 1 root disk 8, 2 nov 12 19:23 /dev/sda2
brw-rw---- 1 root disk 8, 5 nov 12 19:23 /dev/sda5
```

I am so confused because it's like if detected and while not, 
and now I have no idea what the problem.

Thanks for you help and patience :p.

Sorry for the late reply. Had a busy day.

From post #1

```
Bus 001 Device 020: ID 0e8d:0002 MediaTek Inc.
```

What is think is happening is that when you plug the phone in, the kernel is detecting the phone, detecting it has a storage and that storage has a partition.

modeswitching, via the usb_modeswitch binary, is then switching the function of the phone to modem mode and that is why you are getting an entry when you run the command lsusb. That is why you are not seeing an entry in /dev/sd?? for your phone.

I'm not 100% sure if the above is correct but it's where i would start looking for a solution as i assume you want to be able to mount the storage on the phone. Is this correct ? You want to mount the storage ?

If so then there are a couple of things i would look at.

First thing i would look at are the options in the settings on the phone to see there is are connection options when you connect the phone to the PC. One of my phones had this option that changed how the phone identified itself to my PC.

After that (and if the above provide no joy), In the file */etc/usb_modeswitch.conf* the is an option to enable loging

```
EnableLogging=0
```

Setting this to 1 and rebooting should log much more information to the file */var/log/usb_modeswitch_**

You can also disabling modeswitching globally, for a test, in that config file. Edit the file as below and reboot.

```
DisableSwitching=1
```

You can then plug your phone in and get logging information or disable modeswitching and see if you can access storage.

If you need more information or help then please post back.

Kind regards

---

### Post by kevin191 on 2015-11-13
Hi matt thanks for your help, i disable modeswitching globally and now the phone has access storage.
Really thank you very much for all the help, kind regards.

---

### Post by matt_symes on 2015-11-13
Hi

> **kevin191 said:**
> Hi matt thanks for your help, i disable modeswitching globally and now the phone has access storage.
Really thank you very much for all the help, kind regards.

I would not disable modeswitching globally in case you need it in the future. Instead, what i would do is disable it in udev for your phone.

In the file

```
/lib/udev/rules.d/40-usb_modeswitch.rules
```

look for the line that says

```
ATTR{idVendor}=="0e8d", ATTR{idProduct}=="0002", RUN+="usb_modeswitch '%b/%k'"
```
and put a hash sign in front of it like so

```
#ATTR{idVendor}=="0e8d", ATTR{idProduct}=="0002", RUN+="usb_modeswitch '%b/%k'"
```

Enable modeswitching globally again, reboot and plug your phone in.

Can you still access the phones storage ? If so, then you're good to go.

**EDIT:**

Just realised this will be overwritten after a udev rules update so you'll want to make a change in 

```
/etc/udev/rules.d
```

I'll need to research that for you so please ignore every above this edit until i post again.

Kind regards

---

### Post by matt_symes on 2015-11-13
Hi

This may work for you.

Open a terminal and copy and paste this into it. It'll create a udev rule for your phone that should do nothing when you plug your phone in.

```
cat<<-EOF | sudo tee /etc/udev/rules.d/40-ignore-phone.rules
ATTR{idVendor}=="0e8d", ATTR{idProduct}=="0002", GOTO="phone_modeswitch_rules_end"
LABEL="phone_modeswitch_rules_end"
EOF
```

Hit enter on the last EOF line and enter your password as normal.

Enable global modeswitching, reboot (just in case) and plug your phone in.

Kind regards

---

### Post by kevin191 on 2015-11-13
It worked perfectly.
By people like you, every day we are more lazy (I say this because the final solution is only copy and paste), just as thanks for everything, I think I owe you one. Kind regards.

---

