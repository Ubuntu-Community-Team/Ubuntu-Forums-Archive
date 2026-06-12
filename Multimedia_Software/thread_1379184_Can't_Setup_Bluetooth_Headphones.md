---
title: "Can't Setup Bluetooth Headphones"
date: 2010-01-12
forum: Multimedia Software
---

### Post by mcland on 2010-01-12
I just bought a pair of Samsung SBH500 headphones and a USB Bluetooth dongle.  I was able to connect my headphones with no problems but I wanted to set them up to play music.  I found this website:  [http://forums.overclockers.com.au/showthread.php?t=780054]("http://forums.overclockers.com.au/showthread.php?t=780054").  I got to this command:  ```
$ sudo hciconfig hci0 voice 0x0060
``` and got this error message ```
Can't write voice setting on hci0: Connection timed out (110)
```

Does anyone know what might be causing this?

BTW, I'm running 9.10.

---

### Post by prshah on 2010-01-12
> **mcland said:**
> ```
Can't write voice setting on hci0: Connection timed out (110)
```

hci0 refers to your bluetooth dongle. Do you have a 1.2 version bluetooth dongle? (ie, one that supports A2DP or similar audio protocols?)

---

### Post by vertago1 on 2010-02-22
I have a belkin usb bluetooth dongle which supports the SBH500 because I have used it in windows, but I haven't been able to setup in ubuntu. I would appreciate any help.

I am running kde which has a bluetooth manager which is able to detect the "Samsung SBH500" as a device but when I hit the next button and it checks for input capabilities it says "Sorry your Bluetooth Device does not support input Service"

---

### Post by vertago1 on 2010-02-22
I was able to get it to work.

First one of the times I put my headset in pair mode, kbluetooth popped up the pairing dialog for entering the 4 digit pin. After entering the pin it was able to connect.

To actually get the sound to work I had to do:

> 
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover


I also installed pavucontrol for changing the headset between duplex and high-quality audio modes.

---

