---
title: "belkin usb"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by nobody914 on 2012-05-25
Hello everyone. I have a small problem that I need advice on. I am running kubuntu 12.4 and i have a toshiba l675 laptop with a realtech 8188ce wireless built in adapter. I do not like the 8188ce and have some problems with it in linux. I bought a belkin n750 db usb adapter and i want to get it working on my kubuntu install. Is there a way to make that happen either by finding the correct drivers or useing the windows install cd and getting that to work in linux.? My machince is dual boot with win 7 and the belkin works great in windows and now i want to get it working in kubuntu. Thanks.:guitar:

---

### Post by chili555 on 2012-05-26
> I bought a belkin n750 db usb adapter and i want to get it working on my kubuntu install. Is there a way to make that happen either by finding the correct drivers or useing the windows install cd and getting that to work in linux.? Probably. Plug it in and open a terminal and run and post:```
lsb_release -d
lsusb
```Thanks.

---

### Post by KenjaminK on 2012-08-04
> **chili555 said:**
> Probably. Plug it in and open a terminal and run and post:```
lsb_release -d
lsusb
```Thanks.

[QUOTE=Ken's Ubuntu System Terminal]
kenjamink@ubuntu:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS
kenjamink@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:1103 Belkin Components 
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 003: ID 045e:0730 Microsoft Corp. 
kenjamink@ubuntu:~$ 
[/QUOTE]

I have the same Belkin usb wireless adapter, the n750 db and I need to get it working. :) Any help would be greatly appreciated!

---

### Post by KenjaminK on 2012-08-04
This really sucks because every time I need to use the internet to solve the problem, I have to restart and boot into windows. ](*,)

[http://www.wikidevi.com/wiki/Belkin_F9L1103]("http://www.wikidevi.com/wiki/Belkin_F9L1103")

So, I've downloaded the driver listed from the above wiki, but the instructions are really convoluted.

First of all, there are two sets of instructions. One is "Quick Start.txt" and the other "Quick Start DPO.txt" They conveniently forgot to mention what DPO stands for or which set to follow depending on what circumstances. :rolleyes:

[QUOTE=Quick Start.txt]
RT3573 Linux Driver quick start		

====================
Check tools:  

====================
*Before install driver, please check already install compile tool and  kernel source code

1>Install compile tool
    $yum install gcc-c++

2>check kernel source code exists /usr/src/kernels/ "kernel name"

    Download your kernel source code
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/) 		
	or
    $yum install kernel-devel



====================
Build Instructions:  

====================
1> $tar -jxvf DPA_RT3573_LinuxSTA_V2.5.0.0.bz2
     go to "DPA_RT3573_LinuxSTA_vx.x.x.x" directory.
    


2> In Makefile
	 
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 
     define the linux kernel source include file path LINUX_SRC
	 
     modify to meet your need.


3> $make			
	
     # compile driver source code, need administrator.
	
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	 
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

4>go  MODULE folder
    $make install

5>
    $insmod UTIL/os/linux/rtutil3573sta.ko
    $ insmod MODULE/os/linux/rt3573sta.ko
    $ insmod NETIF/os/linux/rtnet3573sta.ko

6>$ifconfig ra0 up

7> unload driver    
    
     $ifconfig ra0 down

     $rmmod rtnet3573sta.ko
     $rmmod rt3573sta.ko
     $rmmod rtutil3573sta.ko
[/QUOTE]

[QUOTE=Quick Start DPO.txt]
RT3753 Linux Driver quick start		

====================
Check tools:  

====================
*Before install driver, please check already install compile tool and  kernel source code

1>Install compile tool
    $yum install gcc-c++

2>check kernel source code exists /usr/src/kernels/ "kernel name"

    Download your kernel source code
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/) 		
	or
    $yum install kernel-devel



====================
Build Instructions:  

====================
1> $tar -jxvf DPO_RT3573_LinuxSTA_vx.x.x.x.tar.bz2
     go to "DPO_RT3573_LinuxSTA_vx.x.x.x" directory.
    


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
	   	   
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
     ** Build for being controlled by WpaSupplicant with Ralink Driver
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make			
	
     # compile driver source code, need administrator.
	
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	 
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $make install
     #install driver
     #copy RT2870STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat

6>$vi /etc/rc.d/rc.local
     #input "ifconfig ra0 up"
    $reboot

7> unload driver    
    
     $ifconfig ra0 down

     $make uninstall
     $reboot


Note: If you want to change os/linux/config.mk setting, please remove driver and  reinstall.
[/QUOTE]

So, I at least found instructions and the driver, but can someone help me figure out how to follow these instructions? :confused:

---

### Post by chili555 on 2012-08-04
> **KenjaminK said:**
> So, I at least found instructions and the driver, but can someone help me figure out how to follow these instructions? :confused:Please get a temporary ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```In the DPO folder that was created when you extracted the bz2, drill down to os/linux and open the file config.mk with any text editor such as gedit and:> Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.All the text before and after these two lines remains unchanged. Proofread, save and close gedit.

I selected DPO because several other working Realtek drivers are labeled DPO. Now open a terminal:```
cd Desktop/DPO_RT3573_LinuxSTA_vx.x.x.x [COLOR="Red"]<--whatever and wherever you extracted[/COLOR]
sudo su
make
make install
modprobe rt3573sta
exit 
```If you encounter any errors, stop, post them here and we'll try to fix them.

---

### Post by killinghours on 2012-08-15
@chili555 

I've seen you on numerous topics helping others get their usb adapters working... and i've tried to resolve my by those posts from you... but I just can't get it working. 

I too have the belkin n750 and have followed your above instructions to the T but I don't get anything showing I have any sort of wireless device at all. 

Here's what I have so far. 

lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:1103 Belkin Components 
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 002 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse

```iwconfig: 

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

This is going in an old desktop. 

Not sure what else you'll need at this point. Your expertise would be greatly appreciated!!

Awaiting reply and guidance.

---

### Post by chili555 on 2012-08-15
Let's have a look at:```
sudo modprobe rt3573sta
dmesg | grep rt3
```Thanks.

---

### Post by killinghours on 2012-08-15
As requested...

```
zack@zack-PC:~$ sudo modprobe rt3573sta
[sudo] password for zack: 
zack@zack-PC:~$ dmesg | grep rt3
zack@zack-PC:~$ 
```I'm assuming this is bad as I don't get any output from it. :(

I have a poker tourny in about an hour (7 central time) and won't be available until afterwards. Thanks for the quick response and your efforts!

Edit** 

Also should have mentioned in the first post that this is on 12.04.

---

### Post by chili555 on 2012-08-15
It's good news and maybe bad news. You modprobed the driver and no error or warning emerged. Let's dig deeper; please be sure the device is inserted when you run:```
sudo modprobe rt3573sta
dmesg | grep -i rt2
iwconfig
rfkill list all
```Thanks.

---

### Post by killinghours on 2012-08-16
here you are sir...

```
zack@zack-PC:~$ sudo modprobe rt3573sta
[sudo] password for zack: 
zack@zack-PC:~$ dmesg | grep -i rt2
[  164.318650] rtusb init rt2870 --->
[  164.321064] usbcore: registered new interface driver rt2870
zack@zack-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

zack@zack-PC:~$ rfkill list all
zack@zack-PC:~$ 

```

Device is plugged into a usb port on the back of the machine and the port is working. (tested usb mouse on it)

This is where I got stuck with all other attempts as I get no output from these commands like I saw in other posts.

---

### Post by chili555 on 2012-08-16
I am suspicious that the driver you compiled doesn't actually cover your device:> ID [COLOR="Red"]050d:1103[/COLOR] Belkin ComponentsPlease post:```
modinfo rt3573sta | grep 1103
```What is the name of the file you compiled?

---

### Post by killinghours on 2012-08-16
you're up early...dogs got me up as you were posting.

```
zack@zack-PC:~$ modinfo rt3573sta | grep 1103
zack@zack-PC:~$ 
```I downloaded the package from the link provided by an earlier poster in this thread. 

see "linux driver" on the right hand side of the page. 
[http://www.wikidevi.com/wiki/Belkin_F9L1103](http://www.wikidevi.com/wiki/Belkin_F9L1103)

Edit** 

For clarity: DPO_RT3573_LinuxSTA_V2.5.0.0.tar.bz2

-------------------------------------------

As a side note, the .inf file directly from the install cd is "rt2870" and I have both it and the sys on hand if ndiswrapper would be a faster/easier route.

---

### Post by chili555 on 2012-08-16
> zack@zack-PC:~$ modinfo rt3573sta | grep 1103
zack@zack-PC:~$Ah, haaa! The driver doesn't (yet) cover your device! Let's try to fix that. Look in the folder you extracted and open the file common/rtusb_dev_id.c with any text editor, such as gedit. Add a line as I've highlighted:```
#endif /* RT35xx */
#ifdef RT3573
	{USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
	{USB_DEVICE(0x7392,0x7733)}, /* Edimax */
	[COLOR="Red"]{USB_DEVICE(0x050D,0x1103)}, /* Belkin */[/COLOR]
	{USB_DEVICE(0x0B05,0x17AD)}, /*ASUS */
#endif /* RT3573 */
	{ }/* Terminating entry */
```All of the text before and after remain unchanged. Proofread carefully twice, save and close gedit. Now recompile:```
cd Desktop/DPO_RT3573_LinuxSTA_vx.x.x.x [COLOR="Red"]<--whatever and wherever you extracted[/COLOR]
sudo su
modprobe -r rt3573sta
make clean
make
make install
modprobe rt3573sta
exit
```Any improvement?

---

### Post by killinghours on 2012-08-16
And bingo was his name-o!

You sir, are a gentleman and a scholar. I really appreciate your help on this... it would have taken me ages to figure this out. 

Thank you so much!

---

### Post by chili555 on 2012-08-16
Please don't forget that when a newer kernel image is installed by Update Manager, you'll need to recompile for the later kernel:```
cd Desktop/DPO_RT3573_LinuxSTA_vx.x.x.x [COLOR="Red"]<--whatever and wherever you extracted[/COLOR]
sudo su
make clean
make
make install
modprobe rt3573sta
exit
```Glad it's working. Have fun!

---

### Post by killinghours on 2012-08-16
Wont be updating this machine anytime soon, its for my son to play school games on and thats it. 

Again thanks for all you do!

---

### Post by seanelectron on 2013-02-26
I have installed Linux Mint 14 and I have the Belkin N750 db usb thing. I read all the details above, but some of the instructions involves downloading programs, how can I do that with only a non functioning usb adapter? I am not sure how I can access my internet with Linux. Can someone help me? I am using KDE.

---

### Post by chili555 on 2013-02-27
> **seanelectron said:**
> I have installed Linux Mint 14 and I have the Belkin N750 db usb thing. I read all the details above, but some of the instructions involves downloading programs, how can I do that with only a non functioning usb adapter? I am not sure how I can access my internet with Linux. Can someone help me? I am using KDE.First, let's verify some details before we proceed. We will get some details from the terminal. Insert the device and open a terminal Ctrl+Alt+t and run and post:```
lsb_release -d
lsusb
```Maybe there is an easier way.

---

### Post by synde44 on 2013-04-08
is there a possibility this soloution will work with ubuntu aswell not just kubuntu?

---

### Post by chili555 on 2013-04-08
> **synde44 said:**
> is there a possibility this soloution will work with ubuntu aswell not just kubuntu?Nope. The desktop environment and the wireless driver and Network Manager are all different things. The k in kubuntu stands for KDE which is just a way to display all the graphical items you use. The underlying drivers, kernel, etc. are all the same.

---

### Post by synde44 on 2013-04-08
ok thanks anyways ive been having a hard time getting the 900 model to work but it uses the same chipset

---

### Post by synde44 on 2013-04-09
so i used the code sudo apt-get install kbuntu-desktop and installed that i then insured that my computer recognized the device but when i tried your first set of instructions and build the generic header it said no file found.:confused:

---

### Post by chili555 on 2013-04-09
Please be sure you have an ethernet connection and run the command again. Copy and paste out of the terminal to post the exact error here.

---

### Post by synde44 on 2013-04-12
bash: cd: home/sydney/desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO: No such file or directory
  thats    the error

---

### Post by chili555 on 2013-04-12
In the terminal, it is not desktop, it is **D**esktop. Please try again.

---

### Post by synde44 on 2013-04-17
so i went through followed your instructions and it didnt get me anywhere ....i then followed your set of second instructions about modifing the file and still nothing ...when i put everything in the terminal it went through fine but it wont recognize the device. :confused: past my warranty so im in this for the long run

---

### Post by chili555 on 2013-04-18
> **synde44 said:**
> so i went through followed your instructions and it didnt get me anywhere ....i then followed your set of second instructions about modifing the file and still nothing ...when i put everything in the terminal it went through fine but it wont recognize the device. :confused: past my warranty so im in this for the long runPlease post:```
lsusb

```

---

### Post by synde44 on 2013-04-19
Bus 001 Device 003: ID 050d:1103 BelkinComponents F9L1103 N750 DB 802.11abgn 2x3:3 [Ralink RT3573]
Bus 003 Device 002: ID 0a5c:4500Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 006 Device 002: ID 413c:3200 DellComputer Corp. Mouse
Bus 001 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 003 Device 003: ID 0a5c:4502Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 004: ID 0a5c:4503Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 003 Device 005: ID 0461:4d75 PrimaxElectronics, Ltd Rocketfish RF-FLBTAD Bluetooth Adapter

---

### Post by chili555 on 2013-04-19
> [COLOR="#FF0000"]050d:1103[/COLOR] BelkinComponents F9L1103 N750 DB 802.11abgn 2x3:3 [Ralink RT3573]Your device is supported by the compiled driver rt3573sta:```
$ modinfo Desktop/Forum/test/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/rt3573sta.ko
filename:       /home/chili/Desktop/Forum/test/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/rt3573sta.ko
version:        2.5.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     8ABC831F2D99D3C564A9FFA
alias:          usb:v0B05p17ADd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="#FF0000"]050D[/COLOR]p[COLOR="#FF0000"]1103[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*
<snip>

```Did it compile correctly? We'll find out by checking for errors or warnings:```
sudo modprobe rt3573sta
dmesg | grep rt3
iwconfig
```

---

### Post by Br3le3 on 2013-04-21
[COLOR=#000000]I just registered to thank you chili your instructions were very helpful[/COLOR]

---

### Post by synde44 on 2013-04-21
sydney@sydney-GA-78LMT-S2:~$ sudo modprobe rt3573sta
FATAL: Module rt3573sta not found.
sydney@sydney-GA-78LMT-S2:~$ dmesg | grep rt3
sydney@sydney-GA-78LMT-S2:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

---

### Post by chili555 on 2013-04-21
> **synde44 said:**
> sydney@sydney-GA-78LMT-S2:~$ sudo modprobe rt3573sta
FATAL: Module rt3573sta not found.
sydney@sydney-GA-78LMT-S2:~$ dmesg | grep rt3
sydney@sydney-GA-78LMT-S2:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.Please return to post #5 above and retrace your steps. If you have no rt3573sta module, then you have missed a step or some step has ended in an error. Please tell us the result of *each step* as you take it. When we see what went wrong, we'll correct it and move forward.

---

### Post by synde44 on 2013-04-22
sydney@sydney-GA-78LMT-S2:~$ cd /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO
sydney@sydney-GA-78LMT-S2:~/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO$ sudo su
[sudo] password for sydney: 
root@sydney-GA-78LMT-S2:/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# make
make -C tools
make[1]: Entering directory `/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools'
/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/Makefile
make -C /lib/modules/3.8.0-19-generic/build SUBDIRS=/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
cp -f /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/rt3573sta.ko /tftpboot
root@sydney-GA-78LMT-S2:/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# make   install
make -C /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
make[1]: Entering directory `/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3573sta.ko /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.8.0-19-generic
make[1]: Leaving directory `/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux'
root@sydney-GA-78LMT-S2:/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# modprobe rt3573sta
root@sydney-GA-78LMT-S2:/home/sydney/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# exit
exit
sydney@sydney-GA-78LMT-S2:~/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO$

---

### Post by synde44 on 2013-04-22
still a no   go

---

### Post by chili555 on 2013-04-22
> # modprobe rt3573staAs you can see, now you got the module to load without error. Let's troubleshoot:```
sudo modprobe rt3573sta
dmesg | grep -i -e rt3 -e rt2
iwconfig
```Thanks.

---

### Post by synde44 on 2013-04-22
sydney@sydney-GA-78LMT-S2:~$ sudo modprobe rt3573sta
[sudo] password for sydney: 
Sorry, try again.
[sudo] password for sydney: 
sydney@sydney-GA-78LMT-S2:~$ dmesg | grep -i -e rt3 -e rt2
[  123.541414] rtusb init rt2870 --->
[  123.541506] usbcore: registered new interface driver rt2870
sydney@sydney-GA-78LMT-S2:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


sydney@sydney-GA-78LMT-S2:~$

---

### Post by Br3le3 on 2013-04-27
Hi chili... I recently installed another Ubuntu based OS running  12.04 (backbox) and I've gone through all the necessary steps to get the driver installed but when I make the file I receive an Error 2.

/lib/modules/3.2.0-36-generic/build: No such file or directory. stop

The directory does in fact exist but the file "build" doesn't, obviously I'm new with Linux and I'm lost. Any ideas? Thanks !!

---

### Post by chili555 on 2013-04-27
> **Br3le3 said:**
> Hi chili... I recently installed another Ubuntu based OS running  12.04 (backbox) and I've gone through all the necessary steps to get the driver installed but when I make the file I receive an Error 2.

/lib/modules/3.2.0-36-generic/build: No such file or directory. stop

The directory does in fact exist but the file "build" doesn't, obviously I'm new with Linux and I'm lost. Any ideas? Thanks !!That's a sure sign that the necessary prerequisites are not all installed:```
sudo apt-get install --reinstall build-essential
sudo apt-get install --reinstall linux-headers-generic
```

---

### Post by synde44 on 2013-04-29
so whats the diognosis doc chili ...will my usb wifi recever ever work?

---

### Post by cesar.ramsan on 2013-05-25
This post in the Arch Linux Forums might be a good reference too. 

[https://bbs.archlinux.org/viewtopic.php?id=149329](https://bbs.archlinux.org/viewtopic.php?id=149329)

---

### Post by Vorgon on 2013-07-12
I would just like to thanks to those who figured this out. I was able to get my wireless adapter working with these steps. Thanks all.

---

