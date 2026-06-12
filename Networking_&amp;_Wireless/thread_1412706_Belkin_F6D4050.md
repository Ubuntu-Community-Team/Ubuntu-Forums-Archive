---
title: "Belkin F6D4050"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by stephenmac7 on 2010-02-21
I have a Belkin F6D4050 and I also have ndiswrapper and I would like to know how to use the adapter in ubuntu

---

### Post by jpl888 on 2010-02-21
Can you post the output of ```
lsusb
``` so we can see what chipset it is and help you?

---

### Post by stephenmac7 on 2010-02-21
where do I put the code?

---

### Post by jpl888 on 2010-02-21
In a terminal.

e.g. Applications -> Accessories -> Terminal

---

### Post by stephenmac7 on 2010-02-21
It says this-
No command '1susb' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
1susb: command not found

---

### Post by jpl888 on 2010-02-21
Type ```
sudo apt-get install usbutils
```

and try the original command again.

---

### Post by stephenmac7 on 2010-02-21
It says I already have it

---

### Post by jpl888 on 2010-02-21
I think you must've typed a one instead of a letter l the first time you typed "lsusb". Try it again with a letter l.

---

### Post by stephenmac7 on 2010-02-21
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:935a Belkin Components 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by stephenmac7 on 2010-02-21
I have a Logitech Mouse

---

### Post by stephenmac7 on 2010-02-21
I removed a usb now it says

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:935a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jpl888 on 2010-02-21
According to a few searches the chipset on that Belkin is an Ralink 2870. See the below link for a how to, post back if you're stuck.

[http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)

---

### Post by stephenmac7 on 2010-02-21
I get a few errors like error [1] & error [2]

---

### Post by jpl888 on 2010-02-21
Perhaps you could ellaborate a bit?

Is there no more accompanying information than that?

---

### Post by stephenmac7 on 2010-02-21
make -C /home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
make: *** [install] Error 2


How about that?

---

### Post by stephenmac7 on 2010-02-21
Thank you so much I value your time. :)

---

### Post by jpl888 on 2010-02-21
```
cannot stat `rt2870sta.ko': No such file or directory
```

Looks to be the main problem.

That is the module that should have been built by the preceding build process. 

Perhaps there was a build error earlier on.

Could you post the output of the previous ```
sudo make
```

command?

---

### Post by stephenmac7 on 2010-02-21
sudo make:
make -C tools
make[1]: Entering directory `/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSIRQRequest&#8217;:
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1068: warning: unused variable &#8216;net_dev&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1282: warning: unused variable &#8216;pid_number&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1624: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1625: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1626: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1627: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1633: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1667: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/stephen/Downloads/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [LINUX] Error 2

---

### Post by stephenmac7 on 2010-02-21
Sudo make: is not part of the code also how do you make those code boxes?

---

### Post by jpl888 on 2010-02-21
Click on the # sign in the editor window.

That first set of instructions doesn't look that good try these instead:-

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

I'm pretty technical and I don't like trying to setup wireless cards that don't have a decent native driver in Linux. My advice to you would be to get another card with a different chipset. 

If you post what makes and models of cards are available to you to buy I can tell you what will work well.

---

### Post by jpl888 on 2010-02-21
Have to go to bed and clean up the kitchen not necessarily in that order. Will pick it up tomorrow.

---

