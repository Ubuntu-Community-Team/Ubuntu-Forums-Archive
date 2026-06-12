---
title: "Mobile Broadband Modem not recognised"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by cesera on 2011-09-26
A friend of mine has a TD-SCDMA/GSM modem, model STD808. She is currently running XP on a very old laptop and has asked me to install lubuntu instead. My problem now is that when I plug the modem into the laptop running the lubuntu live CD it does not appear to be recognised. Is there anyway I can check if this modem works with lubuntu before getting rid of Windows and installing lubuntu properly.

---

### Post by pdc on 2011-09-26
with the modem plugged in;

and lubuntu liveCD running 

.......type

> lsusb

in a terminal (control-alt-t should open a terminal for you);

if you copy and paste the ID of the modem, we can check it out;

if the modem gives you an icon on the desktop for lubuntu;

if you right-click; and select EJECT; that may change the ID of the modem so it is now recognised...................does that help?

---

### Post by cesera on 2011-09-27
lubuntu does not give me an icon on the desktop, but then again, nor does it when I plug in a USB stick, then it just asks if I want to open it with file manager, but even that doesn't happen with the modem.

lsusb and dmesg don't look hopeful. :-(

```
$ lsusb
...
Bus 003 Device 002: ID 21f5:3010
...

$ dmesg|grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.209253] 00:0a: ttyS0 at I/O 03xf8 (irq = 4) is a NS16550A
```I also did the following:
```
$lsusb -vs 003:002

Bus 003 Device 002: ID 21f5:3010  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x21f5 
  idProduct          0x3010 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Connection timed out (110)
```

---

### Post by cesera on 2011-10-01
Bump

---

### Post by drdos2006 on 2011-10-01
Check this thread out. It may help.

[http://ubuntuforums.org/showthread.php?t=1193355](http://ubuntuforums.org/showthread.php?t=1193355)

regards

---

### Post by pdc on 2011-10-01
the threads I found when I looked were mainly in chinese script;

eg

[http://translate.google.com/translate?hl=en&sl=zh-CN&u=http://www.linuxsir.org/bbs/thread376990.html&ei=NNaGTqaoF-GZiAfkvZyyDw&sa=X&oi=translate&ct=result&resnum=6&ved=0CEwQ7gEwBQ&prev=/search%3Fq%3Dubuntu%2B21f5:3010%26hl%3Den%26biw%3D1920%26bih%3D874%26prmd%3Dimvns](http://translate.google.com/translate?hl=en&sl=zh-CN&u=http://www.linuxsir.org/bbs/thread376990.html&ei=NNaGTqaoF-GZiAfkvZyyDw&sa=X&oi=translate&ct=result&resnum=6&ved=0CEwQ7gEwBQ&prev=/search%3Fq%3Dubuntu%2B21f5:3010%26hl%3Den%26biw%3D1920%26bih%3D874%26prmd%3Dimvns)

the advice there seemed to be to create a udev rule for this device;

(as I don't think it has made it into usb_modeswitch)

so the advice seemed to be .........

> sudo gedit / etc / udev / rules.d/70-modem.rules

copy and paste into it

> SYSFS {idVendor} == "21f5", SYSFS {idProduct} == "3010", RUN + = "/ usr / bin / eject / dev / srX" 

save.close.

.............before doing that 

...........test and see if .......

> Eject / dev / srX

works to made the modem be seen

---

### Post by drdos2006 on 2011-10-01
So did you get to this section of the link I gave to you ?

> 
please do some basic tests and supply more info:

Boot without the modem, wait for the system to load, open a terminal window and try:
Code:

ls /dev/ttyU*

attach the modem, wait 15 seconds, try:
Code:

lsusb

and then again:
Code:

ls /dev/ttyU*

The purpose of above is to check VendorID : ProdictID (from lsusb) and see which ports existed or created (ls /dev/ttyU*). If there are no /dev/ttyUSBx ports try:
Code:

sudo modprobe usbserial vendor=0x12d1 product=0x1446

Note: product=0x1446 must be the same as in lsusb command
Above command will try to create the serial communication ports.
Try again:
Code:

ls /dev/ttyU*

Post here all output (copy & paste is better than typing). Be careful with the lower UPPER case of letters: ttyUSB0 is not the same to ttyusb0 (best is to show the full path: /dev/ttyUSB0)ttyUSB0

Which Ubuntu version are you using?


regards

---

### Post by pdc on 2011-10-01
hi drdos;

when George Vita made post #3 in June 2009, he was (I think) giving specific advice on a Huawei modem;

with an ID (in that post); (before switching) of:

> **12d1:1446**

eg in usb_modeswitch it is described as

> # **Huawei, newer modems**
ATTRS{idVendor}=="**12d1**", ATTRS{idProduct}=="**1446**", RUN+="usb_modeswitch '%b/%k'"

the way I see it, the device in this thread has an ID of

> **21f5:3010**

........so I think it is made by a different manufacturer;

so we seem to me to have already been supplied with the lsusb and the 

> dmesg | grep tty

information 

> dmesg|grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.209253] 00:0a: ttyS0 at I/O 03xf8 (irq = 4) is a NS16550A

that (to me) suggests the device is still only seen as a virtual CD-ROM device

if cesera tried

> sudo modprobe usbserial vendor=0121f51 product=0x3010

that might be useful;

there certainly seems very little around on the internet about this device;

---

### Post by cesera on 2011-10-05
Thank you for all your help. Unfortunately my friend had her bag, with the USB device in it, stolen yesterday. So I won't be able to try this.

I have told her I will see if I can help her buy a new device that works for Linux out of the box.

Once again, thank you very much for all your help.

---

### Post by pdc on 2011-10-05
look out for a good Huawei (Made in China!)

---

