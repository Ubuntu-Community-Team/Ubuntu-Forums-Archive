---
title: "USB wifi dongle install"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by Bright Carver on 2011-01-28
Hi

I recently purchased a USB wifi dongle.  It is completely unbranded but it does say "for Linux" on it.  I've been trying to get it to work on my ancient xubuntu laptop but I don't know anything about wifi setup on Linux.  At all.

The CD that comes with the card has many folders on it with stuff in it, but I'm not sure what any of it means.  Here is some of what it is (in case it's useful)

=====================================

-These are mainly folders-

RT2070,RT3070,RT2770,RT3072,RT3572,RT3370
. Linux
. . RT3070_LinuxSTA_V2.3.0.1_20100208.tar
RT2571
. Linux
. . RT2571 Linux_STA_Drv1.1.0.3.zip
. . . 2009_0713_RT73_Linux_STA_Drv1.1.0.3
. . . . Module
. . . . . (a bunch of other files like makefile and config.mk)
. . . . WPA_Supplicant
. . . . . (again, makefile etc)
RTL8191SU,RTL8188SU
. linux_v2.6
. . rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100601
. . . document
. . . driver
. . . . rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100601.tar
. . . wpa_supplicant
. . . . .(loads more stuff)

=====================================

I've looked over the Linux wifi info on the net but it's a little over my head.  My friend has moved from the country and has charged me with selling his monster PC (and I get a cut) but he's taking his Windows CD with him so I'm going to put a Linux on it to sell it, I just want to know the dongle I bought can actually work.

Can anyone help here?

Thanks

Karl

---

### Post by grahammechanical on 2011-01-28
Wow! A manufacturer that supplies a Linux support disc. Pity they are to afraid to put their name on the product. I do not know what it all means either. I will say this, try a live CD with the USB dongle plugged in and see if everything works. Then you will find out if the latest kernel has the driver modules for this USB WiFi dongle.

Regards.

---

### Post by Bucky Ball on 2011-01-28
> **grahammechanical said:**
> Wow! A manufacturer that supplies a Linux support disc. Pity they are to afraid to put their name on the product. I do not know what it all means either. I will say this, try a live CD with the USB dongle plugged in and see if everything works. Then you will find out if the latest kernel has the driver modules for this USB WiFi dongle.

Regards.

+1. I would go as far as installing and working it out when you get there. That looks like Realtek wireless chipset and that is going to work, either 'out of the box' or with minimal tweaking. You have all the correct drivers there. Just a matter of which you need. They are also all available from the Realtek website. It will probably be one of the SU ones for USB, ie:

RTL8191SU or RTL8188SU

... which are both shown there. I have read good reports of functionality in Ubuntu for both. ;)

Good luck.

---

### Post by Bright Carver on 2011-01-29
Hi, thanks for responding :)

Ok, I put it into my Xubuntu Thinkpad, The HD light came on for a bit and went out.  The light didn't come on on the dongle and I can't find anywhere in the menu to look for networks to connect to.

Not sure if it's worked or not, to be honest...

My laptop being very old doesn't handle liveCD's above Slax, so I'm going to try the latest Ubuntu live on my AMD64 machine and see if that notices it, if that fails I've got a Core2duo machine I can try it on.

I can connect my laptop with a pcmcia lan adapter (that's how old it is) so I know it's up to date and can install any extra software if needed.

The CD that came with the dongle also has drivers for some USB sound card on it so I'm guessing it's just a generic driver CD they send out with all their stuff.

Any advice where to go from here?

.......................................
grahammechanical:
I tried the dongle on the family computer and it hasn't shown network.  I tried entering the ssid, wepkey and mac address in the create a wireless network box, but still no connection.  This is on 10.10 on an amd64 (not my xubuntu laptop).

bucky ball:
First, how do I find out which driver on the CD is for my thing, and also, how can I install a driver from the CD to my computer?

Thanks,

Karl

---

### Post by Bright Carver on 2011-01-29
I saw on another forum to have a look at dmesg.  I don't know what it all means, but it seems there's rt2800usb requesting r2870.bin with wlan0:link is not ready message.

does anybody understand this?  I'm completely clueless about how this works.

Thanks

Karl

---

### Post by walt.smith1960 on 2011-01-29
I would hazard a guess that it's looking for a firmware file and not finding it.  The device is probably a Ralink chipset.  It's sometimes necessary to blacklist certain modules to prevent conflicts.  Posting the result of ```
lsusb
``` might be helpful.  Chili555 is well versed with Ralink issues if he checks in.

---

### Post by Bright Carver on 2011-01-29
Ok, cool :)

```
lsusb
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Thanks

Karl

---

### Post by Bright Carver on 2011-01-30
I've been trying to learn how this all works but am just going round in circles.

Can anyone help me get this working?

The only things I've found online are way too technically over my head and/or involve resetting my wireless router to have no security (not an option at the moment).  Anyway, here's the results of a dmesg...

```
dmesg | grep usb
[    0.068797] usbcore: registered new interface driver usbfs
[    0.068867] usbcore: registered new interface driver hub
[    0.069031] usbcore: registered new device driver usb
[    0.351376] usb usb1: configuration #1 chosen from 1 choice
[  177.625100] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  177.833814] usb 1-1: configuration #1 chosen from 1 choice
[  181.393627] Registered led device: rt2800usb-phy0::radio
[  181.393882] Registered led device: rt2800usb-phy0::assoc
[  181.394128] Registered led device: rt2800usb-phy0::quality
[  181.398381] usbcore: registered new interface driver rt2800usb
[  184.076242] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
```


Anyone?

Thanks

Karl

---

### Post by walt.smith1960 on 2011-01-30
Well,  here is what I would probably do if it were mine.  Of course I would do this knowing it's not a time proven solution.  The message about a missing .bin file is similar to what i had with the RTL8192SU adapter.  I downloaded and unpacked Ralink's RT2870USB software. Once unpacked, the first folder is common.  If you look in the folder, one of the files is rt2870.bin, the file you appear to be missing.

The next step I used nautilus because I don't really trust my command line skills.  GKSU nautilus will open nautilus with administrative privileges.  Use with caution, the safeguards in nautilus are bypassed in this mode.  When I did the firmware trick with my adapter, I had to create a folder then copy the .bin folder into the folder. I don't know if you need to do that or just copy the file.  The location is likely to be  file system -> lib -> firmware.  I would try this; it's pretty easy and if it doesn't work you can reverse your steps and no harm done.

Edit:  I just looked in my system's /lib/firmware folder.  There is a file called rt2870.bin.  It's size is 4k.  The rt2870.bin in the current ralink download is 8k so the new file is larger than the existing one.  It's probably worth trying to copy the new file and see if that helps.  Otherwise you can try to compile new drivers.

---

### Post by Bucky Ball on 2011-01-30
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

There seems to be a couple of USB packages there marked RT2870USB.

---

### Post by walt.smith1960 on 2011-01-31
There's one other thing I'd probably try.  The RealTek firmware .bin files are in folders with the same name as the firmware file but without the file extension.  I wonder if the Ralink firmware  .bin files needs to be in a RT2870 folder in order to be recognized?  I don't understand how Linux hardware recognition works, I'm just thinking about what has worked in similar situations.

---

### Post by Bright Carver on 2011-02-03
Ok, so here's what I've been doing over the past couple of days

I searched the driver CD for rt2870.bin, which I found.  I copied it to the /lib/firmware folder (using sudo thunar).  No light comes on when I plug in the USB.  I thought about the folder so I extracted the whole tar.gz2 folder from the CD into firmware.  Plugged in the USB, nothing.

I've tried this with and without my lan line plugged in, restarted several times with and without the USB stick in, nothing.

I even had to plug it into my Windows machine to see if it wasn't actually broken or something.  It jumped to life instantly.  Frustrating!

When I used it on Mint liveCD on the family PC, the light actually came on (although there was no indication of how to connect to a network).

Any ideas?  This has the potential to drive me crazy.  Is it likely to work on a newer PC with the latest Ubuntu just out of the box, rather than on this old dinosaur of a laptop?

Any ideas?

Thanks

Karl

---

### Post by Bright Carver on 2011-02-03
Here's what I seem to have worked out so far:

```
lsusb
Bus 001 Device 004: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

So that's what lsusb thinks my equipment physically is, am I correct?  Something called a 148f:2070 from Ralink.

Now the readme on the CD mentions various other devices, but the only ones that match is the RT2571 and the RT2070 (both 54M devices, others are 150M and 300M), so It's a good guess I want the RT2070 driver to work.

Into the folder called RT2070,RT3070,RT2770,RT3072,RT3572,RT3370 (it's a long folder name), There's Linux, Mac OS, WinCE and Windows folders.

Into the Linux folder, there's a file called RT3070_LinuxSTA_V2.3.0.1_20100208.tar.bz2, so I navigate into the tar file until I get into the folder.

This folder has other folders called chips, common, include, os sta and tools, has other files including a README_STA_usb, which says:-
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
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


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

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
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
	
=======================================================================
CONFIGURATION:  
====================
RT2870 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
           
Configuration File : RT2870STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
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
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡Š¡Š, 
	please store all parameter to RT2870STA.dat, and restart driver. 	

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
	   31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
   	 	                                      
@> CountryRegionABand=value      							
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
		9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
	   10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
	   11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
	value
		AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
		GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
		PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
		"" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165
                                                           
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
		depends on CountryRegion or CountryRegionABand
                    	
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

@> EthConvertMode=value
	value
		dongle
		clone
		hybrid

@> EthCloneMac=value
	value
		xx:xx:xx:xx:xx:xx

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
	    
@> MeshId=value
	value
		Length 1~32 ascii characters

@> MeshAutoLink=value
	value
		0				Disabled
		1				Enabled

@> MeshAuthMode=value
	value
		OPEN	 	For open system	
		WPANONE		For WPA pre-shared key  (Adhoc)

@> MeshEncrypType=value
	value
		NONE		For MeshAuthMode=OPEN                    
		WEP			For MeshAuthMode=OPEN
		TKIP		For MeshAuthMode=WPANONE
		AES			For MeshAuthMode=WPANONE

@> MeshWPAKEY=value
	value
		8~63 ASCII  		or 
		64 HEX characters

@> MeshDefaultkey=value
	value
		1~4

@> MeshWEPKEY=value
	value
		10 or 26 characters
		5 or 13 characters

@> CarrierDetect=value
	value
		0				Disabled
		1				Enabled

MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
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
   
=======================================================================
Dongle/Clone Features:
======================
A) Dongle mode: 
   	Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
   	can transparently connect to the AP.

B) Clone mode:
	Provides a 1-to-1 MAC address mapping mechanism. 
	STA can use own MAC as SA MAC or 
			use user desired MAC as SA MAC or
		    use source MAC of first packet coming from wired device as SA MAC.
	NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
	Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
   	can transparently connect to the AP.
	STA can use own MAC as SA MAC or 
			use user desired MAC as SA MAC or
		    use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.
```

I've also just done another dmesg in case anyone understands any of this, but it seems to be doing something else now, so here it is:-

 ```
dmesg | grep usb
[  180.510750] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  180.719498] usb 1-1: configuration #1 chosen from 1 choice
[  183.892134] Registered led device: rt2800usb-phy0::radio
[  183.892390] Registered led device: rt2800usb-phy0::assoc
[  183.892640] Registered led device: rt2800usb-phy0::quality
[  183.902797] usbcore: registered new interface driver rt2800usb
[  186.206322] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[  720.926904] usb 1-1: USB disconnect, address 2
[  720.970189] phy0 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[ 1219.377630] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 1219.588072] usb 1-1: configuration #1 chosen from 1 choice
[ 1219.659720] Registered led device: rt2800usb-phy1::radio
[ 1219.659964] Registered led device: rt2800usb-phy1::assoc
[ 1219.660200] Registered led device: rt2800usb-phy1::quality
[ 1220.254992] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[ 1961.790736] usb 1-1: USB disconnect, address 3
[ 1961.848286] phy1 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[ 3912.091977] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 3912.301382] usb 1-1: configuration #1 chosen from 1 choice
[ 3912.384287] Registered led device: rt2800usb-phy2::radio
[ 3912.384664] Registered led device: rt2800usb-phy2::assoc
[ 3912.384911] Registered led device: rt2800usb-phy2::quality
[ 3913.870404] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
```

Thanks for your help with all this :)

Karl

---

### Post by Bright Carver on 2011-02-03
Ok, a little success in a way, but not much really.  After googling about, I found a post here:-

[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)

Now, I've followed the instructions to the letter, and it all ran with no problems, downloading, compiling and installing the drivers.

What's happening now is the light is coming on on the USB dongle (which is something) And a dmesg grep usb says:-

dmesg | grep usb
[    0.068800] usbcore: registered new interface driver usbfs
[    0.068870] usbcore: registered new interface driver hub
[    0.069033] usbcore: registered new device driver usb
[    0.351414] usb usb1: configuration #1 chosen from 1 choice
[  134.102340] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  134.311060] usb 1-1: configuration #1 chosen from 1 choice
[  233.295842] usb 1-1: USB disconnect, address 2
[  404.504072] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  404.712837] usb 1-1: configuration #1 chosen from 1 choice

so that seems to be an improvement anyway.

I got as far in the tutorial as configuring the network details at this section:-

/etc/Wireless/RT2870STA/RT2870STA.dat Configuration

I'm not quite sure what the SSID and wpa passkey are, I think my router's on WEP, but I have the passkey for it.

I downloaded wifiscanner in the hope that if my USB was installed properly it would show the networks in my area and I could choose mine and enter the key but it still doesn't seem to work with that either.

Where do you think I should go from here?

Thanks :)

Karl

---

### Post by Bright Carver on 2011-02-04
After Googling around, asking on other forums and repeatedly recompiling the drivers in various strange ways, I have... nothing.

I tried following the readme and a few other similar processes with no luck.  I've seen other tutorials where it seems to work for other people, but not for me.

In order to buy this card, I Googled for Linux compatible.  It had "for Linux" on the product name, has "supported by Linux" written on the packet.  There is a CD with it that contains Linux config.mk files and drivers.  It's driving me nuts.

I'm going to reinstall my Xubuntu and try everything again.  Before I do, is there anything anyone's tried for this thing that might get it working?

Thanks,

Karl

---

