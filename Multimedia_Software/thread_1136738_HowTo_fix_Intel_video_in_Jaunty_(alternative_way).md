---
title: "HowTo fix Intel video in Jaunty (alternative way)"
date: 2009-04-25
forum: Multimedia Software
---

### Post by dentaku65 on 2009-04-25
***Updated 28/04/09**

A new version of Intel driver has been released through PPA.
This driver really improve performances with Jaunty upstream.
The page/repos are here:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

1) Add the PPA repo to the end of your APT sorces.list
```
sudo gedit /etc/apt/sources.list
```
and add the following lines:
> # Intel latest drv for upstream 
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

2) Add the gpg key of this PPA repo
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
```
2) Upgrade the drivers:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
3) Modify your Device section in xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
> Section "Device"
	Identifier	"Configured Video Device"
	Driver	"intel"
	Option "AccelMethod" "UXA"
EndSection

4) Reboot

*** END UPDATE =============**

Hi all.
I'm writing this HowTo in order to give a different way to fix the issues for Intel video cards on Jaunty.

The way showed here is lighter than the one described here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
and I suggest to give a try to this one -before- approaching the one posted by psyke83, that involving the substitution of drivers (xorg-hedgers repository) and kernel (vanilla 2.6.30rc2).

What will follow worked for my Intel card and uses the default Jaunty packages and kernel.
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
I think that on other Intel cards should work as well. Feedbacks are welcome.

1)
Discovering the memory of your card; do this command:
```
lspci -vv
```
and search in the output for the block regarding VGA; in my case:
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 106a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 16
[COLOR="Red"]	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M][/COLOR]
[COLOR="Blue"]	Region 1: Memory at e0380000 (32-bit, non-prefetchable) [size=512K][/COLOR]
	Region 2: I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

In red you can see the amount of the memory that your card can manage and in blue the non-prefetchable memory. In order to use the video card memory in the correct way, you can use Videoram option in xorg.conf; but we must calculate the ram from MB to KB in order to use it in Videoram option; here the table:
> 16 -> 16384
32 -> 32768
64 -> 65536
128 -> 131072
256 -> 262144
Now we have to subtract the value of non-prefetchable to our amount of ram; in my case:
> [COLOR="Red"]131072[/COLOR] - [COLOR="Blue"]512[/COLOR] = 130560

2)
As soon as you calculate your video ram minus the non-prefetchable memory, you can modify your xorg.conf in the device section:
```
sudo gedit /etc/X11/xorg.conf
```
In my case the device section is configured like this:
> Section "Device"
	Identifier	"Configured Video Device"
	Driver	"intel"
	Option "AccelMethod" "UXA"
	VideoRam	130560
EndSection
Please be sure that VideoRam matching the ram of Video card based on what you calculate above. Of course the option UXA is mandatory too.
Save xorg.conf

3)
If you are using Compiz, please modify these settings using Compiz manager:
```
ccsm
```
> Choose General options -> General -> remove the flag on Unredirect Fullscreen Windows
Choose General options -> Display Settings -> remove the flag Sync To VBlank
Close ccsm

4)
Reboot your box

Hope this help

---

### Post by SquiffSquiff on 2009-04-25
Thanks dentaku65

This has worked for me although for 2D only. Still get "Desktop effects could not be enabled" (Compiz). Output of ```
lspci -nn | grep VGA 
``` gives ```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
```

---

### Post by dentaku65 on 2009-04-25
> **SquiffSquiff said:**
> Thanks dentaku65

This has worked for me although for 2D only. Still get "Desktop effects could not be enabled" (Compiz). Output of ```
lspci -nn | grep VGA 
``` gives ```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
```

Did you tried with a 3d game like Ppracer?
```
sudo apt-get install planetpenguin-racer
```
..just to know if is a 3d issue or compiz issue.

---

### Post by psyke83 on 2009-04-25
dentaku,

Precisely what issue does your method fix? I don't think your proposed VideoRam option makes any difference at all, sorry.

```

conn@inspiron:/var/log$ cat /var/log/Xorg.0.log | grep -i videoram
(WW) intel(0): VideoRam configuration found, which is no longer recommended.
(II) intel(0): Continuing with default 131072kB VideoRam instead of 130560 kB.
(**) intel(0): VideoRam: 131072 KB
```

Performance is equal to before. In ppracer - with EXA, about 19-20fps; with UXA, about 25fps. Applying the MTRR fix improves framerate slightly, but not as good as with kernel 2.6.30-rc2 and newer drivers.

P.S. Tested this xorg configuration on kernel 2.6.28-11-generic and the official Jaunty versions of all packages. Also tested using newer kernel and xorg-edgers packages - no difference.

---

### Post by dentaku65 on 2009-04-25
> **psyke83 said:**
> dentaku,

Precisely what issue does your method fix? I don't think your proposed VideoRam option makes any difference at all, sorry.

```

conn@inspiron:/var/log$ cat /var/log/Xorg.0.log | grep -i videoram
(WW) intel(0): VideoRam configuration found, which is no longer recommended.
(II) intel(0): Continuing with default 131072kB VideoRam instead of 130560 kB.
(**) intel(0): VideoRam: 131072 KB
```

Performance is equal to before. In ppracer - with EXA, about 19-20fps; with UXA, about 25fps. Applying the MTRR fix improves framerate slightly, but not as good as with kernel 2.6.30-rc2 and newer drivers.

P.S. Tested this xorg configuration on kernel 2.6.28-11-generic and the official Jaunty versions of all packages. Also tested using newer kernel and xorg-edgers packages - no difference.

I have good performances indeed; unfortunately I cannot post FPS of ppracer because "ppracer -a" give me this:
> get fences failed: -1
param: 6, val: 0
Benchmark error: unable to set course: 

without -a switch is playable very good in fullscreen too

Glxgears give me this:
> 1396 frames in 5.0 seconds = 279.030 FPS
1412 frames in 5.0 seconds = 282.383 FPS
1427 frames in 5.0 seconds = 285.396 FPS
1423 frames in 5.0 seconds = 284.433 FPS
1427 frames in 5.0 seconds = 285.277 FPS
1420 frames in 5.0 seconds = 283.888 FPS
1426 frames in 5.0 seconds = 285.185 FPS


---

### Post by densou on 2009-04-25
it seems your stuff can work better on i8xx cards rather on i9xx ones ;)

have you upgraded your Gnome Mplayer to 0.9.5 ? It solved my awful video output when using UXA with fairly new 2.7.0 driver (GMA950) ....

---

### Post by rnrover on 2009-04-25
Fantastic, your quick fix worked.  Many thanks.:popcorn:

After checking the automatic upgrade option in package manager I have had a terrible 24 hours.  I lost the upgrade completely.  Had to download the "full Jaunty" and start over.  

Compiz was jumpy and opening any window was slow.

My experience with automatic upgrades are over.  I wish Canonical or the developers of new releases would disable that feature until they are sure it works for all platforms.  After my upgrade my system would not boot into a gui or terminal. The safe mode did not fix anything because the eth0 couldn't be enabled to download the broken packages.

My system:
Toshiba Satellite P105 w/ 4Gig memory/ Intel graphics/  

This is my Xorg.conf file that I changed with your instructions.

[INDENT]Section "Device"
	Identifier	"Configured Video Device"
        Driver "intel"
        Option "AccelMethod" "UXA"
        VideoRam 261888
EndSection[/INDENT] 

Again Thanks, Mucho Gracias,

---

### Post by dentaku65 on 2009-04-25
> **rnrover said:**
> Fantastic, your quick fix worked.  Many thanks.:popcorn:

After checking the automatic upgrade option in package manager I have had a terrible 24 hours.  I lost the upgrade completely.  Had to download the "full Jaunty" and start over.  

Compiz was jumpy and opening any window was slow.

My experience with automatic upgrades are over.  I wish Canonical or the developers of new releases would disable that feature until they are sure it works for all platforms.  After my upgrade my system would not boot into a gui or terminal. The safe mode did not fix anything because the eth0 couldn't be enabled to download the broken packages.

My system:
Toshiba Satellite P105 w/ 4Gig memory/ Intel graphics/  

This is my Xorg.conf file that I changed with your instructions.

[INDENT]Section "Device"
	Identifier	"Configured Video Device"
        Driver "intel"
        Option "AccelMethod" "UXA"
        VideoRam 261888
EndSection[/INDENT] 

Again Thanks, Mucho Gracias,

Good :guitar:
Can you post your card model, please?
```
lspci |grep VGA
```

---

### Post by rnrover on 2009-04-25
> **dentaku65 said:**
> Good :guitar:
Can you post your card model, please?
```
lspci |grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Here you go

---

### Post by drbenway2 on 2009-04-25
Thanks much, dentaku65.  Your fix also worked perfectly for me.  I have an older Compaq desktop.
 
brw@brw-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by Happibun on 2009-04-26
Thanks for this alternative dentaku65, it looks a lot less frightening than installing Debian kernels etc.  

It looks like I have the bug too, but my ancient Dell seems to have a different set up. 

> $ lspci -vv  

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)     
Subsystem: Dell Device 01cb     
Control:     
Latency: 0     
Interrupt: pin A routed to IRQ 16     
Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K]     
Region 1: I/O ports at eff8 [size=8]     
Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]    
Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]     
Capabilities:      
Kernel modules: intelfb  

I am not confident using terminal, I don't really know what I am looking at, but I can see that this:-  

> Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K] 
Region 1: I/O ports at eff8 [size=8] 
Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M] 
Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]  

is not the same as this:-  

> Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M] 
Region 1: Memory at e0380000 (32-bit, non-prefetchable) [size=512K] 
Region 2: I/O ports at ec00 [size=8]  

I could stab at it and really mess my lappy up, but I think it might be better for me to ask someone who knows what they are doing first.  

Erm... help?  

Thank you. 

PS. I did preview this post, and the layout and formatting was totally messed up when I checked it out. I can't interact with the WISIWYG editor like I have done before, and I could not find a way to fix it, so I'm posting it anyway. I am really sorry if the end result looks like gobbldygook.

Update: I had to fire up another machine (running mint) to format this post. Something is very wrong with the Dell. It does not interact with the scripts on this site at all well.

---

### Post by Happibun on 2009-04-26
Oh that looks terrible. Things worked before. No carriage return, no java = utter mess. So sorry.

---

### Post by H4F on 2009-04-26
|
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	InputDevice	"Synaptics Touchpad"
EndSection

Where do I write config  ? Device Monitor or Screen . And those things should I change ?:
Identifier "Configured Video Device"
Driver "intel"
Option "AccelMethod" "UXA"

EndSection

---

### Post by dentaku65 on 2009-04-26
> **Happibun said:**
> Oh that looks terrible. Things worked before. No carriage return, no java = utter mess. So sorry.

You can use the same amount of mine memory. See for this the post #1 the options posted under device of xorg.conf.

This is for the video card. But I have the idea that your issues do not belong totally from video card. For about this web site, did you tried with another browser? To see if is a problem of Firefox or a generic problem; you can use Opera
```
sudo apt-get install opera
```

---

### Post by dentaku65 on 2009-04-26
> **H4F said:**
> |
[B]Section "Device"
	Identifier	"Configured Video Device"
EndSection[/B]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	InputDevice	"Synaptics Touchpad"
EndSection

Where do I write config  ? Device Monitor or Screen . And those things should I change ?:
Identifier "Configured Video Device"
Driver "intel"
Option "AccelMethod" "UXA"

EndSection

[B]Section "Device"
	Identifier	"Configured Video Device"
EndSection[/B]
Inside the marker Section "Device" EndSection 
As indicated in post #1

---

### Post by H4F on 2009-04-26
```
	Region 0: Memory at 94000000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at 80000000 (64-bit, prefetchable) [size=256M]

```
you have 512 k and substracted 512
I have 1M should I substract  1 or 1024

---

### Post by psyke83 on 2009-04-26
dentaku,

Can you please explain how using the VideoRAM parameter improves your driver experience?

I think it is only the UXA acceleration method that has improved your setup, as the VideoRAM parameter is completely ignored (you'll see it in your log). If you know otherwise, however, I'd be interested to know why reducing the videoram allocation helps.

---

### Post by dentaku65 on 2009-04-27
> **psyke83 said:**
> dentaku,

Can you please explain how using the VideoRAM parameter improves your driver experience?

I think it is only the UXA acceleration method that has improved your setup, as the VideoRAM parameter is completely ignored (you'll see it in your log). If you know otherwise, however, I'd be interested to know why reducing the videoram allocation helps.

Hi psyke83,
I discovered that putting the Videoram option with UXA the performances of my Intel card became more stable and acceptable for everyday jobs, basically web flash video, G-earth and compiz (or let's say they working nice on my box); I got the ignored message too in xorg log, but without Videoram option the applications I've mentioned above are very problematic (I mean with only UXA enabled), web flash block all resources of my machine, google earth is useless.

Without subtracting the non-prefetchable memory, but putting all whole memory in Videoram option X does not start at all.

I think your HowTo is very advanced but you must consider that many users are newbie and they should have big problems implementing your indications; that why I've ask you somewhere to post my link in order to indicate a sort of easy way for that kind of ubuntu users. In this sense my HowTo is regarding with: play on what you have; and is not comparable in any way to your HowTo that's is more specific and truly improved for Intel cards.

ciao!

---

### Post by dentaku65 on 2009-04-27
> **H4F said:**
> ```
	Region 0: Memory at 94000000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at 80000000 (64-bit, prefetchable) [size=256M]

```
you have 512 k and substracted 512
I have 1M should I substract  1 or 1024

Hi H4F,
ehm...
> 262144 - 1024 = **261120**

---

### Post by drbenway2 on 2009-04-27
psyke83,
 
I have noticed similar results to dentaku65.  I don't know the reason for this, it "just works".  I also tried your method, and it also works, however I use vmware server and there is no vmware patch yet available that I could find that would allow the vmware server modules to compile using the 2.6.30-rc2 kernel sources.
 
So far I have not seen any instability using this method, but time will tell, I suppose.
 
Many thanks to both of you for taking the time to find a workaround to this issue.

---

### Post by mediumcool on 2009-04-27
Worked great for me - UXA without VideoRAM = lockups for me - no more lockups with it explicitly configured in xorg so far.

---

### Post by girtsn on 2009-04-27
It fixed stuff for me as well.
I was unable to get to the login screen most of the time from a cold boot. Now it works constantly (at least until now).
I have disabled the RAM setting because it seems to be ignored anyway.
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) here.

---

### Post by dentaku65 on 2009-04-27
> **girtsn said:**
> It fixed stuff for me as well.
I was unable to get to the login screen most of the time from a cold boot. Now it works constantly (at least until now).
I have disabled the RAM setting because it seems to be ignored anyway.
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) here.

Hi girtsn,
the xorg log say the disabling to me too, but without videoram option my machine look-up watching youtube. Are you able to watch youtube without videoram option?

---

### Post by pebo on 2009-04-27
Dentaku65,
Doesn't work for me, at least, I get a big improvement but when I log out I get a blank screen and complete lock-up, requiring the old magic sysrq. 
Maybe I'm doing the sums wrong - lspci -vv gives me ```
        Region 0: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]                          
        Region 1: I/O ports at ec00 [size=8]                                                         
        Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]                              
        Region 3: Memory at feb40000 (32-bit, non-prefetchable) [size=256K]                          
```I used Region 2 & Region 3 which gives me 261888. The lock-up occurs whether I have the video ram set or not. Any suggestions?
Thanks for your work on this so far...

---

### Post by dentaku65 on 2009-04-27
> **pebo said:**
> Dentaku65,
Doesn't work for me, at least, I get a big improvement but when I log out I get a blank screen and complete lock-up, requiring the old magic sysrq. 
Maybe I'm doing the sums wrong - lspci -vv gives me ```
        Region 0: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]                          
        Region 1: I/O ports at ec00 [size=8]                                                         
        Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]                              
        Region 3: Memory at feb40000 (32-bit, non-prefetchable) [size=256K]                          
```I used Region 2 & Region 3 which gives me 261888. The lock-up occurs whether I have the video ram set or not. Any suggestions?
Thanks for your work on this so far...

Can be the UXA option that causing the problem; try without it in xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
#	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
EndSection

```

---

### Post by brianpeiris on 2009-04-27
[SIZE="4"]Thank you Dentaku65, your fix seems to work perfectly in my case.[/SIZE]

> **pebo said:**
> Dentaku65,
Doesn't work for me, at least, I get a big improvement but when I log out I get a blank screen and complete lock-up, requiring the old magic sysrq. 
Maybe I'm doing the sums wrong - lspci -vv gives me ```
        Region 0: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]                          
        Region 1: I/O ports at ec00 [size=8]                                                         
        Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]                              
        Region 3: Memory at feb40000 (32-bit, non-prefetchable) [size=256K]                          
```I used Region 2 & Region 3 which gives me 261888. The lock-up occurs whether I have the video ram set or not. Any suggestions?
Thanks for your work on this so far...

pebo, it seems your hardware configuration is similar to mine. This is what lspci printed in my case: 

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Gateway 2000 Device 0281
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        [COLOR="Blue"]Region 0: Memory at d8100000 (32-bit, non-prefetchable) [size=512K][/COLOR]
        Region 1: I/O ports at 1800 [size=8]
        [COLOR="Red"]Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M][/COLOR]
        Region 3: Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel modules: intelfb

```

Instead of "Region 3" I used "Region 0" so my calculation was

```
262144 - 512 = 261632
```

Then I added the highlighted lines my xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="DarkOrange"]Driver		"intel"
	Option		"AccelMethod" "UXA"
	VideoRam	261632[/COLOR]
EndSection

```

---

### Post by mediumcool on 2009-04-27
Ok, unfortunately I have now had a lockup with UXA and VideoRam set in xorg.conf.

---

### Post by dentaku65 on 2009-04-27
> **mediumcool said:**
> Ok, unfortunately I have now had a lockup with UXA and VideoRam set in xorg.conf.

Maybe this link can be useful

[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

---

### Post by Happibun on 2009-04-27
> **dentaku65 said:**
> You can use the same amount of mine memory. See for this the post #1 the options posted under device of xorg.conf.

This is for the video card. But I have the idea that your issues do not belong totally from video card. For about this web site, did you tried with another browser? To see if is a problem of Firefox or a generic problem; you can use Opera
```
sudo apt-get install opera
```

Thanks dentaku, I'm sorry about the garbled second message. It is true that the Jaunty upgrade has caused the bug with my graphics card, and also apparently issues with Firefox on that laptop. 

The only way I can access this forum at the moment, and post anything readable is to use a different machine. The second message was an apology for the first one, which I had to originally post without any formatting and in one block - it was utterly unreadable and garbled. I had to re-edit it later to make it make sense. I could not delete the second message, and I thought I had editied it to be blank, but obviously not. Sorry to have caused any confusion.

I will try to fix the video card first, then worry about firefox later :-) 

So, if I understand you right, I will work it with [COLOR=Blue]512[COLOR=Black]k of[/COLOR] RAM[COLOR=Black].[/COLOR]
[/COLOR]

---

### Post by Happibun on 2009-04-27
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Yay! It works beaut. Thank you.

---

### Post by cpeee on 2009-04-28
works great here as well. my glxgear speed increase a whopping 4X. Now need to find a way to get the 3D effect enable. we are getting there :) Thanks a lot!

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

---

### Post by Matt0001 on 2009-04-28
The 4/28 updated instructions worked great for me. Full-screen Flash video from Hulu (the real deal breaker for me) is now working just fine. Planet Penguin Racer is running at about 15-24 fps. Thanks for the simple instructions.

---

### Post by VMC on 2009-04-28
> **dentaku65 said:**
> ***Updated 28/04/09**

A new version of Intel driver has been released through PPA.
This driver really improve performances with Jaunty upstream.
The page/repos are here:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

1) Add the PPA repo to the end of your APT sorces.list
```
sudo gedit /etc/apt/sources.list
```
and add the following lines:

2) Add the gpg key of this PPA repo
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
```
2) Upgrade the drivers:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
3) Modify your Device section in xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

4) Reboot

*** END UPDATE =============**

This did not work for my video chip. The only fix that works is to revert back to Intel 2.4.

My info is this:

```
lspci -nn | grep VGA
```

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

```

If you have the same chip I would like to know exactly how you got it to work with the new updated Intel driver.

---

### Post by dentaku65 on 2009-04-29
> **VMC said:**
> This did not work for my video chip. The only fix that works is to revert back to Intel 2.4.

My info is this:

```
lspci -nn | grep VGA
```

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

```

If you have the same chip I would like to know exactly how you got it to work with the new updated Intel driver.

I have a different chip.
Check the testing report on UXA for your card here:
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

You can try without UXA using EXA that in Jaunty is the default method of accelleration; in Devices section of xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver "intel"
**#**	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
EndSection
```
Restart your machine.

---

### Post by VMC on 2009-04-29
I have yet to find anyone with the "Intel Corporation 82865G Integrated Graphics Controller" with a working video, with the exception of the Intel rollback method.

I updated that UXA wiki to reflect my findings. All the 82865G chips just will not work as you can tell by the notes. The old Intel  v2.4 works fine, I just don't know why on all the PPA's and Intel update notices they state i8xx. It appears that the i9xx series works.

---

### Post by dentaku65 on 2009-04-29
> **VMC said:**
> I have yet to find anyone with the "Intel Corporation 82865G Integrated Graphics Controller" with a working video, with the exception of the Intel rollback method.

I updated that UXA wiki to reflect my findings. All the 82865G chips just will not work as you can tell by the notes. The old Intel  v2.4 works fine, I just don't know why on all the PPA's and Intel update notices they state i8xx. It appears that the i9xx series works.

I think I have an 18xx card on my notebook
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Just different than yours; I really think that UXA in your case/chip is still not ready or, maybe, your card is blacklisted.

---

### Post by muhannadfa on 2009-04-29
the updated method didn't work for me
any more help
jaunty

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)

thanks in advance

---

### Post by dentaku65 on 2009-04-29
> **muhannadfa said:**
> the updated method didn't work for me
any more help
jaunty

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)

thanks in advance

There is a detailed guide here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
but is not upstream and quite bleeding-edge, but works for many folks.

---

### Post by muhannadfa on 2009-04-29
okey thanks folks
i'll see what happens & give feedback

---

### Post by muhannadfa on 2009-04-29
it improves the sysmptoms of the problem, but no complete solving
----------------------
q: is it upgrading the kernel or the whole method, dunn know
-------------------------------
it needs alot of work actually

------------------------------
thanks

---

### Post by muhannadfa on 2009-04-29
> 
There is a detailed guide here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
but is not upstream and quite bleeding-edge, but works for many folks.
__________________
srry for that,
after full testing time
seems it improves the symptoms of the problem but doesn't solve it completely
this is my experince with da provided guide,
any more help

---

### Post by VMC on 2009-04-29
> **dentaku65 said:**
> I think I have an 18xx card on my notebook

Just different than yours; I really think that UXA in your case/chip is still not ready or, maybe, your card is blacklisted.
It is blacklisted. How does that work or effect my outcome. I forgot about it being blacklisted.

---

### Post by eyecolor on 2009-04-30
worked fine for me.
haven't checked everything so far but all seems quite stable now.
thanx a lot for the HowTo

this is my video card
```
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```

on samsung Q35

---

### Post by jpborjas on 2009-04-30
Funny that it also worked for me, as I couldn't get the key added to authenticate the repository:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any ideas?

---

### Post by rowanq on 2009-04-30
I'm also happy to report success with this method. I have an Acer Asper 5570z with Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03).

Thanks, dentaku65, this really helped me out.

---

### Post by tantos on 2009-05-01
hi dentaku,
thx for this howto, it work fine for me
Im using Compaq CQ40-324TU
my card is : 
```

lspci -nn | grep VGA

```
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)

```

when I using your xorg.conf
```

Section "Device"
	Identifier "Configured Video Device"
	Driver "intel"
	Option "AccelMethod" "UXA"
EndSection

```
it makes glxgears approx 600 FPS, but ppracer only run in 9 FPS


but when I using psyke83 howto's in [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582") :
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false"
EndSection

```
it makes glxgears run approx 400 FPS, but ppracer can run in 16-20 FPS

but, thx alot for this howto :guitar:

---

### Post by dentaku65 on 2009-05-02
> **tantos said:**
> hi dentaku,
thx for this howto, it work fine for me
Im using Compaq CQ40-324TU
my card is : 
```

lspci -nn | grep VGA

```
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)

```

when I using your xorg.conf
```

Section "Device"
	Identifier "Configured Video Device"
	Driver "intel"
	Option "AccelMethod" "UXA"
EndSection

```
it makes glxgears approx 600 FPS, but ppracer only run in 9 FPS


but when I using psyke83 howto's in [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582") :
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false"
EndSection

```
it makes glxgears run approx 400 FPS, but ppracer can run in 16-20 FPS

but, thx alot for this howto :guitar:

I think that this line in your xorg.conf for your card
> 	Option		"Tiling"			"false"

makes the difference.

---

### Post by Arup on 2009-05-02
On my G31 PC I tried the latest stable drivers from PPA, however running glxgears or even Penguin racer, the system would lock up, I reverted back to the older xorg which comes with Jaunty and the problem went away. I have UXA enabled on both.

---

### Post by bug67 on 2009-05-02
Worked for me!  :)  

Actually, everything was *almost* working fine from the get-go.  I was having some flickering while streaming online video in full screen and, none of my screensavers were working fight.  I didn't do the vram calculations.  Don't seem to need to.  thanks!

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```

---

### Post by jaithehulk on 2009-05-02
Dude dentaku ur awesome!!!
The second fix worked wonders for me!!!!
The Xserver even detected my MONITOR!!!! which had remained undetected from 8.10!!!!

---

### Post by JamesGu on 2009-05-04
> **SquiffSquiff said:**
> Thanks dentaku65

This has worked for me although for 2D only. Still get "Desktop effects could not be enabled" (Compiz). Output of ```
lspci -nn | grep VGA 
``` gives ```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
```

Your card is [blacklisted](http://wiki.compiz-fusion.org/Hardware/Blacklist) by compiz. If you run 'compiz' at the command line, you'll get a message to this effect. I have a 8086:2a02 and see the same. You can force it to start anyway (see the link above) and it may or may not work, YMMV. Of course, you'll need acceptable intel 3D performance first.

---

### Post by djauto23 on 2009-05-04
Thanks for the effort! It's working fine with me, albeit some intriguing results mentioned below.

First one question: How do I easily revert the changes? And how will this affect updates from Ubuntu repositories? Should I keep that line in sources.list?

Then to the results. When I first boot up the machine, I get this from glxgears, which are roughly the same that I had before doing these changes:
```
2687 frames in 5.0 seconds = 537.297 FPS
2716 frames in 5.0 seconds = 543.009 FPS
2729 frames in 5.0 seconds = 545.661 FPS
2705 frames in 5.0 seconds = 540.729 FPS
```

Then, after a suspend/resume:
```
3699 frames in 5.0 seconds = 739.774 FPS
3719 frames in 5.0 seconds = 743.633 FPS
3733 frames in 5.0 seconds = 746.416 FPS
3721 frames in 5.0 seconds = 744.172 FPS
3750 frames in 5.0 seconds = 749.884 FPS
```

PPRaver gives me about 20fps after fresh reboot, and about 30-35 after a suspend/resume. 

This is what's in xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod" "UXA"
	#Intel fix:
	#Driver "intel"
	#VideoRam 261120
EndSection
```

The lines commented out does not, as far as I can tell, make any difference.

lspci -vv:
```
VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 110f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2297
	Region 0: Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 18f8 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb
```

The machine is a Fujitsu-Siemens U9200.

I'm happy to say that suspend/resume now works, as opposed to before (with UXA), when it made the machine log out upon resuming. Therefore of course I can live with 3d performance being a little worse upon reboot, so things are definetely better than before :P

---

### Post by rudy.b on 2009-05-04
Thanks for posting this fix.  

This method noticeably improved the performance of video on my system.  Although the _[HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")_ actually worked better for me, but the fact that I can't get my wireless card to work with the new kernel was a deal-breaker for me.

My interface:
```
$ lspci
...
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
...
```

---

### Post by bug67 on 2009-05-05
> **djauto23 said:**
> "...And how will this affect updates from Ubuntu repositories? Should I keep that line in sources.list..?"

Yes, I too am interested in an answer to this question.

:popcorn:

---

### Post by dschouten on 2009-05-08
Well, to be honest, I don't see why half the users of Ubuntu, aka those who have Intel cards, should be installing custom kernels (which of course is a lot more work if you need to setup restricted drivers for wireless) or screwing around with Xorg and drivers. 

Intel graphics worked great in Hardy.

Jaunty had a test cycle ... this bug was picked up before it was finally released.

Yet they still released an unworkable version for 1/2 the users. Bullshi*

Get beyond the hype of a new release and take the time to make sure that "basic" functionality, like you know, graphics that don't suck, works! Jaunty is starting to look like Vista ...

My two cents.

---

### Post by kagimaro on 2009-05-09
I agree with you dschouten,

I tried every solutions to get my Intel Graphics card to work, (rev07) .. but with no success, i gave ubuntu the chance manytimes to use it as primary OS on my laptop.

But here i am back to windows, and am using Windows7 RC, and its working fine without any problems.

If you want to get more people to jump on and start using ubuntu, you can't force them to deal with terminal and commands stuff, you should give them something that easy to use.

and plz people .. don't repeat the same thing that linux is more stable than widnows and the usual talk .. i've used OSX / Linux / Windows / OS2 / BeOS .. and each OS has its bad and good.

but still i can't compare any of the above to windows when it comes to something that just WORKS!

---

### Post by Arup on 2009-05-09
On the same note I have few pieces of hardware that I almost threw out before I installed Ubuntu. Notable among them was Yamaha's excellent DSXG Waveforce sound card which doesn't have any support in Windowsx64 world. Also a cheap but good webcam which never had any driver for it in Vista x64 works flawlessly in Ubuntu. Now speaking of Intel, even with Intel's latest driver, it has a EDID issue where it doesn't run resolutions like 1440x900 native on some LCD panels. You have to hack the driver to get it to recognize the LCD's native resolution. So please don't go about blaming Ubuntu, every OS has its fair share of headaches and I have been through all as well.

---

### Post by dschouten on 2009-05-13
> **Arup said:**
> So please don't go about blaming Ubuntu, every OS has its fair share of headaches and I have been through all as well.

@Arup: I am not a Ubuntu or Linux detractor normally; in fact I have been a strong proponent of open source for years. In fact, since I reverted back to Hardy I was reminded how generally awesome this free software is.

However, I think Canonical should rethink its release strategy if some large fraction of laptop owners can't run Jaunty reliably without installing a custom kernel, which then breaks other things. Anyone with a Broadcom wireless card? Do you like compiling the drivers from source? Security updates for your custom kernel? 

On the scale of getting things right, Compiz bling and a new GDM theme are much less important than basic hardware compatibility.

If some hardware works in last year's OS, it should work in this year's. If X > Y, then version X should support all hardware that is supported in Y, and more, especially if the now-unsupported hardware is not anywhere near legacy (Intel cards are in probably 50% of all laptops sold).

But I still love (Ubuntu) Linux.

---

### Post by zenboy on 2009-05-18
> **Arup said:**
> On the same note I have few pieces of hardware that I almost threw out before I installed Ubuntu. Notable among them was Yamaha's excellent DSXG Waveforce sound card which doesn't have any support in Windowsx64 world. Also a cheap but good webcam which never had any driver for it in Vista x64 works flawlessly in Ubuntu. Now speaking of Intel, even with Intel's latest driver, it has a EDID issue where it doesn't run resolutions like 1440x900 native on some LCD panels. You have to hack the driver to get it to recognize the LCD's native resolution. So please don't go about blaming Ubuntu, every OS has its fair share of headaches and I have been through all as well.

Boys, boys, boys!! We all been around Linux for some times (at least at an amateur level, that is), but what bothers me about Linux is that it still expect the user to know a bit about troubleshooting and using CLI to get the OS running smoothly, and this is its own catch-22. For the past 8 years following the status of Linux, I still am not convinced about it being the main OS for most users to use. Among the most important issues that the developers should address before they decide to put this latest release (which is not a beta nor alpha) out, is the graphic card and the wireless/Ethernet NIC. How do we promote Linux as a stable and easy OS for end-users when they can not even see the darn screen when the video setting is misconfigured or the NIC driver and setting are not automatically detected for the users to the Internet to find out about fixing other issues with Linux? Please do not tell us the Intel video card is a small issue that would not affect many people because this goes to show that Linux developers are just as misinformed as Microsoft's about the need of the general audience who happens to have an Intel video card in their PCs. 
It has been now almost two weeks since I have installed this latest release of Ubuntu, and I have not yet to get around fixing the Intel video card that is my PC because I hear different conflicting solutions on this thread to getting the darn video card to work.
On top of that, I have yet to hear any assistant from the developers on releasing a patch for this problem.
  I am just a regular PC user who would like to see if I could finally switch to Linux once and for all (been contemplating for 8 years!), but there is still that haunting feeling inside of me that there will many more of those long nights that I might have to roll up my sleeve to fix an issue that I might not have knowledge of pertaining to Linux.
  If we all want Linux to succeed on the desktop for the general mass, please keep in mind to develop Linux to be intuitive and stable for the least knowledgeable end-users. 
In the meantime, I will have to find some time to fix this nagging video problem once and for all (which is hard when I have two babies waking up the whole house every now and then).

---

### Post by Arup on 2009-05-18
> **zenboy said:**
> Boys, boys, boys!! We all been around Linux for some times (at least at an amateur level, that is), but what bothers me about Linux is that it still expect the user to know a bit about troubleshooting and using CLI to get the OS running smoothly, and this is its own catch-22. For the past 8 years following the status of Linux, I still am not convinced about it being the main OS for most users to use. Among the most important issues that the developers should address before they decide to put this latest release (which is not a beta nor alpha) out, is the graphic card and the wireless/Ethernet NIC. How do we promote Linux as a stable and easy OS for end-users when they can not even see the darn screen when the video setting is misconfigured or the NIC driver and setting are not automatically detected for the users to the Internet to find out about fixing other issues with Linux? Please do not tell us the Intel video card is a small issue that would not affect many people because this goes to show that Linux developers are just as misinformed as Microsoft's about the need of the general audience who happens to have an Intel video card in their PCs. 
It has been now almost two weeks since I have installed this latest release of Ubuntu, and I have not yet to get around fixing the Intel video card that is my PC because I hear different conflicting solutions on this thread to getting the darn video card to work.
On top of that, I have yet to hear any assistant from the developers on releasing a patch for this problem.
  I am just a regular PC user who would like to see if I could finally switch to Linux once and for all (been contemplating for 8 years!), but there is still that haunting feeling inside of me that there will many more of those long nights that I might have to roll up my sleeve to fix an issue that I might not have knowledge of pertaining to Linux.
  If we all want Linux to succeed on the desktop for the general mass, please keep in mind to develop Linux to be intuitive and stable for the least knowledgeable end-users. 
In the meantime, I will have to find some time to fix this nagging video problem once and for all (which is hard when I have two babies waking up the whole house every now and then).


FYI, IGP has quite a few issues in Windows front as well so all is not well there.

---

### Post by zenboy on 2009-05-18
> **Arup said:**
> FYI, IGP has quite a few issues in Windows front as well so all is not well there.

Still playing the defensive game again, huh? 
So are you justifying that if Windows have few issues than it is ok for Linux to have just as well? 2 bads don't make a right.
My video card is able to play movie while in Windows. In the meantime, I am digging in tons of postings to see what is the FINITE SOLUTION to this problem. I have tried 4 times already going along with many suggestions to get the video right; so far, none have worked. I guess I will hang in there for several weeks until some gurus who are kind enough to come around and get us out of this hole before I decide to wipe this Ubuntu off my drive.

---

### Post by Arup on 2009-05-18
> **zenboy said:**
> Still playing the defensive game again, huh? 
So are you justifying that if Windows have few issues than it is ok for Linux to have just as well? 2 bads don't make a right.
My video card is able to play movie while in Windows. In the meantime, I am digging in tons of postings to see what is the FINITE SOLUTION to this problem. I have tried 4 times already going along with many suggestions to get the video right; so far, none have worked. I guess I will hang in there for several weeks until some gurus who are kind enough to come around and get us out of this hole before I decide to wipe this Ubuntu off my drive.

Nope, is it all black and white as that? The problem is Intel, not Ubuntu and crux lies on them to fix the issues, not Ubuntu. Since you are a Win fanboi defending Win, its just useless to talk any sense to you. The same Intel G31 would not run in native resolution on Vista x64, the taskbar would freeze from time to time, check Intel forum and see the myriads of issues being faced by Win users, btw, movies worked fine with the G31 on Jaunty except for CPU usage and that went away once UXA was enabled in xorg. I have installed Jaunty on other IGP notebooks and never faced any issues, granted they were all the newer Intel chips.

So blame Intel, not Ubuntu.

---

### Post by nextekcarl on 2009-05-19
Thanks. I still have a little video tearing, but it is back to the way it was (maybe better) than before I upgraded to 9.04. When I first upgraded most video worked fine in full screen, but with flash video (like hulu) it was horrible. Not only would it tear really badly (3 or 4 simultaneous tears on the screen) but the video would randomly pause for a second or so (while the audio continued without a hiccup) and then it would refresh, only to pause again. It was unplayable, and right before the upgrade it worked pretty well. And now it seems to be at least as well as before the upgrade, if not a bit better.

---

### Post by zenboy on 2009-05-19
> **Arup said:**
> Nope, is it all black and white as that? The problem is Intel, not Ubuntu and crux lies on them to fix the issues, not Ubuntu. Since you are a Win fanboi defending Win, its just useless to talk any sense to you. The same Intel G31 would not run in native resolution on Vista x64, the taskbar would freeze from time to time, check Intel forum and see the myriads of issues being faced by Win users, btw, movies worked fine with the G31 on Jaunty except for CPU usage and that went away once UXA was enabled in xorg. I have installed Jaunty on other IGP notebooks and never faced any issues, granted they were all the newer Intel chips.

So blame Intel, not Ubuntu.


Win fanboi? Moi? Quite the contrary. Whichever OS works best for me, I will stick with that until the underdog gets better. You, on the other hand, are one of those few 'Linux is the only way' occult fanboys who could only see matters in black/white and would blow your top on newcomers who has constructive criticisms and suggestions.    
    Do you know why Linux has not been able to to maintain itself on most of the general users' desktops for the past ten years or emerge from the shadow of Windows? It is because occult fanyboys like you who, just as bad as die-hard Windows followers, could only see from one point of view. It is time for you to step into the middle and look around; learn to listen to newcomers like me who has been willing to step up to the plates years after years to test drive and hope to taste the real juice of Linux you claim it to be.

PS Isn't it ironic how the developers were able to get this particular Intel video card to work correctly under Ubuntu 8.10 and not Ubuntu 9.04?

---

### Post by dentaku65 on 2009-05-20
@arup
@zenboy

Even if your discussions are interesting, I suggest to do not post them in this tread, that is focused to give help to people with Intel card on Jaunty.

Thanks ;)

---

### Post by jsday187 on 2009-05-20
> **rnrover said:**
> Fantastic, your quick fix worked.  Many thanks.:popcorn:

After checking the automatic upgrade option in package manager I have had a terrible 24 hours.  I lost the upgrade completely.  Had to download the "full Jaunty" and start over.  

Compiz was jumpy and opening any window was slow.

My experience with automatic upgrades are over.  I wish Canonical or the developers of new releases would disable that feature until they are sure it works for all platforms.  After my upgrade my system would not boot into a gui or terminal. The safe mode did not fix anything because the eth0 couldn't be enabled to download the broken packages.

My system:
Toshiba Satellite P105 w/ 4Gig memory/ Intel graphics/  

This is my Xorg.conf file that I changed with your instructions.
[INDENT]Section "Device"
    Identifier    "Configured Video Device"
        Driver "intel"
        Option "AccelMethod" "UXA"
        VideoRam 261888
EndSection[/INDENT]Again Thanks, Mucho Gracias,

Where the heck do you find an Automatic UPGRADE option in the package manager?!?

All I see is an Automatic updates option that, at the very most, checks for updates daily and installs security updates without comfirmation.

---

### Post by jsday187 on 2009-05-20
like buddy said this is bogus. I defaults to the same number despite the VideoRam setting.

---

### Post by jsday187 on 2009-05-20
> **kagimaro said:**
> I agree with you dschouten,

I tried every solutions to get my Intel Graphics card to work, (rev07) .. but with no success, i gave ubuntu the chance manytimes to use it as primary OS on my laptop.

But here i am back to windows, and am using Windows7 RC, and its working fine without any problems.

If you want to get more people to jump on and start using ubuntu, you can't force them to deal with terminal and commands stuff, you should give them something that easy to use.

and plz people .. don't repeat the same thing that linux is more stable than widnows and the usual talk .. i've used OSX / Linux / Windows / OS2 / BeOS .. and each OS has its bad and good.

but still i can't compare any of the above to windows when it comes to something that just WORKS!

If you want something easy to use try a television 

Computers are here to stay, so people, instead of complaining about ease of use, should be buckling down and figuring out how to use them. 

Invest in a good removable harddrive, back-up your important files and you'll be fine. 

It'll only be so many times you screw things up and have to start from scratch before you start figuring things out.

It's quite obvious that Computers, like the humans that created and programmed, will ALWAYS be imperfect.

We should be bloody amazed they are as advanced and easy to use as they are.

Take a look at your car for instance. Does IT drive YOU to work? Can you effortlessly reinstall a fresh engine EVERY time your old one goes? NOPE!

You have to do it yourself OR pay someone else to do those things for you.

So unless you have the means to hire yourself a personal tech guy, who'll even print your emails off for you and put them on the table at breakfast, you should really decide its time start thinking of a Computer AS A COMPUTER and not as TV(Monitor) and remote control(keyboard). 

They are not EASY to use, they screw up ALL of the the time, and if you aren't willing to start learning them then YOU WILL BE LEFT BEHIND.

---

### Post by dentaku65 on 2009-05-20
> **kagimaro said:**
> I agree with you dschouten,

I tried every solutions to get my Intel Graphics card to work, (rev07) .. but with no success, i gave ubuntu the chance manytimes to use it as primary OS on my laptop.

But here i am back to windows, and am using Windows7 RC, and its working fine without any problems.

If you want to get more people to jump on and start using ubuntu, you can't force them to deal with terminal and commands stuff, you should give them something that easy to use.

and plz people .. don't repeat the same thing that linux is more stable than widnows and the usual talk .. i've used OSX / Linux / Windows / OS2 / BeOS .. and each OS has its bad and good.

but still i can't compare any of the above to windows when it comes to something that just WORKS!

Unfortunately is known that for Jaunty the Intel cards have problems, due to the change of driver functionality by Intel.
I suggest to stick with Hardy LTS or Intrepid in case of hard trouble with your card on Jaunty

---

### Post by Michelangelo on 2009-05-26
> **dentaku65 said:**
> 2) Add the gpg key of this PPA repo
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
```

I'm following the guide... but I'm getting this error:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

:(:(:(:confused::confused:

---

### Post by FirstByté on 2009-06-02
I guess **SOLVED** my **"Desktop Effects could not be enabled"** issue
:guitar:

Sorry, if this seems a bit off this thread. I've been searching endlessly for solution to this. Knowing fully well that my compiz effects worked flawlessly on Ubuntu 8.10 but seems broke when I upgraded to Ubuntu 9.04 Jaunty.:popcorn:

Like was specified here [[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363967]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363967")], I did removed my video card from the blacklist. Now all seems to be fixed.

Why in the world should it still be blacklisted. I had followed **[psyke83]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=GM965+GL960&page=1")**'s Soft configuration but though, the glitches were removed or probably solved on a prior update, I still wasn't able to get my Desktop Effects back.



My Device:
```
00:02.0 VGA compatible controller [0300]: **Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller **[8086:2a02] (rev 03)

```
```
Linux SP34CE 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```
Intel Core Duo 2 @ 2.2GHz
Dell Studio 14
Ubuntu 9.04 Jaunty Jackalope

$ grep -i UXA /var/log/Xorg.0.log
(--) intel(0): Using UXA for acceleration
(II) UXA(0): Driver registered support for the following operations:

---

### Post by ivan.baldinotti on 2009-06-02
:popcorn: Good howto! Now I am able to play videos, to see youtube smoothly. 3D performance not good but I am satisfied to have normal performance in 2D. I must test with external monitor. Thanks!

---

### Post by jaguar000 on 2009-08-23
Ok so I am still getting the "Desktop Effects could not be enabled" message.  I have everything set up as Dentaku posted but nothing.  
My card is: 

> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)My numbers are:

> Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel modules: intelfb
So my VideoRam should be 130560.  My xorg.conf file looks like this:

> Section "Device"
    Identifier    "Configured Video Device"
    Driver "intel"
    Option "AccelMethod" "UXA"
    VideoRam 130560
EndSectionThe only other issue that I can see based on everyone's replies is the compiz blacklist.  I added the # before the line with Intel

> # Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx" 

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
[COLOR=Red]#[/COLOR]T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset TBut when I restart and try to enable desktop effects, the screen goes to the background graphic with a cursor and the keyboard locks up.  I then have to hit the power button to restart.  I have noticed at least one other poster with my same graphics card who had success.    I also tried the more complicated fix posted by psyke83 but didn't have any luck.  Is my syntax in the code wrong or have I just missed something altogether?

---

