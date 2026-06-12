---
title: "Attempting to use ttyUSB"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by Sjeti on 2009-01-16
Alright, I'm writing some code interfacing a motor controller and some other stuff on a computer running Fedora 7.  I know this isn't exactly an Ubunutu, but I figured someone could help me out.


I've got a program that is trying to establish a connection through "/dev/ttyUSB0". I'm actually running a serial hub through, so for all purposes it is acting as a serial connection.  I can read the data coming in and out and through one of the company's programs I can edit some of the data on the motor controller, if I use sudo.

The problem comes with one of their examples.  They have some code that is supposed to create a serial stream so I can send commands via my c++ program using their libraries.  Everything seems to work but I can't create the serial connection, even with the sudo command.  I think this might be an issue with the read-write properties or permissions on the port.

How can I change the permissions on my ports so I don't need to use the sudo command each time?  This shouldn't be a security issue so that isn't a problem.

Any  other suggestions?

---

### Post by jonobr on 2009-01-16
Heres a link that may help,
Scroll to the bottom for non root access,

Hope its of use

[http://www.howtoforge.com/setting_up_a_serial_console](http://www.howtoforge.com/setting_up_a_serial_console)

---

