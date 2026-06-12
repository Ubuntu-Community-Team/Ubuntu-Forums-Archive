---
title: "Realtek RTL8191SU not detected."
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by pawan98 on 2011-04-17
Hi, I recently installed ubuntu on my computer and when i put in my network wireless usb adapter (Realtek RTL8191SU) it isn't recognize, and the internet doesn't work. When I do lsusb, it comes up with Realtek Corperation however. And also the light on it doesn't flash either. THanks.

---

### Post by josephmills on 2011-04-17
could you please print us out a ```
hwinfo --usb
```and a ```
lsusb
``` make sure the wifi thingy is plugged in thanks let us see the whole print out please

---

### Post by pawan98 on 2011-04-17
pawan@Pawan-Desktop:~$ hwinfo --usb
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
pawan@Pawan-Desktop:~$ lsusb
Bus 001 Device 015: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 014: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 013: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
pawan@Pawan-Desktop:~$ 



Thanks for replying !

---

### Post by josephmills on 2011-04-17
could I see a ```
sudo lshw -C network
```and a ```
iwlist
``` thanks

---

### Post by pawan98 on 2011-04-17
pawan@Pawan-Desktop:~$ sudo lshw -C network
[sudo] password for pawan: 
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:7a:1b:b9
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
pawan@Pawan-Desktop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
pawan@Pawan-Desktop:~$

Thanks!

---

### Post by chili555 on 2011-04-17
I believe my esteemed colleague josephmills will want to see:```
dmesg | grep 819
```This may help: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)> Then we tried a different version of the firmware:

wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

with this one the wifi stick could detect wireless networks and connect
to them (the filesize of the used firmware is 68368 bytes).



---

### Post by pawan98 on 2011-04-17
pawan@Pawan-Desktop:~$ dmesg | grep 819
[    0.735819] cpufreq-nforce2: No nForce2 chipset.
pawan@Pawan-Desktop:~$

---

### Post by MooPi on 2011-04-17
Maybe just needs the correct driver ?

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU")
Navigate to driver folder contained and open a terminal
```
make 
sudo make install
sudo modprobe 8712u
```

---

### Post by pawan98 on 2011-04-17
When I put in the sudo make install command an error comes up:

pawan@pawan:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111$ sudo make install
[sudo] password for pawan: 
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'. Stop.

---

### Post by pawan98 on 2011-04-17
Hi - PROBLEM SOLVED !!! WAHEY !! FINALLY TOOK ME 2 DAYS !!!

Firstly, I done these commands in terminal

wget [http://launchpadlibrarian.net/373876...8192sfw.bin.gz]("http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz")

then

gunzip rtl8192sfw.bin.gz

then 

gunzip rtl8192sfw.bin.gz

then I noticed it came up with an error saying ; mv: cannot move `rtl8192sfw.bin' to `/lib/firmware/RTL8192SU/': Not a directory

Then I done the following commands in terminal;

sudo mkdir /lib/firmware/RTL8192SU 

then

sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

Then it all worked! I rebooted with my Wireless stick in and it worked!! :DDD

---

