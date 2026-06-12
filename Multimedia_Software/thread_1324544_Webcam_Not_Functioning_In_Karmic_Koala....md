---
title: "Webcam Not Functioning In Karmic Koala..."
date: 2009-11-12
forum: Multimedia Software
---

### Post by michaeljanssen on 2009-11-12
Installed Karmic Koala 9.10. 
Updated all needed updates. 
Installed restricted-extras, and multimedia codecs. 
Downloaded Cheese. 
But when it opens, all it shows is color bars with a tv screen static box in the bottom right. 
I go to "Edit -> Preferences' and it shows my webcam "Gateway USB 2.0 Webcam (/dev/video0). 
But it is greyed out. 
I am using a laptop and the webcam is internal in the monitor. 
It worked in 9,04.
How do I go about fixing it? It is currently the only downfall in 9.10 I have found so far.

---

### Post by simynona on 2009-11-13
I have the exact same problem. I also have a Gateway, and the webcam will work once after boot up, but after it's turned off, it won't turn back on. Cheese says it can't detect it. Please help us!

---

### Post by Arup on 2009-11-13
Can you go to the terminal and do a lsusb and list the finding here.

---

### Post by oldsoundguy on 2009-11-13
It also pays to go to the compatible hardware list.
link to this page was there.
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Cameras that worked in the past that are either not supported by their makers in the beginning or have been left back will be found on that list. 

I had to get a new camera as the Logitech 4000-5000 was left behind in Linux support.

---

### Post by michaeljanssen on 2009-11-14
michael@michael-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
michael@michael-laptop:~$

---

### Post by michaeljanssen on 2009-11-14
Oh and another thing. If I do start Cheese, and I see those lines...once I close Cheese, my usb ports dont function, so I then have to reboot my computer for the usb ports to work.

---

### Post by Arup on 2009-11-14
Can you do a dmesg and post.

---

### Post by michaeljanssen on 2009-11-15
not the whole thing right? what parts of the dmesg should i post...it is a TON of lines..

---

### Post by simynona on 2010-01-24
There isn't something wrong with the driver, it's gotta be with the USB connections. The same thing also happens with regular USB drives. If I leave one in and reboot it will show up, but if I take it out and put it back in, it won't show up. It's like I have to reboot my computer every time I need to use a different USB. This is not cool.

---

