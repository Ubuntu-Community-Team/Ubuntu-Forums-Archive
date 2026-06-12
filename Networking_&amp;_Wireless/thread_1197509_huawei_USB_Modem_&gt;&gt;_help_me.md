---
title: "huawei USB Modem &gt;&gt; help me"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by Gladiator-prog4me on 2009-06-26
hello

please help me to install USB Modem

on dell M1530

this the modem :
huawei mobile broadband
model : E1550

thank you

---

### Post by GeorgeVita on 2009-06-26
Hi **Gladiator-prog4me**,
you can read, try and collaborate with other users manage to connect it at:
[http://ubuntuforums.org/showthread.php?t=1193355](http://ubuntuforums.org/showthread.php?t=1193355)

Regards,
George

---

### Post by Gladiator-prog4me on 2009-06-26
> **GeorgeVita said:**
> Hi **Gladiator-prog4me**,
you can read, try and collaborate with other users manage to connect it at:
[http://ubuntuforums.org/showthread.php?t=1193355](http://ubuntuforums.org/showthread.php?t=1193355)

Regards,
George

thank you a lot 

but i can't understant this theard !

so please can you tell me step by step  ?

---

### Post by farbird on 2009-06-27
did u manage to install usb_modeswitch yet?

---

### Post by Gladiator-prog4me on 2009-06-27
> **farbird said:**
> did u manage to install usb_modeswitch yet?

thank you for your reply

and i install usb_modeswitch

---

### Post by Gladiator-prog4me on 2009-06-27
you can see that : 


mohamed@mohamed-laptop:~$ lsusb
[COLOR="Red"]Bus 002 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd.[/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp.
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp.
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by farbird on 2009-06-29
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

how to install..

if u downloaded the [modeswitch]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.2.tar.bz2") file into your desktop

run "terminal"
"cd ~/Desktop"
"sudo mv usb_modeswitch-1.0.2.tar.bz2 /usr/src"
"cd /usr/src"
"sudo tar -xvf usb_modeswitch-1.0.2.tar.bz2"
"cd usb_modeswitch-1.0.2.tar.bz2"
"sudo make clean"
"sudo make install"

that will get your usbmodeswitch installed.

next boot into windows
download the [sniffusb exe]("http://www.pcausa.com/Utilities/UsbSnoop/SniffUSB-x86-2.0.0006.zip")

install in xp.
run the sniffusb.
plug in your 12d1:1446 stick

now in the sniffusb screen, click on the "list device not present"
you shd see 3-4 devices with the id 12d1:1446

select them all and click on "install" under "filter control" on rightside.

u shd see in the main top window that the 3-4 devices with 12d1:1446 have the "filter installed" beside their id.

now, unplug the huawei usb and plug it back in after 5seconds.
if u do that, u shd see the log file size increased.

now view the log and save the logfile into a thumbdrive.

now we restart XP and boot into ubuntu. remove the stick before ubuntu starts booting.

once ubuntu starts. plug in the thumb drive, copy the log file into your desktop.

then run terminal

"cd ~/Desktop"
"sudo gedit snifflog.log"   or whatever filename u saved before

once gedit opens up on the gnome desktop, look for this by Control-F
"TransferBufferMDL"

there should be about 8 instances of it within the log file.
the one critical is the one that appears 4 rows after the line
```
PipeHandle           = 88bced1c [**endpoint 0x00000005**]
  TransferFlags        = 00000000 (USBD_TRANSFER_DIRECTION_**OUT**, ~USBD_SHORT_TRANSFER_OK)"
```

important here is the "out".
And there must be 2 long row of numbers below the transfermdl line which looks like this
```

   00000000: 55 53 42 43 90 4e d6 8a 24 00 00 00 80 00 08 ff
   00000010: 02 44 45 56 43 48 47 00 00 00 00 00 00 00 00

```
ignore the numbers before the colon and delete the spaces between the hex numbers. Join the 2 lines up so that it shows
```
55534243904ed68a24000000800008ff024445564348470000000000000000
``` 

* take note, this is just an example*

you will also need the "pipehandle" output which will show the endpoint hex, in this example, its **endpoint 0x00000005**.

now with these details, you can then create a usbmodeswitch config file

open another terminal
"sudo gedit /etc/usb_modeswitch.conf"
clear away all the contents of this file. 
put in these lines instead
```

DefaultVendor = 0x12d1
DefaultProduct = 0x1446

MessageEndpoint = 0x05
MessageContent = "55534243904ed68a24000000800008ff024445564348470000000000000000"

```

*make sure you use your own endpoint and messengecontent here n not directly clone the example above.*

now save the file in gedit.

next plug in the huawei usb stick, run terminal

"sudo usb_modeswitch"

u shd then be able to connect after u configure the network settings of your isp [ ie 3g access point name etc ]

there is also a way to automate it.

run terminal again
"sudo gedit /etc/udev/rules.d/45-huawei1660.rules"

gedit shd open an empty file
paste this code into it
```

SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"
```

since your vendor and product id is sames mine, u can clone the code above directly.
However, if u are following this guide to get your own huawei device, not 12d1:1446, working, u shd input the original vendor,product id [ ie the one shown in lsusb before switching]

enjoy

---

