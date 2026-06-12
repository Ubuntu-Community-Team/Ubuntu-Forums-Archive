---
title: "just test"
date: 2008-05-01
forum: Multimedia Software
---

### Post by bvidinli on 2008-05-01
Hi,

i have AVERTV usb 1.1 tvcard, 
my card is: [http://www.aver.com/products/tvtuner_AVerTV_usb.shtml](http://www.aver.com/products/tvtuner_AVerTV_usb.shtml)
i have problem with it. it does not work. mplayer does not work, mythtv does not work with it.. 

i use ubuntu 8.04 hardy,

when i connect my usb card,
dmesg shows:
[10472.367753] usb 1-1: USB disconnect, address 6
[10472.367890] usb 1-1: Disconnecting W996[87]CF JPEG USB Dual Mode Camera...
[10472.367897] usb 1-1: V4L device deregistered: /dev/video0
[10474.043197] usb 1-1: new full speed USB device using uhci_hcd and address 7
[10474.073363] usb 1-1: configuration #1 chosen from 1 choice
[10474.084985] usb 1-1: W996[87]CF JPEG USB Dual Mode Camera detected
[10474.085034] usb 1-1: V4L device registered as /dev/video0


But wheneve any program, including cat /dev/video0 > tv0
tries to access /dev/video0,

following message is read in dmesg:
[10577.275368] usb 1-1: No supported image sensor has been detected by the 'ovcamchip' module for the W996[87]CF JPEG USB Dual Mode Camera (/dev/video0). Make sure it is loaded *before* (re)connecting the camera.


i think this is the problem.
i see video0 when i do ls -l /dev/video0

when i do:
bvidinli@bvidinli-laptop:~$ cat /dev/video0 > tv0
cat: /dev/video0: No such device
bvidinli@bvidinli-laptop:~$

it says no such device... note the error, no such device.. it finds file, but an error printed on dmesg, and no such device error is printed by calling program, here cat..

it is same when i use zapping in ubuntu/gnome.
i call zapping, it starts, cannot open /dev/video0, then error printed on dmesg as above...

Can anybody help ?
thanks.

---

