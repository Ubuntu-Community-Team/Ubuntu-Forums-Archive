---
title: "Media Center Infrared Remote Not working in Ubuntu 9.10+lirc"
date: 2009-12-23
forum: Multimedia Software
---

### Post by pricinosus on 2009-12-23
Hello
I have this "NONAME - 
USB 2.0 SD/MMC[COLOR="Red"] IR Remote Control [/COLOR]Digital Media Card Reader " remote in ubuntu 9.10 (karmic) with xbmc but no irw response.
in win xp works but not in karmic :no:

How to make it work in ubuntu 9.10 ?

USB 2.0 SD/MMC [COLOR="Red"]IR Remote Control[/COLOR] Digital Media Card Reader 

[[img]http://img36.imageshack.us/img36/2962/multimediairsoft.th.jpg[/IMG]](http://img36.imageshack.us/i/multimediairsoft.jpg/)
[[img]http://img36.imageshack.us/img36/7311/multimediairunit.th.jpg[/IMG]](http://img36.imageshack.us/i/multimediairunit.jpg/)
[[img]http://img709.imageshack.us/img709/3828/multimediairbox.th.jpg[/IMG]](http://img709.imageshack.us/i/multimediairbox.jpg/)

[[IMG]http://img9.imageshack.us/img9/7499/screenshotremotecontrol.th.png[/IMG]](http://img9.imageshack.us/i/screenshotremotecontrol.png/)

The IR receiver uses rts5161 from realtek
[[IMG]http://img64.imageshack.us/img64/8164/rts5161.jpg[/IMG]](http://img64.imageshack.us/i/rts5161.jpg/)



[[Bug 491860] [NEW] lirc_mceusb doesn't recognize eHome IR receiver]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1905508.html")


xbmc@asusp5b:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0161 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 10d5:55a4 Uni Class Technology Co., Ltd 
Bus 002 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


xbmc@asusp5b:~$ dmesg | grep -i lirc
[   15.084603] lirc_dev: IR Remote Control driver registered, major 61 
[   15.103581] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   15.103584] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   15.103611] usbcore: registered new interface driver lirc_mceusb
[ 2013.622498] usbcore: deregistering interface driver lirc_mceusb
[ 2133.345897] lirc_dev: IR Remote Control driver registered, major 61 
[ 2133.347893] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 2133.347896] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 2133.347936] usbcore: registered new interface driver lirc_mceusb

xbmc@asusp5b:~$ sudo /etc/init.d/lirc start
[sudo] password for xbmc: 
 * Loading LIRC modules                                                                                                                               [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                                                           [ OK ] 


xbmc@asusp5b:~$ dmesg | grep usb
[    0.190928] usbcore: registered new interface driver usbfs
[    0.190928] usbcore: registered new interface driver hub
[    0.190928] usbcore: registered new device driver usb
[    0.784092] usb usb1: configuration #1 chosen from 1 choice
[    0.784292] usb usb2: configuration #1 chosen from 1 choice
[    0.784451] usb usb3: configuration #1 chosen from 1 choice
[    0.784620] usb usb4: configuration #1 chosen from 1 choice
[    0.784781] usb usb5: configuration #1 chosen from 1 choice
[    1.216011] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.415231] usb 1-4: configuration #1 chosen from 1 choice
[    1.656010] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.837726] usb 2-2: configuration #1 chosen from 1 choice
[    1.879352] usbcore: registered new interface driver usb-storage
[    1.879433] usb-storage: device found at 3
[    1.879434] usb-storage: waiting for device to settle before scanning
[    2.125274] usb 2-2.1: new low speed USB device using uhci_hcd and address 3
[    2.266314] usb 2-2.1: configuration #1 chosen from 1 choice
[    2.292543] usbcore: registered new interface driver hiddev
[    2.294350] usbcore: registered new interface driver usbhid
[    2.294352] usbhid: v2.6:USB HID core driver
[    2.310457] input: MLK Trust Deskset 15176 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input3
[    2.310500] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK Trust Deskset 15176] on usb-0000:00:1d.0-2.1/input0
[    2.337834] input: MLK Trust Deskset 15176 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.1/input/input4
[    2.337908] sunplus 0003:04FC:05D8.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Trust Deskset 15176] on usb-0000:00:1d.0-2.1/input1
[    2.377270] usb 2-2.3: new low speed USB device using uhci_hcd and address 4
[    2.535337] usb 2-2.3: configuration #1 chosen from 1 choice
[    2.576362] input: No brand 4 Port KVMSwicther as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input5
[    2.576400] generic-usb 0003:10D5:55A4.0003: input,hidraw2: USB HID v1.10 Keyboard [No brand 4 Port KVMSwicther] on usb-0000:00:1d.0-2.3/input0
[    2.581297] usbhid 2-2.3:1.1: couldn't find an input interrupt endpoint
[    6.876882] usb-storage: device scan complete
[   15.103581] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   15.103584] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   15.103611] usbcore: registered new interface driver lirc_mceusb
[ 2013.622498] usbcore: deregistering interface driver lirc_mceusb
[ 2133.347893] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 2133.347896] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 2133.347936] usbcore: registered new interface driver lirc_mceusb
[ 3174.992197] usbcore: registered new interface driver lirc_imon

---

### Post by TeKniKal on 2010-01-21
I'm having the same problem: I bought a Conrad card reader/MCE Remote bundle which uses the same chip (in any case the USB information is identical). 

I tried to build lirc from the CVS sources (the latest HEAD also added support for this remote and some others), then a checkinstall but that didn't fix it for me. 

I also tried patching the lirc_mceusb-driver myself by following [this guide]("https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes") without any errors and I do get everything to recognize when connecting the USB receiver, but irw and the gnome lirc settings won't bother to recognize the receiver.

I have also checked both source files for this driver for changes, but apart from some extra remotes in the CVS one, my version was equivalent.

My logs give similar information, but I also get the following
```
tail /var/log/syslog
Jan 21 23:45:38 Egon-PCx lircd-0.8.6[21505]: could not open config file ''''
Jan 21 23:45:38 Egon-PCx lircd-0.8.6[21505]: No such file or directory
Jan 21 23:45:38 Egon-PCx lircd-0.8.6[21506]: lircd(default) ready, using /var/run/lirc/lircd
Jan 21 23:45:38 Egon-PCx kernel: [213481.892302] lirc_mceusb[43]: Generic USB2.0-CRW on usb2:43
Jan 21 23:45:38 Egon-PCx kernel: [213481.892579] usbcore: registered new interface driver lirc_mceusb
Jan 21 23:45:42 Egon-PCx lircd-0.8.6[21506]: accepted new client on /var/run/lirc/lircd
Jan 21 23:45:42 Egon-PCx lircd-0.8.6[21506]: could not get file information for ''
Jan 21 23:45:42 Egon-PCx lircd-0.8.6[21506]: default_init(): No such file or directory
Jan 21 23:45:42 Egon-PCx lircd-0.8.6[21506]: Failed to initialize hardware
Jan 21 23:48:01 Egon-PCx lircd-0.8.6[21506]: accepted new client on /var/run/lirc/lircd

```
But I found something to get IRW to detect all key presses:
```

sudo /etc/init.d/lirc stop
sudo lircd
irw

```That will work, but I don't find this workaround very attractive nor do I understand why it works that way.

---

### Post by TeKniKal on 2010-01-29
I think my problem may also be related to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/489394").

---

### Post by Zemy on 2010-03-12
> **pricinosus said:**
> Hello
I have this "NONAME - 
USB 2.0 SD/MMC[COLOR=red] IR Remote Control [/COLOR]Digital Media Card Reader " remote in ubuntu 9.10 (karmic) with xbmc but no irw response.
in win xp works but not in karmic :no:
 
How to make it work in ubuntu 9.10 ?
 
USB 2.0 SD/MMC [COLOR=red]IR Remote Control[/COLOR] Digital Media Card Reader 
 
[[IMG]http://img36.imageshack.us/img36/2962/multimediairsoft.th.jpg[/IMG]]("http://img36.imageshack.us/i/multimediairsoft.jpg/")
[[IMG]http://img36.imageshack.us/img36/7311/multimediairunit.th.jpg[/IMG]]("http://img36.imageshack.us/i/multimediairunit.jpg/")
[[IMG]http://img709.imageshack.us/img709/3828/multimediairbox.th.jpg[/IMG]]("http://img709.imageshack.us/i/multimediairbox.jpg/")
 
[[IMG]http://img9.imageshack.us/img9/7499/screenshotremotecontrol.th.png[/IMG]]("http://img9.imageshack.us/i/screenshotremotecontrol.png/")
 
The IR receiver uses rts5161 from realtek
[[IMG]http://img64.imageshack.us/img64/8164/rts5161.jpg[/IMG]]("http://img64.imageshack.us/i/rts5161.jpg/")
 
 
 
[[Bug 491860] [NEW] lirc_mceusb doesn't recognize eHome IR receiver]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1905508.html")
 
 
xbmc@asusp5b:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0161 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 10d5:55a4 Uni Class Technology Co., Ltd 
Bus 002 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
xbmc@asusp5b:~$ dmesg | grep -i lirc
[ 15.084603] lirc_dev: IR Remote Control driver registered, major 61 
[ 15.103581] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 15.103584] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 15.103611] usbcore: registered new interface driver lirc_mceusb
[ 2013.622498] usbcore: deregistering interface driver lirc_mceusb
[ 2133.345897] lirc_dev: IR Remote Control driver registered, major 61 
[ 2133.347893] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 2133.347896] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 2133.347936] usbcore: registered new interface driver lirc_mceusb
 
xbmc@asusp5b:~$ sudo /etc/init.d/lirc start
[sudo] password for xbmc: 
* Loading LIRC modules [ OK ]
* Starting remote control daemon(s) : LIRC [ OK ] 
 
 
xbmc@asusp5b:~$ dmesg | grep usb
[ 0.190928] usbcore: registered new interface driver usbfs
[ 0.190928] usbcore: registered new interface driver hub
[ 0.190928] usbcore: registered new device driver usb
[ 0.784092] usb usb1: configuration #1 chosen from 1 choice
[ 0.784292] usb usb2: configuration #1 chosen from 1 choice
[ 0.784451] usb usb3: configuration #1 chosen from 1 choice
[ 0.784620] usb usb4: configuration #1 chosen from 1 choice
[ 0.784781] usb usb5: configuration #1 chosen from 1 choice
[ 1.216011] usb 1-4: new high speed USB device using ehci_hcd and address 3
[ 1.415231] usb 1-4: configuration #1 chosen from 1 choice
[ 1.656010] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 1.837726] usb 2-2: configuration #1 chosen from 1 choice
[ 1.879352] usbcore: registered new interface driver usb-storage
[ 1.879433] usb-storage: device found at 3
[ 1.879434] usb-storage: waiting for device to settle before scanning
[ 2.125274] usb 2-2.1: new low speed USB device using uhci_hcd and address 3
[ 2.266314] usb 2-2.1: configuration #1 chosen from 1 choice
[ 2.292543] usbcore: registered new interface driver hiddev
[ 2.294350] usbcore: registered new interface driver usbhid
[ 2.294352] usbhid: v2.6:USB HID core driver
[ 2.310457] input: MLK Trust Deskset 15176 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input3
[ 2.310500] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK Trust Deskset 15176] on usb-0000:00:1d.0-2.1/input0
[ 2.337834] input: MLK Trust Deskset 15176 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.1/input/input4
[ 2.337908] sunplus 0003:04FC:05D8.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Trust Deskset 15176] on usb-0000:00:1d.0-2.1/input1
[ 2.377270] usb 2-2.3: new low speed USB device using uhci_hcd and address 4
[ 2.535337] usb 2-2.3: configuration #1 chosen from 1 choice
[ 2.576362] input: No brand 4 Port KVMSwicther as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input5
[ 2.576400] generic-usb 0003:10D5:55A4.0003: input,hidraw2: USB HID v1.10 Keyboard [No brand 4 Port KVMSwicther] on usb-0000:00:1d.0-2.3/input0
[ 2.581297] usbhid 2-2.3:1.1: couldn't find an input interrupt endpoint
[ 6.876882] usb-storage: device scan complete
[ 15.103581] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 15.103584] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 15.103611] usbcore: registered new interface driver lirc_mceusb
[ 2013.622498] usbcore: deregistering interface driver lirc_mceusb
[ 2133.347893] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 2133.347896] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 2133.347936] usbcore: registered new interface driver lirc_mceusb
[ 3174.992197] usbcore: registered new interface driver lirc_imon
 
Hi pricinosus,
 
have You managed to get this to work?
I have exactly the same symptoms and the same chip inside the reveiver unit.
I have built a HTPC based on Ubuntu minimal and XBMC Live via XCI script.
That eHome Infrared receiver is not somehow supported by lirc.
 
Br, Zemy

---

### Post by brewski2 on 2010-06-16
I don't know if you fixed this, but the cause is that the lirc_mceusb module does not know the vendor and product ID's of the remote receiver. To fix this is easy, just follow these steps:
[INDENT]sudo apt-get install build-essential checkinstall module-assistant
sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.6/drivers/lirc_mceusb/
sudo vi lirc_mceusb.c (or any other editor you might like)
[INDENT]After the line that says:
  #define VENDOR_NORTHSTAR        0x04eb
add the following line:
  #define VENDOR_REALTEK          0x0bda

After the line that says:
        { USB_DEVICE(VENDOR_NORTHSTAR, 0xe004) },
add the following 2 lines:
        /* Realtek card reader and IR receiver */
        { USB_DEVICE(VENDOR_REALTEK, 0x0161) },

Save the file and exit 
[/INDENT]sudo dpkg-reconfigure lirc-modules-source
sudo modprobe -r lirc_mceusb
sudo modprobe lirc_mceusb
[/INDENT]voila, your IR receiver will now work.

---

### Post by mnrbig on 2010-08-31
Worked thanks. If using a harmony remote make sure you set it up as a Xbox MCE.

---

### Post by pils92 on 2011-01-02
Thank you, brewski2. This method worked using terminal: ~@~$ lsusb, and noting relevant lines in generated list. For an RC-6 Rosewill remote that gave me the same problem. \\:D/

---

