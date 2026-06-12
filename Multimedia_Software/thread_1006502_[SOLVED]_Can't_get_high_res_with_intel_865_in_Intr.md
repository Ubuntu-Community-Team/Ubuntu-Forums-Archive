---
title: "[SOLVED] Can't get high res with intel 865 in Intrepid"
date: 2008-12-09
forum: Multimedia Software
---

### Post by nowhere@cox.net on 2008-12-09
Hi, Just upgraded to Intrepid from Gutsy (which was working fine at 1600x1200_85). Now 1152x864_60 is about all I can get. Here is some info:
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: Dell Device 0151
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at ed98 [size=8]
	Capabilities: [d0] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: intelfb

```
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
Attached are some screen shots of the Screen Resolution. Untitled1 shows some mirrored setup, but I have only one monitor. Untitled2 shows two screens when I uncheck mirrored, Unknown and Sony 20 inch. It's actually a 21 inch monitor.  Clicking on unknown, you see only a couple resolutions available in Untitled3 but the full range is available in Untitle4 when clicking on the Sony screen. Running in any mode other than mirrored produces nothing the monitor will display including turning off unknown and selecting the Sony specified preferred resolution of 1600x1200_85. 

Using xrandr only gives the error ```
@ubuntu-desktop:~$ xrandr --output VGA --mode 1600x1200
xrandr: cannot find mode 1600x1200

```

I tried using my xorg.conf file from the Gutsy install but again the monitor clicks then goes to sleep.  Each time I try something I have to go to gdm login, select failsafe terminal session, launch the gnome-display-properties and select the defaults to get graphics back. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```does nothing but reset the xorg.conf to its completely minimalist state as listed above.

This 60hz screen flicker is giving me a huge headache so this is all I can stand to post at one time ;)

Does anyone know how to address this? Intrepid is totally different than all other versions as far as X11 configuration.

Please help.
Thanks!

---

### Post by nowhere@cox.net on 2008-12-11
Here's the output of xrandr showing two screens. I only have one!
```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 2048
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS connected 1152x864+0+0 (normal left inverted right x axis y axis) 388mm x 291mm
   1280x1024      85.3 +   85.0     85.0     75.0     60.0  
   2048x1536      60.0     60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      75.0     60.0  
   1600x1200      85.0     85.0     75.0     70.0     65.0     60.0  
   1680x1050      84.9     74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      85.0     74.8     70.0     60.0  
   1440x900       59.9  
   1280x960       85.0     75.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     85.0     75.0     75.0     70.0     60.0* 
   1024x768       85.0     85.0     75.1     75.0     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.0     85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     85.0     75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        87.8     85.0     70.1  
   640x400        85.1  
   640x350        85.1  

```Anyone help?

---

### Post by nowhere@cox.net on 2008-12-11
OK solved. Here's the solution

Intrepid doesn't auto detect the monitor anymore. My little dell has what looks like a DVI output with a pigtail to VGA. I replaced this with someone elses pigtail that was a "Y" connector with VGA and DVI. This fixed the two monitors being detected but Intrepid still didn't see my Sony E500 and detect the modelines. So I searched for some valid modelines, found a monitor section for this monitor from someone's very very old pre-xorg.conf file and used them. Now I have the resolutions I want (almost)

The modeline settings are probably not right for some of the modes, particularly 1600x1200_85. I am set a bit lower and 65hz doesn't have to much flicker so this will do for now...

Cheers!

---

### Post by Talldarknfugly on 2009-01-29
> **nowhere@cox.net said:**
> OK solved. Here's the solution

Intrepid doesn't auto detect the monitor anymore. My little dell has what looks like a DVI output with a pigtail to VGA. I replaced this with someone elses pigtail that was a "Y" connector with VGA and DVI. This fixed the two monitors being detected but Intrepid still didn't see my Sony E500 and detect the modelines. So I searched for some valid modelines, found a monitor section for this monitor from someone's very very old pre-xorg.conf file and used them. Now I have the resolutions I want (almost)

The modeline settings are probably not right for some of the modes, particularly 1600x1200_85. I am set a bit lower and 65hz doesn't have to much flicker so this will do for now...

Cheers!Nowhere@cox, could you please share your settings? I'm having the same problem with the 82865g. Pleaaaaaaaaase, I've been searching for a while and haven't been able to find a resolution.

---

### Post by nowhere@cox.net on 2009-02-17
I believe these are the mode lines I used. 

```
Section "Monitor"
Identifier "Monitor0"
ModelName "E500"
HorizSync 30.0 - 109.0
VertRefresh 48.0 - 160.0
ModeLine "1600x1200@60" 176.7 1600 1632 2296 2328 1200 1224 1236 1261
ModeLine "1600x1200@70" 221.0 1600 1632 2464 2496 1200 1223 1237 1261
ModeLine "1600x1200@75" 245.7 1600 1632 2560 2592 1200 1223 1238 1261
ModeLine "1600x1200@85" 300.9 1600 1632 2768 2800 1200 1222 1239 1261
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Monitor Vendor"
ModelName "E500"
HorizSync 30.0 - 109.0
VertRefresh 48.0 - 160.0
ModeLine "1600x1200@60" 176.7 1600 1632 2296 2328 1200 1224 1236 1261
ModeLine "1600x1200@70" 221.0 1600 1632 2464 2496 1200 1223 1237 1261
ModeLine "1600x1200@75" 245.7 1600 1632 2560 2592 1200 1223 1238 1261
ModeLine "1600x1200@85" 300.9 1600 1632 2768 2800 1200 1222 1239 1261
EndSection

Section "Monitor"
Identifier "Monitor2"
ModelName "E500"
HorizSync 30.0 - 109.0
VertRefresh 48.0 - 160.0
ModeLine "1600x1200@60" 176.7 1600 1632 2296 2328 1200 1224 1236 1261
ModeLine "1600x1200@70" 221.0 1600 1632 2464 2496 1200 1223 1237 1261
ModeLine "1600x1200@75" 245.7 1600 1632 2560 2592 1200 1223 1238 1261
ModeLine "1600x1200@85" 300.9 1600 1632 2768 2800 1200 1222 1239 1261
EndSection
```

This was the only tricky part since these mode lines are not auto detected and not readily available either. This should give you a start.

---

### Post by Reeman on 2009-02-17
I have this same card on an IBM ThinkCentre ...It can run intels openGL drivers and everything just works fine! It is almost like the Dell's hacked up bios that you are using is not reporting your monitor correctly or doing something silly with the ram allocation. 

I have run GoogleEarth 5 with it and had the bios set to the max 32meg of shared ram. Could be that the bios settings that you are using is not enabling enough vram to work the higher modes. Mine was set to 16meg and after reseting the size to 32meg in the bios all of the modes that my monitor (a cheapo acer 19 inch lcd) could take were available with no screen problems at all.

---

