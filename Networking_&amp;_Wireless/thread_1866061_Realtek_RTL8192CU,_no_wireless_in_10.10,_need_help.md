---
title: "Realtek RTL8192CU, no wireless in 10.10, need help with drivers"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by gps123 on 2011-10-20
I installed 11.10 last Thursday.  I was having too many problems my RTL8192CUdongle (Realtek says kernel 3.0 is not supported).  

I reinstalled 10.10, hoping that my wireless connections would pop right up, but no dice.  

I have the driver from Realtek's site ready to go on a flash drive.  I also have the CD that came with the dongle.  I am an absolute beginner, and I have no idea how to install the driver from either source.  I could really use some help here before I break down and buy Windows... 

Thank you in advance.

desktop@desktop:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. 
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05dc:a768 Lexar Media, Inc. 
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by gps123 on 2011-10-21
I fixed this!

For future searchers, I downloaded every driver package I could find, tried to follow instructions online for opening drivers (something involving a makefile command).  After a few restarts, the "makefile" files in the driver folders became executable, and I somehow managed to install them.

---

### Post by grandads_shed on 2011-10-21
hi can u explain a bit more ?
where are the instructions ?
when u say restart , do you mean you had to restart the comp a few times ? if so did u do anything between restarts .?

i have the same problem, and im new to all this ubuntu stuff and know nothing about useing the terminal.

thank m8 :)

---

### Post by gps123 on 2011-10-21
I just restarted my computer after updates, and found the wireless wasn't working...I'll keep the "solved" tag, but I might be needing some help later.

grandad: I'm probably not the person who should be answering this, but here's what I did.  I downloaded a driver from the Realtek site; rtl8192_8188CU_linux_v3.1.2590.20110299.tar.gz, and unzipped it on the desktop.  There should be a file in there called "makefile."  The first time I opened it, I could double click on this file and it would open as a text file.  I restarted, and it was executable, and had the option to "run in terminal."

I clicked on "run in terminal," and did the following commands;

sudo su (enter password...new line comes up).

make (enter)
make install (enter)
reboot (enter)

This is based on a readme file I found with another .tar driver file.  I hope this helps.

---

