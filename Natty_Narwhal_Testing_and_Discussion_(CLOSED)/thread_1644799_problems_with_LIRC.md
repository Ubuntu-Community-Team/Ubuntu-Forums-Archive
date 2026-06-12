---
title: "problems with LIRC"
date: 2010-12-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2010-12-13
Anyone else have problems with lirc.

i have a remote control and i can only use couple of buttons. 
when i use irw it doesn't show normal things it use to.. 
also when i check the syslog when running irw get message failed to initilise hardware. the remote has worked on every release just not this one so far. 

syslog 
Dec 13 22:28:44 localhost lircd-0.8.7-pre3[2671]: caught signal
Dec 13 22:28:44 localhost lircd-0.8.7-pre3[2788]: lircd(default) ready, using /var/run/lirc/lircd
Dec 13 22:28:46 localhost lircd-0.8.7-pre3[2788]: accepted new client on /var/run/lirc/lircd
Dec 13 22:28:46 localhost lircd-0.8.7-pre3[2788]: could not get file information for /dev/lirc0
Dec 13 22:28:46 localhost lircd-0.8.7-pre3[2788]: default_init(): No such file or directory
Dec 13 22:28:46 localhost lircd-0.8.7-pre3[2788]: Failed to initialize hardware

messages
Dec 13 22:15:02 localhost kernel: [  528.992164] usb 5-5: new full speed USB device using ohci_hcd and address 2
Dec 13 22:15:02 localhost kernel: [  529.167248] Registered IR keymap rc-rc6-mce
Dec 13 22:15:02 localhost kernel: [  529.167728] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0001) as /devices/virtual/rc/rc0/input6
Dec 13 22:15:02 localhost kernel: [  529.167859] rc0: Media Center Ed. eHome Infrared Remote Transceiver (1784:0001) as /devices/virtual/rc/rc0
Dec 13 22:15:02 localhost kernel: [  529.167901] mceusb 5-5:1.0: Registered Topseed eHome Infrared Transceiver on usb5:2

terminal 
terry@ubuntu-desktop:~$ irw 
^[[D^[[C^[[A^[[B

any ideas to fix.

---

### Post by terry_gardener on 2010-12-13
dont know if this will help but:

installed gnome-lirc-properties program and when i try to run it get multiple python2.7 related errors

---

### Post by cariboo on 2010-12-13
That's probably what the problem is, there are quite a few packages that needed updating, and they probably haven't finished yet.

---

### Post by terry_gardener on 2010-12-15
the problem with gnome-lirc-properties with python 2.7 errors is not related to the problem i was having with lirc. 

after searching for an answer i have finally solved the problem with my remote control using another guide from these forums. 

[http://ubuntuforums.org/showthread.php?p=9952389#post9952389]("http://ubuntuforums.org/showthread.php?p=9952389#post9952389")

if you check post #5 which holds the answer to the problem.
apparently it is to do with the way the kernel handles the input device of the remote and now uses imon.

---

### Post by cariboo on 2010-12-15
It's good to see you got the problem solved.

---

