---
title: "rt2500 - usb wlan not recognized"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by mogliii on 2006-07-09
Hi,

I have Xubuntu Dapper installed on an rather old mobile computer

NEC VersaPro VA80J
Pentium III 650 Mhz, 128 mb RAM ...

The build in ethernet works fine, but I also want to get an USB wlan stick to work.

========
usb:
Bufallo Air Station G54
WLI-U2-KG54-YB (only sold in Japan)
chipset: RaLink rt2500 (found that on 3 different pages, so i believe it)
========

I have read some threads and wikis about the rt2500. But all are about getting wpa running. And it is always said, that rt2500 runs out of the box in dapper.

But for me it does not. I still have only modem and eth0. Even booting with xubuntu live cd with the stick plugged in didnt make it show.

So I would like to ask how to get it running.

=====================
Here some other information:
```
$ sudo lsusb -v
....
Bus 001 Device 004: ID 0411:005e MelCo., Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0411 MelCo., Inc.
  idProduct          0x005e
  bcdDevice            0.01
  iManufacturer           1 Buffalo
  iProduct                2 WLI-U2-KG54-YB
  iSerial                 3 000D0BA56A06
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
```

and 
```
$ sudo lspci -v
```
does not give any information about any usb wlan thing

also in network setting there is nothing

---

### Post by kingcharles1666 on 2006-07-10
mogliii,

I had the same problem with my philips usb wifi on Xubuntu with an old system. perhaps because it has no usb2.0 it does not recognise it when you plug it in, not sure.
I had to install ndiswrapper and use the win drivers before it showed up
after that no problem other than the connection drops from time to time and I have to reset the wlan0 to get it back up. Bit annoying but at least it works most of the time. BTW I am using WPA for security.


have you tried ndiswrapper?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Charles

---

### Post by peterthewolf on 2006-07-10
My usb was rt73 not rt2500 but I only found out via this post

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=11799#11799](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=11799#11799)

perhaps they could help you too.

---

### Post by mogliii on 2006-07-10
Hi,

thanx for the reply.

USB 2.0 seems not to be the problem. Have another computer with same ubuntu and usb 2.0 and its also not recognized...
And also i have an pcmcia usb 2.0 card and with the old mobile computer, the usb 2.0 card and the wlan dongle it still doesnt work.

I will post an inquiry on that project site. But I'm still thinking. The point is, that its not my computer, but rather of a sweet japanese girl :cool: 

So maybe it would be a better idea to buy an other usb stick that works well without any ndiswrapper. (~3000 Yen, 30 $, 20 €)
If it was my system, i wouldnt care about restarting the network device. But I think its not good for somebody I try to convert from windows to linux...

And if the driver (as its open source) improves, it will maybe work in the next ubuntu release or I can sell it to an windows user?!?

But if anyone has an other good hint, just tell me. I'm happy about any comment.

---

### Post by mogliii on 2006-07-11
I just found a list for wlan devices officially recommended for linux:

[https://www.fsf.org/resources/hw/net/wireless/cards.html]("https://www.fsf.org/resources/hw/net/wireless/cards.html")

There is a Buffalo WLI-U2-KG54-**_AI_** but not my -YB.

I suppose that the -YB is only slightly different, and this difference is not implemented in the driver.

So I will buy the other buffalo today and try it. Should it still not work, then I will just give it back and try another one :)

See also here: The -YB is not officially in the list for the rt2500 devices:
[http://ralink.rapla.net/]("http://ralink.rapla.net/")

---

### Post by mogliii on 2006-07-11
Hi,

just bought the buffalo WLI-U2-KG54-AI and its recognized as rausb0!!!

So now there should be no more problem with it. And if wpa (how can I test it without an router?) doesnt work, I can follow the many HOWTOs.

Conclusion:

- solved by financial workaround :)
- Buffalo WLI-U2-KG54-YB does not work with ubuntu (2.6.15-25)
I guess its just a special product. There is also a writing on it: YAHOO! BB JAPAN
lets just forget about it...

---

### Post by mogliii on 2006-07-19
Hi,

just wanted to post that the WLI-U2-KG54-AI works with the rt2570 driver from the [serialmonkey page]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads").

I successfully connected with an wep protected network. wpa not tested


Howto I used is [http://www.ubuntuforums.org/showthread.php?t=106846]("http://www.ubuntuforums.org/showthread.php?t=106846")

Thx for everybodys effort

---

### Post by Jongkwan on 2006-11-07
I use WLI-U2-KG54-AI, too.

But, my linux box recognize the network card as both storage device and keyboard.

I found out it through "dmesg | more" command.

[COLOR="Navy"]Result 1:[/COLOR]
[17179600.432000] SCSI subsystem initialized
[17179600.460000] Initializing USB Mass Storage driver...
[17179600.464000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179600.464000] usb-storage: device found at 3
[17179600.464000] usb-storage: waiting for device to settle before scanning
[17179600.464000] usbcore: registered new driver usb-storage
[17179600.464000] USB Mass Storage support registered.
[17179605.288000] ACPI: Power Button (FF) [PWRF]
[17179605.288000] ACPI: Power Button (CM) [PWRB]
[17179605.464000]   Vendor: BUFFALO   Model: WLI-U2-KG54-CD    Rev: 1.00
[17179605.464000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17179605.468000] usb-storage: device scan complete

[COLOR="Navy"]Result 2:[/COLOR]
[17179930.408000] input: BUFFALO WLI-U2-KG54-AI as /class/input/input4
[17179930.408000] input: USB HID v1.00 Keyboard [BUFFALO WLI-U2-KG54-AI] on usb-0000:00:10.3-4

I checked the status using "sudo lsusb -v | less".

================
Bus 004 Device 007: ID 0411:006d MelCo., Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0411 MelCo., Inc.
  idProduct          0x006d
  bcdDevice            1.15
  iManufacturer           1 BUFFALO
  iProduct                2 WLI-U2-KG54-AI
  iSerial                 3 000D0B9F7206
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
=======================

Guys, what can I do next in order to make my linux box recognize it properly?

---

### Post by mogliii on 2006-11-07
There is a small switch you have to change. Look carefully at the side of your stick.

The Stick has integrated flash memory with the driver, and the keyboard is a workaround for win98.

Maybe you will need a thin, sharp tool to change the position of the switch.

Hope it helps

---

### Post by Jongkwan on 2006-11-13
Thank you very much.

Your advice works.

Still, my linux box has been unexpectedly downed since wireless networking was esblished (by myself).

Anyway, thanks all.

---

