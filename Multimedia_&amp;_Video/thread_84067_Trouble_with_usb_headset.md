---
title: "Trouble with usb headset"
date: 2005-10-30
forum: Multimedia &amp; Video
---

### Post by chimera on 2005-10-30
I have a headset with headphones and a microphone which I intent to use for teamspeak.Is there anyway I could make the sound play from my speakers,and use the microphone at the same time?I need to use the speakers because the headphones don't work(they're broken)

---

### Post by AlexMR on 2005-10-30
Hello chimera,

usually the headset has two pluggers, one for the headphones and one for the microphone. Just unplug the one for the headphones and plug in your PC-Speakers.

Greets,
Alex.

---

### Post by chimera on 2005-10-30
No,it's a USB headset,and it only has one plug

---

### Post by chimera on 2005-10-30
I'm pretty sure someone from such a large community would know how to do it...

---

### Post by chimera on 2005-10-31
Although I am slowly losing my confidence...

---

### Post by ubuntu_demon on 2005-10-31
[QUOTE=chimera]Although I am slowly losing my confidence...[/QUOTE]

I moved this thread to the correct section(hardware video/sound) and changed the title to "Trouble with usb headset".

People want to help but you have to post in the correct section and present as much relevant information as you can. 

Please tell us your headset brand and model. 

Please report the result of this command :

$ lsusb

good luck with your headset :)

---

### Post by chimera on 2005-10-31
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:0a01 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

---

### Post by ubuntu_demon on 2005-10-31
you forgot this :) ==>

[QUOTE=ubuntu_demon]
Please tell us your headset brand and model.
[/QUOTE]

I forgot to mention that you have to connect the headset (and turn it on if it has a power switch) before you did lsusb. Was it connected ?If not please do it again.

Please post the result of this command too :
$lspci

---

### Post by chimera on 2005-10-31
yes it was connected.and no,it doesn't have the power switch

lsusb:

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:0a01 Logitech, Inc.  #this is the headset I think#
Bus 001 Device 001: ID 0000:0000

lspci:

0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82875P Processor to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corp. 82875P Processor to PCI to CSA Bridge (rev02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (re v 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (re v 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (re v 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (re v 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1(rev a2)
0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)
0000:03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:03:04.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:03:0b.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

---

### Post by ubuntu_demon on 2005-10-31
Did you search the forums ? (I had assumed you did but when I searched I got a lot of results) Feel free to ask for help but try searching the forums first.

What did you try already to make it work ?

this might work :

$ sudo modprobe snd_usb_audio
and connect your headset now and see if it works

if it doesn't work first go to this thread :
[http://www.ubuntuforums.org/showthread.php?t=79678](http://www.ubuntuforums.org/showthread.php?t=79678)

If it still doesn't work search the forum for "usb headset" and/or "logitech usb headset" if you have a logitech

Let us know when you have solved the problem. 

good luck :)

---

### Post by ubuntu_demon on 2005-10-31
[QUOTE=chimera]
lsusb:

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:0a01 Logitech, Inc.  #this is the headset I think#
Bus 001 Device 001: ID 0000:0000

[/QUOTE]

If you have an usb mouse it might very well be the mouse. Do you have an usb mouse ? Do you have a logitech mouse ?

What brand/type/model of usb headset do you have ?

---

### Post by chimera on 2005-10-31
yes,I have a lugitech usb mouse,keyboard and headset

---

### Post by ubuntu_demon on 2005-10-31
you can find out more with 
$ lsusb -v

but first try what I told you and search the forums. (I gotta go now)

---

