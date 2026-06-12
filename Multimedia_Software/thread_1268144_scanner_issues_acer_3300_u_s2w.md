---
title: "scanner issues: acer 3300 u s2w"
date: 2009-09-16
forum: Multimedia Software
---

### Post by Sprawn! on 2009-09-16
In ubuntu 9.04. I can't get my scanner to work. It is an acer 3300u. I have followed instructions from a variety of sources and done the following:

sudo mkdir /usr/share/sane/snapscan
moved u176v046.bin into the usr/share/sane/snapscan directory
chmod 777 u176v046.bin

modified etc/sane.d/snapscan.conf with the line:
firmware /usr/share/sane/snapscan/u176v046.bin

in snapscan.conf, I also pointed to the device:

/dev/usb/scanner0 bus=usb is their suggestion, and does nothing
/dev/bus/usb/006/002 didn't work
/dev/bus/usb/006/002 bus=usb doesn't work.

I created a 'scanner' user group and added my username to it, as suggested elewhere. Now, I don't know how or IF I should undo that.

sane-find-scanner FINDS the scanner and reports:

found usb scanner (vendor=0x04a5, product=0x20de) at libusb:006:004

Changing the snapscan.conf file to reflect the current usb does nothing.

Changing the permissions on the usb "file" does nothing.

I've tried quite a lot of things... and nothing works. The scanner worked on my girfriends computer running 8.04 yesterday, but now I am getting the same errors!

It's driving me batty...

---

