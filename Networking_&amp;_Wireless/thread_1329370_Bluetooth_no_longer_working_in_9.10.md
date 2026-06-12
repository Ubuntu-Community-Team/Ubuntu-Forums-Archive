---
title: "Bluetooth no longer working in 9.10"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2009-11-17
I did a fresh install of Karmic Koala. At first, my bluetooth adapter was recognized and working ... but now it's neither working and as far as I can tell it's not recognized.

```
$ hciconfig -a
hci1:	Type: USB
	BD Address: 4E:00:64:50:68:B4 ACL MTU: 1017:8 SCO MTU: 64:0
	DOWN 
	RX bytes:7169 acl:0 sco:0 events:238 errors:0
	TX bytes:3457 acl:0 sco:0 commands:241 errors:5
	Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 

$ hcitool scan
Device is not available: No such device
$ sudo /etc/init.d/bluetooth start
$ sudo /etc/init.d/bluetooth status
 * bluetooth is running
$ sudo /etc/init.d/bluetooth stop
$ sudo /etc/init.d/bluetooth status
 * bluetooth is not running
$ sudo /etc/init.d/bluetooth start
$ hcitool dev
Devices:
$ sudo hciconfig hci0 reset
Can't get device info: No such device
$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bb4:0c02 High Tech Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 007: ID 0a5c:2100 Broadcom Corp. Bluetooth 2.0+eDR dongle
Bus 005 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I've waited for more than a week for hopefully the problem to resolve itself. I've also been looking for solutions. I've scoured Google and these forums and have yet to see any solutions that work.

I'm dual-booting and my bluetooth works perfectly on Windows XP. 

If someone could at least point me in the right direction, it'll be much appreciated.

---

### Post by loneowais on 2009-11-26
I'm facing the same problem.

---

### Post by levicivita on 2009-12-12
Same problem here - Mythbuntu 9.10.

---

### Post by ScottinSoCal on 2009-12-12
The most recent update - the one I just got today - temporarily killed my bluetooth. The OS said there were no bluetooth adapters in the computer, even after a reboot. I did a complete shutdown, went into setup, reinitialized the bluetooth, and when the computer came back up, so did my bluetooth.

---

### Post by manwithastick on 2009-12-12
I have upgraded since hardy with no problems with bluetooth on my laptop. Today 
i decided to do a fresh install of karmic and for 8 hours I've been fighting this issue with karmic uninstalling, reinstalling, different versions of blueman and/or bluez to no avail.
I just came across this post with ScottinSoCal replying over one hour ago stating his finds. Could it be that simple? I went into the BIOS of my latitude e5500 and turned off bluetooth and saved settings and then turned bluetooth back on and saved settings and proceeded to boot and finally for the first time bluetooth mouse is working! bluyaa! 

Thanks ScottinSoCal

---

### Post by gunkaragoz on 2009-12-14
I had the same problem today. 

I didn't upgrade to 9.10 but did some updates yesterday. Yesterday my bluetooth adapter was working, but today I couldn't make it started. I've restarted again and again but no solution. Then I switched to Windows. I've used bluetooth, so it was working, then switched to Ubuntu. Bluetooth started at startup automatically. How magic!

---

### Post by lajevardi on 2009-12-22
Same f**** exact hell here!

---

### Post by clevertomato on 2010-01-23
I don't know if gunkaragoz meant his post to be a solution or if others took it that way, but this thread sounds like the problem I just had and solved. I have not yet removed Windows 7 from my new Dell Studio 1555 with bluetooth. Bluetooth was working great in Karmic. Then one day I noticed it disappeared. The hardware wasn't even recognized as existing! I freaked out. I checked the BIOS but bluetooth was already/still enabled there. I got to thinking... booted into Win 7. BT was off. I turned it on in Windows, rebooted into Ubuntu and all is well again. It blows my mind how settings in one OS can persist like that and effect another OS, but that's reality I guess. I'm not sure whether it's more Microsoft's fault or the PC manufacturer's fault--probably both. But at least I found a solution.

Before I delete Windows partition, I'll sure need to make sure all settings are the way I need them beforehand. What a pain. Anyway, I hope this helps someone who may be struggling to figure out why their bluetooth disappeared.

---

