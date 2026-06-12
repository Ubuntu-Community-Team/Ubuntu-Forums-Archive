---
title: "lirc and mceusb"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by newlinux on 2007-01-11
Trying to install lirc with mceusb following [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy).

When I get to the step to test with irw. it just returns the prompt. Tried rebooting and restarting lirc and reloading the lirc_mceusb module. no luck. 

relevant dmesg:

```

[17179596.168000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179596.168000] lirc_mceusb: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179596.168000] usbcore: registered new driver lirc_mceusb
[17179596.168000] /usr/src/modules/lirc/drivers/lirc_mceusb/lirc_mceusb.c: USB Microsoft IR Transceiver Driver v0.2

```

I'm guessing it has something to do with the second line.

any suggestions?

This is my first crack at lirc. I was hoping to use my harmony 680 to learn my IR keyboad, but it doesn't seem to learn the ACK-581 keypresses properly, so off to lirc...

---

### Post by newlinux on 2007-01-12
bump... I know some mythtv guy out there has to have had this problem before... I'm so close, just need a remote control to work...

---

### Post by the Goat on 2007-01-13
I'm having the same problem trying to get lirc working with my serial port ir blaster.  Here is the dmesg output from lircd
```

[17179609.872000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179609.884000] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179610.892000] lirc_serial: auto-detected active high receiver
[17179610.892000] lirc_dev: lirc_register_plugin: sample_rate: 0

```

---

### Post by newlinux on 2007-01-13
It turned out for me the problem was two fold. First I wasn't using the right module. I needed to be using lirc_mceusb2, not lirc_mceusb.  When I tried to switch, rebuild and everything, it never could find the module lirc_mceusb2 (even though I know I selected it for building). I ended up searching for lirc_mceusb2.ko, found it and copied into the kernel module directory (/lib/modules/2.6.17-10-generic/misc/lirc_mceusb.ko). So are you stuck on the irw readin step, and you get the same behavior I did?

---

