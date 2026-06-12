---
title: "tp-link tl-wn727n usb adpater not working after reboot, ubuntu 12.04"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by SithSolo1 on 2012-05-12
Last week I bought a new TL-WN727N and couldn't get it working, after asking about it on ASKUbuntu I was referred to this thread, [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715) , and told to type this code: ```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ;  /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo  tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -v rt2800usb
```That got it working and it was working well until today when I shut down the system to move it to its new home.

Upon starting it up again the adapter was no longer showing up once more.  I didn't know what to do so after re-reading the thread I tried the ```
sudo modprobe -v rt2800usb
``` command again but it gave me an error:

```
insmod /lib/modules/3.2.0-24-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-24-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
insmod /lib/modules/3.2.0-24-generic-pae/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
install modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800/new_id
insmod /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
sh: 1: cannot create /sys/bus/usb/drivers/rt2800/new_id: Directory nonexistent
FATAL: Error running install command for rt2800usb

```I've literally been using Linux for less than a week so I really have no clue what I'm doing and I'm afraid I've messed it up.  This computer is a gift for my mother for tomorrow so if anyone can help me I'd be eternally grateful.

The lsusb reads: ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 006 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 008 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business

```"Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter" is the wireless usb stick.

If you need any additional info please let me know.  Right now the computer is up and running in a temporary spot with ethernet. 

Thank You for taking the time to read this,
Brian

---

### Post by chili555 on 2012-05-12
You might want to proofread your work:> echo 'install rt2800usb modprobe --ignore-install rt2800usb ;  /bin/echo "148f 5370" > [COLOR="Red"]/sys/bus/usb/drivers/rt2800**usb**/new_id[/COLOR]' | sudo  tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -v rt2800usbCompare:> sh: 1: cannot create [COLOR="Red"]/sys/bus/usb/drivers/rt2800/new_id[/COLOR]: Directory nonexistentI wonder if you missed a 'usb' in there.

---

### Post by SithSolo1 on 2012-05-12
Edit: Of course now that I open my big, fat mouth the **sudo modprobe -v rt2800usb** is working again.  I swear, nothing has gone right since I got up this morning.  Its just been one of those days.

Is there anyway to make this automatically work every time the system is rebooted?

---

### Post by Falc7 on 2012-05-12
[http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715)

> Next I added rt2800usb to /etc/modules. Rebooted and my wireless starts up automatically.

This seems to be the solution

---

### Post by SithSolo1 on 2012-05-12
> **Falc7 said:**
> [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715)


**Next I added rt2800usb to /etc/modules. Rebooted and my wireless starts up automatically.**


This seems to be the solution

ok, but I have no clue how to do that.

---

### Post by chili555 on 2012-05-12
> **SithSolo1 said:**
> ok, but I have no clue how to do that.Please open a terminal and do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```

---

### Post by SithSolo1 on 2012-05-12
> **chili555 said:**
> Please open a terminal and do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```

Thanks for the quick reply.  I went on a reading spree and used ```
sudo gedit /etc/modules
``` and manually added rt2800usb to the list.  It appears to be working. Should I undo what I did and use the above code or did I just do the same thing the long way?

---

### Post by chili555 on 2012-05-12
> did I just do the same thing the long way?Exactly. The way you did it is exactly the same but just takes a few moments longer. Either method is fine. Let us know if you need additional assistance.

---

### Post by SithSolo1 on 2012-05-12
I'm still learning bit by little bit so thank you all for the help. :)

---

### Post by chili555 on 2012-05-12
> **SithSolo1 said:**
> I'm still learning bit by little bit so thank you all for the help. :)Please see Private Messages at the top.

---

