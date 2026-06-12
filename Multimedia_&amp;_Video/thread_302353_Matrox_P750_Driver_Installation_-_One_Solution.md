---
title: "Matrox P750 Driver Installation - One Solution"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by dmBriarwood on 2006-11-18
This was my experience installing the proprietary driver for my Matrox P750 video card for use with my new widescreen LCD.  I thought it might be useful to share with everyone – if anyone has comments, feedback, tips or hints, please don't hesitate to leave a comment or send me a note!
 
 Thanks,
 dm    
 
 **Post Outline:**[LIST=1]
[*]**What I was trying to do**
[*]**My System**
[*]**Useful Resources**
[*]**Procedure**
[*]**Aftermath**[/LIST][B]
What I was trying to do:[/B]
 
 I bought a wide-screen LCD monitor to replace the faithful CRT that has served me through several installations of RedHat and Ubuntu.  The X-org default driver has always worked without any tweeking.  The LCD worked out of the box with the X-org default – I was able to use my computer, but the entire screen was distorted.   Unfortunately the widescreen LCD requires a 1440x900 @ 60 Hz resolution – a setting not supported by the default driver.  My goal was to install the proprietary driver for a Matrox P-series video card so I could operate my new monitor at the recommended resolution and refresh rate.
 

 **My System:**
 
 _AMD Athlon XP 3200 Barton 400 FSB_ with _1 Gb of memory_, a _Matrox P750 DDR 64 Mb Dual_ video card, a _Creative Labs Soundblaster Live! DE 5.1_ sound card all on a  _ASUS A7V600_ motherboard.
 
 When I query Ubuntu for the system's hardware, it is slightly different (I don't know if these differences could be a source of trouble or just the nomenclature for a “family” of drivers):
 
 _AMD Athlon XP 2500+_  with _1 Gb of memory_, a _Matrox Graphics, Inc. Millenium P650/P750 (rev 02)_ video card, a _Creative Labs SB Live! EMU10k1 (rev 0a)_ sound card all on a _VIA KT 400/KT600 AGP_ motherboard.
 

 **Useful Resources:**
 
 The Video Card Support Ubuntu Community Wiki: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)
 
 Ubuntu Community Wiki: Matrox Parhelia Binary Driver How To: [https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia)
 
 Matrox driver installation instructions (pp 199-200) found in:
 
 Oxer J, Rankin K, Childers B. _Ubuntu Hacks – Tips & Tools for Exploring, Using and Tuning Linux_. O'Reilly Media Inc: USA. 2006.  ISBN 0-596-52720-9
 
 The official Matrox Drivers/Utilities website: [http://www.matrox.com/graphics/en/corpo/support/drivers/home.php](http://www.matrox.com/graphics/en/corpo/support/drivers/home.php)
 
 The official General Linux Matrox Technical Support Forum: [http://forum.matrox.com/mga/viewforum.php?f=64&sid=8a32257a6b8cdfc5cc5ce85816e254be](http://forum.matrox.com/mga/viewforum.php?f=64&sid=8a32257a6b8cdfc5cc5ce85816e254be)
 
 Alexander Griesser's unofficial Matrox driver version release: [http://www.tuxx-home.at/](http://www.tuxx-home.at/)
 
 The X-org Foundation Supported Video Card Wiki: [http://wiki.x.org/wiki/VideoDrivers](http://wiki.x.org/wiki/VideoDrivers)
 
 *X-org Configuration* from Free Me! blog: [http://www.freeme.in/node/15](http://www.freeme.in/node/15)
 

 **Procedure:**
 
 There seems to be no cookie cutter method to get the Matrox P proprietary driver working in 6.06.  Ubuntu 6.10 has a raft full of compatibility problems, and I decided NOT to upgrade from 6.06.  I don't know if any of the packages on my system from step 2 played a role in getting the driver to work – so that's why I've included them.  This is what I did to start:

**One**: Thanks to an ill-advised, poorly recorded, anger driven, multi-method approach to installing the Matrox driver I broke my 6.06 installation and was forced to start from a fresh 6.06 installation.:oops:

**Two:** Experimenting individually with the different approaches outlined in the resources listed in the previous section, I installed the following packages (1 and 2 using command line, 3 through 11 using Synaptic) on my system without successfully installing neither the official nor unofficial matrox driver:[LIST=1]
[*]**gcc-3.4 **
[*]**gcc-3.4-base**
[*]**binutils-doc (version         2.16.1cvs20060117-1ubuntu2.1)**
[*]**g++-3.4 (version         3.4.6-1ubuntu2)**
[*]**gcc-3.4-doc (version         3.4.6-1ubuntu2)**
[*]**lib64gcc1 (version         1:4.0.3-1ubuntu5) **
[*]**libc6-amd64 (version         2.3.6-0ubuntu20) **
[*]**libc6-dev (version         2.3.6-0ubuntu20) **
[*]**libc6-dev-amd64 (version         2.3.6-0ubuntu20)**
[*]**libstdc++6-dev (version         3.4.6-1ubuntu2) **
[*]**linux-kernel-headers         (version 2.6.11.2-0ubuntu1)**[/LIST]**Three: **I received     some advice from a few friends that ultimately provided some success     with the driver installation.  Using Synaptic, I installed:[LIST=1]
[*]**linux-k7     2.6.15.25 (Complete Linux kernel on AMD K7)**
[*]**linux-headers-k7     2.6.15.25 (Linux kernel headers on AMD K7)**
[*]**build-essential     11.1 (informational list of build-essential packages)**[/LIST]**Four: **I     made sure I had the most recent driver file for my Matrox P series     video card.  (available at:  [http://www.tuxx-home.at/](http://www.tuxx-home.at/)**)     (Note: I believe the Matrox G-series drivers are “mga” and the     P-series are “mtx”)**

**Five: **I     changed the permissions of the driver file **$ chmod 777     matroxdriver_mtx-x86_32-1.4.4.3-installer.run **     (I'm not sure if this was necessary or not, but I didn't want to     take any chances!)

**Six: **I ran the     driver installer from the command line: **$ sudo sh     matroxdriver_mtx-x86_32-1.4.4.3-installer.run** – instructing it     to install in **/usr/lib/**

**Seven: **With the     driver installed, I then modified the X-org configuration file.      Using the command line I entered:  **$ sudo gedit**     **etc/X11/xorg**.**conf –** which opened gedit in super-user     mode, allowing me to make changes to the xorg.conf file[INDENT]**Change         1:** I inserted “mtx” in the Device Section:[/INDENT][INDENT][INDENT][FONT=Verdana, sans-serif]Section "Device"[/FONT][INDENT][FONT=Verdana, sans-serif]    Identifier    "Generic Video Card"[/FONT]
[FONT=Verdana, sans-serif]    Driver        "**mtx**"[/FONT]
[FONT=Verdana, sans-serif]    BusID        "PCI:1:0:0"[/FONT]
[/INDENT][FONT=Verdana, sans-serif]EndSection[/FONT][/INDENT][/INDENT][INDENT]**Change 2: **I         inserted my monitor model number (HW192D) in the Monitor Section         and the Screen Section (this was probably not necessary for a         single screen system like mine)[/INDENT][INDENT][INDENT][FONT=Verdana, sans-serif]Section "Monitor"[/FONT][INDENT][FONT=Verdana, sans-serif]    Identifier    "**HW192D**"[/FONT]
[FONT=Verdana, sans-serif]    Option    "DPMS"[/FONT]
[/INDENT][FONT=Verdana, sans-serif]EndSection[/FONT]
[FONT=Verdana, sans-serif]
Section "Screen"[/FONT][INDENT][FONT=Verdana, sans-serif]    Identifier    "Default Screen"[/FONT]
[FONT=Verdana, sans-serif]    Device        "Generic Video Card"[/FONT]
[FONT=Verdana, sans-serif]    Monitor        "**HW192D**"[/FONT]
[FONT=Verdana, sans-serif]    DefaultDepth    24[/FONT][/INDENT][/INDENT][/INDENT][INDENT]**Change 3:**         The 1440x900 resolution my monitor required was not listed in the         Display Subsection. So, in the Modes line for each Depth level (1,         4, 8, 15, 16, 24) I entered “1440x900” - as an example, here is          Section “Screen” Subsection “Display” Depth 8 (remember to         do this for all the depth levels):[/INDENT][INDENT][INDENT][FONT=Verdana, sans-serif]SubSection "Display"[/FONT][INDENT][FONT=Verdana, sans-serif]    Depth        8[/FONT]
[FONT=Verdana, sans-serif]    Modes        **"1440x900"** "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"[/FONT]
[/INDENT][FONT=Verdana, sans-serif]EndSubSection[/FONT][/INDENT][/INDENT][INDENT]**Lastly: **In         the ServerLayout Section, ensure the name given to the Screen line         item is the same as the identifier in the Screen Section:[/INDENT][INDENT][INDENT][FONT=Verdana, sans-serif]Section "Screen"[/FONT][INDENT][FONT=Verdana, sans-serif]    Identifier    "Default Screen"[/FONT]
[FONT=Verdana, sans-serif]    Device        "Generic Video Card"[/FONT]
[FONT=Verdana, sans-serif]    Monitor        "**HW192D**"[/FONT]
[FONT=Verdana, sans-serif]DefaultDepth    24[/FONT]
[/INDENT][FONT=Verdana, sans-serif]Section         "ServerLayout"[/FONT]
[FONT=Verdana, sans-serif]<...>[/FONT][/INDENT][/INDENT][INDENT][INDENT][FONT=Verdana, sans-serif]Identifier    "Default Layout"[/FONT][INDENT][FONT=Verdana, sans-serif]**Screen        "Default Screen"**[/FONT]
[FONT=Verdana, sans-serif]    InputDevice    "Generic Keyboard"[/FONT]
[FONT=Verdana, sans-serif]    InputDevice    "Configured Mouse"[/FONT]
[FONT=Verdana, sans-serif]    InputDevice     "stylus" "SendCoreEvents"[/FONT]
[FONT=Verdana, sans-serif]    InputDevice     "cursor" "SendCoreEvents"[/FONT]
[FONT=Verdana, sans-serif]    InputDevice     "eraser" "SendCoreEvents"[/FONT]
[/INDENT][FONT=Verdana, sans-serif]EndSection[/FONT][/INDENT][/INDENT]**Eight: **Save and     close xorg.conf

**Nine: **Restart     system (upon restart, you should see the blue Matrox Parhalia splash     screen)

**Ten: **Then from the     Ubuntu 6.06 desktop select <System> <Preferences>     <Screen Resolution>.

**Eleven: **Finally, if it is     not already so, using the drop down menu set <Resolution> to     1440x900 and <Refresh Rate> to 60 Hz
[B]

Aftermath:[/B]

After following the outlined procedure, I was able to set my widescreen monitor to the recommended resolution of 144x900 @ 60 Hz.   
 Unfortunately I've had some trouble with my system, but I'm not certain what the root cause is.  The two show-stoppers are kernel panics during boot-up, and a system freeze shortly after starting Evolution.  Both crashes seem to lock the keyboard and mouse forcing me to manually reset the desktop by turning off the power for several minutes.  I wonder if the kernel panics have something to do with the K7 kernel?  The Evolution problem could be due to my repeated and failed attempts to sync with my Palm Pilot using gpilot.  But, I'm not sure.

---

### Post by dmBriarwood on 2006-11-19
Just an update - looks like all the above was for naught - my system is fried - nothing but kernel panics when I boot from my hard-drive.  Downloaded a fresh Knoppix V - worked fine.  Downloaded both the live CD version of 6.10, and the alternate install - both CDs were corrupted when I tried to verify them.  Seemed to be the nvidia driver package (according to image burn).  Tried booting with both CDs anyway - if you guessed kernel panics, you'd be right.  I'm really at a loss here - any ideas?

---

### Post by dmBriarwood on 2006-11-20
Man, I feel like I'm talking to myself here.  Oh, wait.  I am.  

In case anyone is following - My computer worked tonight - after one full day of kernel panics!  Can you believe it?  I was turning it on to re-install dapper, and it booted right up.  Quite a mystery.  Quite a mystery indeed.

---

