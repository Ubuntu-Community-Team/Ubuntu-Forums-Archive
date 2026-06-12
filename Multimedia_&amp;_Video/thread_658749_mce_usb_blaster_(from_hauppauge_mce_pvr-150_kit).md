---
title: "mce usb blaster (from hauppauge mce pvr-150 kit)"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by columbo on 2008-01-05
Hi guys,

My problem is that I am not able to have a working ir blaster.

Here are the info:

os: kubuntu 7.10 (gutsy)
kernel: 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

mce usb ir receiver with ir1 and ir2 "holes". I plug the blaster in ir1 (I have aslo
tried in ir2 with no success)

from dmesg:
[   32.083173] lirc_dev: IR Remote Control driver registered, at major 61
[   32.087464]
[   32.087465] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   32.087468] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>


from lsusb:Bus 005 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 002: ID 1784:0001
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Strange, nothing from lsusb refer to the IR device?

irw detect correctly all the buttons on my remote.

My problem is with irsend:

irsend SEND_ONCE blaster 2
irsend: command failed: SEND_ONCE blaster 2
irsend: transmission failed

The code for the blaster are entered in /etc/lirc/lircd.conf:

begin remote

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
    name 0
    4718592
    name 1
    4718593
    name 2
    4718594
    ...
   end raw_codes
end remote   

lircd daemon is runnig (ps -ef):
root     /usr/sbin/lircd --device=/dev/lirc0


lsmod | grep lirc
lirc_mceusb2           14980  0
lirc_dev               15860  1 lirc_mceusb2
usbcore               138632  4 lirc_mceusb2,ehci_hcd,uhci_hcd


ll /dev/lirc*
srw-rw-rw- 1 root root     0 2008-01-04 23:30 /dev/lircd
crw-rw---- 1 root root 61, 0 2008-01-04 23:30 /dev/lirc0


I have only installed lirc with: apt-get install lirc
No compilation. 

I understand that the lirc_mceusb2 from gutsy should be able to 
drive the blaster. I am correct?

Any help would be appreciated.

Thanks

---

### Post by nola504 on 2008-02-11
Were you able to figure this out?

I have the same exact problem and have searched all over and can't find a solution.  No matter what I do I get the same error you're receiving below.

Tried re-running the Gutsy remote control setup and no luck.

Please post back if you've found a solution.

---

