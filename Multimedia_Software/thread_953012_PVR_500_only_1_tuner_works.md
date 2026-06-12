---
title: "PVR 500 only 1 tuner works"
date: 2008-10-19
forum: Multimedia Software
---

### Post by cbhatt on 2008-10-19
Hi all. I have Mythtv setup as a backend on my server computer running Ubuntu Server with a PVR-500. Under kernel version 2.6.24-19 everything worked fine. In my most recent update I upgraded to version 2.6.24-21. After that /dev/video0 had no audio and had green blocks across the screen. The other tuner, /dev/video1, works fine.

Its not a mythtv problem because "mplayer /dev/video0" doesn't work but "mplayer /dev/video1" works. I'm thinking its a kernel module problem so I tried the steps in [http://www.gossamer-threads.com/lists/mythtv/users/156030?search_string=Only%20one%20tuner%20PVR-500;#156030](http://www.gossamer-threads.com/lists/mythtv/users/156030?search_string=Only%20one%20tuner%20PVR-500;#156030)

in short:
cd /lib/modules/`uname -r`/kernel/drivers/media/video/
mv tuner.ko tuner.ko.bak
mv tveeprom.ko tveeprom.ko.bak
mv msp3400.ko msp3400.ko.bak
mv tda9887.ko tda9887.ko.bak

cd /lib/modules/`uname -r`/updates/drivers/media/video
cp tuner-ivtv.ko tuner.ko
cp tveeprom-ivtv.ko tveeprom.ko

modprobe -r ivtv
depmod -a
modprobe ivtv 
 
But that did not work. 

I'm considering reverting to version 2.6.24-19 unless the community has a solution. Thanks.

---

### Post by cbhatt on 2008-10-20
Update

I decided to revert back to 2.6.24-19 to see if /dev/video0 would behave like it used to (before I upgraded to 2.6.24-21). Unfortunately I got the exact same result.

So I have a 2 tuner card on which only one tuner has usable video. Hopefully someone out there can help me out with this one.

Here is some outputs to help with my hw config.

Also attached is the output of "mplayer /dev/video0"

lspci:
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller      
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1         
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:00.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev01)
06:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev01)

dmesg | grep ivtv:
[   63.561403] ivtv:  Start initialization, version 1.1.0
[   63.561477] ivtv0: Initializing card #0               
[   63.561479] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   63.624308] ivtv0: Autodetected WinTV PVR 500 (unit #1)       
[   64.070093] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   64.074030] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   64.074283] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   64.286003] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   64.370660] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)       
[   64.379256] ivtv0: Registered device video0 for encoder MPG (4096 kB)   
[   64.379270] ivtv0: Registered device video32 for encoder YUV (2048 kB)  
[   64.379284] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)     
[   64.379297] ivtv0: Registered device video24 for encoder PCM (320 kB)   
[   64.379310] ivtv0: Registered device radio0 for encoder radio
[   64.379311] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   64.379349] ivtv1: Initializing card #1
[   64.379351] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   64.385266] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   64.388499] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   64.405051] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   64.405307] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   64.474722] ivtv1: Correcting tveeprom data: no radio present on second unit
[   64.474724] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   64.492578] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   64.492593] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   64.492606] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   64.492626] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   64.492627] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   64.492666] ivtv:  End initialization
[   76.451674] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   76.644567] ivtv0: Encoder revision: 0x02060039
[   78.982647] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   79.180793] ivtv1: Encoder revision: 0x02060039

Thanks!

---

