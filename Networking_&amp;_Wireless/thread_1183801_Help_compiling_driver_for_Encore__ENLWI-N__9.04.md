---
title: "Help compiling driver for Encore  ENLWI-N  9.04"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by Matt_Rapp on 2009-06-10
I’m having trouble installing my new Encore ENLWI-N PCI Wi-Fi card, ndiswrapper and the chipset maker’s drivers have not been working for me, I can connect to open networks but not anything with WPA. I've decided to try and install the Linux driver from the manufacture, but it’s too confusing for me to do on my own, I am still new to Linux.

Attached is the driver zip file from Encore's [**_website_**]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=2&pid=269"). There is a readme inside on how to compile it, which I've also inserted at the end of this post. I am going to have to do a clean reinstall of 9.04 to get rid of the previous attempts I've made with the chipset driver. All I want to do is connect to a wireless g network on start up with WPA2-PSK security and manage the connection through Network Manager. I know about leaving the keyring password blank to get Network Manager to run on its own.

If someone could post better step by step instructions on how to compile this driver for a clean installation of Ubuntu 9.04 it would be great. You could test it out of a live CD, hopefully the updates that are not installed on a live version will not mess anything up. Much thanks in advance!!
```
* README
*
* Ralink Tech Inc.
* 
* http://www.ralinktech.com
*

=======================================================================
ModelName:
===========
RT2860 Wireless Lan Linux Driver


=======================================================================
Driver lName:
=============
rt2860.o/rt2860.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2860 ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile	        : Makefile
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

1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.

4> $make									# compile driver source code

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    # !!!check if it is a binary file before loading !!!  
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta
	
=======================================================================
CONFIGURATION:  
====================
RT2860 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2860STA.dat" in /etc/Wireless/RT2860STA/RT2860STA.dat.
           
Configuration File : RT2860STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2860STA/RT2860STA.dat
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
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BasicRate=15
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡¦¡¦, 
	please store all parameter to RT2860STA.dat, and restart driver. 	

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
	value
		0: use 1 ~ 11 Channel
		1: use 1 ~ 13 Channel
		2: use 10 ~ 11 Channel
		3: use 10 ~ 13 Channel
		4: use 14 Channel
		5: use 1 ~ 14 Channel
		6: use 3 ~ 9 Channel
		7: use 5 ~ 13 Channel
   	 	                                      
@> CountryRegionForABand=value      							
	value	
		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
		4: use 149, 153, 157, 161, 165 Channel
		5: use 149, 153, 157, 161 Channel
		6: use 36, 40, 44, 48 Channel
		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
		8: use 52, 56, 60, 64 Channel
		9: use 34, 38, 42, 46 Channel
		10 use 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel
                                                           
@> SSID=value                	
	value
		0~z, 1~32 ascii characters.
                    	
@> WirelessMode=value
	value	
		0: legacy 11b/g mixed 
		1: legacy 11B only 
		2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		4: legacy 11G only
		5: 11ABGN mixed
		6: 11N only
		7: 11GN mixed
		8: 11AN mixed
		9: 11BGN mixed
	   10: 11AGN mixed	
                     
@> Channel=value
	value
		depends on CountryRegion or CountryRegionForABand
                    	
@> BGProtection=value
	value
		0: Auto 
		1: Always on 
		2: Always off
                    	
@> TxPreamble=value
  	value
		0:Preamble Long
		1:Preamble Short 
		2:Auto
                    	
@> RTSThreshold=value
	value
		1~2347                                                       
                    	                                       
@> FragThreshold=value
	value       	
		256~2346
                    	
@> TxBurst=value
	value
		0: Disable
		1: Enable

@> NetworkType=value	    		
	value 
		Infra: infrastructure mode
       	Adhoc: adhoc mode
                                                                                                                                                        	                                                          
@> AuthMode=value
	value
		OPEN	 	For open system	
		SHARED	  	For shared key system	
		WEPAUTO     Auto switch between OPEN and SHARED
		WPAPSK      For WPA pre-shared key  (Infra)
		WPA2PSK     For WPA2 pre-shared key (Infra)
		WPANONE		For WPA pre-shared key  (Adhoc)
		WPA         Use WPA-Supplicant
		WPA2        Use WPA-Supplicant

@> EncrypType=value
	value
		NONE		For AuthMode=OPEN                    
		WEP			For AuthMode=OPEN or AuthMode=SHARED 
		TKIP		For AuthMode=WPAPSK or WPA2PSK                    
		AES			For AuthMode=WPAPSK or WPA2PSK                     
		
@> DefaultKeyID=value
	value
		1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
	value
		10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
		0   hexadecimal type
		1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
		10 or 26 characters (key type=0)
		5 or 13 characters  (key type=1)
    (usage : reading profile only)	

@> WPAPSK=value              	
	value
		8~63 ASCII  		or 
		64 HEX characters
																                    																		
@> WmmCapable=value
	value
		0: Disable WMM
		1: Enable WMM
        
@> PSMode=value
    value
    	CAM			    Constantly Awake Mode
		Max_PSP		    Max Power Savings
		Fast_PSP		Power Save Mode

@> FastRoaming=value
	value
		0				Disabled
		1				Enabled

@> RoamThreshold=value
	value
		Positive Interger(dBm)

@> HT_RDG=value
	value
		0				Disabled
		1				Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
	value
		0				Below
		1 				Above

@> HT_OpMode=value
	value
		0				HT mixed format
		1				HT greenfield format

@> HT_MpduDensity=value
	value (based on 802.11n D2.0)
		0: no restriction
		1: 1/4 £gs
		2: 1/2 £gs
		3: 1 £gs
		4: 2 £gs
		5: 4 £gs
		6: 8 £gs
		7: 16 £gs

@> HT_BW=value
	value
		0				20MHz
		1				40MHz

@> HT_AutoBA=value
	value
		0				Disabled
		1				Enabled

@> HT_BADecline
	value
		0				Disabled
		1			    Enabled <Reject BA request from AP>

@> HT_AMSDU=value
	value
		0				Disabled
		1				Enabled

@> HT_BAWinSize=value
	value
		1 ~ 64

@> HT_GI=value
	value
		0				long GI
		1				short GI

@> HT_MCS=value
	value
		0 ~ 15
		33: auto

@> HT_MIMOPSMode=value
	value (based on 802.11n D2.0)
		0				Static SM Power Save Mode
		1				Dynamic SM Power Save Mode
		2				Reserved
		3				SM enabled
	(not fully support yet)

@> IEEE80211H=value
	value
		0				Disabled
		1				Enabled

@> TGnWifiTest=value
	value
		0				Disabled
		1				Enabled

@> WirelessEvent=value
	value
		0				Disabled
		1				Enabled <send custom wireless event>
	    
MORE INFORMATION
=================================================================================
If you want for rt2860 driver to auto-load at boot time:
A) choose ra0 for first RT2860 WLAN card, ra1 for second RT2860 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2860sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
```

---

### Post by carcar1 on 2009-06-10
Why do compiling?  If you have a dual boot just install the encore driver/software.  Go to the folder where it installed copy it over and use ndiswrapper with the net.inf file.  I don't know about you but I have it working out of the box with 9.04 non-upgrade and updates are fine :)

Because you are new to ubuntu use ndisgtk a frontend to ndiswrapper much easier to use then command line.

---

### Post by Matt_Rapp on 2009-06-10
When I said ndiswrapper I meant the graphical interface, my bad.

I already tried using the .inf file from the CD, installed it on a windows machine and copied it over. See [**_this thread_**]("http://ubuntuforums.org/showthread.php?t=1180394"). 

The file I used was called netr28.inf though, in the 802.11n PCI Wireless LAN Card/Driver folder. If you have a net.inf file that works for you could you post a reply and attach it so I could try it, remember to include the net.sys file as well in order to make sure it works. Would still like to have the option of compiling my own driver though.

---

### Post by chili555 on 2009-06-10
The driver you downloaded is a bit old. I recommend this HOWTO: [http://ubuntuforums.org/showthread.php?t=966185](http://ubuntuforums.org/showthread.php?t=966185)

---

### Post by Matt_Rapp on 2009-06-11
I did a clean install on a different hard drive and followed the other threads instructions. I got the module installed but couldn’t edit the /ect/modules file or the /ect/network/interfaces file. I did use sudo and sudo su. Also configuring the card without network manager does not look like fun.

---

### Post by carcar1 on 2009-06-11
both worked for me


for the modules one type "Sudo gedit /etc/modules"
and you didnt go to the right directory type 
"sudo gedit /etc/network/interfaces"

---

### Post by chili555 on 2009-06-11
> /ect/modulesI hope you really meant /[COLOR="Red"]etc[/COLOR]/modules. Moreover, if the module is loaded and you are able to connect, I'm not sure why you would remove Network Manager, either.

---

### Post by Matt_Rapp on 2009-06-11
Nope, still can&#8217;t save changes to /ect/... see attached screenshot., there I was trying to add the line "test"
I also have tried using vi and echo but neither work.

---

### Post by chili555 on 2009-06-11
Matt -

It is not [SIZE="4"]/ect[/SIZE], it is [SIZE="6"]/etc[/SIZE]!!!

---

### Post by carcar1 on 2009-06-11
Hehe don't be mean to the poor lad.  You can't save it because you are making a new file.  I am not going confuse you further.  As we have been saying it is "/etc/network/interfaces" and if that denies you type "sudo su" to give you root power.

---

### Post by Matt_Rapp on 2009-06-11
Woops, my bad. I guess that's what you get if you stay up working late all night. ;) Will try again and report back soon.

---

### Post by Matt_Rapp on 2009-06-11
Okay I don't know what's up but I can't connect. I did go ahead and remove network manager like it was suggested in the tutorial. I don't know if it is my connection settings or installing the driver that is screwing it up, but I noticed when looking at the included readme that I never copied that .dat file or defined DCC LD CFLAGS in step 3. I don't know if going right from the readme would help, however it's pretty vague and I can't follow all of it on my own if doing this is a good idea. Below is my take, is it a good idea to install it this way and if so can you help me figure the rest out? Thanks.


1. Download and untar the file from their website, get into that file in terminal
2. Got the first half, what do they mean by define Linux kernel source, what file path??
3. DCC LD CFLAGS???? Got the changing n to yes part
4. Got it sudo make && sudo make install
5. Got it, copies a file over
6. & 7. ??? I can understand the go to /os/linux part, but the commands to load and upload are… (One must be modprobe but I don’t really know)
```

=======================================================================
Build Instructions:  
====================

1> $tar -xvzf RT2860_Linux_STA_x.x.x.x.tgz
    go to "./RT2860_Linux_STA_x.x.x.x" directory.
    
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

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta
```

As for connection settings, I am using WPA2-AES, and my routers IP address is 192.168.0.1

The tutorials don't use AES and the gateway, broadcast settings are a little confusing to me.

The other settings like SSID, passphrase and country code I've got figured out.

---

### Post by carcar1 on 2009-06-11
Right now I'm on an install of 9.04 on the same pc with this wireless card.  Works right out of the box.  I have proof I think its something other then your wireless card when did you install ubuntu when did you download because they are sometimes putting new things in it.

---

### Post by Matt_Rapp on 2009-06-11
I just downloaded a new iso and burned the disk a few days ago, probably on Tuesday. Did you get my message about Skype? Right now I am also reinstalling 9.04 on the same test hard drive 40% done. :D

---

### Post by carcar1 on 2009-06-11
Found yet another guide that people are having more success with.  [http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2860]("http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2860")

Try that first and then try downloading all of the rt2860 packages and other files on this site.  Its halfway down, its there trust me. :)

[https://launchpad.net/~stgraber/+archive/ppa]("https://launchpad.net/~stgraber/+archive/ppa")

---

### Post by Matt_Rapp on 2009-06-11
What's the deal when you get to step 16, do you proceed only if it doesn't work? Also why does he have install build-essential at the end of his instructions, shouldn't I do that first?

---

### Post by carcar1 on 2009-06-11
If you get to step 16 completely then you got it working.  If not you do the next 2 steps then when you do that you go down to the bottom and that fixes up the install.  I am now sure exactly, did it work for you?  Try using his old driver there old ones usually work better till bugs have been patched.

---

### Post by Matt_Rapp on 2009-06-11
Okay, I followed all the steps without problems, used his old driver. Nothing worked so I kept going past 16 and still nothing, though network manager still shows networks and is trying to connect-it keeps failing and turns my AES passphrase into a long string of numbers and letters. You do know that the tutorial was for a ra2870 chipset right? I did a lsmod and it showed the installed module to be ra2860 though, that was weird.

Can I use the other package now, or do I have to remove my previous module attempt and how? Reinstall again?

---

### Post by carcar1 on 2009-06-11
Try ndiswrapper again with windows drivers you find online because ndiswrapper apparently is the main way to get this card working.

---

### Post by carcar1 on 2009-06-11
Try switching the card to a different pci slot.  Yea undo what you did and try the other package.

---

### Post by Matt_Rapp on 2009-06-11
Okay I'll try the package, the only way I know how to completely get rid of everything is to do a reinstall, so that will take like 10 min. 

What driver should I use in ndiswrapper if the package doesn't work? I already got one from you, and extracted one from my CD and neither worked remember.


I don't think it is the PCI slot, I had my old adapter in that slot for 5 months and it worked fine, plus the new card can connect to open networks just fine.

---

### Post by Matt_Rapp on 2009-06-11
Okay, with the fresh reinstall I tried to install the package, it failed to install because it was missing a dependency called dkms. I did apt-get install and Synaptic for it but both turned up nothing. I have a wired connection temporarily.

---

### Post by carcar1 on 2009-06-12
Looked at this some more and if thats a live cd dkms is for the kernel and it should install when you install ubuntu.  Also your synaptic package manager cant find it because you dont have new repos.  [http://www.psychocats.net/ubuntu/sources]("http://http://www.psychocats.net/ubuntu/sources") and [https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine") make sure you list is long!!!!

By the way the package exists as it is installed on my computer.  I think all you have to do is install Ubuntu and it auto installs on default install or with some form of update.

Or if you want to skip the repos which is a good idea to do you can download this package directly from [http://linux.dell.com/dkms/]("http://linux.dell.com/dkms/")

---

### Post by Matt_Rapp on 2009-06-12
Okay I install the dkms deb from the dell site and then was able to install the rt2860 - 1.8.0.0-0ubuntu1~ppa2 package successfully. Then I reinstalled and attempted to connect through network manager. It failed in the same way as before, but also showed another secure network that I have never seen around my neighborhood before if that means anything. It could be my motherboard I guess, although I don&#8217;t know why. I&#8217;m going out of town for a week and probably will just end up reinstalling my old card and hanging on to this Encore one, unless there are some more tricks up your sleeve. I&#8217;m sure the card is fine and will work in Windows if I ever have to fix a family members computer, or hopefully a new release of Ubuntu will clear things up. Everything shows it being tested under Red Hat, so I might give that a try too. Thanks for all your help carcar1. :)

---

### Post by carcar1 on 2009-06-12
I have one more try.  This is my last effort.  This is an automatic installation of ndiswrapper which was built around ubuntu 8.04 hopefully with the new  kernel it will till work.  [https://launchpad.net/auto-ndiswrapper]("https://launchpad.net/auto-ndiswrapper")  I personally will be trying this out on 8.10 or a modded version of it.  Sorry mods if I say this I **AM NOT** promoting Ultimate Edition but I am trying it on that with an atheros chip.  You might want to try fedora 11 it might support this card natively.  Maybe :) if not stick around and wait for Ultimate 2.2 to come out.

Maybe pull some transistor out or something and say it didnt work in windows hopefully your warranty is still active.

---

### Post by Matt_Rapp on 2009-06-12
Will have to try next week, python is giving me too much trouble right now and I have to go. :)

---

### Post by carcar1 on 2009-06-13
Wait for Ultimate Edition 2.2 to come out it will be a morph between Jaunty and Karmic also it has a badda++ theme which I am using now.

---

### Post by carcar1 on 2009-06-14
This method works works!!!!

ITs from chili

Scare you? C'mon, compiling from source is just clean fun!

First, be sure you have build-essential and linux-headers-generic installed. Synaptic is your friend. Then open a terminal and do, each command separately and in order:
Code:

lspci -v
sudo lshw -C network

Please verify you have a rt2860 device. If so, please proceed, if not, post back and tell us what you really have. Now do:
Code:

wget [http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2)
tar -xvzf 2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2
cd 2008_0522_RT2860_Linux_STA_v1.6.1.0
sudo su

If your card will connect using WPA, we will have some adjustments to make:
Code:

gedit os/linux/config.mk

In line 11, change HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y; in line 14, change HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y. Proofread, save and close. Now, do:
Code:

make
cp RT2860STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
make install
modprobe rt2860sta

Does your device wink, blink and spring to life? Can you connect?

---

