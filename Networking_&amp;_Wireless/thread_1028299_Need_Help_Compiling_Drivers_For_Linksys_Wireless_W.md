---
title: "Need Help Compiling Drivers For Linksys Wireless WMP54G PCI Card"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-01-02
I have a Linksys WMP54G Wireless PCI card in an old computer running Ubuntu 8.10.  The card no longer works with 8.10 (it did with 7.04) so I'm trying to find a fix.  The card has the Ralink RT2561/RT61 chipset in it.  I've searched these forums and there seems to be a lot of problems with this particular wireless card.

I've decided to download the latest driver and try to compile and install it myself.  This is where I need help.

Ralink provides opensource drivers for this chipset but I'm having errors when I try to compile it. Would anyone be willing to help me build them? The RT61 drivers are here   [www.ralinktech.com/ralink/Home/Support/Linux.html](www.ralinktech.com/ralink/Home/Support/Linux.html).  I downloaded the drivers and opened the "Readme" file for instructions on how to compile/install the drivers.  I think I did everything correctly but I'm getting an error when I type "make all".  See below for the output.

```
:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ sudo apt-get install kernel-headers kernel-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kernel-headers is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-headers has no installation candidate
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ export KBUILD_NOPEDANTIC=1
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ cp Makefile.6 Makefile
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ sudo make all
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$


```

Can some help me figure this out?  I'd really appreciate it.

Thanks,
Mike

---

### Post by wmdiem on 2009-01-02
it looks like kernel-headers wasn't actually installed. It is probably easier to use synaptic for this so you get the right thing, but the package should be named something like, linux-headers-2.6.24-22-generic
Of course the last part should correspond to uname -r

---

### Post by umechanism on 2009-01-02
> **wmdiem said:**
> it looks like kernel-headers wasn't actually installed. It is probably easier to use synaptic for this so you get the right thing, but the package should be named something like, linux-headers-2.6.24-22-generic
Of course the last part should correspond to uname -r

I'll check that.

What exactly are Linux headers and what do they do?

Thanks for the help.

---

### Post by wmdiem on 2009-01-02
I believe they are part of the source code for the kernel that are linked in when it is compiled. I don't understand the whole make process but they also need to be present when you compile modules and whatnot.

---

### Post by umechanism on 2009-01-02
Ok.  Uname -r gives me this:
```
michael@Michael-Ubuntu:~$ uname -r
2.6.27-9-generic

```
I checked Synaptic and those headers are installed.  The only one not installed was the "linux-headers-2.6.27-9-server".  Do I need that one?

These are the instructions I am following as copied from the "Readme.txt" file:
```
 README

*

* Ralink Tech Inc.

* 

* http://www.ralinktech.com

*



=======================================================================

ModelName:

===========

RT61 Wireless Lan Linux Driver





=======================================================================

Driver lName:

===========

rt61.o/rt61.ko





=======================================================================

Supporting Kernel:

===================

linux kernel 2.4 and 2.6 series. 

Tested in Redhat 7.3 or later.





=======================================================================

Description:

=============

This is a linux device driver for Ralink RT61 a/b/g WLAN Card.





=======================================================================

Contents:

=============

Makefile.4	        : Makefile for kernel 2.4 series

Makefile.6	        : Makefile for kernel 2.6 series

Makefile.RTL865x	: Makefile for big endian platform

*.c					: c files

*.h					: header files





=======================================================================

Features:

==========

   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 

   open or shared or WPA-PSK or WPA2-PSK authentication method. 

   NONE, WEP, TKIP and AES encryption. 





=======================================================================

Build Instructions:  

====================



1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

    or

   $cp Makefile.RTL865x ./Makefile  #  big endian platform

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code

4.1> $make install



5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware

   $cp rt2561s.bin /etc/Wireless/RT61STA/

   $cp rt2661.bin /etc/Wireless/RT61STA/



6>  $dos2unix rt61sta.dat

    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt61.o

    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt61.ko

    #    $/sbin/ifconfig ra0 inet YOUR_IP up



        

Note: Script functionality:

load            load module to kernel

unload          unload module from kernel

Configure       retrieve linux version 





=======================================================================

CONFIGURATION:  

====================

RT61 driver can be configured via following interfaces, 

i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file,

     (iv)RaConfig61



i)  iwconfig comes with kernel.  

ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

iii)copy configuration file "rt61sta.dat" to /etc/Wireless/RT61STA/rt61sta.dat.

iv) RaConfig61 is utility for rt61.

           

Configuration File : rt61sta.dat

---------------------------------------

# Copy this file to /etc/Wireless/RT61STA/rt61sta.dat

# This file is a binary file and will be read on loading rt.o module.

#

# Use "vi -b rt61sta.dat" to modify settings according to your need.

# 

# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure

# 2.) set Channel to "0" for auto-select on Infrastructure mode

# 3.) set SSID for connecting to your Accss-point.

# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

# for more information refer to the Readme file.

# 

# The word of "[Default]" must not be removed

[Default]

CountryRegion=0

CountryRegionABand=7

WirelessMode=0

SSID=AP350

NetworkType=Infra

Channel=0

AuthMode=OPEN

EncrypType=NONE

DefaultKeyID=1

Key1Type=0

Key1Str=0123456789

Key2Type=0

Key2Str=

Key3Type=0

Key3Str=

Key4Type=0

Key4Str=

WPAPSK=abcdefghijklmnopqrstuvwxyz

TxBurst=0

PktAggregate=0

WmmCapable=0

APSDCapable=0

APSDAC=0;0;0;0

BGProtection=0

ShortSlot=0

IEEE80211H=0

TxRate=0

RTSThreshold=2347

FragThreshold=2346

PSMode=CAM

TxPreamble=0

FastRoaming=0

NativeWpa=1



-----------------------------------------------

*NOTE:

WMM parameters:

1.) WmmCapable			

    Set it as 1 to turn on WMM Qos support

	

2.) APSDCapable

	Set it as 1 to use automatic power-save delivery(APSD) on an Non-AP QSTA



3.) APSDAC

	Set ACs corresponding BE, BK, VI and VO as delivery-enabled or delivery-disabled



	

All WMM parameters do not support iwpriv command but WmmCapable, 

	please store all parameter to rt61sta.dat, and restart driver. 	







NetworkManager and WPS:

If Native WPA Supplicant (NetworkManager) is enabled, WPS CAN NOT be triggered.

For this case, we have to set NativeWpa=1 in rt61sta.dat.

Otherwise, if we want to use WPS, we have to disable NetworkManager by setting

NativeWpa=0 in rt61sta.dat.



-----------------------------------------------

syntax is 'Param'='Value' and describes below. 



1. CountryRegion=value                                 

	value

		0: use 1 ~ 11 Channel

		1: use 1 ~ 13 Channel

		2: use 10, 11 Channel

		3: use 10 ~ 13 Channel

		4: use 14 Channel

		5: use 1 ~ 14 Channel

		6: use 3 ~ 9 Channel

		7: use 5 ~ 13 Channel

   	 	                                      

2. CountryRegionABand=value      							

	value	

		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel

		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel

		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel

		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel

		4: use 149, 153, 157, 161, 165 Channel

		5: use 149, 153, 157, 161 Channel

		6: use 36, 40, 44, 48 Channel

		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel

		8: 52, 56, 60, 64 Channel

		9: 34, 38, 42, 46 Channel

		10: 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel

                                                   

3. SSID=value                	

	value

		0~z, 1~32 ascii characters.

                    	

4. WirelessMode=value

	value	

		0: 11b/g mixed 

		1: 11B only 

		2: 11A only          //Support in RfIcType=1(id=RFIC_5225) or RfIcType=2(id=RFIC_5325)

		3: 11a/b/g mixed     //Support in RfIcType=1(id=RFIC_5225) or RfIcType=2(id=RFIC_5325)

		4: 11G only

		

5. TxRate=value

	value

		 0: Auto    	//WirelessMode=0~4	

		 1: 1 Mbps	 	//WirelessMode=0 or 1 or 3

         2: 2 Mbps	 	//WirelessMode=0 or 1 or 3

         3: 5.5 Mbps 	//WirelessMode=0 or 1 or 3

         4: 11 Mbps 	//WirelessMode=0 or 1 or 3

         5: 6  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         6: 9  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         7: 12 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         8: 18 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         9: 24 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        10: 36 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        11: 48 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        12: 54 Mbps  	//WirelessMode=0 or 2 or 3 or 4

 	                                       

6. Channel=value

	value

		depends on CountryRegion or CountryRegionABand

                    	

7. BGProtection=value

	value

		0: Auto 

		1: Always on 

		2: Always off

                    	

8. TxPreamble=value

  	value

		0:Preamble Long

		1:Preamble Short 

		2:Auto

                    	

9. RTSThreshold=value

	value

		1~2347                                                       

                    	                                       

10. FragThreshold=value

	value       	

		256~2346

                    	

11. TxBurst=value

	value


		0: Disable

		1: Enable



12. NetworkType=value	    		

	value 

		Infra: infrastructure mode

       	Adhoc: adhoc mode

                                                                                                                                                        	                                                          

13. AuthMode=value

	value

		OPEN	 	For open system	

		SHARED	  	For shared key system	

		WEPAUTO     Auto switch between OPEN and SHARED

		WPAPSK      For WPA pre-shared key  (Infra)

		WPA2PSK     For WPA2 pre-shared key (Infra)

		WPANONE		For WPA pre-shared key  (Adhoc)

		WPA         Use WPA_Supplicant

		WPA2        Use WPA_Supplicant



14. EncrypType=value

	value

		NONE		For AuthMode=OPEN                    

		WEP			For AuthMode=OPEN or AuthMode=SHARED 

		TKIP		For AuthMode=WPAPSK or WPA2PSK                    

		AES			For AuthMode=WPAPSK or WPA2PSK                     

		

15. DefaultKeyID=value

	value

		1~4



16. Key1=value

    Key2=value

    Key3=value

    Key4=value

	value

		10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

    (usage : "iwpriv" only)     



17. Key1Type=vaule

    Key2Type=value

    Key3Type=vaule

    Key4Type=vaule

    value

		0   hexadecimal type

		1   assic type

    (usage : reading profile only)



18. Key1Str=value

    Key2Str=value

    Key3Str=vaule

    Key4Str=vaule

    value

		10 or 26 characters (key type=0)

		5 or 13 characters  (key type=1)

    (usage : reading profile only)	



19. WPAPSK=value              	

	value

		8~63 ASCII  		or 

		64 HEX characters



20. PktAggregate=value

	value

		0: Disable

		1: Enable when the peer supports it

																

21. WmmCapable=value

	value

		0: Disable WMM

		1: Enable WMM

        

22. PSMode=value

    value

    	CAM			    Constantly Awake Mode

		Fast_PSP		Power Save Mode

		MAX_PSP			Max power save mode

		

23. IEEE80211H=value

	value

		0:	Disable

		1:	Enable	Spectrum management

		(This field can be enable only in A band)

		

24. FastRoaming=value				

	value

		0: Disable Fast Roaming

		1: Enable Fast Roaming



25. RoamThreshold=value

	value [Valid on FastRoaming=1]      	

		60~90



26. APSDCapable=value

	value [Valid on WmmCapable=1]

		0: Disable APSD

		1: Enable APSD



27. APSDAC=value

	value [Valid on APSDCapable=1]

		0: Delivery-disabled AC 

		1: Delivery-enabled AC

	

		//========================//

		AC_BE  AC_BK  AC_VI  AC_VO

		{0, 1};{0, 1};{0, 1};{0, 1}

        //========================//







MORE INFORMATION

=================================================================================

If you want for rt61 driver to auto-load at boot time:

A) choose ra0 for first RT61 WLAN card, ra1 for second RT61 WLAN card, etc.

 

B) go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

   $make install



NOTE:

	if you use dhcp, 

	add this line

	BOOTPROTO='dhcp'

	in the file ifcfg-ra0 .





*C) To ease the Default Gateway setting, 

    add the line

    GATEWAY=x.x.x.x   

    in /etc/sysconfig/network



D) When build for SUSE, please unmark the part for SUSE in Makefile.

   When build for Mandriva 2007.1, please unmark the part for Mandriva in Makefile.
```
The odd thing about these instructions is that they do not follow the old "configure, make, make install" protocol that I have used in the past.  They only list a "configure" if you are using the 2.24 Kernel (older kernel).  See steps #3 and #4 in the readme file.

What should I try next?

---

### Post by wmdiem on 2009-01-02
wait isn't that was 4 and 4.1 are? It looks like unless otherwise specified you are supposed to do all the steps (e.g. step 3 or the fork in 7). 
btw, you don't need the server headers, just what you have.

---

### Post by wmdiem on 2009-01-02
posible solution: [http://www.linuxquestions.org/questions/linux-software-2/an-error-about-fix-it-to-use-extracflags-625753/](http://www.linuxquestions.org/questions/linux-software-2/an-error-about-fix-it-to-use-extracflags-625753/)
type
export KBUILD_NOPEDANTIC=1
before running make

---

### Post by umechanism on 2009-01-03
I set KBUILD_NOPEDANTIC=1 as directed and I really thought the "make all" might actually work because the computer took about 10 seconds before it crapped out.  I call that progress.:D

Here is the results of the "make all".

```
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ export KBUILD_NOPEDANTIC=1
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ make all
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.o
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: In function ‘rt61_get_drvinfo’:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:78: warning: unused variable ‘pAd’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: In function ‘rt61_get_regs’:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:104: warning: unused variable ‘counter’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:103: warning: unused variable ‘pAd’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: In function ‘rt61_ethtool_get_link’:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:120: warning: unused variable ‘pAd’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: In function ‘rt61_get_eeprom’:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:146: warning: unused variable ‘counter’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:145: warning: unused variable ‘pAd’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: At top level:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:169: warning: initialization from incompatible pointer type
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:238: warning: assignment discards qualifiers from pointer target type
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:343: warning: ISO C90 forbids mixed declarations and code
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:344: error: ‘struct net_device’ has no member named ‘nd_net’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:345: error: ‘struct net_device’ has no member named ‘nd_net’
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c: In function ‘RT61_open’:
/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.c:464: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/michael/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
michael@Michael-Ubuntu:~/RT2561/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ 


```

---

### Post by wmdiem on 2009-01-03
yeah i really don't know what to tell you. 
but I am glad you are making progress : P

---

### Post by umechanism on 2009-01-03
Thanks for your help.

Will anyone else take a stab at it?

---

### Post by kevdog on 2009-01-03
Any thoughts of compiling the serial monkey rt61 driver rather than the ra rt61 drivers?

---

### Post by umechanism on 2009-01-03
> **kevdog said:**
> Any thoughts of compiling the serial monkey rt61 driver rather than the ra rt61 drivers?

At this point, I'll try just about anything.  What is the "serial monkey driver"?  I've never heard of it.

Thanks!

---

### Post by kevdog on 2009-01-04
Here is the link:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

Also do a search on the forum for rt73 looking for a link by I think another poster called depruis (or something similar to that) -- I would be in the tutorials archive section.  He gives good guidance on compiling and installing the rt73 driver -- your process will be exactly similar except for the rt61 device.

Lastly I thought these drivers were already included in the kernel or ubuntu.

---

### Post by umechanism on 2009-01-06
> **kevdog said:**
> Here is the link:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

Also do a search on the forum for rt73 looking for a link by I think another poster called depruis (or something similar to that) -- I would be in the tutorials archive section.  He gives good guidance on compiling and installing the rt73 driver -- your process will be exactly similar except for the rt61 device.

Lastly I thought these drivers were already included in the kernel or ubuntu.

Thank you for the information.  I looked at the link you provided but I do not think I have the skills/knowledge to do this in Linux.  I'll give it a whirl and see what happens.  I will also search the tutorials as you suggested for additional help.

Thank you again.

---

