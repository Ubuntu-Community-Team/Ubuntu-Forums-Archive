---
title: "SoundGraph imon - MCE Remote &amp; MCE Keyboard"
date: 2009-05-29
forum: Mythbuntu
---

### Post by roundhay on 2009-05-29
I am using mythbuntu 8.10 and have been happily using the Microsoft MCE remote and the receiver that came with it for the last few months. As I had a separate IR receiver and there was a IR receiver in the SoundGraph imon I could not get the MCE remote at start up. To solve this I followed the instruction in the following thread:

[http://ubuntuforums.org/showthread.php?t=892647&page=2](http://ubuntuforums.org/showthread.php?t=892647&page=2)

This uses udev to separte the MCE USB reciever from the iom reciever

Basically you would use :-
sudo udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)
sudo udevinfo -a -p $(udevinfo -q path -n /dev/lirc1)

to find unique differences between the lirc devices and then get udev to create a consistent symlink

Now that I am happy that I have a working system I have decided that it is time to try and get the LCD of the imon working and the MCE keyboard. I followed the following threads (my imon is the 15c2:ffdc version)

1. MCE Keyboard
[http://ubuntuforums.org/showthread.php?t=782889&highlight=mce+keyboard](http://ubuntuforums.org/showthread.php?t=782889&highlight=mce+keyboard)

Success!! The MCE Keyboard works.....

2. LCD & LCDproc 
[http://ubuntuforums.org/showthread.php?t=1069267](http://ubuntuforums.org/showthread.php?t=1069267)
I only followed the first part to get the LCD working

Success!! The LCD now displays info and I have mythtv communicating with it

Problem - The MCE Remote no longer works!

I have read a lot of threads on various forums and blogs but I have found one which explains how to get all three of these working. Can anyone help?

---

### Post by roundhay on 2009-05-30
Here are some logs which might help sort out this issue?

ls -la /dev/lirc
> crw-rw---- 1 root root 61, 0 2009-05-30 11:00 /dev/lirc0
crw-rw---- 1 root root 61, 1 2009-05-30 11:00 /dev/lirc1
lrwxrwxrwx 1 root root     5 2009-05-30 11:00 /dev/lirc101 -> lirc0
srw-rw-rw- 1 root root     0 2009-05-30 11:00 /dev/lircd

dmesg |grep lirc
> [   11.594664] lirc_dev: IR Remote Control driver registered, major 61 
[   11.685750] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   11.685752] lirc_imon: Venky Raju <dev@venky.ws>
[   11.686160] lirc_imon: imon_probe: found IMON device
[   11.686163] lirc_dev: lirc_register_plugin: sample_rate: 0
[   11.686210] lirc_imon: imon_probe: Registered iMON plugin(minor:0)
[   11.686265] lirc_imon: imon_probe: iMON device on usb<1:4> initialized
[   11.686280] usbcore: registered new interface driver lirc_imon
[   11.826703] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.1.5
[   11.826706] lirc_mod_mce: Florian Demski
[   12.516262] lirc_dev: lirc_register_plugin: sample_rate: 0
[   12.553242] lirc_mod_mce[2]: Philips eHome Infrared Transceiver on usb6:2
[   12.553277] usbcore: registered new interface driver lirc_mod_mce
[   12.568068] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   12.568070] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   12.576114] usbcore: registered new interface driver lirc_mceusb2
[   33.410535] lirc_imon: VFD port opened
[   64.895136] lirc_imon: IR port opened
[   87.192023] lirc_imon: IR port closed
[  675.448772] usbcore: deregistering interface driver lirc_mceusb2
[  682.668568] lirc_imon: IR port opened
[  705.708342] lirc_imon: IR port closed
[  890.970650] lirc_imon: IR port opened
[  914.328598] lirc_imon: IR port closed


lsusb
> Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mode2
> mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

---

