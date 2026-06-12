---
title: "[SOLVED] 1920X1200 nvidia 6600gt, benq g2400wa"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by ildella on 2008-01-15
Hi all. I have installed the new monitor and it worked at a low resolution. 
Then I have imported the .inf definition from the manufacturer driver CD and in displayconfig-gtk there are some new resolution. 
1680X1050@72 is working. 
There is no 1920X1200. The .inf files contains that resolution but there is no sign in xorg.conf. 

xorg.conf is automatically edited by displayconfig-gtk. 

Here are my xorg.conf relevant sections and the whole .inf
Note that in xorg.conf there is no sign of the 1680X1050 resolution. 

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Boardname	"nv"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"BenQ FP937s"
	Vendorname	"BenQ"
	Modelname	"BenQ G2400W (Analog)"
	Horizsync	31-83.0
	Vertrefresh	55.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"BenQ FP937s"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1600x1200@65"	"1600x1200@60"	"1400x1050@75"	"1792x1344@60"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

***************************************************************************

;================================ 

; BenQ_G2400W.INF 10/16/06 Ver. 1.0 

; INF File for Windows Vista/XP/Me/9x/2000

; Copyright (c) 2006, BENQ Corporation

;================================

;

[version]

signature="$CHICAGO$"

Class=Monitor

ClassGuid={4D36E96E-E325-11CE-BFC1-08002BE10318}

Provider=%BenQ%

catalogfile=G2400W.cat

DriverVer=10/16/2006,1.0







[ControlFlags]

ExcludeFromSelect.NT=Monitor\BNQ7809

ExcludeFromSelect.NT=Monitor\BNQ780A





[DestinationDirs]

DefaultDestDir  = 11

G2400W_Analog.copyfiles = 23

G2400W_Digital.copyfiles = 23



[SourceDisksNames]

1=%diskname%,,



[SourceDisksFiles]

G2400WDSUB.icm=1

G2400WDVI.icm=1

; Manufacturers

;-------------------------------------------------



[Manufacturer]

%BenQ%=BenQ,NTx86,NTAMD64





; Manufacturer sections

;-------------------------------------------------

[BenQ] 

%G2400W_Analog%=G2400W_Analog.Install, Monitor\BNQ7809

%G2400W_Digital%=G2400W_Digital.Install, Monitor\BNQ780A



;-------------------------------------------------

 [BenQ.NTx86] 

%G2400W_Analog%=G2400W_Analog.Install, Monitor\BNQ7809

%G2400W_Digital%=G2400W_Digital.Install, Monitor\BNQ780A



;-------------------------------------------------

 [BenQ.NTAMD64] 

%G2400W_Analog%=G2400W_Analog.Install, Monitor\BNQ7809

%G2400W_Digital%=G2400W_Digital.Install, Monitor\BNQ780A





; Install Sections

;-------------------------------------------------



[G2400W_Analog.Install]

DelReg=DEL_CURRENT_REG

AddReg=G2400W_Analog.AddReg, 1920, DPMS

CopyFiles=G2400W_Analog.CopyFiles



[G2400W_Digital.Install]

DelReg=DEL_CURRENT_REG

AddReg=G2400W_Digital.AddReg, 1920, DPMS

CopyFiles=G2400W_Digital.CopyFiles



; AddReg & DelReg sections

;-------------------------------------------------





[DEL_CURRENT_REG]

HKR,MODES

HKR,,MaxResolution

HKR,,DPMS

HKR,,ICMProfile



[1920]

HKR,,MaxResolution,,"1920,1200"



[DPMS]

HKR,,DPMS,,1



; AddReg sections

;----------------------------------------------------------------------------------





[G2400W_Analog.AddReg]

HKR,"MODES\640,480",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\800,600",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\832,624",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\1024,768",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\1280,1024",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\1680,1050",Mode1,,"31-83.0,55.0-60.0,+,+"

HKR,"MODES\1920,1200",Mode1,,"31-83.0,55.0-60.0,+,+"



HKR,,ICMProfile,0,"G2400WDSUB.icm"



[G2400W_Digital.AddReg]

HKR,"MODES\640,480",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\800,600",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\832,624",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\1024,768",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\1280,1024",Mode1,,"31-83.0,55.0-76.0,+,+"

HKR,"MODES\1680,1050",Mode1,,"31-83.0,55.0-60.0,+,+"

HKR,"MODES\1920,1200",Mode1,,"31-83.0,55.0-60.0,+,+"

HKR,,ICMProfile,0,"G2400WDVI.icm"







[G2400W_Analog.CopyFiles]

G2400WDSUB.ICM



[G2400W_Digital.CopyFiles]

G2400WDVI.ICM







[Strings]

MonitorClassName="Monitor"

BenQ="BenQ"

diskname="BenQ LCD Monitor installation diskette"

G2400W_Analog="BenQ G2400W (Analog)"

G2400W_Digital="BenQ G2400W (Digital)"

---

### Post by revoltism on 2008-01-16
I had a similar problem to get 1600-1080.. I found a post with a modeline from a screen similar to mine and it worked after i changed that.

Try find a modeline with a similar screen on 1920x1200 and change the Horizsync  and Vertrefresh to what the manual tell for that resolution.

---

### Post by ildella on 2008-01-16
I found the solution... I was missing the most simple part of the process. 

I have alkready imported inf file from CD using configdisplay-gtk. What was missing is that there is a checbox in the monitor options that says "widescreen monitor". If I check it the 1920 resolution becomes available. 
I just select that resolution and restarted gdm so it is done.

---

