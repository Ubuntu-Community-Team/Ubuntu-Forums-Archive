---
title: "SYNCE doesn't recognize Pocket PC WM5"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by T1000-kernel on 2009-08-28
Hi Folks:
This is my first time (posting, only) I was newbee in Linux one year ago. 
Now I'm struggling to synchronize the holy PocketPC unsuccessfully. This is the point:

The laptop...
- ACER Travelmate 4230, 2 GB RAM. 
- Ubuntu Hardy Heron 8.04, kernel 2.6.24-24-generic
- Installed on encrypted LVM, with ALTERNATE CD, no major changes on default installation
- Evolution installed

The holy Pocket...
- AIRIS T620
- Windows Mobile 5, version 5.0 (5.1.195)
- I haven't messed in default configuration, so RNDIS should be working.

I followed the steps in 
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)
I haven't done the step indicated for old kernels (<2.6.24-19), but I break in doing the 
synce-pls step.

It returns:
$ synce-pls
** Message: Hal reports no devices connected
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

My dmesg is the following:

[ 7580.302833] usb 1-1: new full speed USB device using uhci_hcd and address 10
[ 7580.500885] usb 1-1: configuration #1 chosen from 1 choice
[ 7580.594360] rndis_host 1-1:1.0: RNDIS_MSG_QUERY(0x01010101) failed, -110
[ 7580.594367] rndis_host 1-1:1.0: rndis get ethaddr, -110
[ 7580.594387] rndis_host: probe of 1-1:1.0 failed with error -110

I have been reading a proposed solution in 
[http://www.nabble.com/RNDIS-error--110-with-HP214-Ubuntu-8.04-td21119002.html](http://www.nabble.com/RNDIS-error--110-with-HP214-Ubuntu-8.04-td21119002.html)
but it doesn't show anything useful.

This other post also claims for help:
[http://www.opensource-archive.org/showthread.php?t=60124](http://www.opensource-archive.org/showthread.php?t=60124)
but no valid answer.

Any idea??

---

### Post by tipocomico on 2009-08-31
Hi I am having a similar issue. 

Running jaunty kernel 2.6.28-15-generic in thinkpad and Qtek s200 (aka htc prophet).

When I first installed synce it seemed to recognize the phone and was able to respond to synce-pls, however after a reboot all functionality was lost.

here is lsusb:

[INDENT]$ lsusb
Bus 001 Device 011: ID 0bb4:0bce High Tech Computer Corp. Vario MDA
Bus 001 Device 006: ID 0e6a:6001 Megawin Technology Co., Ltd 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/INDENT]and Kernel.log
[INDENT]usb 1-3.3.2: new full speed USB device using ehci_hcd and address 13
usb 1-3.3.2: configuration #1 chosen from 1 choice
ipaq 1-3.3.2:1.0: PocketPC PDA converter detected
usb 1-3.3.2: PocketPC PDA converter now attached to ttyUSB8
ipaq 1-3.3.2:1.1: PocketPC PDA converter detected
usb 1-3.3.2: PocketPC PDA converter now attached to ttyUSB9
BUG: unable to handle kernel NULL pointer dereference at 0000003c
IP: [<f7f23867>] ipaq_open+0x1e7/0x3c0 [ipaq] 
*pde = 00000000 
Oops: 0002 [#8] SMP 
last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3.2/1-3.3.2:1.1/ttyUSB9/port_number
Modules linked in: binfmt_misc radeon drm bridge stp bnep vboxnetflt vboxdrv input_polldev lp pcmcia snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device yenta_socket ipw2100 rndis_wlan rsrc_nonstatic thinkpad_acpi iTCO_wdt iTCO_vendor_support nsc_ircc rndis_host cdc_ether ipaq pcmcia_core ieee80211 ieee80211_crypt psmouse video snd led_class ppdev intel_agp serio_raw shpchp output soundcore irda nvram pcspkr usbnet usbserial joydev agpgart parport_pc snd_page_alloc crc_ccitt parport usbhid ohci1394 e100 mii ieee1394 floppy fbcon tileblit font bitblit softcursor
Pid: 13450, comm: pppd Tainted: G      D    (2.6.28-15-generic #49-Ubuntu) 2722GG0
EIP: 0060:[<f7f23867>] EFLAGS: 00210286 CPU: 0
EIP is at ipaq_open+0x1e7/0x3c0 [ipaq]
EAX: f350c000 EBX: f4ec6c20 ECX: f351d800 EDX: 00000000
ESI: f351d800 EDI: 00000100 EBP: f35e1df4 ESP: f35e1db8
DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Process pppd (pid: 13450, ti=f35e0000 task=f359bed0 task.ti=f35e0000)
Stack:
00000001 00200296 f35e1de0 f35e1dd0 c04fef4b f433f200 f351d800 f4ecd000
f4ec6c34 f3576720 00000064 f351d800 f7f2aa00 f351d800 f3576720 f35e1e24
f7cbb547 f4ecd000 f35e1e24 c032f299 f34929c0 f4ecd000 f351d850 f351d804
Call Trace:
[<c04fef4b>] ? mutex_lock+0xb/0x20
[<f7cbb547>] ? serial_open+0xe7/0x180 [usbserial]
[<c032f299>] ? tty_init_dev+0x89/0x160
[<c032f524>] ? __tty_open+0x1b4/0x460
[<c032f7ef>] ? tty_open+0x1f/0x40
[<c01c063d>] ? chrdev_open+0xcd/0x1a0
[<c01bbbe6>] ? __dentry_open+0xb6/0x260
[<c01bbe67>] ? nameidata_to_filp+0x47/0x60
[<c01c0570>] ? chrdev_open+0x0/0x1a0
[<c01c9119>] ? do_filp_open+0x1c9/0x7b0
[<c05001f8>] ? _spin_lock+0x8/0x10
[<c01d3b7d>] ? mntput_no_expire+0x1d/0x120
[<c01d2230>] ? alloc_fd+0xe0/0x100
[<c01bb9af>] ? do_sys_open+0x5f/0x130
[<c01bee7f>] ? fput+0x1f/0x30
[<c01bbae9>] ? sys_open+0x29/0x40
[<c0103f6b>] ? sysenter_do_call+0x12/0x2f
Code: 00 00 b8 30 80 72 c0 e8 18 4b 29 c8 85 c0 89 86 90 00 00 00 0f 84 62 01 00 00 8b 45 dc 89 c1 8b 90 88 00 00 00 8b 80 80 00 00 00 <89> 42 3c 8b 81 90 00 00 00 8b 91 98 00 00 00 89 42 3c 8b 81 88 
EIP: [<f7f23867>] ipaq_open+0x1e7/0x3c0 [ipaq] SS:ESP 0068:f35e1db8
---[ end trace 76f2cd3d46b4b87e ]---
[/INDENT]I followd the instructions from synce's site for ubuntu.

any help would be appriciated thnx in advance.

---

### Post by T1000-kernel on 2009-09-01
So far, what I have discovered is that synce-hal and other packages simply remove the odccm, because they are incompatible, and create a conflict. And very few forums talk about that. So instructions that you find over there are simply incoherent, as they ask you to install odccm and afterwards they order you to install another packages that uninstall it.

Well, the point is: if you simply don't follow the install step of those stuff, you get the PDA being recognized via odccm. You have to do a 'sudo odccm -f' and type 'synce-pls' in another terminal, and you'll see the folders and files.
But whatever other step that you'll do will REMOVE the odccm, so you do a step back, and it is not possible to synchonize.

So questions to answer are:

- How do I sync with odccm if the other packages (opensync-plugin-engine, synce-sync-engine... ) remove it?
- How do I sync then with other packages WITHOUT odccm? So far I can only see the PDA with odccm running.

if you do 
STEP 1 : sudo apt-get install odccm librra0-tools librapi2-tools
STEP 2 : synce-pls
(Great, you can see the PDA)

STEP 3: sudo apt-get install multisync-tools opensync-plugin-evolution opensync-plugin-synce
(Then, these packages UNINSTALL odccm and synce-pls won't work any more)
So Step 1 and Step 3 are incoherent. Any solution for that??????

---

### Post by mbolivar on 2013-01-23
Somebody have found the solution for this problem. I'm facing the same problem in ubuntu 12.04(precise).

---

