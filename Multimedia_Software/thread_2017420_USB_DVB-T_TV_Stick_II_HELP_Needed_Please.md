---
title: "USB DVB-T TV Stick II HELP Needed Please"
date: 2012-07-05
forum: Multimedia Software
---

### Post by skimitchell on 2012-07-05
Hi,

I am going CRazY trying to get my Kworld USB DVB-T TV Stick II usb tv card to work on ubuntu 12.04. :confused:

I have ready forum after forum and tried several ways to get it working but still no luck. 

I came across this review of the almost exact tuner and this is what they said:

[I]Works well in Linux
Pros: Cheap, works under Linux.

Other Thoughts: I wanted to use this in Linux on a Genesi EfikaMX Smarttop (ARM based) but I found that despite the drivers for the hardware all being in kernel the device ID for this particular model was not (so it could not tell which drivers to apply to the device). I just downloaded the kernel source, bunged the device ID into the array, recompiled and bingo! Lots of DVB-T adapters are just re-branded base models so it's easy to get them working if the base-model is supported.[/I]

Firstly - where do i find the kernel source i am after?
Secondly - what do i do with it (how do i bunge the ID into the array)?
Thirdly - how do i recompile? 

ANY help would be MUCH APPRECIATED.

Thanks
Justin

---

### Post by BicyclerBoy on 2012-07-05
Plug it in & then in a terminal:
lsusb

find the device & the associated USB IDs..
Look for any driver/firmware activity with
dmesg
dmesg | grep dvb

Find & search LinuxTV.org for your tuner & check if the exact USB IDs match.
[http://www.linuxtv.org/wiki/index.php/KWorld_DVB-T_355U](http://www.linuxtv.org/wiki/index.php/KWorld_DVB-T_355U)

[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices)

There are older USB dvb-t tuners that work & cost < $10..

---

### Post by skimitchell on 2012-07-08
Hi and thanks for your help.

I managed to get it working. YAHOooooooooo.

This was the link that got it sorted. 

[http://k0bet.com/kworld/index.html](http://k0bet.com/kworld/index.html)

Thanks again for your help.

Cheers
J

---

