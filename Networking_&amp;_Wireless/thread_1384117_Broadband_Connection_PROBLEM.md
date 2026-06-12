---
title: "Broadband Connection PROBLEM"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by harryjocom on 2010-01-18
Hi all, I'm a newbie Ubuntu 9.10. I have a problem regarding to internet connection through mobile broadband. There is no problem if I connected by LAN or Wireless. 
This is a message when I tried to connected through nm-applet:
  	 	 	 	 	 	  

ppma@ppma-laptop:~$ nm-applet
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 

 ** (nm-applet:1963): WARNING **: Tried to set deprecated property gsm/band
 ** (nm-applet:1963): DEBUG: foo_client_state_changed_cb
 ** (nm-applet:1963): DEBUG: foo_client_state_changed_cb
 ** (nm-applet:1963): DEBUG: going for offline with icon: notification-gsm-disconnected
 ** (nm-applet:1963): DEBUG: old state indicates that this was not a disconnect 9
 ** (nm-applet:1963): DEBUG: going for offline with icon: notification-gsm-disconnected
 ** (nm-applet:1963): DEBUG: foo_client_state_changed_cb
 ** (nm-applet:1963): DEBUG: foo_client_state_changed_cb
 ** (nm-applet:1963): DEBUG: going for offline with icon: notification-gsm-disconnected
 ** (nm-applet:1963): DEBUG: old state indicates that this was not a disconnect 9
 ** (nm-applet:1963): DEBUG: going for offline with icon: notification-gsm-disconnected
 ** (nm-applet:1963): DEBUG: foo_client_state_changed_cb
 ** (nm-applet:1963): DEBUG: foo_client_state_changed_cb
 ** (nm-applet:1963): DEBUG: going for offline with icon: notification-gsm-disconnected
 ** (nm-applet:1963): DEBUG: old state indicates that this was not a disconnect 9
 ** (nm-applet:1963): DEBUG: going for offline with icon: notification-gsm-disconnected
 

 Please help me... anyone... 
Thank you 

Harry Jocom

---

### Post by GeorgeVita on 2010-01-18
Hi **harryjocom**, welcome to this forum!

Some more 'technical' info will help readers of your thread to help you:
1. exact model of your modem (manufacturer/type look at the sticker on case)
2. do the following test and post output
- Boot without modem, **wait** for the system to load
- open a terminal window (Applications>Accessories>Terminal) and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem, **wait** 30 seconds
- from terminal: **dmesg**
- from terminalQ **lsusb**
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and lsusb, post it here.

Regards,
George

---

### Post by harryjocom on 2010-01-18
Hi George, 
Thanks for your help, herewith the documentation after followed the several instruction. I hope could help me to fixed the problem.  

ppma@ppma-laptop:~$ dmesg 
[  415.236168] usb 1-7: new high speed USB device using ehci_hcd and address 3 
[  415.381989] usb 1-7: configuration #1 chosen from 1 choice 
[  415.928479] Initializing USB Mass Storage driver... 
[  415.929188] scsi2 : SCSI emulation for USB Mass Storage devices 
[  415.929458] usb-storage: device found at 3 
[  415.929465] usb-storage: waiting for device to settle before scanning 
[  415.929474] usbcore: registered new interface driver usb-storage 
[  415.929483] USB Mass Storage support registered. 
[  415.931368] usb 1-7: USB disconnect, address 3 
[  421.040135] usb 1-7: new high speed USB device using ehci_hcd and address 4 
[  421.187951] usb 1-7: configuration #1 chosen from 1 choice 
[  421.209307] scsi5 : SCSI emulation for USB Mass Storage devices 
[  421.211598] usb-storage: device found at 4 
[  421.211604] usb-storage: waiting for device to settle before scanning 
[  421.215088] scsi6 : SCSI emulation for USB Mass Storage devices 
[  421.218500] usb-storage: device found at 4 
[  421.218507] usb-storage: waiting for device to settle before scanning 
[  426.210237] usb-storage: device scan complete 
[  426.212513] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2 
[  426.218594] usb-storage: device scan complete 
[  426.221850] scsi 6:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2 
[  426.237379] sr0: scsi-1 drive 
[  426.237389] Uniform CD-ROM driver Revision: 3.20 
[  426.237658] sr 5:0:0:0: Attached scsi CD-ROM sr0 
[  426.237809] sr 5:0:0:0: Attached scsi generic sg1 type 5 
[  426.238172] sd 6:0:0:0: Attached scsi generic sg2 type 0 
[  426.255448] sd 6:0:0:0: [sdb] Attached SCSI removable disk 
[  439.265508] UDF-fs: No VRS found 
[  439.265517] UDF-fs: No partition found (1) 
[  439.290509] ISO 9660 Extensions: Microsoft Joliet Level 1 
[  439.293484] ISOFS: changing to secondary root 
ppma@ppma-laptop:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader 
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub 
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
ppma@ppma-laptop:~$

---

### Post by GeorgeVita on 2010-01-18
Hi **harryjocom**,
your modem is a Huawei (**check sticker label on it** to determine exact model). Use any alternative method for connectiong to internet (wifi or ethernet) and try to update your system as initial version (from LiveCD iso) has a bug that affects 3g modems.

You can check kernel# using terminal command: **uname -a**
You need kernel version >= **2.6.31-15-generic**

If your kernel is >= 2.6.31-15-generic or you cannot update, repeat your test (as in previous post), check **dmesg** for the message:
```
[ 426.237658] sr 5:0:0:0: Attached scsi CD-ROM sr0 
``` and eject that drive using the terminal command: **sudo eject sr0**

Check again **dmesg** if new data exist regarding ttyUSBx port creation

Post your progress to follow up.

Regards,
George

---

### Post by harryjocom on 2010-01-18
HI GeorgeVita,

I didn't updated the system yet, because I'm in the home this night. Tommorow morning I will be update after arrive in the office. Meanwhile, the modem I used is corret HUAWEI E220, and I had to follow your guide as your mentioned, and here the result is:

 ppma@ppma-laptop:~$ uname -a 
Linux ppma-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux 
ppma@ppma-laptop:~$ sudo eject sr0 
ppma@ppma-laptop:~$ dmesg 
[  402.268178] usb 1-7: new high speed USB device using ehci_hcd and address 3 
[  402.414742] usb 1-7: configuration #1 chosen from 1 choice 
[  402.930754] Initializing USB Mass Storage driver... 
[  402.932651] scsi2 : SCSI emulation for USB Mass Storage devices 
[  402.932923] usb-storage: device found at 3 
[  402.932929] usb-storage: waiting for device to settle before scanning 
[  402.932939] usbcore: registered new interface driver usb-storage 
[  402.932947] USB Mass Storage support registered. 
[  402.934487] usb 1-7: USB disconnect, address 3 
[  408.060132] usb 1-7: new high speed USB device using ehci_hcd and address 4 
[  408.206415] usb 1-7: configuration #1 chosen from 1 choice 
[  408.240960] scsi5 : SCSI emulation for USB Mass Storage devices 
[  408.243336] usb-storage: device found at 4 
[  408.243341] usb-storage: waiting for device to settle before scanning 
[  408.243762] scsi6 : SCSI emulation for USB Mass Storage devices 
[  408.249773] usbcore: registered new interface driver usbserial 
[  408.249795] USB Serial support registered for generic 
[  408.249906] usbcore: registered new interface driver usbserial_generic 
[  408.249909] usbserial: USB Serial Driver core 
[  408.250139] usb-storage: device found at 4 
[  408.250143] usb-storage: waiting for device to settle before scanning 
[  408.254398] USB Serial support registered for GSM modem (1-port) 
[  408.254454] option 1-7:1.0: GSM modem (1-port) converter detected 
[  408.254599] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB0 
[  408.254614] option 1-7:1.1: GSM modem (1-port) converter detected 
[  408.254681] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB1 
[  408.254709] usbcore: registered new interface driver option 
[  408.254713] option: v0.7.2:USB Driver for GSM modems 
[  413.242113] usb-storage: device scan complete 
[  413.250153] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2 
[  413.251065] usb-storage: device scan complete 
[  413.255586] scsi 6:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2 
[  413.274875] sr0: scsi-1 drive 
[  413.274885] Uniform CD-ROM driver Revision: 3.20 
[  413.275143] sr 5:0:0:0: Attached scsi CD-ROM sr0 
[  413.275301] sr 5:0:0:0: Attached scsi generic sg1 type 5 
[  413.275650] sd 6:0:0:0: Attached scsi generic sg2 type 0 
[  413.286580] sd 6:0:0:0: [sdb] Attached SCSI removable disk 
[  426.285632] UDF-fs: No VRS found 
[  426.285641] UDF-fs: No partition found (1) 
[  426.310634] ISO 9660 Extensions: Microsoft Joliet Level 1 
[  426.313608] ISOFS: changing to secondary root 
[  696.952128] usb 1-5: new high speed USB device using ehci_hcd and address 5 
[  697.086215] usb 1-5: configuration #1 chosen from 1 choice 
[  697.095635] scsi7 : SCSI emulation for USB Mass Storage devices 
[  697.100136] usb-storage: device found at 5 
[  697.100142] usb-storage: waiting for device to settle before scanning 
[  702.100345] usb-storage: device scan complete 
[  702.101531] scsi 7:0:0:0: Direct-Access     UT163    USB Flash Disk   0.00 PQ: 0 ANSI: 2 
[  702.102424] sd 7:0:0:0: Attached scsi generic sg3 type 0 
[  702.103353] sd 7:0:0:0: [sdc] 1003520 512-byte logical blocks: (513 MB/490 MiB) 
[  702.103848] sd 7:0:0:0: [sdc] Write Protect is off 
[  702.103855] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00 
[  702.103861] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[  702.108097] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[  702.108108]  sdc: sdc1 
[  702.170698] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[  702.170709] sd 7:0:0:0: [sdc] Attached SCSI removable disk

After I update, I will contact again ASAP ... thanks,

---

### Post by GeorgeVita on 2010-01-18
> [ 408.254398] USB Serial support registered for GSM modem (1-port)
[ 408.254454] option 1-7:1.0: GSM modem (1-port) converter detected
[ 408.254599] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB0
[ 408.254614] option 1-7:1.1: GSM modem (1-port) converter detected
[ 408.254681] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB1
[ 408.254709] usbcore: registered new interface driver option
[ 408.254713] option: v0.7.2:USB Driver for GSM modemsAfter ejecting it seems to have at least /dev/ttyUSB0 and /dev/ttyUSB1:
> ppma@ppma-laptop:~$ uname -a
Linux ppma-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/LinuxYour kernel is OK.

Try to setup a new broadband connection via network manager icon and

**Also note that E220 possibly needs a firmware update** as done at:
[http://ubuntuforums.org/showthread.php?t=1368494](http://ubuntuforums.org/showthread.php?t=1368494)

Search your provider's site for any firmware update and follow carefully the instructions to do it. It is possible to need windows to make it.

G

---

### Post by harryjocom on 2010-01-20
Hi George, 

It's a bright day ... my connection problem through mobile broadband has been solved... it's success 100%, so I could mobile again without worry about internet.
Thanks a lot for your consider and attention, it's very helpfull...

See u later on next discussion.

Warm Greetings from Indonesia,
Harry Jocom

---

