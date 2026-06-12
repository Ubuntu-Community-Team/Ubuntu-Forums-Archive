---
title: "W-Network issues"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by mc228608 on 2011-02-06
im on a HP Pavilion Entertainment PC (DV2500)
ive already tried to get info for this problem on another thread to no avail.
Trying to set up my wireless connection with no means of Internet access so I found my Card\Driver jazz with :
  lspci -vvnn | grep 14e4

  -which gave me the following::

  04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

Using instruction that from an ubuntu help forum, i found the drivers online from another computer and transferred them to my computers homefolder. I need to navigate to the home folder to finish the process.
which is:

b43-fwcutter is located on the Ubuntu install media under **[FONT=&quot]../pool/main/b/b43-fwcutter/[/FONT]** and patch is located under **[FONT=&quot]../pool/main/p/patch/[/FONT]** **[FONT=&quot]or[/FONT]** both in the official repositories online. 
  Double click on the package to install **[FONT=&quot]or[/FONT]** in a **[FONT=&quot]terminal[/FONT]** (under the desktop menu **[FONT=&quot]Applications > Accessories > Terminal[/FONT]**) navigate to the folder containing the package and issue the following command: 
  [B][FONT=Courier]:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*

[/FONT][/B][FONT=Courier]^this is what is giving my problems[/FONT][B][FONT=Courier]
[/FONT][/B]
(sorry for the some-what sketchy info, i had typed this up, much better, once before but it was closed before being posted GRRRR)

here are the steps that ive been taking, you don need to read it but if you llok over to get a better understand of what im doing it would be appreciate.::

 **b43 - No Internet access**

  If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch packages from the install media. After that you will need to setup firmware manually (without the firmware automatically downloading and being set up). 
  **[FONT=&quot]Setp 1.[/FONT]** 
  b43-fwcutter is located on the Ubuntu install media under **[FONT=&quot]../pool/main/b/b43-fwcutter/[/FONT]** and patch is located under **[FONT=&quot]../pool/main/p/patch/[/FONT]** **[FONT=&quot]or[/FONT]** both in the official repositories online. 
  Double click on the package to install **[FONT=&quot]or[/FONT]** in a **[FONT=&quot]terminal[/FONT]** (under the desktop menu **[FONT=&quot]Applications > Accessories > Terminal[/FONT]**) navigate to the folder containing the package and issue the following command: 
  :/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
  **[FONT=&quot]Step 2.[/FONT]** 
  On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
  **[FONT=&quot]Step 3.[/FONT]** 
  Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware: 
  ~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
  **[FONT=&quot]Step 4.[/FONT]** 
  Under the desktop menu **[FONT=&quot]System > Administration > Hardware Drivers[/FONT]**, the **[FONT=&quot]b43[/FONT]** drivers can be activated for use. 
  **[FONT=&quot]Note:[/FONT]** A computer restart may be required before using the wifi card. 
  **LiveCD/LiveUSB**

  **[FONT=&quot]Note:[/FONT]** The install media contents are mounted under **[FONT=&quot]/cdrom[/FONT]** of the filesystem. 
  **[FONT=&quot]Step 5.[/FONT]** 
  For temporary use with the LiveCD and LiveUSB environments, instead of a computer restart, in a terminal issue the following commands: 
  ~$ sudo modprobe -r b43 ssb~$ sudo modprobe b43

---

### Post by arjuntank on 2011-02-06
what does *sudo dpkg -i b43-fwcutter** say? can you dump the output?

---

### Post by mc228608 on 2011-02-06
Dpkg: error processing b43-fwcutter* (--install)
cannot access archive: no such directory
Errors were encountered while processing:
b32-fwcutter*

---

### Post by arjuntank on 2011-02-06
cant you just double-click and install through the gdebi package installer? there is only one file in that directory. for example on ubuntu 10.10, its b43-fwcutter_013-2_i386.deb
plus, you might need a patch if you have kernel 2.6.24. you can check your kernel version by *uname -r*

---

### Post by mc228608 on 2011-02-06
It doesn't open properly, when it is opened in search's for a repository via internet  (obviously finds nothing) and then when the panel comes up the list is empty.

---

### Post by arjuntank on 2011-02-06
it should not look online for files. the package contains just a binary file which installs to /usr/bin/b43-fwcutter and other man pages of course. right click the file and open with gdebi package manager. it should not need any dependencies.

---

### Post by mc228608 on 2011-02-06
sorry i went to Hardware driver. where is the gdebi located if you would?

---

### Post by arjuntank on 2011-02-06
generally double click works, it should either open software center or package installer. if not, right click and "open with"-> Gdebi package installer

---

### Post by mc228608 on 2011-02-07
ohhh okay, yeah i understand what you mean now. however this is a Tar archive (bzip-compressed...
and not a software package so it only opens with the archive manager ive  tried finding it with open with but it doesnt come up, what command  list do i need to enter to open GDebi?

---

### Post by robsoles on 2011-02-07
Just as an aside to all that, can this PC be physically picked up and taken near the router to be plugged into the ethernet to just get this done the most straightforward way you could hope to do this?

(GDebi is a simple tool to install .deb files and if you just use nautilus to access whatever files you need to access then the right 'tool' will be automatically selected for you when you select the file - unless there is no registered 'tool' for that particular file-type but .deb is good and registered :))

---

### Post by arjuntank on 2011-02-07
robsoles, i would have told that if it was a laptop. it isnt a laptop and we dont know where the router is and if he has a LAN cable. 

mc228608, press alt+f2 and type file-roller and press enter. click file->open and selece the *tar.gz file..extract to some location

---

