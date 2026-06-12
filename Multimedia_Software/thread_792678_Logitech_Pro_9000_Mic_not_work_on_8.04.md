---
title: "Logitech Pro 9000 Mic not work on 8.04"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Sharker on 2008-05-13
Hi, 

i buyed this great webcam of logitech, but i have a problem. Video is great quality but mic don't work correctly on system, skype, ekiga and more. See all debug:

dmesg

 [332962.443069] usb 2-8: new high speed USB device using ehci_hcd and address 12
[332962.680122] usb 2-8: configuration #1 chosen from 1 choice
[332966.647265] Linux video capture interface: v2.00
[332966.651557] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[332966.665584] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:0b.1/usb2/2-8/2-8:1.0/input/input17
[332966.692384] usbcore: registered new interface driver uvcvideo
[332966.692390] USB Video Class driver (SVN r209)

lsusb

Bus 002 Device 012: ID 046d:0990 Logitech, Inc.

arecord -l
**** Lista de CAPTURE Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: AD198x Analog [AD198x Analog]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0
tarjeta 1: U0x46d0x990 [USB Device 0x46d:0x990], dispositivo 0: USB Audio [USB Audio]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0

lsmod | grep uvc
uvcvideo 58376 0
compat_ioctl32 2304 1 uvcvideo
videodev 29440 1 uvcvideo
v4l1_compat 15492 2 uvcvideo,videodev
v4l2_common 18304 2 uvcvideo,videodev
usbcore 146028 14 uvcvideo,snd_usb_audio,snd_usb_lib,ehci_hcd,rndis_host,cdc_ether,usbnet,usblp,hci_usb,usbhid,usb_storage,libusual,ohci_hcd

any ideas?

---

### Post by DutchLoki on 2008-06-21
Hi I have the same camera end no problem. Was your problem solved?

---

### Post by Sharker on 2008-06-21
not, not solved how you working the mic?

---

### Post by DutchLoki on 2008-06-27
> **Sharker said:**
> not, not solved how you working the mic?

I believe the microphone was autodetected on my system. No problem at all with it. Excelent webcam, much beter than anything else and excelent sound from the mic. 

What version of mythBuntu do you use? is it possible you test it under windows xp? possible its the hardware thats not working?

---

### Post by Sharker on 2008-06-27
> **DutchLoki said:**
> I believe the microphone was autodetected on my system. No problem at all with it. Excelent webcam, much beter than anything else and excelent sound from the mic. 

What version of mythBuntu do you use? is it possible you test it under windows xp? possible its the hardware thats not working?

On windows works, and hardware is OK, and on my system autodetect microphone also, but the sound is crap, what driver have you on your system? I am on ubuntu 8.04 with all updates.

---

### Post by DutchLoki on 2008-07-04
> **Sharker said:**
> the sound is crap, what driver have you on your system? I am on ubuntu 8.04 with all updates.

I would look for you but the last and following weeks I'm not at home to take a look at my MythBox. 

Do a search on "pro 9000" here on the forum, this give a lot of usefull information about drivers and dependencies you can update. This could do the trick. 


Anyone else driver suggestions or a clue what the problem can be?

---

### Post by pfeels on 2008-07-05
For Skype make sure under SOUND DEVICES on the SOUND IN TAB they have USB Device instead of Default selected, there are two USB selection I use the 2nd choice ...

---

