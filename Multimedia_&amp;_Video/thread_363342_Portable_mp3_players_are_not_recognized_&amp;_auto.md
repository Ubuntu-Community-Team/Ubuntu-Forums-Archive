---
title: "Portable mp3 players are not recognized &amp; automounted!!"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by jdarias on 2007-02-16
Hello.
When i connect a usb drive it gets mounted and working, but other usb devices are not mounted. I´ve tried Motorola E398 phone and a generic ipod-look-alike mp3 player. (maybe some s1mp3 variant). None of these work when i connect them.

How can i solve this? My ubuntu installation is up to date. Edgy, last kernel (2.6.17-11)

---

### Post by MetalMusicAddict on 2007-02-16
> **jdarias said:**
> Hello.
When i connect a usb drive it gets mounted and working, but other usb devices are not mounted. I´ve tried Motorola E398 phone and a generic ipod-look-alike mp3 player. (maybe some s1mp3 variant). None of these work when i connect them.

How can i solve this? My ubuntu installation is up to date. Edgy, last kernel (2.6.17-11)

Not all devices support this. It has to be supported as a MSD. (mass storage device)

---

### Post by alyoung on 2007-02-16
I'm not sure about your MP3 player, but the Motorola E398 requires P2K drivers.

[http://sourceforge.net/projects/moto4lin/]("http://sourceforge.net/projects/moto4lin/") - phone drivers available here.

---

### Post by jdarias on 2007-02-17
Hello. Got some news about this.
```
sudo rmmod ehci_hcd
```
With this the motorola phone is detected with lsusb, but it doesn't mount and therefore i cannot access it.
```
jdarias@familia-arias:~$ lsusb
Bus 004 Device 002: ID 03f0:2405 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 021: ID 22b8:4810 Motorola PCS E398 Storage
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:1904 Hewlett-Packard DeskJet 3820
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

It also makes the mp3 player to be visible and it mounts.
```
jdarias@familia-arias:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 03f0:2405 Hewlett-Packard 
Bus 002 Device 002: ID 03f0:1904 Hewlett-Packard DeskJet 3820
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 10d6:1101 Actions Semiconductor Co., Ltd 
Bus 001 Device 001: ID 0000:0000
```
The bad thing is that the rmmod command has to be issued everytime i reboot :(

I remind being able to use the motorola phone as mass storage device a time ago, but as of now it doesn´t work anymore. So i´ll try the Mot4lin suggestion.

Please, how do i remove the ehci_hcd module permanently so i don´t have to do sudo rmmod everytime i boot? I hope that´s the right thing to do...

Thanks guys :)

PS: Would it be a good idea to install usbmount? what does it do? Do i need it?

---

