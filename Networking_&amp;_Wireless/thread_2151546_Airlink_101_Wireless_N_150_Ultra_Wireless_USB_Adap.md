---
title: "Airlink 101 Wireless N 150 Ultra Wireless USB Adapter"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by bluedot33 on 2013-06-04
Hello, 

I am a newbie to linux and I have installed Linux Mint 14 to my HP Pavillion DV9205US. The wireless card in my laptop has gone bad so I've been using a Netgear USB adapter which has been working well; however the adapter is long and sticks out quite a bit. I purchased the Airlink 101 Wireless N 150 Ultra Wireless USB Adapter which is much smaller and tried installing the drivers and utilities via WINE; however I received an error. Is there a way to get this adapter to work with linux. 

Thank You.

Mike

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by bluedot33 on 2013-06-04
mdh-laptop@mdhlaptop-HP-Pavilion-dv9000-RP115UA-ABA ~ $ lsusb
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mdh-laptop@mdhlaptop-HP-Pavilion-dv9000-RP115UA-ABA ~ $ sudo lshw -C network
[sudo] password for mdh-laptop: 
  *-network:0             
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:22:3f:de:68:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-17-generic firmware=N/A ip=192.168.0.114 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan1
       serial: 00:21:2f:30:f6:7d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.5.0-17-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
mdh-laptop@mdhlaptop-HP-Pavilion-dv9000-RP115UA-ABA ~ $ c

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by bluedot33 on 2013-06-04
I downloaded the file but I'm not sure which folder/file to install. There is a file named install.sh, do i use that one

---

### Post by bluedot33 on 2013-06-05
Also how do I copy something into the terminal. I copied the three blacklisted files but nothing happens when I paste them into the terminal.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by bluedot33 on 2013-06-05
Thank you so much for your help, I am installing the new link now. I also entered 

gksu gedit /etc/modprobe.d/rtl8192cu_old.conf

into the terminal. It asked me for my password and when I entered it, it showed

mdh-laptop@mdhlaptop-HP-Pavilion-dv9000-RP115UA-ABA ~ $

and nothing else so I think it worked. 

Not sure what to do with the blacklists, once the packets for the new driver are installed. I believe I can use gksu because I used it for the command line you had me enter to remove the old driver. 

Hope I am doing this right but thats the great thing about linux, if I mess up I can just reinstall linux and start over, lol. 

I have 50% left on my install and will update you when I'm finished.

Thanks again

---

### Post by bluedot33 on 2013-06-05
Packets installed it says: 

Package - rtl8192cu-tjp-dkms
Status - Same Version in Already Installed

Description: 

rtl8192cu-tjp driver in DKMS format

Details:

V 1.6

Maintainer:

Dynamic Kernel Modules Support Team <pkg-dkms-maint@lists.alioth.dabian.org

Priority:

Optional

Section:

Misc

Size:

5384

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by bluedot33 on 2013-06-05
installed gedit and created a file with "/etc/modprobe.d/rtl8192cu_old.conf" in the text, now what do I name it and where do I save it. Also how do I located the file second, "existing file"

---

### Post by bluedot33 on 2013-06-05
Tried the echo command and received this 

bash: /etc/modules: Permission denied

---

### Post by bluedot33 on 2013-06-05
Wow, Ok I installed gedit and when I went into the terminal and entered 

gksu gedit /etc/modules

gedit opened and says

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

The good thing is I think gedit is working; however I don't know what this means

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by bluedot33 on 2013-06-05
Ok,

I did what you told me in the begining reference to going into the terminal and entering


gksu gedit /etc/modprobe.d/rtl8192cu_old.conf

which was empty. I pasted 



blacklist rtl8192cu blacklist rtl8192c_common blacklist rtlwifi

into the fole and saved it; however when I entered

gksu gedit /etc/modules

Terminal opened and said

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

I don't think this is right but at least I think i'm on the same page with you regarding the terminal, gedit and how to save and edit files.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by bluedot33 on 2013-06-05
Well, I think I did everything you said too. I entered the command line

8192cu

at the end of the file with a space after it, restarted it, and the mini wireless adapter still dosn't work. 

I'm going to try to get some sleep before I have to go to work. I appreciate all the help and if you think of anything else I could do to get this to work please reply and I will check it when I log back on.

Thanks again, 

Mike

---

