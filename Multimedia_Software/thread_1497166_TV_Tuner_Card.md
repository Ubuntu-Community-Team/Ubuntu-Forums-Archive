---
title: "TV Tuner Card"
date: 2010-05-30
forum: Multimedia Software
---

### Post by pradeepthundiyil on 2010-05-30
Hi,

I bought a TV Tuner card. Could anyone help in configuring it ? I got driver cd for XP & Vista.. How can use the same in Ubuntu ?  Please help..

---

### Post by howefield on 2010-05-30
What is the make/model of the tv tuner ?

Use the commands lspci or lsusb (depending on whether it is a pci or usb card) and post the details.

---

### Post by pradeepthundiyil on 2010-05-31
It is Techcom made TV Tuner Card (USB).

Model is SSD-TV-813. The device is not getting detected when giving the command.

I almost Quit windows, but now for watching TV I m using Vista. I really want to install Tuner card in Ubuntu...

---

### Post by jimmers on 2010-05-31
Try installing:-
dvb-apps
w-scan

Applications and utilities geared towards the initial setup, testing
and operation of a DVB device supporting the DVB-S, DVB-C, DVB-T,
and ATSC standards.

Worth a try

Luck

---

### Post by buntudawg on 2010-05-31
To get mine working I also had to install:

linux-firmware-nonfree

---

### Post by fishbulb1022 on 2010-05-31
try looking here [http://www.linuxtv.org/wiki/index.php/Hardware_Device_Information](http://www.linuxtv.org/wiki/index.php/Hardware_Device_Information)

---

