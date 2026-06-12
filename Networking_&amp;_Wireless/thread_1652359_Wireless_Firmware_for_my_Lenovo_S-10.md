---
title: "Wireless Firmware for my Lenovo S-10"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by thattallkid on 2010-12-24
I installed the latest version of ubuntu on my lenovo s10 netbook and have installed all of the updates etc including jockey-kde & gtk and broadcom 802.11 Linux STA driver however my wireless manager still is telling me that my wireless device is not ready because it is missing firmware.  What else do I need to download or how can I fix this problem?

Thank you in advance for the help as all I want for christmas is to get my netbook working.

Just in case here are the specs for a lenovo s10
[http://mobility10.blogspot.com/2008/11/lenovo-ideapad-s10-specifications.html](http://mobility10.blogspot.com/2008/11/lenovo-ideapad-s10-specifications.html)

---

### Post by walt.smith1960 on 2010-12-25
I'm not an expert like some here are but two things for starters.

1.  What does the command 'LSUSB' tell you? How do you know you have a Broadcom chip?

2.  Is there anything listed under system -> administration -> hardware drivers that you can enable?

---

### Post by thattallkid on 2010-12-25
Sorry I must be much more of a newb than I originally thought since 1) I do not know how or where to enter a command for ubuntu...2) I do not know how to explore the system menu you are referring to.  Thanks again for any direction

---

### Post by bkratz on 2010-12-26
> **thattallkid said:**
> Sorry I must be much more of a newb than I originally thought since 1) I do not know how or where to enter a command for ubuntu...2) I do not know how to explore the system menu you are referring to.  Thanks again for any direction

If you are using a "standard" version of Ubuntu, the command the last person wanted would be entered in the terminal and would be accessed at the top of the screen under the pull-down menu
Applications>>Accessories>>Terminal.  You would get something like

Yourname@Yourname-desktop:~$

to show up (with your name!). Here is where that command would be entered. As a matter of fact it should have been in lowercase, "lsusb" . Case is very important!  This would only be helpful if your wireless card is a usb version. If not, the command you would want would be

```
lspci -nn
```

The wireless card should "showup" labeled as Network--not the ethernet entry. You can copy/paste the output back here and receive good support from the group.  The other entry mentioned above would be under the Systems pulldown. System>>Administration>>hardware drivers and should have a wired connection if used for the update process.

---

### Post by thattallkid on 2010-12-26
Here is my output

 csj@csj-Lenovo:~$ lspci -nn
    00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
    00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
    00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
    00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
    00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
    00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
    00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    

Let me know if you need any more info.

---

### Post by amsterdamharu on 2010-12-26
If you don't have a cable internet connection then I suggest this solution:
[http://ubuntuforums.org/showthread.php?t=1652957](http://ubuntuforums.org/showthread.php?t=1652957) (post 4)

If you do have a wired connection than you can install the broadcom driver like this:
press alt + F2, type gnome-terminal and click run.
Copy and paste the following command in the terminal
```
sudo apt-get install firmware-b43-lpphy-installer
```

---

### Post by thattallkid on 2010-12-26
posting via my wireless!  thanks a lot guys!  

My only other question is you guys seemed to know a lot of basic codes to put into terminal to make things work...do you know of any pdf type cheat sheets of these commands I can use to help me along as I learn more about open source operating systems?

thanks again

---

### Post by bkratz on 2010-12-26
> **thattallkid said:**
> posting via my wireless!  thanks a lot guys!  

My only other question is you guys seemed to know a lot of basic codes to put into terminal to make things work...do you know of any pdf type cheat sheets of these commands I can use to help me along as I learn more about open source operating systems?

thanks again

Just got back and see you solved your problem, congratulations! here is one place to start about the terminal commands.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

You might want to go to the thread tools (above) and mark the thread as solved in case it helps someone else.


Found this thread too, maybe some help
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9247017](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9247017)


and this

[http://ubuntuforums.org/showthread.php?t=936906](http://ubuntuforums.org/showthread.php?t=936906)

---

