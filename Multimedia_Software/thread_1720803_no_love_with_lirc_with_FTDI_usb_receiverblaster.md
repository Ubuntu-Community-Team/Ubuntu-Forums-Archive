---
title: "no love with lirc with FTDI usb receiver/blaster"
date: 2011-04-03
forum: Multimedia Software
---

### Post by ZanexGt on 2011-04-03
Hey all,

I recently bought a FTDI usb receiver / blaster from irblaster.info [http://www.irblaster.info/usb_receiver.html]("http://www.irblaster.info/usb_receiver.html").  I realize that it's for 'experts', but the amount of pain I have gone through has been more than expected.  At this point I only want to use it as a receiver, but no luck there thus far.  

I have followed all the directions I can find from [http://www.huitsing.nl/irftdi/]("http://www.huitsing.nl/irftdi/"), specifically the section on compiling lirc with ftdi support.  The compile was successful but I can't seem to get the receiver working appropriately.

Here's my OS details / stats:

uname -a
```

mythings@mythings:~$ uname -a
Linux mythings 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686 GNU/Linux

```

lsusb
```
mythings@mythings:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

udevadm info
```
mythings@mythings:~$ udevadm info -q all -n /dev/ttyUSB0
P: /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/ttyUSB0/tty/ttyUSB0
N: ttyUSB0
S: char/188:0
S: serial/by-path/pci-0000:00:12.0-usb-0:1:1.0-port0
S: serial/by-id/usb-FTDI_FT232R_USB_UART_A900fCv0-if00-port0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/ttyUSB0/tty/ttyUSB0
E: SUBSYSTEM=tty
E: DEVNAME=ttyUSB0
E: ID_PORT=0
E: ID_PATH=pci-0000:00:12.0-usb-0:1:1.0
E: ID_VENDOR=FTDI
E: ID_VENDOR_ENC=FTDI
E: ID_VENDOR_ID=0403
E: ID_MODEL=FT232R_USB_UART
E: ID_MODEL_ENC=FT232R\x20USB\x20UART
E: ID_MODEL_ID=6001
E: ID_REVISION=0600
E: ID_SERIAL=FTDI_FT232R_USB_UART_A900fCv0
E: ID_SERIAL_SHORT=A900fCv0
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=ftdi_sio
E: ID_IFACE=00
E: ID_VENDOR_FROM_DATABASE=Future Technology Devices International, Ltd
E: ID_MODEL_FROM_DATABASE=FT232 USB-Serial (UART) IC
E: MAJOR=188
E: MINOR=0
E: DEVLINKS=/dev/char/188:0 /dev/serial/by-path/pci-0000:00:12.0-usb-0:1:1.0-port0 /dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A900fCv0-if00-port0
```

ftdi modules loaded

```
mythings@mythings:~$ lsmod |grep ftdi
ftdi_sio               30070  0
usbserial              33357  1 ftdi_sio
```


Here's my configurations (lirc specific)

lircd.conf

```

mythings@mythings:/etc/lirc$ cat lircd.conf
#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

```

hardware.conf

```

mythings@mythings:/etc/lirc$ cat hardware.conf
REMOTE="Windows Media Center Transceivers/Remotes (all)"
TRANSMITTER="None"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

I had tried the lirc_i2c and dev modules, and those also didnt' seem to work.  I changed to MCE in the hopes that this driver would work, better.

IRW

Output from irw yields a hanging terminal (expected) but no output from remote control key presses.  Also, ls on dev shows no lirc, lirc0, or lirc1

lookin for lirc* in /dev
```
mythings@mythings:~$ ls -l /dev/lirc*
lrwxrwxrwx 1 root root 19 2011-04-03 17:13 /dev/lircd -> /var/run/lirc/lircd
```

i also set up some udev rules:

```

mythings@mythings:/etc/udev/rules.d$ ls -l
total 16
-rw-r--r-- 1 root root   99 2011-04-03 15:34 10-lirc.rules
-rw-r--r-- 1 root root  855 2011-04-02 22:26 70-persistent-cd.rules
-rw-r--r-- 1 root root  411 2011-04-02 22:05 70-persistent-net.rules
-rw-r--r-- 1 root root 1157 2010-09-24 08:25 README
mythings@mythings:/etc/udev/rules.d$ cat 10-lirc.rules
KERNEL=="lirc[0-9]*", NAME=="lirc%n", GROUP=="disk", MODE=="0660"
KERNEL=="lirc0", SYMLINK=="lirc"

```

here's what starting lirc in non-daemon mode returns:
```

mythings@mythings:~/lirc/daemons$ sudo ./lircd -n
lircd: lircd(ftdi) ready, using /var/run/lirc/lircd

```

If anyone has any thoughts, suggestions, or ideas it would be greatly appreciated.  I have been workin at this for around 5+ hours thus far with no end in sight.  Personally, I think the issue is that the lirc0 dir is not showing in /dev, but I guess it could be something else also.

---

### Post by johnr320 on 2011-04-15
With lirc-0.9.0 compiled from source, I had to change the baud in daemons/hw_ftdi.c to:

static int rx_baud_rate = 2400;

This is per notes here:

[http://www.irblaster.info/blog/2010/02/alberts-ftdi-ir-receivertransmitter.html](http://www.irblaster.info/blog/2010/02/alberts-ftdi-ir-receivertransmitter.html)

Email exchange with irblaster.info indicated this would not be needed with recent source but that is not the case.

John

---

### Post by cvig on 2011-05-11
I think it's a recent lirc/kernel update that is causing a lot of pain with the mce hardware. Mine is completely broken with 2.6.35-28 and the next newer kernel. It was fine in 10.x but 11.x is not so great... I'm guessing you already figured this out by your second post but just a thought.

---

### Post by marr99 on 2011-06-01
> **johnr320 said:**
> With lirc-0.9.0 compiled from source, I had to change the baud in daemons/hw_ftdi.c to:

static int rx_baud_rate = 2400;

This is per notes here:

[http://www.irblaster.info/blog/2010/02/alberts-ftdi-ir-receivertransmitter.html](http://www.irblaster.info/blog/2010/02/alberts-ftdi-ir-receivertransmitter.html)

Just wanted to mention that this method that 'johnr320' used seems to **greatly** improve my situation too. (Thanks, John!)

I'm using a simple hardware setup with a Vishay TSOP1138 crudely plugged into the end of an FTDI cable, just as described on Albert Huitsing's aforementioned website ([http://www.huitsing.nl/irftdi/](http://www.huitsing.nl/irftdi/)).

More specifically, the FTDI cable I'm using is the TTL version (TTL-232R-3V3-WE) which provides the requisite voltage on the red/black pins, unlike the FTDI USB-RS232-WE cable (at least, in its default configuration at time of purchase from Mouser).

This setup is not quite working perfectly just yet but I have more experimentation to do. But the waveforms shown in LIRC's 'xmode2' utility were completely inconsistent for the same button on the remote control (which meant that nothing really worked at all) prior to changing the "9600" to "2400" in LIRC 0.9.0's 'hw_ftdi.c' file.

After the change, the waveforms are much more consistent so now LIRC's 'irexec' utility (etc) are working very nicely.

Thanks again, John!

Regards,
Bill Marr

---

### Post by KRavEN on 2012-01-27
I had one of the USB FTDI receiver dongles from them that doesn't have the transmitter.  I wasn't able to get it working with lirc 0.9.0 by changing the rx_baud_rate to 2400.  I ended up getting the lirc 0.8.6 source from dharma and compiling a deb with the 0.9.0 build files.  Everything working perfectly now.

---

