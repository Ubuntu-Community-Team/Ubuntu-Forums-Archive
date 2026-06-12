---
title: "D12-500 STB Serial Port Channel Changing Problems"
date: 2008-08-27
forum: Mythbuntu
---

### Post by squiggie on 2008-08-27
I'm new to setting up mythtv and using serial within linux. I'm having a hard time getting the serial port channel changing perl script to work and I'm beginning to think my serial port isn't working. Here is what I've done so far.

I've followed the [this guide]("http://www.mythtv.org/wiki/index.php/Controlling_DirectTV_D11_via_USB") and purchased all the hardware from the recommended vendors. I've got a usb>serial then a null modem cable>gender changer going into the male serial port in the back of my PC. I know the cabling works because I tested this out in windows using the Windows Perl and Windows version of the pl script and it worked like a champ from my laptop.

The desktop that mythbuntu is only has 1 serial port. Here is the output from dmesg | grep tty

```
[   35.374030] console [tty0] enabled
[   36.787278] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   36.787764] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   71.176150] audit(1219858067.185:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5587 profile="/usr/sbin/cupsd" namespace="default"
```

I'm pretty sure that the serial port is /dev/ttyS0 as I only have 1 port and that is what it looks like in dmesg. Now, when I try to use the script with 

./directv.pl port /dev/ttyS0 baudrate 115200 box_type D11 get_signal

I get getattr: Input/output error. I have tried all kinds of baud rates, box types, different commands and everything but all gives the same output. This is why I'm thinking my serial port isn't working on this PC, but I don't know enough about serial in linux to test this out. Does anyone have any suggestions or input on how to get this working or test out the serial port by itself?

---

### Post by squiggie on 2008-08-28
/bump for anyone who can help me test out my serial port

---

### Post by dynospectrum on 2008-08-28
Same exact problem here.  Could use some help also.  I have a D12-500 using Mythdora 4.0.  I'm using a Serial to USB adapter and and a null modem cable connected from the PC to the USB to Serial adapter.  I get the following trying to test the connection:

[mythtv@localhost bin]$ /usr/local/bin/directv3.pl port /dev/ttyS0 baudrate 9600 verbose get_channel
Initializing Serial Port... done!
SEND: 0xFA [ú] 0x87 []
RECV: Timeout Error


Retry Thu Aug 28 22:09:35 2008
SEND: 0xFA [ú] 0x87 []
RECV: Timeout Error


Retry Thu Aug 28 22:09:37 2008
SEND: 0xFA [ú] 0x87 []
RECV: Timeout Error


Retry Thu Aug 28 22:09:39 2008
SEND: 0xFA [ú] 0x87 []
RECV: Timeout Error


Retry Thu Aug 28 22:09:41 2008
Error excessive retries

---

