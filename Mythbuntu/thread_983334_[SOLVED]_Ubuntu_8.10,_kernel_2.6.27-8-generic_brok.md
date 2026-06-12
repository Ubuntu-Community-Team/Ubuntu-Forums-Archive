---
title: "[SOLVED] Ubuntu 8.10, kernel 2.6.27-8-generic broke my system"
date: 2008-11-15
forum: Mythbuntu
---

### Post by ghuber on 2008-11-15
Ubuntu 8.10, kernel 2.6.27-8-generic downloaded with the last round of updates.  After rebooting, LIRC was dead, WinPVR USB2 was dead and my USB Wireless NIC was dead.  LIRC is using the PVRUSB2 so all my problems are on USB devices.
Attached are the parts of the syslog regarding these. 

could it be looking in the wrong place for firmware?  

I fixed my problem by stepping back to 2.6.27-7


```
Nov 15 11:18:19 mythtv kernel: [   13.535452] parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
Nov 15 11:18:19 mythtv kernel: [   14.142576] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Nov 15 11:18:19 mythtv kernel: [   14.142609] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov 15 11:18:19 mythtv kernel: [   14.193160] Linux video capture interface: v2.00
Nov 15 11:18:19 mythtv kernel: [   14.534176] pvrusb2: Unknown parameter `initusbreset'
Nov 15 11:18:19 mythtv kernel: [   14.701130] usb 3-2: reset high speed USB device using ehci_hcd and address 3
Nov 15 11:18:19 mythtv kernel: [   14.833967] phy0: Selected rate control algorithm 'pid'
Nov 15 11:18:19 mythtv kernel: [   15.147804] zd1211rw 3-2:1.0: phy0
Nov 15 11:18:19 mythtv kernel: [   15.147910] usbcore: registered new interface driver zd1211rw
Nov 15 11:18:19 mythtv kernel: [   15.853358] udev: renamed network interface wlan0 to eth1
Nov 15 11:18:19 mythtv kernel: [   16.989386] lp0: using parport0 (interrupt-driven).
Nov 15 11:18:19 mythtv kernel: [   17.436358] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
Nov 15 11:18:19 mythtv kernel: [   18.206147] EXT3 FS on sda1, internal journal

```





```
Nov 15 11:47:16 mythtv NetworkManager: <info>  (eth1): device state change: 1 -> 2
Nov 15 11:47:16 mythtv NetworkManager: <info>  (eth1): bringing up device.
Nov 15 11:47:16 mythtv kernel: [   46.883416] firmware: requesting zd1211/zd1211b_ub
Nov 15 11:47:16 mythtv kernel: [   47.001618] firmware: requesting zd1211/zd1211b_uphr
Nov 15 11:47:16 mythtv kernel: [   47.109360] usb 3-2: USB control request for firmware upload failed. Error number -71
Nov 15 11:47:16 mythtv kernel: [   47.109376] usb 3-2: Could not upload firmware code uph. Error number -71
Nov 15 11:47:16 mythtv kernel: [   47.109402] zd1211rw 3-2:1.0: couldn't load firmware. Error number -71
Nov 15 11:47:16 mythtv nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_19_bb_4e_b0_be
Nov 15 11:47:16 mythtv NetworkManager: <WARN>  nm_device_hw_bring_up(): (eth1): device not up after timeout!
Nov 15 11:47:16 mythtv NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Nov 15 11:47:16 mythtv kernel: [   47.128963] firmware: requesting zd1211/zd1211b_ub
Nov 15 11:47:16 mythtv kernel: [   47.132585] firmware: requesting zd1211/zd1211b_uphr

```

---

### Post by ghuber on 2008-11-15
hmmm... 

So I rolled back to the previous kernel and that got my NIC and PVRUSB2 working but now the front end crashes when I play DVD's....

> Nov 15 14:15:23 mythtv kernel: [ 6281.657961] mythfrontend.re[8694]: segfault at aaced008 ip b7a276c0 sp ac59f0b0 error 4 in libmythtv-0.21.so.0.21.0[b75c5000+a1e000]


G

:EDIT:  Not all DVDs...  the first two I tried crashed it....  Others have been working.

---

### Post by maks_zbogar on 2008-11-17
I installed some updates today too.
My Ubuntu 8.10 64-bit can't boot now at all. Very strange, but I can remember that one of updates were marked as "untested" or so (I can't remember exactly...). But I hit update anyway and bang. After reboot, boot process seemed to be normal: Splash screen with progress bar went till the end, but after that (right after auto login) there was only black screen.

I couldn't figure out how to repair or rollback updates, so I am reistalling Ubuntu right now. Now I see all my data are gone.

Should I trust Ubuntu further?

My computer is new - (Intel Q6600, 4GB ram, MB: MSI P35). I have installed Ubuntu 64bit 3 weeks ago as I wanted to use it for my primary work machine. Right now I am not sure what is happening... After clean reinstall there was no updates for new kernel.. ????

---

### Post by ghuber on 2008-11-25
[RESOLVED]

When Mythbuntu 8.10 came out with kernel 2.6.27-7 the PVRUSB2 driver did not work at first.

The fix for it was this:
> "do this before you plug in the device for the
first time:

modprobe pvrusb2 initusbreset=0

Alternatively, putting the following into a file anywhere under
/etc/modprobe.d/ should work even better:

options pvrusb2 initusbreset=0

That causes udev to set this parameter for you whenever the driver gets
loaded." 

Turns out that all kernels released since then DO NOT need this and in fact it breaks the driver.  So you have to REMOVE this change.

I am now up and running with the driver on kernel 2.6.27-10

---

