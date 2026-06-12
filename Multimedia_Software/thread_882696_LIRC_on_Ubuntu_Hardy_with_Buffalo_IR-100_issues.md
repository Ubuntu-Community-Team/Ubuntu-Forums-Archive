---
title: "LIRC on Ubuntu Hardy with Buffalo IR-100 issues"
date: 2008-08-07
forum: Multimedia Software
---

### Post by ktsui on 2008-08-07
I defer to the knowledge of the masses...

I'm trying to control a robot via IR using a Buffalo IR-100 on a Ubuntu Hardy machine. I seem to be having some disconnect between LIRC and the serial port, as I can't actually send the ir commands through my serial port using LIRC.

Here's what I've done:
*sudo apt-get install lirc lirc-modules-source*, which also got setserial. When the configuration screen pops up, I set remote and transmitter to custom.

*sudo setserial /dev/ttyS1 uart none* to release the serial port from Ubuntu's control, then *sudo modprobe lirc_dev*. /dev/lirc0 now appears. *sudo modprobe lirc_serial*.

dmesg shows:
[16534.441637] lirc_dev: IR Remote Control driver registered, major 61 
[16562.802901] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.        **IS THIS AN ISSUE????**  
[16617.808461] lirc_serial: auto-detected active high receiver
[16617.808470] lirc_dev: lirc_register_plugin: sample_rate: 0

/var/log/messages shows:
Aug  6 14:31:35 sugaree kernel: [  101.860586] lirc_dev: IR Remote Control driver registered, major 61 
Aug  6 14:31:35 sugaree kernel: [  101.870469] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.             **IS THIS AN ISSUE????**
Aug  7 08:19:55 sugaree kernel: [16617.808461] lirc_serial: auto-detected active high receiver
Aug  7 08:19:55 sugaree kernel: [16617.808470] lirc_dev: lirc_register_plugin: sample_rate: 0


*sudo lirc -d /dev/lirc0* and /dev/lircd now appears.

*irsend LIST "" ""* will list the remotes shown in /etc/lirc/lircd.conf. Right now I have one entry for NEC, and two Apple remotes that should work with my Macbook.

As I understand it, lirc_serial is build for COM0. However, without specifying options in /etc/modprobe.d/lirc_serial, it doesn't know what to do. I've tried both COM0 (alias char-major-61 lirc_serial
options lirc_serial irq=4 io=0x3f8) and COM1 (options lirc_serial irq=3 io=0x2f8). (Currently I'm using COM1.)

The issue right now is that I can't get any data to flow through the serial port. There is an LED on the blaster box which does show when data is coming through. I checked this when COM1 was under Ubuntu's control (before I used setserial) with *echo 1 > /dev/ttyS1* and the LED blinked. The Buffalo IR-100 simply replicates the received signal across 4 IR LEDs, but as of right now, it doesn't receive any signals from LIRC using irsend. Also, once I use setserial with COM1, then I can't cat /dev/ttyS1 to see what's being sent; this produces an input/output error (makes sense since it's no longer under Ubuntu's control).

I've replicated this process on another Ubuntu machine with exactly the same results. I must be missing a step in the process. I just don't know where I'm going wrong or what I'm missing. I've tried all the usual places (dmesg, /var/log/messages).

Any help is much appreciated.

Thanks!
Kate

---

