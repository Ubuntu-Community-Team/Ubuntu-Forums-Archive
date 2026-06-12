---
title: "Verizon Novatel USB760 under Oneiric/Mint 12"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by zerubbabel on 2011-12-11
I've used my Verizon/Novatel USB760 for over two years under several releases of Ubuntu (10.04, 10.10, and 11.04), but now after a fresh install of 11.10/Mint 12, it is not recognized when I insert it. 

But oddly enough, on a hunch, I configured my virtual box (running Windows XP) to recognize USB devices, then plugged in my Novatel USB760, and it recognized it instantly. Then I installed the Verizon Access Manager and connected to Verizon right away. Then I shut down virtual box, and clicked on my network indicator in Gnome, and, lo and behold, the Verizon connection was included in the available connections - and it worked! Bizarre way to add a device under Linux! 

However, the device is still not accessible under Linux unless I FIRST connect with it in the virtual box. In other words, EACH TIME I want to connect I have to first do so within the virtual box. This is ridiculous, of course. There must be a way to get Linux to recognize the modem as soon as I insert it in the the USB port, right? Can anyone tell me how?

---

### Post by zerubbabel on 2011-12-12
I discovered that after connecting to Verizon from within a virtual box (running Windows XP), and then disconnecting and exiting the virtual box, the modem is available at /dev/ttyUSB3, whereas before or without connecting within the virtual box, /dev/ttyUSB3 is not defined. 

So, after exiting the virtual box, I can actually use wvdial (with the configuration set for /dev/ttyUSB3) to connect to Verizon, but before or without connecting within the virtual box, I cannot connect with wvdial, since there apparently is no port defined for it in /dev.

So can anyone tell me how I can get Linux to assign a port for the modem without having to start up a virtual box?

---

### Post by zerubbabel on 2011-12-14
Post #66 in this thread seems to have solved my problem: [http://ubuntuforums.org/showthread.php?t=1002262&page=7]("http://ubuntuforums.org/showthread.php?t=1002262&page=7")

---

