---
title: "Hawking HWUN3 Hi-Gain Wireless Adapter"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by tallbus1 on 2010-02-03
So, I have this new Hawking adapter, and have googled some, and have found no one who has had sucess, but then again I only saw two threads. So, what I was wondering was, does anyone know if these are compatible with ubuntu in any way, shape, or form, and how I would install them, I have Ndiswrapper, but am just learning Ubuntu's OS and don't know how to work the commands.  Your help would be greatly appreciated :)

---

### Post by tallbus1 on 2010-02-04
Bump, please help

---

### Post by tallbus1 on 2010-02-04
Anybody?

---

### Post by tallbus1 on 2010-02-04
Please?

---

### Post by tallbus1 on 2010-02-05
I'm probably going to keep posting until somone helps me.

---

### Post by Victormd on 2010-02-12
Try this thread:
[http://art.ubuntuforums.org/showthread.php?p=8682269](http://art.ubuntuforums.org/showthread.php?p=8682269)

---

### Post by mamamiapapapia on 2010-02-18
HWUN3 uses the RaLink 3070 chipset.  I got it to work under 9.1 by building the driver from the code available at [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) . (this driver was already available on my system, but didn't recognize the Hawking adapter, see below)

 I followed the build instructions at [http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/](http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/) (using the 3070 code of course)

Be sure to add a USB_DEVICE line to the array in os/linux/usb_main_dev.c with the hex id from the adapter (use 'lsusb | grep Hawking' to find it... 0x0E66,0x0013 IIRC) so the driver will recognize the HWUN3

I also had to copy the .ko from the build to a different spot than where the 'make install' dropped it... just 'sudo modprobe rt3070sta', then 'sudo modprobe -v -r rt3070sta', to see where ubuntu expects it to be...

Also, the driver looks for /etc/Wireless/RT2870STA/RT2870STA.dat , but the install puts it in /etc/Wireless/RT3070STA , so just make the RT2870STA directory and copy the .dat over

Oh boy, Linux is so much fun ;)

---

### Post by unactiveaccount on 2010-02-26
[mamamiapapapia]("http://ubuntuforums.org/member.php?u=1020916"), I followed your directions which took me your link on how to build the installation and such. 

I followed every direction step by step until I hit the part where I'm suppose to type "sudo make" and "sudo make install" within the root installation directory. 

"sudo make" outputs this: 
```
 gcc -g bin2h.c -o bin2h 
```"sudo make install" outputs: 
```
 make: *** No rule to make target `install'.  Stop. 
```I downloaded the correct driver package and successfully followed all the directions up until that point. Do you, or anyone else, have any suggestions? I REALLY want to get this working. 

By the way, I'm fairly new to the Linux world so apologies in advance if I don't quite understand what you're saying.

---

### Post by unactiveaccount on 2010-02-28
I'd really like some help on this; I've been trying to get this card working for ages now.

---

### Post by mamamiapapapia on 2010-03-01
unactiveaccount,

  what is the full output when you run 'sudo make' ?

---

### Post by unactiveaccount on 2010-03-01
mama, that is the full output. The next line after that is the command line.

---

### Post by unactiveaccount on 2010-03-03
I hate to be the nuisance, but could anyone please help?

---

