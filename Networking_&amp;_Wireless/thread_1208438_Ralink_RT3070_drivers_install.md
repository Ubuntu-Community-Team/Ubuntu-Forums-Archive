---
title: "Ralink RT3070 drivers install?"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by scarfays on 2009-07-09
hello  
 I buy a USB stick ZIONCOM WL 0162  
 with RT3070L chipset and RT3070 drivers  
 I use mainly for injection Aicrack-ng  
 installing the RT3070 drivers as explained on this tutorial: [http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)  
 the problem is after installation airodump-ng always scanned the channels 11 and not other channels  
 how to correctly install the RT3070 driver?  
 I do like the tutorial [http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage) for RT2870 or not?  
 it's been a week trying to install but it works not  
 thank you for your help

---

### Post by Tony37 on 2009-09-26
I have the Classmate 2Go (CTL model NL1) with the Ralink RT3070. This system has Ubuntu 8.10. Initially wifi did not work.

To make it work, download the driver from [http://www.ralinktech.com](http://www.ralinktech.com) -> software -> linux -> RT3070USB(RT307x). 

First you must use tar -jxf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2 which will extract the contents into a folder with the same name (except .bz2). Go into this folder. There is a file 'README_STA_usb'. Follow the instruction in section: "build instructions" starting from #3. (You don't need wpa_supplicant).

In #4, you should run make and then make install (as root). 

There is a problem with the make install. It places a file RT3070STA in /etc/Wireless. However, the driver is still looking for file RT2870STA.
You need to make a symbolic link ln -s RT3070STA RT2870STA. 

Restart and it should work.

---

### Post by sundeepprakash on 2010-06-12
Tony37, nice instructions, although I'm not through yet. Would love some help.

I have Ubuntu 10.0.4 on a Pentium 4, 2GB machine. Trying to install the Medialink MWN-USB150N Wireless-N USB Adapter. It has the RT3070 chipset. I followed the instructions in the driver's README_STA_usb file. As Tony37 says, in the "sudo make install" step, it was getting an error finding the RT3070.dat file - instructions with the driver seem to be for the 2870 chipset. I simply did "ln -s RT2870.dat RT3070.dat". That got me past make install.

Next step, according to the  readme is:

6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
So, since "uname -a" tells me  that my machine is (pardon the machine name, it's for my young kids, getting em started on Ubuntu early :-):
"Linux fluffer-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux"
I ran insmod, but I get "-l unknown symbol in module". dmesg shows the following (shown below). Any ideas how to proceed at this point? 

Thanks much,

Sundeep

[ 2037.050104] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 2037.059421] rtusb init --->
[ 2037.059487] usbcore: registered new interface driver rt2870
[ 2037.136746] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin
[ 2037.390807] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6573.423981] rt3070sta: module license 'unspecified' taints kernel.
[ 6573.423990] Disabling lock debugging due to kernel taint
[ 6573.424401] rt3070sta: Unknown symbol usb_alloc_urb
[ 6573.424703] rt3070sta: Unknown symbol usb_free_urb
[ 6573.425559] rt3070sta: Unknown symbol usb_register_driver
[ 6573.425966] rt3070sta: Unknown symbol usb_put_dev
[ 6573.426098] rt3070sta: Unknown symbol usb_get_dev
[ 6573.426355] rt3070sta: Unknown symbol usb_submit_urb
[ 6573.426959] rt3070sta: Unknown symbol usb_control_msg
[ 6573.427390] rt3070sta: Unknown symbol usb_deregister
[ 6573.427991] rt3070sta: Unknown symbol usb_kill_urb
[ 6573.428126] rt3070sta: Unknown symbol usb_buffer_free
[ 6573.429070] rt3070sta: Unknown symbol usb_buffer_alloc
[ 7157.876622] rt3070sta: Unknown symbol usb_alloc_urb
[ 7157.876791] rt3070sta: Unknown symbol usb_free_urb
[ 7157.877280] rt3070sta: Unknown symbol usb_register_driver
[ 7157.877791] rt3070sta: Unknown symbol usb_put_dev
[ 7157.878030] rt3070sta: Unknown symbol usb_get_dev
[ 7157.878490] rt3070sta: Unknown symbol usb_submit_urb
[ 7157.879545] rt3070sta: Unknown symbol usb_control_msg
[ 7157.880381] rt3070sta: Unknown symbol usb_deregister
[ 7157.881500] rt3070sta: Unknown symbol usb_kill_urb
[ 7157.881747] rt3070sta: Unknown symbol usb_buffer_free
[ 7157.882867] rt3070sta: Unknown symbol usb_buffer_alloc
[ 9378.393067] rt3070sta: Unknown symbol usb_alloc_urb
[ 9378.393253] rt3070sta: Unknown symbol usb_free_urb
[ 9378.393730] rt3070sta: Unknown symbol usb_register_driver
[ 9378.394085] rt3070sta: Unknown symbol usb_put_dev
[ 9378.394217] rt3070sta: Unknown symbol usb_get_dev
[ 9378.394473] rt3070sta: Unknown symbol usb_submit_urb
[ 9378.395070] rt3070sta: Unknown symbol usb_control_msg
[ 9378.395502] rt3070sta: Unknown symbol usb_deregister
[ 9378.396214] rt3070sta: Unknown symbol usb_kill_urb
[ 9378.396439] rt3070sta: Unknown symbol usb_buffer_free
[ 9378.397459] rt3070sta: Unknown symbol usb_buffer_alloc

---

### Post by sundeepprakash on 2010-06-13
The instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070) worked for me eventually. It was only a matter of disabling the rt2800usb driver, exactly as chili555 says.

Net result: If you use the 
[B]Medialink - Wireless N USB Adapter - 802.11n - 150Mbps -Windows 2000 / XP / Vista 64-Bit /128-Bit Windows 7 Compatible
[/B]USB adapter, which I believe is a very popular one, then it does work with Lucid Lynx without needing to compile anything - simply disable the rt2800usb driver that's all

---

### Post by Yuseinov on 2012-07-11
I have widemac N96000 wireless adapter. I can't instal drivers. Chipset is rt3070.

---

