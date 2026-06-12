---
title: "ASUS USB-N13 Wireless Network Adapter Not Working"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by hallandnash on 2011-01-11
As suggested by [chili555]("http://ubuntuforums.org/member.php?u=35909") I've created a new thread to try and get this thing working ...

 can't seem to get by the make stage, using either the driver in this thread or the newest one from ralink.

Here's the output:
     Code:
     ~/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ sudo make

make -C tools
make[1]: Entering directory `/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitRecv&#8217;:
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
make[2]: *** [/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2 
     Code:
     $ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
any help would be great

I've never gotten anything to install or work with this usb. Currently I have my internal wifi working.. but that's all

     Code:
     $ sudo modprobe rt2870sta
$ lsmod | grep rt2
rt2870sta             405890  0 
crc_ccitt               1351  1 rt2870sta
 $ dmesg | grep -i rt2
[  735.021326] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.

[  735.039687] usbcore: registered new interface driver rt2870 [URL="http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=1219783"]
[/URL]

---

### Post by chili555 on 2011-01-11
Tell me more about your internal card. Is it not performing correctly? Why did you want the Asus, N speeds? Or do you just love configuration, /etc files, pain and anger? (Just kidding!) Is the wireless switch on or off? Often, if the wireless switch is off, the USB wireless will also be blocked.

Modinfo tells us that rt2870sta is correct for your device:```
modinfo rt2870sta | grep 1784
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```

---

### Post by hallandnash on 2011-01-11
not sure what the internal card is in the laptop -- how can I find out?

I want the N, because of the speed .. the built in is G.

The wireless switch for the internal is on. (i've tried it both ways and the usb still won't power up (go green))

---

### Post by chili555 on 2011-01-11
Is there any better information, with the device plugged in here?```
sudo cat /var/log/syslog | grep -i rt2
```If the log is scant, try:```
sudo cat /var/log/syslog.1 | grep -i rt2
```On the other hand, if it's long, feel free to remove the repeats. We ought to see something informative in 20-25 lines.

Do you have an interface?```
iwconfig
```

---

### Post by hallandnash on 2011-01-13
don't ask me how or why .. but the usb is working now. 

I just booted up today and noticed it's green .. and it's working. Maybe any update I did sparked something, I dunno. I'm going to try and reboot and see if it still works

---

