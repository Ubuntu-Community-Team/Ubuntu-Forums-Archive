---
title: "Trouble with b43-fwcutter"
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by shimita on 2012-03-08
I have just installed a fresh installation of Ubuntu 11.10 onto a 32gb flash drive using a LiveCD and my Linux experience is practically nil. Almost everything is working perfectly, yet I cannot connect to the internet. Under the network options in the pannel it says, "device not ready...firmware missing".
 
I have a Broadcom 802.11g Wireless Network Adapter, and I understand that I need the firmware for it (wl_apsta-3.130.20.0.o **and** broadcom-wl-4.150.10.5.tar.bz2) which I already have readily available. However, to my understanding, I need b43-fwcutter, to access the files I need from wl_apsta-3130.20.0.o, which I also have already as well. 
 
Now **to the heart of the problem**, when ever I double click the b43-fwcutter_014-9ubuntu0.1_i386.deb file, the "Install" button, in the top right corner, is greyed out, preventing me to install it. I know it's not installed already because when I type:
```
~$ b43-fwcutter
```
in the terminal, it will state that it's not installed and that I could simply type
```
sudo apt-get install b43-fwcutter
```
to download it. 
 
I do not have a router. I am using a public network available in my neighborhood, so please do not advise a wired connection, because I am aware of that option, and it is not available to me.
 
All of my previous attempts to install the file by Terminal have failed, usually stating that "there is no such file or directory".
 
I've read around the forum, checked countless threads regarding an issue similar to my own, reviewed the advice listed here ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers")), and have attempted everything advised in the "Help" documents provided Ubuntu itself; however my problem eludes answers.
 
Thank you for your time.

---

### Post by bkratz on 2012-03-09
According to this page

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The b43 fwcutter is on the installation disk. Look at the page about 1/2 way down under the section labeled   
**b43 - No Internet access**

Perhaps you can find some help there.

---

### Post by praseodym on 2012-03-10
b43fwcutter and firmware-b43-installer dont work properly in 11.10. Download the firmware from here:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

and unpack it via

> sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 

---

