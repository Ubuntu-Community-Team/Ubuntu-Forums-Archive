---
title: "UMAX USB TV tuner not detected/ working on Ubuntu 10.04"
date: 2011-04-09
forum: Multimedia Software
---

### Post by anilkumart on 2011-04-09
I am a beginner @ Ubuntu. I am using using ver 10.04 (net book) and I am a satisfied user of the wonderful OS.

The only thing that troubles me is that my Umax external USB tv tuner card does not get detected/ work on Ubuntu.  I tried various ways given on the internet but to no avail as the card is not getting detected as one with proprietary software/driver.  Certain outputs with the card plugged in is as follows:-
...............................................................
>>
lsusb
>>
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 1f71:3301  
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
---------------------------------------------------------------
NOTE: Bus 002 Dev 006 1f71:3301  could be the tv tuner

Please help me out to get my card up and working on Ubuntu... I don't want to switch back to windows just for this :(

---

### Post by anilkumart on 2011-04-09
Just so you are informed:-

.................
>>
(Last Few Lines of)  dmesg
>>
[  257.278221] scsi 4:0:0:0: Direct-Access     StoreJet Transcend             PQ: 0 ANSI: 2 CCS
[  257.279156] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  257.281027] sd 4:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[  257.283549] sd 4:0:0:0: [sdb] Write Protect is off
[  257.283557] sd 4:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  257.283561] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  257.287067] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  257.287076]  sdb: sdb1
[  257.314921] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  257.314967] sd 4:0:0:0: [sdb] Attached SCSI disk
[10286.375330] usb 2-2: USB disconnect, address 4
[10296.472601] usb 2-2: new high speed USB device using ehci_hcd and address 5
[10296.608406] usb 2-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[10296.611579] usb 2-2: configuration #1 chosen from 1 choice
[10492.603047] usb 2-2: USB disconnect, address 5
[10492.968069] usb 2-2: new high speed USB device using ehci_hcd and address 6
[10493.103967] usb 2-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[10493.107119] usb 2-2: configuration #1 chosen from 1 choice
..............................................................

Waiting for a positive way out

---

### Post by sanderj on 2011-04-09
I would live-boot the 11.04 Natty Beta 1 CD (no need to install!), and then see if it works and/or see the diagnostics output (see below).


Reason: my own USB-tv-stick is only correctly recognized by the newer kernel in 11.04.




Furthermore two tips to get the diagnostics output even better:

Find the exect USB id this way:
with the usb device *unplugged*, run lsusb
then plug in the usb device, and run lsusb again
then find the difference; that's the usb id. Post it here.

dmesg output:
with the usb device *unplugged*, type 'tail -f /var/log/messages' and keep it running. 
Press ENTER in that screen to create an empty line.
then plug in the usb device and see the output from the tail command. Post that output here.

---

### Post by anilkumart on 2011-04-09
(output of):: tail -f /var/log/messages


Apr 10 08:27:47 anil-laptop pulseaudio[1641]: ratelimit.c: 520 events suppressed
Apr 10 08:27:52 anil-laptop pulseaudio[1641]: ratelimit.c: 528 events suppressed
Apr 10 08:38:01 anil-laptop pulseaudio[1641]: ratelimit.c: 211 events suppressed




Apr 10 08:40:41 anil-laptop kernel: [ 6312.072588] usb 2-2: new high speed USB device using ehci_hcd and address 5
Apr 10 08:40:42 anil-laptop kernel: [ 6312.211430] usb 2-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
Apr 10 08:40:42 anil-laptop kernel: [ 6312.214532] usb 2-2: configuration #1 chosen from 1 choice

-----------------------------------------------------------------------

(output of):: lsusb  (w/out connecting tv tuner)

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

----------------------------------------------------------------------

(output of):: lsusb  (after connecting tv tuner)

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 1f71:3301  
Bus 005 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
----------------------------------------------------------------------

I had tried the lsusb (disconnect / connect) once, thatz how I inferred the dev-ID.

I hope the log/messages is of some use for you to help me out.

---

### Post by anilkumart on 2011-04-09
Sanderj,

I would prefer being in LTS version 10.04 at present.  Please help me!

---

### Post by sanderj on 2011-04-10
> **anilkumart said:**
> Sanderj,

I would prefer being in LTS version 10.04 at present.  Please help me!

I understand, but I can't: It took about 20 pages of Ubuntu forum to get my own usb-tv-stick working on an older kernel 10.04/10.10, whereas with 11.04 it's a matter of plugging in the stick, copying in the firmware, and that's it.

So my advice is to download 11.04 beta 1, burn it to CD, and live-boot the CD (do *not* install it). That will take a few minutes. If that works, you know your device *can* be supported by linux.


(The other way is checking what others have *tried* based on the dmesg error message you get ( [http://www.google.nl/search?q=config+1+interface+0+altsetting+1+bulk+endpoint+0x83+has+invalid+maxpacket+256](http://www.google.nl/search?q=config+1+interface+0+altsetting+1+bulk+endpoint+0x83+has+invalid+maxpacket+256) ), but with a quick look at the forum I haven't seen success. It looks even more difficult than my 20-page usb-tv-stick.)

---

