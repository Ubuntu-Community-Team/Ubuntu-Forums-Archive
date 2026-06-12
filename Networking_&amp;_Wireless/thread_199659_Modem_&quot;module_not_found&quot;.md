---
title: "Modem: &quot;module not found&quot;"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by jnoreiko on 2006-06-19
I'm following the instructions on [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) exactly.

Could someone tell me what the error message "FATAL: module not found" actually means?
I don't understand how the module can't be there, since all I'm doing is following instructions designed for Ubuntu.

---

### Post by zxee on 2006-06-19
The module is not in the correct directory or it is not a valid module. If you're sure that not the case then maybe check permissions on the module you installed.
What did the scanmodem tool output for your modem?

---

### Post by jnoreiko on 2006-06-20
I don't remember offhand, but it indicated it was a Lucent.

So "FATAL: module not found" can actually mean the module IS there, but isn't valid to be loaded?
That would make more sense, but it's not a very good error message in that case.

---

### Post by blastus on 2006-06-21
Have you tried my guide [HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial)](http://www.ubuntuforums.org/showthread.php?t=198730)?

---

### Post by nucleusfermi on 2007-07-30
[COLOR="DarkRed"][SIZE="2"]**I too have the same problem, I want to use my "Huewai MT882 USB Remote Network Device(SmartAX MT882) for connecting to internet(ADSL via WAN PPPoE) (i.e establishing internet connection). Though I had installation disk, and Linux supported documentations in which there are some "inc, src subfolders with same CDCEther file in them as well as one "makefile" named file and a patch notepad kinda file named USB CDCEther Readme File." But since I'm absolutely novice to this OS, I don't know how to use them. I searched whole forum very intensively and got some instructions via "UeagleAtm" website, by downloading a file named "ueagle-data-1.1.tar.gz", I followed all instructions and created subfolder in "/lib/firmware" and copy untarred files (in order to install "firmware"); **[/SIZE][/COLOR]
**[COLOR="Red"][SIZE="3"]When I tried to start the 'bridge' between the ATM modem and Ubuntu by typing in terminal "sudo modprobe 2684", I get message "FATAL: module 2684 not found".[/SIZE][/COLOR]** [COLOR="Magenta"]**_*[SIZE="4"]Help:([/SIZE]*_**[/COLOR]

---

### Post by nucleusfermi on 2007-07-30
**[SIZE="2"][COLOR="Teal"]I came to know it  happens if your firmware is not installed properly, if anyone has any suggestion to my post above, plese send quickly to me via any possible method (i.e. reply here or PM or by e-mail or through ICQ/AOL); Thanks.[/COLOR][/SIZE]**

---

### Post by geraldm on 2007-07-30
Please try using the full path filename to the module.

Gerald

---

### Post by nucleusfermi on 2007-07-31
**[COLOR="Green"][SIZE="2"]Geraldm, could you tell me what are modules, how they are made, what does they do and how can we get them included or if disabled then enable them??[/SIZE][/COLOR]** 
[COLOR="Red"][SIZE="2"]**Second thing which I wanted to ask many people in this forum had said numerous times that their USB modem simply failed to work in Ubuntu and they all had to opt for "Routers", is this right??**[/SIZE][/COLOR]

---

