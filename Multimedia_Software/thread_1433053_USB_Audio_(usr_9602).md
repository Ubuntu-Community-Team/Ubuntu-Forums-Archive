---
title: "USB Audio (usr 9602)"
date: 2010-03-18
forum: Multimedia Software
---

### Post by bellalamb on 2010-03-18
Hi

Using 9.10 on dual boot P4


Try to use a USR 9602 voip phone plugged into USB port (this device works on WinXP)

It does not show in Sound Preferences

Any ideas please!

I have tried on a different computer with U9.10 and same problem

Regards

Paul

further info ......



System Testing does show it plugged in
> 
Detecting your sound device(s):

0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with CMI9761A+ at 0xd000, irq 22
 1 [U0x62a0x9004   ]: USB-Audio - USB Device 0x62a:0x9004
                      USB Device 0x62a:0x9004 at usb-0000:00:10.2-1, full speed

Is this correct?


Log report when plugged in ....

> 
Mar 18 18:38:51 ICL1 kernel: [ 1453.503658] generic-usb: probe of 0003:062A:9004.0002 failed with error -32
Mar 18 18:38:56 ICL1 pulseaudio[1919]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.0/sound/card1 (alsa_card.usb-062a_USB_Phone-00) more often than 5 times in 10s

---

### Post by RedSingularity on 2010-03-18
While its plugged in post the output of 

lsusb

---

### Post by bellalamb on 2010-03-18
output of lsusb

> 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 041e:403a Creative Technology, Ltd WebCam NX Pro 2
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 062a:9004 Creative Labs USR9602 USB Internet Mini Phone
Bus 001 Device 006: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 001 Device 003: ID 050d:0307 Belkin Components 
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



---

### Post by RedSingularity on 2010-03-18
Is your phone made by creative labs?

---

### Post by bellalamb on 2010-03-18
It is labled US Robotics - but might well be made by Creative Labs - didn't notice that before

---

### Post by RedSingularity on 2010-03-18
Is the phone supposed to be used with some piece of software?

---

### Post by bellalamb on 2010-03-18
no - just a stand alone audio device

---

### Post by RedSingularity on 2010-03-18
Have pulseaudio installed?

---

### Post by bellalamb on 2010-03-18
pulse audio not installed

---

### Post by RedSingularity on 2010-03-18
The following will install pulseaudio for you

sudo apt-get install pavucontrol

Then look in Apps>Sound>Pulseaudio volume control

Look and see if your hardware is listed there.

---

### Post by bellalamb on 2010-03-18
thanks for your quick replies

installed pulse

hardware is not shown in there

---

### Post by RedSingularity on 2010-03-18
Hmmmm what exactly is the device supposed to do?

---

### Post by bellalamb on 2010-03-18
just a microphone and speaker

---

### Post by RedSingularity on 2010-03-18
In the pulseaudio volume control did you look under the output and input devices tabs?

---

### Post by bellalamb on 2010-03-18
yes - just not showing 

this device works if I reboot into Windows

If I can't get it working, will just have to get another phone or headset -

---

### Post by RedSingularity on 2010-03-18
One more thing

in a terminal type the following

alsamixer

mess with the settings there and see if you can get it working.

---

