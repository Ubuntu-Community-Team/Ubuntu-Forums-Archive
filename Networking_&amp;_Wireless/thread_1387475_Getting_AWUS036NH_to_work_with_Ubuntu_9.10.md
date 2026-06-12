---
title: "Getting AWUS036NH to work with Ubuntu 9.10"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by CharlesA on 2010-01-21
I bought an Alfa Network AWUS036NH adapter that I want to use with Ubuntu 9.10 Desktop.

Unfortunately, it looks like it won't connect automatically and the install instructions don't make any sense to me.

I've installed from source before, but this is different. See here:

> Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

**5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat**
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
	
================================================================

The bolded part is what's confused me the most.

Any ideas would be great.

Thanks!

EDIT: [Link to the adapter.]("http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NH&Category=105463") Chipset is RT3070.

Found a few threads, but I'm not quite sure I understand.
[http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)
[http://ubuntuforums.org/showthread.php?t=1369806](http://ubuntuforums.org/showthread.php?t=1369806)
[http://ubuntuforums.org/showthread.php?t=1312717](http://ubuntuforums.org/showthread.php?t=1312717)

---

### Post by CharlesA on 2010-01-22
Would the other wireless driver need to be blacklisted before compiling the driver for the rt3070?

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by CharlesA on 2010-01-24
Got it working. I followed the guide (somewhat) that was posted here: [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)

Here's the steps I used:

1.  Copy driver for network card to Desktop
2.  Open a terminal
3.  sudo -i
4.  cd /home/ubuntu/Desktop/rt3070alfa
5.  tar -xf 036NH_2009_1110_Linux.tar.bz2
6.  cd 2009_1110_RT3070_Linux_STA_v2.1.2.0
7.  gedit os/linux/config.mk
8.  Change "HAS_WPA_SUPPLICANT=n" and "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n" to y
9.  make && make install
10. gedit /etc/modprobe.d/blacklist.conf and add:
a.  blacklist rt2x00usb
b.  blacklist rt2x00lib
c.  blackist rt2800usb
11. reboot

---

### Post by pdc on 2010-01-24
well done;

good work

---

### Post by TheDoctor54 on 2010-02-19
Nice post! 
But I think there's a shorter way to solve that problem :)

Actually I have an ALFA [COLOR=Red]AWUS036NH[/COLOR] and use it with [COLOR=Red]Ubuntu 9.10,[/COLOR] which I downloaded and installed 2 days ago. So I run Update Manager and now have the latest drivers and stuff installed, which is suggested by Update Manager. [COLOR=Red](No additional patch/drivers or downloads are required!)[/COLOR]

The adapter AWUS036NH should actually work out of box simple as just plug and play.
But the reason why it didn't do that is a simple conflict between the driver rt2800usb and rt2870sta which we simply can solve by this 3 following steps:

1. [COLOR=Blue]Launch Terminal - and copy&paste or type this code:[/COLOR]

  sudo gedit /etc/modprobe.d/blacklist.conf

2. [COLOR=Blue]The Blacklist - will popup and add this line:
[/COLOR]
  blacklist rt2800usb

3. [COLOR=Blue]Save the Blacklist file and reboot.[/COLOR]

  ENJOY AWUS036NH :D

So simple!

Feedbacks will be appreciated

---

### Post by Andreas Müller on 2010-03-03
Thanks Doctor54 - worked for me!

---

### Post by aztechclan on 2010-04-30
TheDoctor54, blacklist works for me too!  Thanks a bunch!

---

### Post by pyjnet on 2010-06-19
Hello,

I had just try the tip of Doctor54 on Ubuntu 10.04 on a new installation up to date, unfortunately, i have a problem when i boot with my ASUS036NH connected on an USB port, it freeze tha graphical mode...

i have this message in log :

Jun 19 14:14:40 localhost kernel: [   23.615413] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
Jun 19 14:14:40 localhost kernel: [   23.615424] 1. Phy Mode = 0
Jun 19 14:14:40 localhost kernel: [   23.615428] 2. Phy Mode = 0
Jun 19 14:14:40 localhost kernel: [   23.844299] ERROR!!! E2PROM: WRONG VERSION 0xff, should be 1
Jun 19 14:14:40 localhost polkitd[1066]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun 19 14:14:41 localhost anacron[1097]: Anacron 2.3 started on 2010-06-19
Jun 19 14:14:41 localhost anacron[1097]: Normal exit (0 jobs run)
Jun 19 14:14:41 localhost kernel: [   24.028287] 3. Phy Mode = 0
Jun 19 14:14:41 localhost kernel: [   24.028297] E2PROM error, hard code as 0xffff
Jun 19 14:14:41 localhost kernel: [   24.028388] ------------[ cut here ]------------
Jun 19 14:14:41 localhost kernel: [   24.028398] kernel BUG at /build/buildd/linux-2.6.32/drivers/staging/rt2870/common/../../rt2860/common/rtmp_init.c:1739!
Jun 19 14:14:41 localhost kernel: [   24.028406] invalid opcode: 0000 [#1] SMP 

in fact, there is no /Wireless in /etc 

I had test also the tip of CharlesA : same result for me :(

If anyone can help or have a tip for Ubuntu 10.04, he is welcome ):P

Pyjnet

---

