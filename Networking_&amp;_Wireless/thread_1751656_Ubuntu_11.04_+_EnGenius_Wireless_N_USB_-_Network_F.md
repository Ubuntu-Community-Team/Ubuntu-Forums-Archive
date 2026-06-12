---
title: "Ubuntu 11.04 + EnGenius Wireless N USB - Network Firmware Problem"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by JoeMcP-STG on 2011-05-06
First off I would like to say "Hello" to the people of Ubuntu Forums.  I am new here.

When Ubuntu 11.04 was officially released I downloaded a WUBI and installed it onto my computer. After I finished the install I tried to connect to my wireless router, but no signals were displayed. So, I tried using ndiswrapper to install the respective driver like I did in the past. Unfortunately there were no results.

I thought that I have done something wrong with installing via WUBI so I tried reinstalling. I still got the same results though. I tried reading through threads here about what other people did with similar problems, but they didn't really help me because I am not using a wireless card like others. I did pick up some commands to run and tried them. I figured I should post some of them because they might help.

```

joseph@ubuntu:~$ ndiswrapper -l
netr28u : driver installed
	device (1740:9706) present (alternate driver: rt2800usb

```
```
joseph@ubuntu:~$ lsusb
[...]
Bus 001 Device 002: ID 1740:9706 Senao EnGenius 802.11n Wireless USB Adapter
[...]

```
```
joseph@ubuntu:~$ dmesg
[...]
**[   16.324574] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.**
[   16.327776] eth0: link down
[   16.331204] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.329757] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   23.085723] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   47.928513] UDF-fs: Partition marked readonly; forcing readonly mount
[   47.976827] UDF-fs INFO UDF: Mounting volume 'CNCTFD', timestamp 2005/12/09 11:44 (1f10)
[  186.234251] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  467.666433] ISO 9660 Extensions: Microsoft Joliet Level 3
[  467.767469] ISO 9660 Extensions: RRIP_1991A
**[  654.848872] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.**
**[  716.723055] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.**
[ 1059.499738] Disabling lock debugging due to kernel taint
[ 1059.512792] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1059.528644] usbcore: registered new interface driver ndiswrapper
[ 1546.005023] VFS: busy inodes on changed media or resized disk sr0

```

I put the firmware results of the dmesg command in bold because I thought it was important.

Please help me with this problem.

---

### Post by Dirge on 2011-05-15
Same issue here. The driver that's part of this kernel build is loading and isn't the one designed for that chipset. Try blacklisting the rt2x00 drivers.

---

### Post by JoeMcP-STG on 2011-05-15
> **Dirge said:**
> Same issue here. The driver that's part of this kernel build is loading and isn't the one designed for that chipset. Try blacklisting the rt2x00 drivers.

Thanks for replying.

What exactly do you mean by "blacklisting?" I don't know a lot of the terminology, sorry.

Would you think waiting for a newer version of the kernel and trying to upgrade Ubuntu's might help also?

---

### Post by Renagade on 2011-06-23
Don't know if YOU'VE found it yet, but here's the easiest and most effective way :-)
[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

Peace
:-)

---

### Post by JoeMcP-STG on 2011-06-25
> **Renagade said:**
> Don't know if YOU'VE found it yet, but here's the easiest and most effective way :-)
[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

Peace
:-)

Thanks for the reply. I was going to try buying an Ethernet Cable to stretch across my house, but I will try this to get things working.

---

### Post by chili555 on 2011-06-25
I don't believe you need ndiswrapper at all, just a bit of blacklisting. If you need specific instructions, please post back.

---

### Post by JoeMcP-STG on 2011-06-26
The Instructions that Renagade gave really did solve the problem.  

Thank You!! :D

I will now mark this thread as solved.

---

