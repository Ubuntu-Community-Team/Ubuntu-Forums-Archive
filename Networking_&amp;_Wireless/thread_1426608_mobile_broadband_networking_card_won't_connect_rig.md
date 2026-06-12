---
title: "mobile broadband networking: card won't connect right"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Gonz_91 on 2010-03-10
Hi everyone!

Since my recent re-conversion into Ubuntu, I noticed Network-Manager now has mobile broadband support out of the box. Splendid!

I've been using my Huawei (Vodafone) modem since around two weeks, and so far it's been great, except for a little detail: sometimes, them modem simply won't work. I plug it in, "cd" drive (where the Vodafone Mobile Connect files are) shows up, but no "Vodafone" on Network-Manager.
I believe this has something to do with settings the modem may leave behind after each use, but I'm quite newb, so...


Thanks a lot ;)

---

### Post by alexfish on 2010-03-10
Hi

Could you give details of Ubuntu Version

Also could you post details of the outputs with these commands from the terminal, if possible please remove all usb device except the modem 
Code:

dmesg | grep -e "modem" -e "tty" 

Code:

lsusb

thanks in advance

alexfish

---

### Post by Gonz_91 on 2010-03-10
Thank you for your reply!
So, running Ubuntu 9.10, modem connected and running:

_dmesg | grep -e "modem" -e "tty"_ returns nothing. Is that bad?
Can't be too bad, the modem's working, at least for now...

_lsusb_ returns this messy stuff:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 016: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 002: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```



As to the cause of the problem, I'm sort of biased towards some settings file the modem creates, maybe related to the usb port itself, even, which may or may not need be deleted/altered in some way...

---

### Post by alexfish on 2010-03-10
Hi

I presume you are using Ubuntu with this modem 
as you mention the modem is working now



can you clarify 

1. does the modem at times appear to be connect to the network but the browser does not work

2. the modem at times just does not connect

3. does the modem vanish from the network manager when the file or cd is removed or ejected from the desktop

also check the the dmesg again . copy the code into the terminal . yes it would be odd if this code does not work ,esp if you have the modem connected and your on the net , just does not make sense.

regards

alexfish

---

### Post by Gonz_91 on 2010-03-11
G'morning!

Well, I rechecked dmesg, and this time (okay, maybe I didn't paste it right last time...) it returned as follows:
```
[    0.001427] console [tty0] enabled
[  702.650232] USB Serial support registered for GSM modem (1-port)
[  702.650333] option 2-1:1.0: GSM modem (1-port) converter detected
[  702.650534] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  702.650559] option 2-1:1.1: GSM modem (1-port) converter detected
[  702.650673] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  702.650727] option: v0.7.2:USB Driver for GSM modems
```

So, on to clarifying:
When I plug in the usb modem, a "cd" drive shows up, containing the files used to install the software on Windows. This appears every time I plug it in.
But, the thing is, the connection is also supposed to appear under "Mobile Broadband" on the network manager, and it almost never does, now. Connecting requires me to plug in/out several times for the connection to appear there...

Thanks a lot :D

---

### Post by alexfish on 2010-03-11
Hi

I had this problem When I upgraded the original installation of Ubuntu 9.10, but can't remember the kernel version, however the device seemed to work fine with Kernel -17
 which kernel are you using 

one thing of note was that the dongle did not connect properly into the socket, so I used the extension lead provided,


 other problem with this device, when it is continuously plugged in and out the tty ports would change , IE swapping between TTY0,TTY1,TTY2. So the best check is to use the command  ls -al /dev/ttyU* . as connection can't be made when the device is on the wrong ports, also when the device shows up on the desktop , try Rt click and eject the device

You could also try using the usb-modeswitch from 

[LIST]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package  ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]


Another problem is the connection appears to be working but the browser does not work , for a solution to this please look at this post 

[http://ubuntuforums.org/showthread.php?p=8951944#post8951944](http://ubuntuforums.org/showthread.php?p=8951944#post8951944)

---

### Post by Gonz_91 on 2010-03-13
Thank you very very much for your kind reply :)

I will try all of this out monday, since until then I'm a few hundred miles away from say modem, spending the weekend at home.

Once again, thanks a lot =D

---

