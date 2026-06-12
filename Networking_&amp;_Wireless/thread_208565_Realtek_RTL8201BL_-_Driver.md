---
title: "Realtek RTL8201BL - Driver ??"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by BoilingPoint on 2006-07-03
I've an Asrock 939A8X-M motherboard
It uses the '10/100 Ethernet LAN PHY' Built In Lan Controller.

I've tried various different Linux Distributions and none of them appear to properly detect this Lan controller properly. I've even tried the latest 64-Bit build of Ubuntu, but am currently using v5.50 32-bit Version.

I'd be greatful if anyone could point me in the right direction ... the chip works fine as running through XP (as I am at the moment) it works a treat. I really want to get away from Bill Gates and his buggy OS, but this is holding me back.

Thanks in advance ... Lee

---

### Post by BoilingPoint on 2006-07-04
I had an email from Asrock this morning.
Asking me to go to the following location for updated drivers.

[http://www.uli.com.tw/eng/support/drivers.php](http://www.uli.com.tw/eng/support/drivers.php)  chipset: Uli m1689

Been there now and downloaded all the linux drivers (the appropriate one for me is v2.6xx).
Then returned to Ubuntu v 5.50 and read the readme file. started to follow the installation instructions (which involved re-compiling the linux kernel). However the path that was in the readme wasn't the same as the path in ubuntu's linux. So I was unable to proceed.

Has anyone done this before and if so could you please send a linux beginner a detailed step by step set of instructions please.

Thank you... Lee

---

### Post by BoilingPoint on 2006-07-04
Sorry to double post, thought the readme file might be of some use to someone that knows what their doing....

The driver is called :- uli526x.c

The Installation is as follows :-

1. ULi M5263 10/100M Ethernet Controller Core
2. File Signature
3. Installation Guide 
4. Revision History
5. Disclaimer


1. ULi M5263 10/100M Ethernet Controller Core
============================================= 
You can use command
        /sbin/lspci -n                          ......  (didn't work)
    or
        cat /proc/pci | grep 5263          ...... (didn't work) 
to determine whether ULi M5263 Ethernet controller exists in your 
system. If yes, simply follow the steps below to install the driver.

This driver is dedicated to support ULi M5263 10/100M Ethernet 
Controller under Linux platform.

Any improper use of this module, such as combining it with different 
hardware and/or software environment, may produce unpredicable results.
The author of the driver and its property owner do not have 
responsibility for any property lose or damage.


2. File Signature
====================
/driver/uli526x.c	           source codec c file
readme.txt                            this file
====================
/sample/Kconfig.in                 configuration sample file
/sample/Makefile.in                sample makefile

3.Installation Guide
====================
To install the driver, you should reconfigure and recompile your Linux 
kernel as follows:

Make sure your kernel version number is 2.6.x.

Copy uli526x.c to /usr/src/linux-2.6.x/drivers/net/tulip/, and modify the
following file in this directory. (Make a backup of them.)

                  ................ (the path only went as far as .../usr)


1.Kconfig.in
add the following lines to Kconfig.in file.(refer to the Kconfig.in file we provide to you)

config ULI526X
	tristate "ULi M526x controller support"
	depends on NET_TULIP && PCI
	select CRC32
	---help---
	  This driver is for ULi M5261/M5263 10/100M Ethernet Controller
	  (<http://www.uli.com.tw/>).

	  To compile this driver as a module, choose M here.

2.Makefile
add the following lines to Makefile.(refer to the Makefile we provide to you)

obj-$(CONFIG_ULI526X)	+= uli526x.o
------------------------------------
Install as a kernel module
------------------------------------

  Step 1: 
        Change directory to /usr/src/linux-2.6.x
        Use the command "make menuconfig" or "make xconfig", and make 
        sure "ULi M526x controller support" is set as module.
	
	Example:	
	Select "Device Drivers"
        Select "Networking support"
        Select "Ethernet (10 or 100Mbit)"
	Select "Tulip family network device support"
	Unselect "DECchip Tulip (dc2114x) PCI support"
        Select "ULi M526x controller support" as "m"

  Step 2:
        Select "Loadable module support", and unselect "Set version information
        on all module symbols"
	
	Before exit, save your configration.


  Step 3:
	make modules
	make modules_install

  Step 4:
	rmmod tulip
        modprobe uli526x	

 Then, you can bind any protocol into M5263 driver and use it.

------------------------------------------
Install as a part of linux kernel
------------------------------------------

  Step 1:
        Change directory to /usr/src/linux-2.6.x
        Use the command "make menuconfig" or "make xconfig", and make 
        sure "ULi M526x controller support" is set as kernel.
	
	Example:	
	Select "Device Drivers"
        Select "Networking support"
        Select "Ethernet (10 or 100Mbit)"
	Select "Tulip family network device support"
	Unselect "DECchip Tulip (dc2114x) PCI support"
        Select "ULi M526x controller support" as "y"
	

  Step 2:
        Select "Loadable module support", and unselect "Set version information
        on all module symbols"
	
	Before exit, save your configration.


  Step 3:
	make
	cp arch/i386/boot/bzImage /boot

  Step 4:
	If you use grub to boot your linux, then
	  1) Modify the file /etc/grub.conf by adding
		title 2.6.x
		root (hd0,2)
		kernel /boot/bzImage ro root=/dev/hd1
		The disk partition where your linux resides in, 
                for example: /dev/hda1
	  2) Reboot and select the kernel 2.6.x 
  
 Then, you can bind any protocol into M5263 driver and use it.

---

### Post by BoilingPoint on 2006-07-06
So this is the level of support one can expect from Ubuntu then is it ??

Thanks for nothing guys !!

---

### Post by BoilingPoint on 2006-07-13
Ok... replaced the problem with a nice new Network card.
Good news ... the card is being detected and appears to be setup properly.
Bad news ... my router says it's connected, but also says it's not ready to surf. As you can see it works perfectly under XP.
Reading some bit's online it would appear that no special commands or setup instructions need to be sent to the router, so my question is a simple one.

How do I establish a connection with my router that will allow me to surf the web. I can get my router config page, but nothing else. And yes the router is setup correctly, I've been to the manufacturers site and checked it out. I have also asked a similar question there and am getting some feedback, but figured that it won't hurt to have some here too.

If your interested the link is [http://adsltech.com/portal/forum/forum_posts.asp?TID=6650&TPN=1](http://adsltech.com/portal/forum/forum_posts.asp?TID=6650&TPN=1)

Thank you...

---

### Post by king_arthur on 2006-07-14
Is your IP collected dynamically or is it fixed?
Can you ping-out an IP directly into the Internet?

If yes, than your DNS is not setup properly.

Try adding the DNS address (IP xxx.xxx.xxx.xxx) into the Ubuntu Network setup. Either your router's IP or an external DNS.

That normally does the trick.

---

### Post by BoilingPoint on 2006-07-14
The IP is Dynamic.
I'll try that and let you know what happens
Thank you for your reply...

---

### Post by BoilingPoint on 2006-07-14
The IP is already inserted into the DNS section of Networking. Also tried Pinging the router and that was ok too. But still no Connection. :(

---

### Post by king_arthur on 2006-07-14
When you say "no connection" what do you exactly mean??
As you just said you can ping into the router hence, **THERE IS A CONNECTION**.

You just cannot surf the web, that is the problem, please confirm this by pinging directly into a known (external) IP.

If that is the case, you can try modifying your /etc/resolv.conf file and write there the IP of your DNS.
You can find more info at **$man resolv.conf**.

BTW, what DNS are you picking up?

---

### Post by BoilingPoint on 2006-07-14
That's right, I have a connection (sorry) but can't surf the web. the address I've attempted to ping is 192.168.1.1 which is also the same one the DNS is using.
I'll try pinging an external address and get back to you on it.
Thanks again...

---

### Post by BoilingPoint on 2006-07-14
Ok sorted.... I disabled IPv 6 as per instructions at [http://adsltech.com/portal/forum/forum_posts.asp?TID=6650&TPN=1](http://adsltech.com/portal/forum/forum_posts.asp?TID=6650&TPN=1)
Thanks to all involved with helping me out on this one.

Now then... I've a new problem hehehe

Email.... I've configured the default email package for both Gmail and my ISP (Demon) and yes it's correct as per the instructions on both websites, however they don't work ... the same is true of GAIM and my MSN and Google IM profiles.

Are there specific ports that need forwarding on my router?

Speaking of which why is it that the router never holds the port forwarding information? Every time I reboot I need to log back into my router and tell it all over again what ports I need forwarding .. and yes I've selected the save option in advanced every time. I could understand if the router was turned off but it's always on.

Sorry for bombarding you with questions but I finally feel like I'm getting somewhere. Oah' and thanks to all the help thusfar...

---

