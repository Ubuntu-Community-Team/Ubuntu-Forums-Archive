---
title: "ir-keytable delay then multiple repeats"
date: 2018-08-26
forum: Multimedia Software
---

### Post by daninca on 2018-08-26
I just upgraded to 18.04 Bionic Beaver and my IR remote is now useless.

What happens is kind of weird.  If I BRIEFLY press a button, I get the expected key, then a pause, then a bunch more keys (exact number varies).  That last bit is the really weird part.  This happens both in mythtv and on the command line.

I have a USB MCE remote.
I've purged every lirc package except liblirc-client0 (a bunch of things depend on that existing).  I know that it's built into the kernel and that may be part of it.  I have ir-keytable installed to control the built in drivers.

I've set the ir-keytable repeat delay and rate to be very slow, but I still get the extra keys.
The ir-keytable seems to see two MCE remotes (but there is only one).

Can anyone help me to get just one key for one button press?
Is only ir-keytable in play here, or do I need the user lirc package?

The MCE remote is pretty common, so I'm guessing that someone has figure this out before.

Thanks,
Dan

Here is everything that I though might be relevant:

```
$ ir-keytable 
Found /sys/class/rc/rc1/ (/dev/input/event4) with:
        Name: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011)
        Driver: mceusb, table: rc-rc6-mce
        lirc device: /dev/lirc1
        Supported protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp 
        Enabled protocols: lirc rc-6 
        bus: 3, vendor/product: 1784:0011, version: 0x0100
        Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
        Name: Nuvoton w836x7hg Infrared Remote Transceiver
        Driver: nuvoton-cir, table: rc-rc6-mce
        lirc device: /dev/lirc0
        Supported protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp 
        Enabled protocols: lirc 
        bus: 25, vendor/product: 1050:00c5, version: 0x0062
        Repeat delay = 999 ms, repeat period = 500 ms

$ lsusb --tree -v
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/9p, 480M
    |__ Port 1: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 3: Dev 3, If 0, Class=Vendor Specific Class, Driver=mceusb, 12M
    |__ Port 5: Dev 4, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
    |__ Port 6: Dev 5, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 6: Dev 5, If 1, Class=Wireless, Driver=btusb, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M

$ dmesg | egrep -i '(lirc|mce)'
[    0.024000] mce: CPU supports 7 MCE banks
[    3.392830] lirc_dev: IR Remote Control driver registered, major 238
[    3.394565] IR LIRC bridge handler initialized
[    3.650296] Registered IR keymap rc-rc6-mce
[    3.721128] lirc lirc0: lirc_dev: driver ir-lirc-codec (nuvoton-cir) registered at minor = 0
[    3.722318] Registered IR keymap rc-rc6-mce
[    3.722692] lirc lirc1: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 1
[    3.904074] mceusb 2-3:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver with mce emulator interface version 2
[    3.904076] mceusb 2-3:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x1 active)
[    3.904117] usbcore: registered new interface driver mceusb

harvey@mediacenter:~/tmp$ lsmod | egrep -i '(lirc|mce)'
mceusb                 32768  0
rc_rc6_mce             16384  0
ir_lirc_codec          16384  0
lirc_dev               16384  3 ir_lirc_codec
rc_core                36864  8 mceusb,ir_rc6_decoder,rc_rc6_mce,ir_lirc_codec,lirc_dev,nuvoton_cir

```

---

### Post by wyliecoyoteuk on 2018-08-27
Long time since I used a remote with a PC, but I am guessing that you need to blacklist the Nuvoton driver module.
in /etc/modprobe.d/blacklist.conf

---

### Post by daninca on 2018-09-21
I blacklisted the Nuvoton, rebooted, and nothing changed.

---

### Post by vidtek on 2018-10-11
Danica-

Check out my how-to.   [https://ubuntuforums.org/showthread.php?t=2403337]("https://ubuntuforums.org/showthread.php?t=2403337")

Any problems, please post, cheers Tony.

---

