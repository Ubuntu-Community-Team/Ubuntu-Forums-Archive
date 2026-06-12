---
title: "Errors compiling drivers for ralink RT2870 (no member named ‘fsuid’)"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by lakshman_ab on 2009-12-05
Ubuntu 9.10 *Karmic Kola *(32bit) on ASRock ION 330
Edimax EW-7711UTn Wireless nLite USB adaptor (RT2870)

Folks,
This is my first post! I'm new to Ubuntu but come from a Solaris development background. I'm getting compilation errors when trying to compile the RT2870 source downloaded from either EDIMAX or RALink as follows. The errors seem to suggest that my header files are out of synch with the downloaded source. Your thoughts on this would be appreciated.

/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1068: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1069: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1070: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1070: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1133: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.c:1134: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.o] Error 1
make[1]: *** [_module_/home/lab1301/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2

lab1301@ubuntu:~/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0$ [B]lspci | grep Network
[/B]*lab1301@ubuntu:~/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0$ *

lab1301@ubuntu:~/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0$ **iwconfig**
[I]lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
[/I]

Regards

Lakshman

---

### Post by chili555 on 2009-12-06
> The errors seem to suggest that my header files are out of synch with the downloaded source.Yes, indeed. Your headers are *too new* for this antique driver file, evidently built in 2008. I believe a newer version exists. Please check here: [http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870)

---

### Post by lakshman_ab on 2009-12-06
> **chili555 said:**
> Yes, indeed. Your headers are *too new* for this antique driver file, evidently built in 2008. I believe a newer version exists. Please check here: [http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870)


Thanks Chiii555.
I did go through the steps listed in that post but either got no joy or errors.  These are the steps I've just tried again.  Is _step 1_ the bit which fixes the header problem?
[U]
step 1[/U]
lab1301@ubuntu:~$ **sudo apt-get install build-essential linux-headers-generic**
[I][sudo] password for lab1301: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/I]

lab1301@ubuntu:~/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0$ [B]cd ~/Desktop
[/B]lab1301@ubuntu:~/Desktop$ 
lab1301@ubuntu:~/Desktop$ **tar -xvf ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0.WUSB100v2MOD.2.6.31.tar.bz2**
[I]tar: /home/lab1301/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0.WUSB100v2MOD.2.6.31.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
[/I]

lab1301@ubuntu:~/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0$** lsusb**
[I]Bus 001 Device 004: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 050d:0131 Belkin Components Bluetooth Device with trace filter
Bus 002 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lab1301@ubuntu:~/tmp/2008_1225_RT3070_Linux_STA_v2.0.1.0$ 
[/I]

---

### Post by chili555 on 2009-12-06
> tar: /home/lab1301/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0.WUSB100v2MOD.2 .6.31.tar.bz2: Cannot open: No such file or directoryDid you download the file referred to, attached to the post, actually, to your desktop before you began? Why can't tar find it?

---

### Post by chili555 on 2009-12-06
> Bus 001 Device 004: ID [COLOR="Red"]7392:7711[/COLOR] > chili@LAPTOP40:~$ modinfo rt2870sta 
filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E5C45807808E721690B4101
--- snip ---
alias:          usb:[COLOR="Red"]v7392p7711[/COLOR]d*dc*dsc*dp*ic*isc*ip*
I guess I am wondering if the built-in rt2870sta module works for you and others. If you do:```
sudo modprobe rt2870sta
```Is an interface created? Find out with:```
iwconfig
```

---

### Post by lakshman_ab on 2009-12-06
Thanks chili555.  It looks like it compiles now.  I did try the instructions in that post before I opened this thread but it didn't compile.  I must have done something wrong earlier.  Anyway, 

lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$ **sudo make**
[I]...
...
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
cp -f /home/lab1301/Downloads/T/2009_0820_RT2870_Linux_Sls -altr /home/lab1301/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko
-rw-r--r-- 1 root root 647207 2009-12-06 17:13 /home/lab1301/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko
TA_V2.2.0.0/os/linux/rt2870sta.ko /tftpboot
[/I]
The size of the binary is as follows: 

lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$ **file /home/lab1301/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko**
[I]/home/lab1301/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$[/I] 

lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$ **ls -altr /home/lab1301/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko**
[I]-rw-r--r-- 1 root root 647207 2009-12-06 17:13 /home/lab1301/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko
lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$ 

[/I][B]sudo modprobe rt2870sta
[/B]*gives no o/p*
lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$ **iwconfig**
[I]lo        no wireless extensions.
eth0      no wireless extensions.
ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-50 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.
[/I]
lab1301@ubuntu:~2009_0820_RT2870_Linux_STA_V2.2.0.0$ **modinfo rt2870sta **
[I]lab1301@ubuntu:~/Downloads/T/2009_0820_RT2870_Linux_STA_V2.2.0.0$ modinfo rt2870sta 
filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E5C45807808E721690B4101
[/I]snip xx
[I]alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*[/I]

The o/p from **lsusb** is:
[I]Bus 001 Device 004: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 050d:0131 Belkin Components Bluetooth Device with trace filter
Bus 002 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/I]
From the above o/p what is my ISB dev id?  Is it: *[COLOR=Red]7392[/COLOR]?*

I'm now following the instructions in the link from which I downloaded the source but first I'm off for a swim!

---

### Post by chili555 on 2009-12-06
> ra0 RT2870 Wireless ESSID:"" Nickname:"RT2870STA"
Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s
RTS thrff Fragment thrff
Link Quality=100/100 Signal level:-50 dBm Noise level:-97 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0Looks like you are all set! Enjoy the swim!!!> From the above o/p what is my ISB dev id? Is it: 7392?The ID is 7392:7711.

I see an issue in your post above, but it may be trivial. Let's see if Network Manager gets you connected (I suspect it will!) and, if so, I'll never tell anyone!

---

### Post by lakshman_ab on 2009-12-06
I'm sorted!!!
I didn't have to do anything else apart from entering the WEP key and unplugging the Ethernet cable.  I've now moved the router back to the living room next to my Sonos and NAS I'm getting 4 bars in the signal strength on Ubuntu and all looks kosher.  I had to re-enter the WEP key when the router restarted but will investigate and fix that post swim.  Thanks for putting me on the right track.
What is the issue with the post by the way?

---

### Post by chili555 on 2009-12-06
> What is the issue with the post by the way?Before I tell you, remember, don't fix what ain't broke. If you are connected and working, I wouldn't change a thing.

Looking at *modinfo rt2870*, it looks like the version is the one built-in to the kernel. Also, I do not see any *sudo make install*, so I wonder if you built, but did not actually install the module.

But, no matter, it works!

---

### Post by lakshman_ab on 2009-12-06
You are correct.  I didn't do a *sudo make install*. All I did was download and copy the config file across as instructed in the link you sent.

However, I do have a old Dell D610 laptop with the HDD on the way out and with the same Ubuntu software.  I'll disable the built in wireless adapter on that and see what exactly it takes to get the RT2870 USB wireless  adapter to work.  If the solution is documented here someone else might find it useful.  Will post tomorrow hopefully.

---

### Post by lakshman_ab on 2009-12-07
I just had this from Edimax tech support.  I've just tried it and it won't compile with the same errors which I logged earlier!  I've informed them of the compilation error.

Dear lakshman,
 
Have you downloaded it from the below link?
 
[http://www.edimax.co.uk/images/Image/Driver_Utility/Wireless/NIC/2009/RT3070_Linux_STA_v2.0.1.0.tar.zip](http://www.edimax.co.uk/images/Image/Driver_Utility/Wireless/NIC/2009/RT3070_Linux_STA_v2.0.1.0.tar.zip)
 
 
Kind regards,
 
Paul Chung
Edimax UK Technical Support

---

### Post by lakshman_ab on 2009-12-07
Chilli555 I've just tried the RT2870 adaptor on the dell laptop and it all works fine.  The steps I followed were:
1) sudo apt-get install build-essential linux-headers-generic
2) Disable built in wireless adaptor on laptop and confirm that there is no connection
3) Insert USB adaptor and enter WEP key.  This failed to connect.
4) Reboot laptop and it connected fine
5) Pull wireless adaptor out and connection broke as expected
5) Re-enable internal card and connection re-established

Obviously step 1 is not needed.  So it looks like as you suggested this adaptor will work with Ubuntu 9.10 straight out of the box as long as you've entered the WEP key and rebooted with the adaptor inserted.   All I've done here is shown my ignorance of Ubuntu!  Please feel free to correct me.  I'm now off to install SYBASE ASE15...

---

### Post by lakshman_ab on 2009-12-08
In response to my email saying that the source in the link he sent earlier doesn't compile I received this from Edimax support.  I've not tried the download though.

Dear Lakshman,
 
In this case, please download the linux source code from the chipset vendor&#8217;s website on below:
[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpBM0wyUnZkMjVzYjJGa05UVTFNalF6TVRVeE5TNTBaM285UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakJmTWpBd09URXlNRFE9Qw%3D%3D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpBM0wyUnZkMjVzYjJGa05UVTFNalF6TVRVeE5TNTBaM285UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakJmTWpBd09URXlNRFE9Qw%3D%3D)
 
I hope this helps!
 
 
Kind regards,
 
 
Paul Chung
Edimax Technology (UK) Ltd

---

### Post by chili555 on 2009-12-08
It makes for me with warnings, but no errors.

---

