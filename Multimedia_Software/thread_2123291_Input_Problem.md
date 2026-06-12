---
title: "Input Problem"
date: 2013-03-07
forum: Multimedia Software
---

### Post by Stryars on 2013-03-07
Hi,

I have a problem with the sound input: When I click on the "Input" settings, the window crashes, and I get a error message who says that ubuntu got an internal error...
Any ideas ?

Thanks,

Stryars

---

### Post by gordintoronto on 2013-03-07
More details, please! What version of Ubuntu? Description of your computer? lspci output?

---

### Post by Stryars on 2013-03-08
Sorry for the lack of details :/

So: I have an M-Audio Fast Track Sound Card, My Ubuntu version is 12.10, the output works perfectly.
Anything else ?

---

### Post by gordintoronto on 2013-03-08
Yes, more details, please! lspci! lsusb! Brand and model of computer? CPU, memory, video card?

Sounds Settings/input, what shows up?

---

### Post by Stryars on 2013-03-16
What is lspci and lsusb ? I built my computer something like one year ago:
CPU: Intel i5 3570k
 RAM: 8Gb
Video Card: AMD Radeon HD 7850

Sounds settings: my sound card shows up, but when I click on input, it gives me an error : [http://hpics.li/4a8ed92](http://hpics.li/4a8ed92) [http://hpics.li/bad51bf](http://hpics.li/bad51bf)

Thanks !

EDIT: By the way, please excuse the mistakes, I'm french.

---

### Post by gordintoronto on 2013-03-16
What motherboard? Open terminal, enter the command: lspci
At least one of the lines of output will describe a sound device.
The command: lsusb
will probably show the M-Audio device. (Am I correct in saying you have a USB sound device?)

Assuming you have on-board audio, and also the USB device, which one do you want to use for input?

Your English is excellent! I wish you would say more.

---

### Post by Stryars on 2013-03-17
My motherboard is an Asus P8Z77-V LK.

I'll try these two commands in a few minutes, thanks !

And by the way, yes you're right, my sound card is the M-Audio Fast Track USB, and I would prefer to use the input of the M-Audio device if possible.

Thanks again !

---

