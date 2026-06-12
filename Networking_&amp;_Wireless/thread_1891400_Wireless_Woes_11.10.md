---
title: "Wireless Woes 11.10"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by fleamour on 2011-12-05
Just bought a wireless PCI NIC (Edimax EW-7722In) which assures me on box of being Linux compatible. I'm having trouble connecting to router. Basically it repeatedly asks for wireless key, even though entered multiple times correctly. 

I have entered the MAC address into whitelist correctly, triple checked & then some. I have selected DHCP & disabled MAC filtering to no avail.

I have the setup CD which has a Linux driver folder, however trying to extract tar.bz2 archive returns this error when loading the archive:

"bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now"

It makes no difference if I copy file to HDD then try to extract. So all in all not much help. Is this an 11.10 bug, in which case I need to sit tight till Pangolin, or can it be made to work? Hopefully someone can advise...


:confused: :shock: :confused:

EDIT:  I can however mount archive, though not extract.  The following is the README txt file.  All double Dutch to me & no auto make executable?!?

* README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
RT2860 Wireless Lan Linux Driver


=======================================================================
Driver lName:
=============
rt3562sta.o/rt3562sta.ko


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
This is a linux device driver for Ralink RT3562/RT3062/RT2860 PCI ABGN WLAN Card.


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

1> $tar -xvzf RT3562_Linux_STA_x.x.x.x.tgz
    go to "./RT3562_Linux_STA_x.x.x.x" directory.
    
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
    #    $/sbin/insmod rt3562sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt3562sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt3562sta
	
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
# Use "vi RT2860STA.dat" to modify settings according to your need.
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
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡&#352;¡&#352;, 
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
	    
@> CarrierDetect=value
	value
		0				Disabled
		1				Enabled

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

---

### Post by praseodym on 2011-12-05
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by fleamour on 2011-12-05
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: ASRock Incorporation Device [1849:8136]
	Kernel driver in use: r8169
--
05:02.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Edimax Computer Co. Device [1432:7722]
	Kernel driver in use: rt2800pci
fleamour@ASRock:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
fleamour@ASRock:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  50 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  12849  0 
arc4                   12473  2 
rt2800pci              18340  0 
snd_seq_midi           13132  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
snd_rawmidi            25241  1 snd_seq_midi
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
w83627ehf              29165  0 
hwmon_vid              12658  1 w83627ehf
coretemp               13188  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
fleamour@ASRock:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by fleamour on 2011-12-05
```
fleamour@ASRock:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
```

---

### Post by praseodym on 2011-12-05
"Tx-Power=off" and "Soft blocked = yes" mean, that the card is "off". Try

```
sudo rfkill unblock all
```

---

### Post by fleamour on 2011-12-05
There is a physical button, but no mention of it in quick setup guide...

EDIT:  Now you mention it there are no lights.  Damn, will try reinserting or another PCI slot, could be dead.

---

### Post by fleamour on 2011-12-05
> **praseodym said:**
> "Tx-Power=off" and "Soft blocked = yes" mean, that the card is "off". Try

```
sudo rfkill unblock all
```


No joy.

---

### Post by praseodym on 2011-12-05
Try this:

```
sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
```
Check:
```
iwconfig
rfkill list
```
Alternatively try to install this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential linux-firmware
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf 
```
Reboot. Check then:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
uname -a
ifconfig -a
iwlist chan
sudo iwlist scan
```

---

### Post by fleamour on 2011-12-05
> **praseodym said:**
> Try this:

```
sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
```
Check:
```
iwconfig
rfkill list
```

Well that got the lights flashing! 

```
 fleamour@ASRock:~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

However keeps prompting for wireless key & not connecting.

[QUOTE]Alternatively try to install this driver:

Will try this next...

---

### Post by fleamour on 2011-12-05
Lights now show but it continues to prompt for network key repeatedly without actually connecting:

```
fleamour@ASRock:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: ASRock Incorporation Device [1849:8136]
	Kernel driver in use: r8169
--
05:01.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Edimax Computer Co. Device [1432:7722]
	Kernel driver in use: rt2800pci
fleamour@ASRock:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  50 
snd_hda_codec_realtek   254125  1 
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
parport_pc             32114  1 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              28932  2 snd_seq,snd_pcm
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
w83627ehf              29165  0 
hwmon_vid              12658  1 w83627ehf
coretemp               13188  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
fleamour@ASRock:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
fleamour@ASRock:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
fleamour@ASRock:~$ uname -a
Linux ASRock 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux
fleamour@ASRock:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:66:70:d7:fe  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe70:d7fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1084770 (1.0 MB)  TX bytes:293526 (293.5 KB)
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:195200 (195.2 KB)  TX bytes:195200 (195.2 KB)

wlan3     Link encap:Ethernet  HWaddr 80:1f:02:1c:fa:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

fleamour@ASRock:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan3     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
fleamour@ASRock:~$ sudo iwlist scan
[sudo] password for fleamour: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan3     No scan results
```

---

### Post by praseodym on 2011-12-05
Did you blacklist **rt2800pci**? Reboot after that.

---

### Post by fleamour on 2011-12-05
I do not understand?

> **praseodym said:**
> Did you blacklist **rt2800pci**? Reboot after that.

---

### Post by praseodym on 2011-12-05
```
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf

```

---

### Post by fleamour on 2011-12-05
Ah, sorry, not paying attention.  Have to enter code line by line not contiguously.  Stupid, stupid...

I get this error:

```
fleamour@ASRock:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.
--2011-12-05 22:07:27--  http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-12-05 22:07:27 ERROR 404: Not Found.
```

I guess address wrong or syntax error?

---

### Post by praseodym on 2011-12-05
Its a "tar.gz" file:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
```

---

### Post by fleamour on 2011-12-05
Yeh, I did not enter whole line of code.  I was being stooooopiiid, again...

The code needed entering in whole & in the right order without forgetting what you just entered.  But suffice to say, you iz like a walking talking genius, or something!  I now proudly type this over the magic of wireless, oh yes!

To recap, thanks to your ninja like CLI skillz, installing this driver solved it for me:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential linux-firmware
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```

Gotta lurve Linux!

---

### Post by praseodym on 2011-12-05
:guitar:

Please show

```
uname -a
```
You should install the metapackage of the kernel-headers (e.g. linux-headers-generic, -generic-pae, whatever kernel is in use). Dont remove the driver folder, after a kernel upgrade the driver needs to be installed again via:

```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean
sudo make
sudo make uninstall
sudo make install
```

---

### Post by fleamour on 2011-12-05
```
fleamour@ASRock:~$ uname -a
Linux ASRock 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux

```

So this is a non standard driver?  I guess it's not in the kernel then, hence reinstall each kernel upgrade?  OK must make a note.

---

### Post by praseodym on 2011-12-05
No, its non-standard. Install

```
sudo apt-get install linux-headers-generic
```
and you're done with those other 5 command lines.

---

### Post by fleamour on 2011-12-05
OK.  Thanks for your help.

:D :mrgreen: :D

---

### Post by fleamour on 2011-12-21
Wireless connection nose dives & will not be resurrected after roughly five minutes.  Disabled auto channel scan for fixed channel, tried rebuilding driver & same behaviour.

Have rolled back a kernel & seems stable.

Proper bummer.  Advise?  Sit & wait out new kernel release & test again, I guess?


:confused: :-k :confused:

EDIT:  Rolled back a kernel, no dice.  Connection goes down & repeatedly asks for wireless key.  Restarting seems the only way, whereupon it will repeat...

---

### Post by fleamour on 2011-12-21
Seems I had to blacklist old standard driver again:

```
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```

Working so far...

EDIT:  Yey! Solution!

:guitar:\\:D/

---

### Post by barneym on 2012-05-26
Just to record somewhere on the internet that I had no joy getting my wireless card (Edimax EQ-7722In; [FONT="Courier New"]01:09.0 Network controller [0280]: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062][/FONT]) to work with Ubuntu, even following these instructions.

I resorted to posting a support request to help.ubuntu.com.  I followed the [instructions]("https://help.ubuntu.com/community/WirelessTroubleshootingProcedure"), and noticed something interesting in the output.

The command "[FONT="Courier New"]sudo hwinfo --netcard[/FONT]" includes this entry for the wireless card.

[FONT="Courier New"]32: PCI 109.0: 0280 Network controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1814_3062
  Unique ID: CCKF.RHWTd0hqlz0
  Parent ID: H0_h.+lpLGDZYiJF
  SysFS ID: /devices/pci0000:00/0000:00:06.0/0000:01:09.0
  SysFS BusID: 0000:01:09.0
  Hardware Class: network
  Model: "RaLink Network controller"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x3062 
  SubVendor: pci 0x1432 "Edimax Computer Co."
  SubDevice: pci 0x7722 
  Memory Range: 0xfdde0000-0xfddeffff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00001814d00003062sv00001432sd00007722bc02sc80i00"
  Driver Info #0:
    Driver Status: rt2800pci is not active
    Driver Activation Cmd: "modprobe rt2800pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)[/FONT]

I noticed these two lines:
[B][FONT="Courier New"]    Driver Status: rt2800pci is not active
    Driver Activation Cmd: "modprobe rt2800pci"[/FONT][/B]

And ran
**[FONT="Courier New"]sudo modprobe rt2800pci[/FONT]**
And lo and behold, my wireless connection came back to life.

Hope that helps someone.

---

### Post by ratcheer on 2012-05-29
I have been using rt3562sta / rt2860 for my RT3062 PCI card since Jun, 2011 on every distro. I have never been able to get rt2800pci to work at all.

But this morning, every time I tried to use the wireless connection on Siduction, which uses Linux kernel 3.4, it resulted in a kernel panic. In trying to research how I might be able to fix it, I came across an article on the Debian Wiki that states that rt2800pci will work as long as I install the rt2860.bin firmware. They pointed me to a non-free Debian package that contains the firmware. The package is named firmware-ralink.

I installed the package and looked at the binary it installed. The ine from the package is 8192 bytes and is dated Jan 18, 2012. The one downloaded from the Ralink site is also 8192 bytes, but it is dated Jan 27, 2010. Since they are binary, I do not know how to tell whether there is any real difference between them.

So, I uninstalled my rt3562sta driver and un-blacklisted the rt2800pci driver. And now my wireless connects with rt2800pci. However, according to Network Manager, it is connected at a lower speed than rt3562sta, 80 mbps vs 130 mbps.

Anyway, maybe there is some useful info here, somewhere.

Tim

---

### Post by ratcheer on 2012-05-29
> **ratcheer said:**
> ...

So, I uninstalled my rt3562sta driver and un-blacklisted the rt2800pci driver. And now my wireless connects with rt2800pci. However, according to Network Manager, it is connected at a lower speed than rt3562sta, 80 mbps vs 130 mbps.



I tried the same thing on Ubuntu 12.04 and it works, too.

Tim

---

### Post by fleamour on 2012-05-30
Not using this card any more because of problems with Win 7 & sleep function, dropping network after sleep.

I booted Parted Magic CD & noticed card worked out of box.  Parted magic uses latest Linux kernel, so this card should work no tweaking.

---

### Post by noahandersen on 2012-06-01
I could type an almost exact "me too" with [ratcheer]("http://ubuntuforums.org/member.php?u=848769") a couple of postings above.

i have a D-Link n 150 DWA-525 and was installing rt356sta by hand (insmod...etc (because i couldn't get DKMS to work)) and it gave me pretty good through-put.   after kernel 3.4 i started getting kernel panics and someone on LWN told me to try rt2800pci (once again) as it's now "fixed".  well... it does work now (whereas it didn't previously), but it does so at a much reduced throughput and once again, i'm getting some rare "sync" kernel panics.

so here's my question to this august forum:

what is a good solid compliant wireless card that i buy to replace this troubled D-Link card?

thankee!

---

### Post by ratcheer on 2012-06-01
> **noahandersen said:**
> 

so here's my question to this august forum:

what is a good solid compliant wireless card that i buy to replace this troubled D-Link card?

thankee!

Definitely go for an **Intel Pro 1000**. It costs a little more, but it is well-supported and stable.

Tim

---

### Post by noahandersen on 2012-06-01
> **ratcheer said:**
> Definitely go for an **Intel Pro 1000**. It costs a little more, but it is well-supported and stable.

Tim
I don't see a "Intel Pro 1000" **wireless** card.  i see them as wired and fiber adapters...  ?  maybe i'm somehow getting all bad searches? 

thank you in anycase!

---

### Post by ratcheer on 2012-06-01
> **noahandersen said:**
> I don't see a "Intel Pro 1000" **wireless** card.  i see them as wired and fiber adapters...  ?  maybe i'm somehow getting all bad searches? 


Sorry, my mistake. My mind drifted to something else. I have no idea what are well supported, stable wireless cards.

Tim

---

### Post by praseodym on 2012-06-01
Most of Broadcom, but no USB of them!

---

