---
title: "Error in Compiling Third Party Modem Driver"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by abhijit_boro on 2010-09-04
I am trying to compile a third-party USB Modem Driver ZTE AC8710 Ubuntu 9.10 ([FONT=Calibri]linux-headers-2.6.31-14-generic)[/FONT] from the source code provided inside their windows installation cd. As directed in Redame file, I have changed the makefile to point to the correct linux source header files. 

However I am geting the following compilation errors:
 
[FONT=Batang][SIZE=3]abhijit@LENOVO:~$ cd linux[/SIZE][/FONT]
[FONT=Batang][SIZE=3]abhijit@LENOVO:~/linux$ make[/SIZE][/FONT]
[FONT=Batang][SIZE=3]make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/abhijit/linux modules[/SIZE][/FONT]
[FONT=Batang][SIZE=3]make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'[/SIZE][/FONT]
[SIZE=3][FONT=Batang]  CC [M]  /home/abhijit/linux/usb-serial.o[/FONT][/SIZE]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c: In function ‘destroy_serial’:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:159: error: ‘struct usb_serial_driver’ has no member named ‘shutdown’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:165: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c: In function ‘serial_open’:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:246: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:251: error: ‘struct usb_serial_port’ has no member named ‘tty’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:253: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:265: warning: passing argument 1 of ‘serial->type->open’ from incompatible pointer type[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:265: note: expected ‘struct tty_struct *’ but argument is of type ‘struct usb_serial_port *’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:265: warning: passing argument 2 of ‘serial->type->open’ from incompatible pointer type[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:265: note: expected ‘struct usb_serial_port *’ but argument is of type ‘struct file *’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:265: error: too few arguments to function ‘serial->type->open’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:276: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:278: error: ‘struct usb_serial_port’ has no member named ‘tty’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c: In function ‘serial_close’:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:357: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:371: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:372: error: ‘struct usb_serial_port’ has no member named ‘open_count’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:375: error: too many arguments to function ‘port->serial->type->close’[/SIZE][/FONT]
[FONT=Batang][SIZE=3]/home/abhijit/linux/usb-serial.c:377: error: ‘struct usb_serial_port’ has no member named ‘tty’[/SIZE][/FONT]
 
I am searching the net for the solution but to no avail. Am I missing a patch or some other package that needs to be present for the compilation to be successful? Please help

---

