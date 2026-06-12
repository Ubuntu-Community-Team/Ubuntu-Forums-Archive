---
title: "ubuntu 11.04 can't detect modem novatel wireless"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by Abdika on 2011-05-14
Hello, i am using ubuntu 11.04, 
When I try connect to internet, I always failed. because my modem is not detected by ubuntu. i already conffigure the provider. but when i try use my modem's friend huawai t-mobile i'ts works. 
Help me to Solve it,
Thanks:D

---

### Post by suya4ocha on 2011-06-26
> **Abdika said:**
> Hello, i am using ubuntu 11.04, 
When I try connect to internet, I always failed. because my modem is not detected by ubuntu. i already conffigure the provider. but when i try use my modem's friend huawai t-mobile i'ts works. 
Help me to Solve it,
Thanks:D

I got this problem too
my modem is Novatel Wireless MC930D
Once the connection is made, soon enough it will be disconnected
then the Mobile Broadband option is gone from the menu (top bar menu -- i don't know what is the name of it) 

when I ask (lsusb command)the terminal, no modem is existed (but physically still attached and turned on)

---

### Post by Abdika on 2011-09-19
i got the solution Bro, you have eject your modem as a disc. Because this modem must be a USB, so don't unmount it. just eject. before u eject that, try to type lsusb in ur terminal, than after that check one more with ls usb, ok.
after this step you must know your vendor and your product, usually in lsusb you can got it. try to type sudo modprobe usbserial vendor='0xbla' product='0xbla'

i hope this can help:)

---

