---
title: "Blackmagic Intesity Pro not recognized"
date: 2011-06-14
forum: Multimedia Software
---

### Post by DanAllan on 2011-06-14
I'm looking for ideas for getting a Blackmagic Intensity Pro working on 10.04 LTS. The official driver from Blackmagic is tested on 10.04 and they claim to support it, but the technical support agent I spoke with was unable to help me with anything Linux.

I installed the DesktopVideo 8.0.1 driver manually. ([Official Readme]("http://www.blackmagic-design.com/media/1110770/Blackmagic_Desktop_Video_Linux_8.0.1.txt").)

Because there are [known conflicts]("http://ubuntuforums.org/showthread.php?t=1441259") between some video capture drivers and Nvidia drivers, I removed my video card for testing purposes. (Using built-in video only.)

The Intensity Pro PCI card is recognized:
```
dallan@video-PC:~$ lspci | grep Blackmagic
02:00.0 Multimedia video controller: Blackmagic Design Device a117
```

I updated the card's firmware, and the update process claimed to execute successfully. But the upgrade may have created some problems, because now I cannot boot with the Blackmagic driver in place.

I blacklisted the driver; the machine boots. I start the driver manually. I confirm that it has loaded.
```
sudo modprobe blackmagic
lsmod | grep blackmagic
blackmagic            429253  0 
```

(A mysterious, crucial detail: I must exit the terminal and open a new one after modprobe blackmagic. Any command at all typed into that same terminal causes the system to immediately crash to black screen. It is still prone to crash later, seemingly randomly.)

The device file, which should be at /dev/blackmagic/card0, is not present:
```
dallan@video-PC:~$ ls /dev/blackmagic
ls: cannot access /dev/blackmagic: No such file or directory
```

The readme suggests that, in the case that the driver appears to be loaded by the device file is absent, the UDEV rule may be incorrect. The file at /etc/udev/rules.d/20-blackmagic.rules reads:
```
KERNEL=="blackmagic[0-9]*", NAME="blackmagic/card%n", MODE="0666", GROUP="video", RUN+="/usr/lib/blackmagic/BlackmagicPreferencesStartup %n", OPTIONS="last_rule"
KERNEL=="blackmagic_serial[0-9]*", NAME="blackmagic/serial%n", MODE="0666", GROUP="video", OPTIONS="last_rule"
```

I'm not sure what to make of that. Unsurprisingly, starting any Blackmagic software prompts the message, "No Blackmagic devices were found."

Thanks for any suggestion you can offer.

---

### Post by DanAllan on 2011-06-16
bump

---

### Post by DanAllan on 2011-06-20
Blackmagic developer support chimed in. I had not correctly followed the instructions in the readme.

Edit line 9 of /etc/default/grub to read
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```

Success.

---

### Post by garbage2 on 2011-07-01
First thing: a BIG **thank you**!!! Your post saved my day!!! 
Just a little addon for the people who came here looking for help (as like me): after editing line 9 of /etc/default/grub as DanAllan wrote, don't forget to apply the new grub configuration using the command 'update-grub'.
Thank you again!

---

