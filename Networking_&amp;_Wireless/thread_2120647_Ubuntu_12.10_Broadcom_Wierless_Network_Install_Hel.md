---
title: "Ubuntu 12.10 Broadcom Wierless Network Install Help"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by Side01 on 2013-02-27
Hello everybody, i am new to ubuntu and a totally beginner, i installed Ubuntu 12.10 next to windows 7 to test it before i switch.

The problem is, i am not able to install Broadcom driver. I tryed lot of solutions but nothing helped me.
The other problems are the following,
- I dont have a cdrom drive in my notebook so i installed it from usb stick.
- Second, i only can go on the internet with wifi.

Is there any way to install it with out internet connection? I would be really happy if someone could help me a bit because right now im ripping my hair out a bit

Thank you

---

### Post by bellaseem on 2013-02-27
EDIT: varunendra pointed out that the following doesn't work for broadcom... works for realtek though if you want.. ( I can't figure out how to delete this btw, the edit button says edit/delete but there's no delete option I can find when i press edit)

Yes you can install when offline, but you need to download the files for the broadcom driver from their website... Can you elaborate more on what you tried to do?

My suggestion would be to do this:
1- Find out exactly what driver your card uses (using terminal)
2- Go broadcom's website and download the driver files
3- extract them, then you usually have to change directory using terminal into the extracted folder using the command " cd " , for example : cd /home/x/downloads/broadcomdriver
4- after changing directory type in " sudo make " , then "  sudo make install " , then reboot
5- Also after extracting, you might want to check the readme file that comes in the folder... see what it tells you there. ..

Another approach would be to download the driver for windows (or use it from a CD, if you have one) then find a tutorial on how to use ndiswrapper to install the windows drivers on ubuntu... 

Good luck!

---

### Post by Side01 on 2013-02-27
thanks i will give it a try

---

### Post by varunendra on 2013-02-27
Welcome to the forums Side01!

Please post output of :
```
lspci -nnk | grep -iA2 net
```

PS:
bellaseem,
Broadcom drivers do not need to be installed that way.

---

### Post by Side01 on 2013-02-27
Hello [[COLOR=#C61919]**varunendra**[/COLOR]]("http://ubuntuforums.org/member.php?u=1043629") thank you for the greeting and for your reply, did what you ask, i got the following results

```
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller [11ab:4357] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:308c]
    Kernel driver in use: sky2
--
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1508]
    Kernel driver in use: b43-pci-bridge

```

---

### Post by varunendra on 2013-02-27
> **Side01 said:**
> ```

--
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY **[COLOR="Red"][14e4:4315][/COLOR]** (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1508]
    Kernel driver in use: b43-pci-bridge

```
Please download linux-firmware-nonfree package choosing any of the mirrors on this page : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Copy it to your Ubuntu desktop, and double-click to install. If required, reboot and try to connect.

Post back the result. Thank you.

---

### Post by Side01 on 2013-02-27
Varunendra, first i want to say sorry for holding you up with my silly question.
I did more research a firend offerd me a place for my solution it worked, i dont need to download anything, actually the ubuntu cd containts the install package for it and i followed these steps

[http://acervulus.info/2011/install-wireless-network-card-driver-without-existing-internet-connection-ethernet-or-usb/](http://acervulus.info/2011/install-wireless-network-card-driver-without-existing-internet-connection-ethernet-or-usb/)

And it worked, im am replying from ubuntu now :)

And thank you again for takeing the time to answer my question, i wish you a wonderfulday

---

### Post by varunendra on 2013-02-27
No problem ! :)

Actually, the link is more or less the same solution I suggested. The kernel already has b43 driver, only thing required is firmware which is included in the package I suggested to download (among many other non-free firmwares).

The name of this package is easier to remember, and it solves many other firmware issues one may encounter in future, so I recently changed my recommendation :) (my earlier method was same that you followed ;))

As you have got your problem solved now, please consider marking the thread as [Solved] using "Thread Tools" link above the top post on this page.

And thanks for the feedback :)

---

