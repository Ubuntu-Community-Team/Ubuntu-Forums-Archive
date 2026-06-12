---
title: "Can't compile RT25USB-SRC-V2.0.8.0!!"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by marcopolos on 2009-04-14
Hey guys

I'm totally new to Ubuntu/Linux, but i think it is about time to switch, although this is more complicated than expected! i've got intrepid 8.10 on acer aspire 6920g.

Anyway, i'm trying to compile a source to get my USB wireless card working asap. i also wanted to learn how to use backtrack, so i will need the injection packages.

i've been reading posts for two days and still can't compile the drivers, so i read the readme file:

* README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

===============================================================================================
ModelName:
===========
RT2500USB

===============================================================================================
Driver lName:
===========
rt2570.ko

===============================================================================================
Ralink Hardware:
===========
Ralink 802.11b/g wireless network card.

===============================================================================================
Description:
=============
This is a linux device driver for Ralink RT2500USB b/g WLAN Card.
This driver implements basic 802.11 function. 
Infrastructure and Ad-hoc mode with open or shared or wpapsk or wpa2psk authentication method.
WEP-40 and WEP-104 or tkip or aes encryption. 


===============================================================================================
Compatibility:
===================
Testing has been done with LinEX kernel 2.6.9, Fedora Core 3.
You may encounter some rough edges when working with recent other Linux kernels branch.


===============================================================================================
FILE LAYOUT:
=============
*.c		    : c files
*.h		    : header files                   
Makefile.6		:Makefile for kernel 2.6
Makefile.4		:Makefile for kernel 2.4
./LINUX_RACONFIG_Vx.x.x.x  : source code for utility RaConfig2500 version x.x.x.x
./LINUX_RACONFIG_Vx.x.x.x/bin/LINUX/RaConfig2500  : utility RaConfig2500

===============================================================================================
Build Instructions:  
====================
0) $dos2unix *
      $chmod 644 *
      $chmod 755 Configure

1) cp Makefile.x Makefile               // x is your kernel

2) $make
3) $insmod rt2570.ko     # Insert driver module
4) $ifconfig rausb0 up  # Bring up device 
5) $dhclient rausb0  # Get network IP address

  Note: Script functionality:
  Configure       retrive linux version 
6) ./LINUX_RACONFIG_Vx.x.x.x/bin/"Linux"/RaConfig2500

if lack of libstdc++.so.6, cp ./LINUX_RACONFIG_Vx.x.x.x/libstdc++.so.6 /usr/lib

7)Edit(or add the line) in /etc/modules.conf
   alias rausb0 rt2570

8) Create and edit 'ifcfg-rausb0' file in /etc/sysconfig/network-script/
   DEVICE='rausb0'
   ONBOOT='yes'
   BOOTPROTO='dhcp' 

===============================================================================================
CONFIGURATION:  
====================
RT2500 driver can be configured via following interfaces, 
i.e. i)RaConfig2500, ii)wireless extension,
i) RaConfig2500 is utility for rt25usb.

ii)  Wireless extension usage please refer to man page of 'iwconfig', 'iwlist' and 'iwpriv'. 
     Here is definition for private command 'iwpriv'
-------------------------------------------------------------------------------------------------------
NAME
       iwpriv - configure optionals (private) parameters of a wireless network
       interface
	
SYNOPSIS
       iwpriv [interface]
       iwpriv [interface] [parameters] [val]


DESCRIPTION 
[interface]      [parameters]             [val]                    explaination
-----------    -----------------     ----------------         --------------------------------
rausb0		    auth		  1~5			 1:Open
								 2:Shared
								 3:WPAPSK
								 4:WPA2PSK
								 5:WPANONE
								
rausb0		    psm		  	  0~1			 0:Continuous wake up
								 1:power safe mode

rausb0		    enc			  1~4			 1:none
								 2:wep
								 3:tkip
								 4:aes
								
rausb0		    wpapsk		  8~64 chars		 WPAPSK password


===============================================================================================
EXAMPLE:  
====================
Example I: Config STA to link with AP and OPEN/NONE(Authentication/Encryption)
	1. iwconfig rausb0 mode Managed
	2. iwconfig rausb0 key off
	3. iwconfig rausb0 essid "AP's SSID"

Example II: Config STA to link as Ad-hoc mode and OPEN/NONE(Authentication/Encryption)
	1. iwconfig rausb0 mode ad-hoc
	2. iwconfig rausb0 key off
	3. iwconfig rausb0 essid "Desired SSID"
	
Example III: Config STA to link with AP and OPEN/WEP(Authentication/Encryption). 
            Default Key ID = 3
	1. iwconfig rausb0 key [3]
	2. iwconfig rausb0 key s:abcde
	3. iwconfig rausb0 essid "AP's SSID"
	
Example IV: Config STA to link with ad-hoc mode and WPAPSK/TKIP(Authentication/Encryption)
            WPA PreShared-Key is 12345678
        1. iwconfig rausb0 mode ad-hoc
        2. iwpriv rausb0 auth 4
	3. iwpriv rausb0 enc 3
	4. iwconfig rausb0 essid "Desired SSID"
	5. iwpriv rausb0 wpapsk 12345678
	6. iwconfig rausb0 essid "Desired SSID"
	
Example V: Config STA to link with AP and WPAPSK/AES(Authentication/Encryption)
            WPA PreShared-Key is 12345678
	1. iwpriv rausb0 enc 4
	2. iwpriv rausb0 auth 3
	3. iwconfig rausb0 essid "AP's SSID"
	4. iwpriv rausb0 wpapsk 12345678
	5. iwconfig rausb0 essid "AP's SSID"
	
Example VI: Config STA to link with AP and WPA2PSK/TKIP(Authentication/Encryption)
            WPA PreShared-Key is 12345678
	1. iwpriv rausb0 enc 3
	2. iwpriv rausb0 auth 4
	3. iwconfig rausb0 essid "AP's SSID"
	4. iwpriv rausb0 wpapsk 12345678
	5. iwconfig rausb0 essid "AP's SSID"
	
p.s Step 2 is part of generating wpapsk password and is necessary.

Ok, so right after typing

dosunix*

i get

marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ dos2unix*
bash: dos2unix*: command not found

i already installed tofrodos, so i typed

marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ dos2unix .c
dos2unix: Unable to access file .c.
marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ dos2unix .h
dos2unix: Unable to access file .h.

as it said in the readme, and nothing happened. i decided to go on with the following instructions  and seemed to be fine until "make":

marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ chmod 644 *
marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ chmod 755 Configure
marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ cp Makefile.6 Makefile
marco@ubuntu:~/RT25USB-SRC-V2.0.8.0$ make
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/marco/RT25USB-SRC-V2.0.8.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/marco/RT25USB-SRC-V2.0.8.0/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/marco/RT25USB-SRC-V2.0.8.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2

i presume that chmod 644 is also followed by something that i'm missing. as you can see this is horrible, because i spent 2 days and there's no way to bring it forward..

thanks in advance to all of you, and congratulations for this amazing community

---

### Post by chili555 on 2009-04-14
> i presume that chmod 644 is also followed by something that i'm missingNope. You had it in there, it was the *****, which is a wildcard symbol. That means, 'Change the permissions for everything in the current directory to user can read and write and group and root can read only. When the prompt popped back with no comment or error, that meant, 'Command executed perfectly, sir. No errors or warnings to report.'> there's no way to bring it forward..Indeed.

You can get rid of the error you quoted with: ```
KBUILD_NOPEDANTIC=1 make
```But that just exposes another 20 errors and so on. This was written in mid-2006, which, in Linux years is a half century. I sincerely doubt it will ever compile.

---

### Post by marcopolos on 2009-04-14
oh no!!

thanks a lot for replying. the chipset is Ralink's RT2500..is there any way to get some drivers for it? and will they work with the superusb a-20? you can check the specs on:


[http://cgi.ebay.ca/38-5dBm-802-11b-g-WIFI-USB-CPE-Antenna-RANGE-EXTENDER_W0QQitemZ110290826955QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item110290826955&_trksid=p3286.c0.m14&_trkparms=72%3A1215%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318](http://cgi.ebay.ca/38-5dBm-802-11b-g-WIFI-USB-CPE-Antenna-RANGE-EXTENDER_W0QQitemZ110290826955QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item110290826955&_trksid=p3286.c0.m14&_trkparms=72%3A1215%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318)

another thing is my built in Intel 4965agn; it works fine excepting my wifi is set on channel 13, so it's not picked up by my connection either..

thanks again!!

---

### Post by chili555 on 2009-04-14
> my built in Intel 4965agn; it works fine excepting my wifi is set on channel 13Now that I think we might be able to fix...maybe. I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268388](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268388) and was especially interested in this part:> I was removing and reinserting cfg80211 on the command-line to adjust the ieee80211_regdom param. What I didn't realise is that it's case-sensitive, so the correct command is:

modprobe cfg80211 ieee80211_regdom=JP

I was using lower-case - "=jp". I've tried "=AU" (Australia) but it doesn't work.

Using the correct case has now allowed me to select channel 13 with iwconfig, but with the ieee80211_regdom set, the network-manager tools aren't seeing any wireless networks at all.So let's open a terminal and do:```
sudo rmmod -f cfg80211
sudo modprobe cfg80211 ieee80211_regdom=JP
sudo modprobe iwlagn
sudo ifconfig wlan0 up
```Is your 4965 working now?

---

### Post by marcopolos on 2009-04-15
It didnt work:

marco@ubuntu:~$ sudo rmmod -f cfg80211
[sudo] password for marco: 
ERROR: Removing 'cfg80211': No such file or directory
marco@ubuntu:~$ sudo modprobe cfg80211 ieee80211_regdom=JP
marco@ubuntu:~$ sudo modprobe iwlagn
marco@ubuntu:~$ sudo ifconfig wlan0 up

and then i turned back on the wireless connections and still the same..thing is if there's no "cfg80211" then it might be something else? not sure

really appreciate your help here

---

### Post by chili555 on 2009-04-15
> and then i turned back on the wireless connections Are you saying you did the commands with the wireless switch *off*? Please turn the switch on, let that LED blink and try these commands:```
sudo rmmod -f lbm_cw-cfg80211
sudo modprobe lbm_cw-cfg80211 ieee80211_regdom=JP
sudo modprobe iwlagn
sudo ifconfig wlan0 up
```Thanks.

---

### Post by marcopolos on 2009-04-15
this is what i got right after the first command

marco@ubuntu:~$ sudo rmmod -f lbm_cw-cfg80211
ERROR: Removing 'lbm_cw_cfg80211': Resource temporarily unavailable

wireless was on both times; however i turned it off and back on again the first time right after using the console; i never touched it this time though

thanks alot

---

### Post by chili555 on 2009-04-15
Well, let's authorize the use of brute force. Please try:```
sudo ifconfig wlan0 down
sudo rmmod -f lbm_cw-cfg80211
sudo modprobe lbm_cw-cfg80211 ieee80211_regdom=JP
sudo modprobe iwlagn
sudo ifconfig wlan0 up
```Now can you reach channel 13?

---

