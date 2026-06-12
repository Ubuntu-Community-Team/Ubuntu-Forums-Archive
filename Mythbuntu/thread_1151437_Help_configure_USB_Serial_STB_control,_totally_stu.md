---
title: "Help configure USB Serial STB control, totally stuck"
date: 2009-05-06
forum: Mythbuntu
---

### Post by phroman on 2009-05-06
UPDATE, go ahead and just read post #2, thanks.

---

### Post by phroman on 2009-05-09
New Errors:

I had to re-install mythbuntu today, I'm trying to control my Direct tv HR21-100 box with a null modem serial cable, and serial-usb adapter.  I read this is possible in a mythwiki article here:  [http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial](http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial)

 I'm set up with: Computer >> Null Modem Serial Cable >> USB to Serial Adapter >> HR21-100 STB.  It's an iogear guc232a serial-usb adapter, commonly supported in mythTV.  I got a fresh install up and running with my Firefly remote first.  I manually added the serial transmitter info to my hardware.conf file, which is posted directly below.  And I did follow the Ubuntu User Guide about enabling serial support.  Upon re-boot, my Firefly remote is not working.  I've posted various system checks below.  I came across a post that I cannot find for the life of me now, it talked about x windows maybe using a serial port or something, causing a conflict...  When trying irsend, I get the famous:  

> could not connect to socket, and no such file or directory stuff

Since I did follow the user manual about serial support, I don't understand the error about that in the output of:  sudo dmesg | grep -e serial

EDIT: I ran dkpg-reconfigure lirc, and enabled a Serial UART Directtv ir transmitter (even though I'm not using ir).  I've added the change in results of various system checks at the end of this post. 


  BEFORE RUNNING DPKG-RECONFIGURE LIRC

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream_X10_RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="snapstream/lircd.conf.firefly"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="SERIAL_PORT"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyS0"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```


Here are system checks

```

joe@mediaserver:~/Desktop$ sudo dmesg | grep -e serial 
[    1.272753] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.861242] usbcore: registered new interface driver usbserial
[    3.861259] usbcore: registered new interface driver usbserial_generic
[    3.861260] usbserial: USB Serial Driver core
[    6.974812] tveeprom 0-0050: Hauppauge model 32062, rev B185, serial# 2843044
[   11.858195] lirc_serial: port 03f8 already in use
[   11.858197] lirc_serial: use 'setserial /dev/ttySX uart none'
[   11.858198] lirc_serial: or compile the serial port driver as module and
[   11.858200] lirc_serial: make sure this module is loaded first
joe@mediaserver:~/Desktop$ 


joe@mediaserver:~/Desktop$ sudo ps aux | grep -i lirc
root      1614  0.0  0.0   3116   648 ?        S<s  15:12   0:00 /usr/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd --listen
root      1644  0.0  0.0   3164   744 ?        S<s  15:12   0:00 /usr/sbin/lircd --device=/dev/lirc1 -d /dev/ttyS0 --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd1.pid
joe       4124  0.0  0.0   3340   884 pts/0    S+   15:16   0:00 grep -i lirc
joe@mediaserver:~/Desktop$ 



joe@mediaserver:~/Desktop$ sudo dmesg | grep lirc
[    5.947042] lirc_dev: IR Remote Control driver registered, major 61 
[    6.236360] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
[    6.236361] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[    6.237880] lirc_dev: lirc_register_plugin: sample_rate: 0
[    6.256947] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb7:2
[    6.273964] usbcore: registered new interface driver lirc_atiusb
[   11.858195] lirc_serial: port 03f8 already in use
[   11.858197] lirc_serial: use 'setserial /dev/ttySX uart none'
[   11.858198] lirc_serial: or compile the serial port driver as module and
[   11.858200] lirc_serial: make sure this module is loaded first
joe@mediaserver:~/Desktop$
```

  AFTER RUNNING DPKG-RECONFIGURE LIRC

```
joe@mediaserver:~/Desktop$ sudo dmesg | grep -e serial 
[    1.272753] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.861242] usbcore: registered new interface driver usbserial
[    3.861259] usbcore: registered new interface driver usbserial_generic
[    3.861260] usbserial: USB Serial Driver core
[    6.974812] tveeprom 0-0050: Hauppauge model 32062, rev B185, serial# 2843044


joe@mediaserver:~/Desktop$ sudo ps aux | grep -i lirc
root      2525  0.0  0.0   3116   648 ?        S<s  15:12   0:00 /usr/sbin/lircd --device=/dev/lirc0


joe@mediaserver:~/Desktop$ sudo dmesg | grep lirc

It gave no output at all


```



I'm at a complete standstill at this point.  I know it's a long post, thanks for any help.

---

