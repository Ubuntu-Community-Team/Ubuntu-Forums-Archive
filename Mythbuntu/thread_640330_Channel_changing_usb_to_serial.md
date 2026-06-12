---
title: "Channel changing usb to serial"
date: 2007-12-14
forum: Mythbuntu
---

### Post by docdailey on 2007-12-14
Ok..here is my setup:

 directv box d10... I only have one serial port...used for touchscreen...I want to get the channel changing script to work via usb to serial so I can add another box.  I got it to work using serial so that is not the problem but when I switch over to usb to serial I have a little linux problem and am not good at troubleshooting it.

Device is detected:

willy@ubuntu-server:/usr/local/bin$ lsusb
Bus 002 Device 003: ID 0bc2:0500 Seagate RSS LLC 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 058f:9720 Alcor Micro Corp. 
Bus 001 Device 003: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 001 Device 004: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
Bus 001 Device 001: ID 0000:0000  
willy@ubuntu-server:/usr/local/bin$ 

willy@ubuntu-server:/usr/local/bin$ dmesg | grep USB0
[   16.888000] usb 1-10: pl2303 converter now attached to ttyUSB0
[  176.728000] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0


Connecting and disconnecting shows that the USB to serial is Alcor Micro Corp

And it is connecting at port USB0

willy@ubuntu-server:/usr/local/bin$ dmesg | grep serial
[    1.792000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.880000] usbcore: registered new interface driver usbserial
[   16.880000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   16.880000] usbcore: registered new interface driver usbserial_generic
[   16.880000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   16.888000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[   16.888000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[   18.220000] tveeprom 2-0050: Hauppauge model 48132, rev K268, serial# 8229854

So...for my directv.pl script I should use "directv.pl port /dev/ttyUSB0 off" to turn the box off for instance....but I get:

getattr: Inappropriate ioctl for device

i have also tried "directv.pl port /dev/ttyUSB0 baudrate 9600 off" hoping that for some reason it was sending too fast but same error.

obviously something is wrong but I don't know what.

---

### Post by docdailey on 2007-12-14
Hmmm..may have solved this myself (best way)

I dug around and found out that sometimes the brltty (brail) thing messes up USB to serial sometimes. 

([http://ubuntuforums.org/showthread.php?t=425830&highlight=Usb](http://ubuntuforums.org/showthread.php?t=425830&highlight=Usb))

So I removed it:

sudo apt-get remove brltty

This removed both brltty and brltty-x10  (not sure if this helped me or not but I will likely not need it...hopefully)

I then did a dmesg | grep -i usb after before and after plugging and realized the port it was being assigned was /dev/ttyACM0

so I then issued:

Rebooted and now back to /dev/ttyUSB0 but it works now...wierd.

sudo ./directv.pl port /dev/tty/ACM0 off and low and behold the box went off.

and

sudo ./directv.pl port /dev/ttyACM0 on and the box came back on

time to refine.

---

