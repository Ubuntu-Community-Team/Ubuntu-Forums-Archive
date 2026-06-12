---
title: "USB serial cable to change channels is it possible?"
date: 2009-05-04
forum: Mythbuntu
---

### Post by phroman on 2009-05-04
Just go ahead and skip down to post 4.

---

### Post by tgm4883 on 2009-05-04
I know for a fact the patterson cables work with directv H20 boxes.  Work great here.

---

### Post by phroman on 2009-05-04
Sweet, thanks.  My ASUS P5Q mobo has a serial port header but it didn't come with the actual adapter, so I ordered one.  I'll try my old nullmodem/iogear adapters for the hell of it, but that USB to USB cable would be the best thing in the world right now.  Cheers!

---

### Post by phroman on 2009-05-05
Update: I bought the USB Null cable from FTDI CHIP, link here:  [http://apple.clickandbuild.com/cnb/shop/ftdichip?op=catalogue-products-null&prodCategoryID=73&title=USB+NMC-2.5m]("http://apple.clickandbuild.com/cnb/shop/ftdichip?op=catalogue-products-null&prodCategoryID=73&title=USB+NMC-2.5m")
Its USB on both ends with some kind of chip in it to handle the serial conversion. Anyone know if this sort of trickery will work? It looks to me like the biggest area of trouble with home dvr is remotes and stb control, at least from my time on the forums here and when I was trying beyond tv. Maybe a cable like this could solve a lot of headaches...  
I'm hoping to use this with my Direct TV HR21-100 STB.  I'll just show the important stuff from the cable's info page below:  

> Each of the USB sockets conceal a small PCB with a FT232RQ based USB-UART converter IC plus support components inside. The interconnect cable cross-connects the TXD / RXD data signals, RTS / CTS handshaking signals and interconnects the common GND reference rail betwen the two converter PCBs.  When used together with FTDI&#8217;s supplied Virtual COM Port ( VCP ) drivers, the USB NMC cable may be used to establish inter-PC COM Port based communication at baud rates of up to 3M baud.

How much potential does this have?  No more ir blaster stuff, just plug in a USB cable and go!  I currently have a functioning Firefly remote, and a USB UIRT2 blaster occasionally working, it's extremely intermittent.  Sometimes it works in one place, then it doesn't.  So, I'm posting relevant cuts from my working setup from dmesg, lsusb and ps aux | grep lirc. Hoping to show the difference from after I plug in the USB null cable.  

```
dmesg | grep -i usb         using firefly and usbuirt

[    6.288047] USB Serial support registered for FTDI USB Serial Device
[    6.288112] ftdi_sio 7-2:1.0: FTDI USB Serial Device converter detected
[    6.288141] usb 7-2: Detected FT232BM   >> This is my UIRT2<<
[    6.288184] usb 7-2: FTDI USB Serial Device converter now attached to ttyUSB0
[    6.288207] usbcore: registered new interface driver ftdi_sio
[    6.288208] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver


lsusb          using firefly and usbuirt
 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 008 Device 002: ID 0c16:0001 Gyration, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0403:f850 Future Technology Devices International, Ltd   >>This is my UIRT2<<
Bus 007 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)

 ps aux | grep -i lirc      using firefly and usbuirt

ps aux | grep lirc
root      1639  0.0  0.0   3116   684 ?        S<s  18:23   0:00 /usr/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd --listen
root      1671  0.0  0.0   3164   768 ?        S<s  18:23   0:00 /usr/sbin/lircd --driver=uirt2_raw --device=/dev/lirc1 -d /dev/ttyUSB0 --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd1.pid
joe       4148  0.0  0.0   3336   788 pts/0    R+   18:27   0:00 grep lirc
```

Turn of PC, unplug the USB UIRT2, plug in the USB Null cable, restart.  The ONLY differences are this:  In dmesg, it shows up as FT232RL, where the USB UIRT2 shows up as FT232BM.  And, in lsusb, it shows up with Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC.   The USB UIRT2 only shows up as Future Technology Devices International, Ltd.  Those are the only differences I can see.  I'm using all the same lirc settings that I use for the USB UIRT2, except I'm plugging in this USB - USB Null cable instead.   

At the terminal I try: irsend -d /dev/lircd1 SEND_ONCE USB_UIRT2 guide 

I get no error, it just goes back to a prompt, but it does not bring up my guide, if I try the same command again, I get:
                               
```
irsend: could not connect tosocket
irsend: Connection refused
```

I can restart lirc, and the same thing again.  Here is my lirc log file from syslog:

```

May  6 09:16:45 mediaserver lircd-0.8.4a[1672]: accepted new client on /dev/lircd1
May  6 09:16:46 mediaserver lircd-0.8.4a[1672]: uirt2_raw: did not receive results
May  6 09:16:47 mediaserver lircd-0.8.4a[1672]: uirt2_raw: did not receive results
May  6 09:16:47 mediaserver lircd-0.8.4a[1672]: uirt2_raw: No UIRT2 device found at /dev/ttyUSB0
May  6 09:16:47 mediaserver lircd-0.8.4a[1672]: Failed to initialize hardware
May  6 09:16:47 mediaserver lircd-0.8.4a[1672]: select() failed
May  6 09:16:47 mediaserver lircd-0.8.4a[1672]: Bad file descriptor 
May  6 09:16:47 mediaserver lircd-0.8.4a[1640]: removed client
```

Is this an issue with Lirc? I have not loaded the drivers supplied with the cable, as their website only shows instructions/support for driver install for windows.  When I emailed them to ask about Linux, I got this response:
  

> Do not install anything the driver is already there as part of the kernel.
You should see the device (when plugged in) in the /dev folder as a ttyUSBx device.

 Well, that does happen, but, obviously, no joy.  What's the difference between FT232RL and FT232BM?  Why is lirc resetting after trying to send with no error?  It's the holy grail guys, Thoughts?


Further notes:

Taken from Direct TV Manual:  

> Data Ports:  STB Model: HR21  Type of Data Port Conector:  USB  data Rate:  Baud 9600
All new Direct TV STBs have USB 2.0 data ports.  The STB USB port has a host configuration.  Serial comands are interfaced through the data port using a USB-Serial adapter.  The jfollowing RS-232 compatabile serial port adapters will be supported.  

Manufacturer:            Model:              USB Vendor ID:                 USB Product ID:
IOGEAR		GUC232A		0x067B			0x2303
ATEN			UR-232A		0x067B			0x2303
BAFO			BF-810		0x067B			0x2303

The USB port on most STBs support hot-plug.  Than means USB ports will work any time when a USB-serial adapter is plugged in.  Only the HR20 and HR21 USB ports work differently.  The USB-serial adapter mush be plugged before the STB is booted.  If the USB connector is plugged in when the STB is running, it must be reset.  All STBs have a default baud rate of 9600.  The data format is 1 start bit, 8 data bits, no parity, 1 stop bit, and no handshaking.


Help!
:guitar:

---

### Post by phroman on 2009-05-05
I emailed Christof Bartelmus from Lirc asking him about this cable, his response was: 

> I don't think this is possible with LIRC.

Ugh..  Anyone feel like proving him wrong?

---

