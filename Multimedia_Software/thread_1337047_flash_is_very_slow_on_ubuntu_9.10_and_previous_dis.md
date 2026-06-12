---
title: "flash is very slow on ubuntu 9.10 and previous dists"
date: 2009-11-25
forum: Multimedia Software
---

### Post by balki2005 on 2009-11-25
Hello,

It's  very frustating  that  I need  to  install windows on my pc  to  see  flash movies  from  youtube or other sites. because on ubuntu it's very slow. 
I tried  several solutions  but none  works. 

is it ubuntu (linux) that have problems with playing flash movies and when will come a solution for it ?

do  somebody  found  a  solution somewhere ???

thanks  in advance,

Balki2005

---

### Post by ajgreeny on 2009-11-25
This is not a Ubuntu problem, but an Adobe Flash problem, I'm afraid.  Linux seems to be a second thought to Adobe and flash is as good now as it has ever been on linux, and getting better, but it still has a way to go.

There is a beta version of flash 10.1, available from Adobe which may help, but is unlikely to make any real difference, in my trial experience of it.  It is slightly better in some ways, with slightly lower cpu usage, but it has problems on my machine with colour rendering on many videos, with many youtube movies just showing green and pink flashing colours and totally un-watchable.

---

### Post by jwbrase on 2009-11-25
> **balki2005 said:**
> Hello,

It's  very frustating  that  I need  to  install windows on my pc  to  see  flash movies  from  youtube or other sites. because on ubuntu it's very slow. 
I tried  several solutions  but none  works. 

is it ubuntu (linux) that have problems with playing flash movies and when will come a solution for it ?

do  somebody  found  a  solution somewhere ???

thanks  in advance,

Balki2005


I've found that flash is a coin-toss on Ubuntu, largely for the reasons listed by ajgreeny.

On this machine, with Ubuntu pre-installed by System76, Flash works perfectly. On our desktop at home, with Ubuntu installed by me, I could never get Flash to work in Firefox while I was on 8.10, but it worked fine in Opera.

---

### Post by varangian on 2009-11-25
> **balki2005 said:**
> 

is it ubuntu (linux) that have problems with playing flash movies and when will come a solution for it ?

do  somebody  found  a  solution somewhere ???


Don't give up, at least not yet. Like you I found Flash was pretty bad on previous versions - I stuck with Gutsy until installing Karmic and it was pretty poor, jerky and prone to crash.

With Karmic 64 bit I initially got Flash via the restricted-extras package. This worked OK for YouTube but I ran into problems with the BBC iPlayer. So I got the Flash 10.0 direct from the Macromedia site and set it up manually and I'm now pretty happy. It's as fast as it needs to be and hasn't crashed. So you might like to explore that option if you haven't tried it already - search the threads here and you'll find various sets of instructions as to how to go about it.

That said there's no guarantee, there seem to be various factors at work here involving other video and audio components and you might be unlucky.

---

### Post by viljander on 2009-12-23
Hi!

I found a solution and my 9.10 flash is fast again.

I have Ubuntu 9.10 on HP NC6000 laptop with ATI Mobility Radeon 9600 chip.

Problem:
In previous Ubuntus ATI Radeon special commands are given in /etc/X11/xorg.conf but in 9.10 Ubuntu this file is not used by default anymore. Thus special ATI commands are not given and flash is *slug* slow (youtube etc.). This solution might help you if you have laptop with ATI Mobility Radeon and Ubuntu 9.10.

What I did:
Ubuntu 9.10 can use xorg.conf settings but it needs to be configured first
1) open terminal
2) shut down Gnome (sudo services gdm stop)
3) make xorg.conf (sudo xorg -configure)
4) start Gnome (sudo services gdm start)

Now you have xorg.conf in the /etc/X11/ folder.

5) Add following options to xorg.conf (sudo gedit xorg.conf)
         Option "AGPMode" "1"
	 Option "AccelMethod" "EXA"
	 Option "MigrationHeuristic" "greedy"
	 Option "AccelDFS" "true"
	 Option "EnablePageFlip" "true"
	 Option "EnableDepthMoves" "true"
6) Save
7) shut down Gnome (sudo services gdm stop)
8) start Gnome (sudo services gdm start)

Now you should have ATI with faster flash settings enabled.

Ville

---

### Post by blur xc on 2009-12-23
One thing you can try is to right click any flash contect, select setttings, and disable hardware acceleration.  

From my perspective, and from my understanding of reading many threads on this exact subject, flash performance has as much to do w/ your hardware as it does with the flash plugin.  Graphics performance in a linux is gererally poorer than in Windows, and the issue comes down to drivers.  We all (well, almost all) use the same flash plugin, yet we all have varying levels of flash performance.  On my dekstop, Flash is wicked fast and smooth.  I play online flash games and watch any full screen hd video for any site w/o any hiccups.  The only varible left is your cpu, gpu, and gpu drivers...

BM

---

### Post by damphoud on 2010-02-02
> **blur xc said:**
> One thing you can try is to right click any flash contect, select setttings, and disable hardware acceleration.  

From my perspective, and from my understanding of reading many threads on this exact subject, flash performance has as much to do w/ your hardware as it does with the flash plugin.  Graphics performance in a linux is gererally poorer than in Windows, and the issue comes down to drivers.  We all (well, almost all) use the same flash plugin, yet we all have varying levels of flash performance.  On my dekstop, Flash is wicked fast and smooth.  I play online flash games and watch any full screen hd video for any site w/o any hiccups.  The only varible left is your cpu, gpu, and gpu drivers...

BM


Disabling hardware acceleration worked just fine for me. 

Thanks! :popcorn:

---

### Post by JosephGarrison on 2010-02-02
Flash seems to work fine for me. I'm using Ubuntu 9.10 on an Acer Aspire 4720z. I hated the computer when it ran windows, and I like it loads more now. I never had a problem with flash while running windows or Ubuntu.

---

### Post by RainmanATX on 2010-02-03
Howdy all!  I just stumbled upon a fix for the Flash 10 video performance issues, well, the fix worked for me.  Running 8.04 LTS for a little over a year now, flash video has been 'the suck' the whole time.  Was messing around with it this afternoon, when I stumbled upon an easy fix.  Using Synaptic, I uninstalled the adobe-flashplugin ver. 10.0.42.34-2.  I then went to Adobe's site and grabbed their .deb, which was ver. 10.0.42.34-1.  Upon attempting to install it, got message that there was a newer version in a software channel.  Now, before closing it out, I looked to see if there were any 'companion packages' for the .deb.  There was, something called libnspr4-dev.  Stange, there was not a companion package for the 34-2 version via synaptic?  So, I decided to close out the .deb file, open synaptic, load up the adobe-flashplugin ver. 10.0.42.34-2 in addition to the libnspr4-dev package, restarted my browser, and bam!  Flash video rockin like on Winders, and now when paused, the frickin cpu usage drops to ZERO!  I then read the description for libnspr4-dev;

This library provides platform independent non-GUI operating system
facilities including:
 * threads,
 * thread synchronisation,
 * normal file I/O and network I/O,
 * interval timing and calendar time,
 * basic memory management (malloc and free),
 * shared library linking.

Sounds like that did it.  Not sure who to contact in order to make the synaptic 10.0.42.34-2 link/buddy/companion with the libnspr4-dev package though.  Anyways, try it out, and feedback me aye.

****Update - I think I spoke too soon, it only 'fixes' flash video playback issues, and drops the process to zero when paused, ONLY for the first tab you go to with your browser, when multiple tabs are opened, old behavior returns.  Guess its a start though.  (shrug) ****

---

### Post by chaumurky on 2010-02-04
> **RainmanATX said:**
> Howdy all!  I just stumbled upon a fix for the Flash 10 video performance issues, well, the fix worked for me.  Running 8.04 LTS for a little over a year now, flash video has been 'the suck' the whole time.  Was messing around with it this afternoon, when I stumbled upon an easy fix.  Using Synaptic, I uninstalled the adobe-flashplugin ver. 10.0.42.34-2.  I then went to Adobe's site and grabbed their .deb, which was ver. 10.0.42.34-1.  Upon attempting to install it, got message that there was a newer version in a software channel.  Now, before closing it out, I looked to see if there were any 'companion packages' for the .deb.  There was, something called libnspr4-dev.  Stange, there was not a companion package for the 34-2 version via synaptic?  So, I decided to close out the .deb file, open synaptic, load up the adobe-flashplugin ver. 10.0.42.34-2 in addition to the libnspr4-dev package, restarted my browser, and bam!  Flash video rockin like on Winders, and now when paused, the frickin cpu usage drops to ZERO!  I then read the description for libnspr4-dev;

This library provides platform independent non-GUI operating system
facilities including:
 * threads,
 * thread synchronisation,
 * normal file I/O and network I/O,
 * interval timing and calendar time,
 * basic memory management (malloc and free),
 * shared library linking.

Sounds like that did it.  Not sure who to contact in order to make the synaptic 10.0.42.34-2 link/buddy/companion with the libnspr4-dev package though.  Anyways, try it out, and feedback me aye.

****Update - I think I spoke too soon, it only 'fixes' flash video playback issues, and drops the process to zero when paused, ONLY for the first tab you go to with your browser, when multiple tabs are opened, old behavior returns.  Guess its a start though.  (shrug) ****

Wow, what a difference! So this is really a dependency bug?[SIZE=2][SIZE=1]
[/SIZE][/SIZE]

---

### Post by WhErEeVeR on 2010-02-04
> **viljander said:**
> Hi!

I found a solution and my 9.10 flash is fast again.

I have Ubuntu 9.10 on HP NC6000 laptop with ATI Mobility Radeon 9600 chip.

Problem:
In previous Ubuntus ATI Radeon special commands are given in /etc/X11/xorg.conf but in 9.10 Ubuntu this file is not used by default anymore. Thus special ATI commands are not given and flash is *slug* slow (youtube etc.). This solution might help you if you have laptop with ATI Mobility Radeon and Ubuntu 9.10.

What I did:
Ubuntu 9.10 can use xorg.conf settings but it needs to be configured first
1) open terminal
2) shut down Gnome (sudo services gdm stop)
3) make xorg.conf (sudo xorg -configure)
4) start Gnome (sudo services gdm start)

Now you have xorg.conf in the /etc/X11/ folder.

5) Add following options to xorg.conf (sudo gedit xorg.conf)
         Option "AGPMode" "1"
	 Option "AccelMethod" "EXA"
	 Option "MigrationHeuristic" "greedy"
	 Option "AccelDFS" "true"
	 Option "EnablePageFlip" "true"
	 Option "EnableDepthMoves" "true"
6) Save
7) shut down Gnome (sudo services gdm stop)
8) start Gnome (sudo services gdm start)

Now you should have ATI with faster flash settings enabled.

Ville

Thank you Viljander! That worked beautifully. I too have an ATI Radeon 9600 but its a desktop PC. I just wanted to correct a few errors I found in your instructions. At least for me they were errors.


(Note: when you run the command below, in step 2, Gnome will shut down, as in you won't be able to read these instructions as you go through them. Write them down. At least steps 2 through 4. After completing those steps, you can follow the rest of the steps online)

1) open terminal
2) shut down Gnome by typing 'sudo service gdm stop'
3) create an xorg.conf.new by typing 'sudo Xorg -configure' (this creates the xorg.conf.new file in the root of the user folder ~/ Note: X in Xorg is capitalized)
4) restart Gnome by typing 'sudo service gdm start'
5) add the below options to the newly created xorg.conf.new file located in ~/ I used alt-F2 then typed 'gksu gedit xorg.conf.new' to edit the file which only has root permissions. The below options are added under the Section "Device"

Option "AGPMode" "1"
Option "AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"
Option "AccelDFS" "true"
Option "EnablePageFlip" "true"
Option "EnableDepthMoves" "true"

For example, in my file, under Section "Device" it was like as below:

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV350 AP [Radeon 9600]"
	BusID       "PCI:3:0:0"
	Option      "AGPMode" "1"
	Option      "AccelMethod" "EXA"
	Option      "MigrationHeuristic" "greedy"
	Option      "AccelDFS" "true"
	Option      "EnablePageFlip" "true"
	Option      "EnableDepthMoves" "true"
EndSection

6) Save the file named as xorg.conf to the folder /etc/X11/ where it is used once you restart Gnome one more time.
7) shut down Gnome 'sudo service gdm stop'
8) restart Gnome 'sudo service gdm start' 

Test it out!

---

### Post by sikrip on 2010-02-14
Thanks for the solution, it saved my old good compag nx7000 laptop/w ati mobility radeon.

Not only the flash is now smooth and fast, it also improved the overall speed of the laptop (less cpu for gui stuff?).

Thanks again!

---

### Post by AgentWiggles on 2010-02-16
The workaround with Xorg worked very well for me. Flash isn't perfect, but it's incredibly and noticeably better than before.

---

### Post by DCMR2 on 2010-04-26
Worked great for me too, thanks! I have a Dell 4500 and an ATI Radeon 9550.

---

### Post by raviolli on 2010-06-24
Hi there,

I'm trying to get this working for myself and have already tried installing that package with no avail.

My problems arise when I type the "sudo service gdm stop" my screen goes black and it turns off, as if no signal is being delivered to it from the video card.

I'm not sure what gdm stop is supposed to do, other then shut down gnome, which I thought would bring me into some sort of command line. 

I should note I'm using Ubuntu 10.04 (lucid)

Thanks for the help

---

### Post by drazaelb on 2010-07-07
> **raviolli said:**
> 
My problems arise when I type the "sudo service gdm stop" my screen goes black and it turns off, as if no signal is being delivered to it from the video card.


Try Alt-F1 to get the first console.  Worked for me.

I swear, Flash is going to drive me bonkers. We all know Flash sucks on Linux, but I have two machines running Lucid.  The slower one (my home file server) works acceptably well with Flash, but the slightly faster one (my notebook) just chokes on anything Flash.  By "chokes" I mean I can count individual video frames on my fingers.  The slower machine isn't great, but it can at least play video that looks like video and not a slide show.

I've tried every suggestion in this thread and everything else I've been able to find, and nothing seems to help. This notebook is 7+ years old, maybe I'm just going to have to dig up the cash to replace it.  Seems a shame, though, as it does everything else I need fairly well.

I wonder if the audio processing can kill Flash performance.  That's the biggest difference I can think of, as my file server doesn't have any audio hardware in it.  (I can see the video, but without audio it isn't very interesting... I actually didn't even want a Flash player on that machine but installed it just to see how it compared.)

I can certainly post more details if anyone is curious and feels like helping me dig in to this mystery.

---

### Post by texla on 2010-07-08
> **blur xc said:**
> One thing you can try is to right click any flash contect, select setttings, and disable hardware acceleration.  

From my perspective, and from my understanding of reading many threads on this exact subject, flash performance has as much to do w/ your hardware as it does with the flash plugin.

BM

Trying this fix - hope it works...

---

### Post by petrus250 on 2010-07-18
I have found that, even with the same machine (asus eee pc), flash is very variable and that youtube is often solved by closing everything but chrome or firefox and allowing it to buffer.

---

### Post by lostinberlin on 2010-09-13
Hi,

might not be what you're looking for but here's my 'long sought after and highly satisfying' solution - depending on your priorities.

Turn off "desktop effects". It's as simple as that. If you can't live without them, you could find a shortcut to turn them on or off at will, but I am quite happy without them and the video play back is fantastic.

There you have it. Hope someone finds this useful.

Stats:
Kubuntu 10.04
Thinkpad W510 (1920 x 1080)

---

