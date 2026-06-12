---
title: "no network devices available"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by david9 on 2010-02-06
Fresh rookie to ubuntu and no idea how to make my ubuntu 9.04 get internet. Well from reading posts im assuming its not picking up my wireless card and i might need ndiswrapper but since i have not the slightest idea how to do it properly i was wondering if someone can help step by step please! ive tried learning from the forums but half the stuff i dont understand or get stuck haha well any help will be appreciated thanks!

---

### Post by chili555 on 2010-02-06
Dr. Chili is here to help. This won't hurt...much! First, let's ask the computer what kind of wireless it has. If it's an internal wireless, please open Applications -> Accessories -> Terminal and type in:```
lspci -nn | grep Network
```If it's a USB device, do:```
lsusb
```Post the result and we'll have a better idea of how to get it going.

---

### Post by david9 on 2010-02-06
this is what came out when i posted the code:

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI Express) [168c:002b] (rev 01)

---

### Post by chili555 on 2010-02-06
If you have internet connectivity, please do:```
sudo apt-get install linux-backports-modules-karmic-generic
```After it finishes, please do:```
sudo modprobe ath9k
```Your wireless should come to life!

---

### Post by david9 on 2010-02-06
i have internet but it doesn't seem to detect it. after the code it says..

Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package linux-modules-karmic-generic

i noticed it also says karmic..shouldn't mine say jaunty? idk if im jumping the gun or anything just curious

---

### Post by tmebishop on 2010-02-07
Will that only work for him due  to his card or can I put that in too? im new to the Linux game also and cannot connect to the internet at all

---

### Post by chili555 on 2010-02-07
> **david9 said:**
> i have internet but it doesn't seem to detect it. after the code it says..

Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package linux-modules-karmic-generic

i noticed it also says karmic..shouldn't mine say jaunty? idk if im jumping the gun or anything just curious
You are quite correct; I missed that. Please try:```
sudo apt-get install linux-backports-modules-jaunty-generic
```Also, it looks like you may have missed the key word *backports.*

---

### Post by chili555 on 2010-02-07
> **tmebishop said:**
> Will that only work for him due  to his card or can I put that in too? im new to the Linux game also and cannot connect to the internet at allIt works for quite a number of cards, but not all. Without knowing what card you have, it's impossible to say. Please start a new thread and be sure to provide the information requested here: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by david9 on 2010-02-07
i ran the new code but the same thing came out..

E: Couldn't find package linux-backports-modules-jaunty-generic


since i do not have internet on the netbook im trying fix can anybody tell me a reliable source where i can get this file then transfer via usb.  ive looked in debian and ubuntu but i keep gettin versions that do not seem to work thanks regardless!

---

### Post by 2hot6ft2 on 2010-02-07
I have the same card. Let me guess, this is a laptop right?
Have you pressed the WiFi button next to the power button?
You may have to play with it a bit to get it to come on but once it's on it will stay on.

Some times it the simple things.
If the button is off it wont be available when clicking on the network manager applet in the toolbar.

Same is true if the button is off and you plug in a usb wifi adapter it wont be available if the button is off.

---

### Post by chili555 on 2010-02-07
> **david9 said:**
> i ran the new code but the same thing came out..

E: Couldn't find package linux-backports-modules-jaunty-generic


since i do not have internet on the netbook im trying fix can anybody tell me a reliable source where i can get this file then transfer via usb.  ive looked in debian and ubuntu but i keep gettin versions that do not seem to work thanks regardless!Please run:```
uname -r
```You will need *both *the generic *and* the version that matches your kernel version, 2.6.28-18, for example. [http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty](http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty)

Assuming that is, in fact, your kernel version, you'd need *both*:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.18.23_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.18.23_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty-generic_2.6.28.18.23_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty-generic_2.6.28.18.23_i386.deb)

When you get them transferred to your Ubuntu machine, install with:```
sudo dpkg -i linux-backports*
```

---

### Post by Nuetouch on 2010-02-07
When installing new devices, it is always a good idea to always have an internet connection first. You may have to connect using an ethernet connection  first while you set up your device...Why? Because linux may have to automatically download some files(packages) from the net, if no connection, then errors will occur, I am not an expert, but an advanced user for about two years. Also, most commands from the terminal will most likely fail with out a connection...Hope it helps...

---

### Post by david9 on 2010-02-07
i got it working! thanks for your help guys!:)

---

### Post by ephraimdw on 2010-06-17
> **chili555 said:**
> Please run:```
uname -r
```You will need *both *the generic *and* the version that matches your kernel version, 2.6.28-18, for example. [http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty](http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty)

Assuming that is, in fact, your kernel version, you'd need *both*:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.18.23_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.18.23_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty-generic_2.6.28.18.23_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty-generic_2.6.28.18.23_i386.deb)

When you get them transferred to your Ubuntu machine, install with:```
sudo dpkg -i linux-backports*
```

Hey I'm just met the problem david had. Will you please help me?

I read all your solutions and tried them all, but when i doing
sudo dpkg -i linux......
It says 
> 
sudo dpkg -i '/media/PERSONAL/4Ubuntu/linux-backports-modules-jaunty_2.6.28.19.24_i386.deb' 
(Reading database ... 103594 files and directories currently installed.)
Preparing to replace linux-backports-modules-jaunty 2.6.28.19.24 (using .../linux-backports-modules-jaunty_2.6.28.19.24_i386.deb) ...
Unpacking replacement linux-backports-modules-jaunty ...
dpkg: dependency problems prevent configuration of linux-backports-modules-jaunty:
 linux-backports-modules-jaunty depends on linux-backports-modules-jaunty-generic (= 2.6.28.19.24); however:
  Package linux-backports-modules-jaunty-generic is not installed.
dpkg: error processing linux-backports-modules-jaunty (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-backports-modules-jaunty

 
I don't know what to do next.... Please help!~

---

