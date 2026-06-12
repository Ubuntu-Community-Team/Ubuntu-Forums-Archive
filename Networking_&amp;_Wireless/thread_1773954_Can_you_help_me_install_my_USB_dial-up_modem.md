---
title: "Can you help me install my USB dial-up modem?"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by doctorbighands on 2011-06-02
I've done everything I can find, and it feels like the installation is perpetually half-done.

An lsusb reveals that I have the following:
```
Bus 002 Device 002: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem

```

I've tried to follow the Dialup HowTo in the Ubuntu docs, I tried installing linmodem drivers, and I just can't seem to get there. I'd really like to get this device up and running with efax-gtk, but I'm stuck.

I'm not sure what info I can provide that might be helpful, so let me know what you need, and I'll happily post it.

Help!

EDIT:
If it helps, efax-gtk gives me the following message at startup:
```
No serial port device specified in efax-gtkrc configuration file
and /dev/modem does not exist
```

---

### Post by happy_heyoka on 2011-06-03
Try viewing your kernel log just after you plug in the device.
From the console you can also do this immediately after you plug it it in:

**[FONT=Courier New][SIZE=2]dmesg | grep usb[/SIZE][/FONT]**

I'm guessing your device *won't* be /dev/modem... more likely /dev/ttyXXX

try these to track it down:

x@x:~$ **[FONT=Courier New][SIZE=2]ls -l /dev/serial/by-path[/SIZE][/FONT]**
total 0
lrwxrwxrwx 1 root root 13 2011-06-03 14:33 pci-0000:00:1d.7-usb-0:1.4:1.6 [COLOR=Red]-> ../../ttyACM0[/COLOR]
x@x:~$ **[FONT=Courier New][SIZE=2]ls -l /dev/serial/by-id[/SIZE][/FONT]**
total 0
lrwxrwxrwx 1 root root 13 2011-06-03 14:33 usb-Nokia_N900__PC-Suite_Mode_-if06 [COLOR=Red]-> ../../ttyACM0[/COLOR]

These two examples show how my phone (pretending to be a modem) is mapped to /dev/ttyACM0 via a couple of aliases.

With this info you should be able to set the configuration for your fax software.

If you plan to have more than one 'modem' device plugged in at any given time, you might need to get more elaborate with the device path to specifically point to a particular modem.

---

