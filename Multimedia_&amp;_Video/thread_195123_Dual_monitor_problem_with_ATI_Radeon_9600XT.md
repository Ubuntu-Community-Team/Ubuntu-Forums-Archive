---
title: "Dual monitor problem with ATI Radeon 9600XT"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by genghis on 2006-06-12
Hello,

This post may become rather lengthy but I'm trying to include the most information possible.

The other day I installed Ubuntu 6.06 and just bought two Samsung SyncMaster 740N LCDs.  I have been trying furiously to figure out how to get these to work with my ATI 9600XT video card so that I can have an extended desktop across both LCD's.  I have yet to have any success, and as of now, both screens display the same thing.

My most recent attempt was following the steps outlined in this thread:
[http://www.ubuntuforums.org/showthread.php?t=191944](http://www.ubuntuforums.org/showthread.php?t=191944)

After restarting the xserver I do fglrxinfo and get the following output:
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Then I do glxinfo and get the following output:
~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3

So then I go to the ATI Control Panel and select big desktop horizontal
as shown in the attached image.

Next, I restart xserver and nothing is different, and if I go back into the
ATI Control Panel it does not seem like the setting were even saved.

I have also attached my xorg.conf file which probably needs to be edited in some way and is the cause of my problem I think.  Any help you guys can provide would be greatly appreciated.

---

### Post by RudolfMDLT on 2006-06-12
Hi,

I was about to ask you how you got the 9600 card to work but then I saw that you didn't. I run a ATI 9600 Pro. You are running Mesa not the ATI drivers. Run this command for about 15 secs and you should get a FPS of around 250 

glxgears -printfps

Sorry for not being able to help, but you first need to get your card's drivers to work proparly before (i think) you can start using it's special fucntions. And I have tried what I think is every how to and driver on the web. Please link the post you used in your Print Screen picture, maybe I could find some use out of it and hopefully pass it on to you and every one else! 

Cheers,

Annoyed ATI user.

PS: here is my thread:
[http://www.ubuntuforums.org/showthread.php?t=194882](http://www.ubuntuforums.org/showthread.php?t=194882)
and a guide
[https://wiki.ubuntu.com/BinaryDriver...29%7C%28ATI%29](https://wiki.ubuntu.com/BinaryDriver...29%7C%28ATI%29)
and a driver page
[https://support.ati.com/ics/support/...ge&folderID=27](https://support.ati.com/ics/support/...ge&folderID=27)
and some other ATI post's
[http://ubuntuforums.org/showthread.php?t=189000&highlight=ATI](http://ubuntuforums.org/showthread.php?t=189000&highlight=ATI)
[http://ubuntuforums.org/showthread.php?t=186824&highlight=ATI](http://ubuntuforums.org/showthread.php?t=186824&highlight=ATI)
do a search for ATI on this forum and you'll probally find about 50 users struggeling with these damn cards!

---

### Post by RudolfMDLT on 2006-06-12
Sorry for being so negative in my previous post! It's just that I've been struggling now for 4 days, day and night with this card! 

You are currently using Mesa to drive your 3D acceleration which will give you very little 3D functionality at all. If you ever used Microsoft Windows, Mesa is the equivalent of the MS soft driver used by windows when your current card is dis functional. It looks pretty, and allows you to do most things, but no advanced stuff. I can offer you no advice as everything that I tried failed. There are some good How To's on the forum. Just keep searching.

The main problem sofar that I could find is that Xorg 7 is what dapper uses and apparently this has a bug in it preventing certain ATI card from working, but I've only read that in one post, can't remember where, so it may be fud.

---

### Post by genghis on 2006-06-12
Hey RudolfMDLT,

I appreciate the quick response.  I too have been struggling with this for couple of days with little success and am beginning to get very frustrated.  I've read through your other post and through the wiki, and it seems like we have a similar problem.  I too am a student who is fairly competent in Windows.  I am not new to linux either but I have had little experience in the past with dealing with these graphics card drivers.  Usually, on my past linux installation experiences, the video card configuration is easy and it's usb things that cause me problems, but such is not the case with this new computer I got.

Anyway, I was just curious as to what state you have been able to get your ATI 9600 to work in.  I'm not quite ready to give up on this, and I think if you and I can put our heads together we can figure this out.

Thanks again for your time!

---

### Post by RudolfMDLT on 2006-06-12
Hi! 

I like your attitude! :) AND I'm glad you aren't new to linux!

genghis, You're going to have to give me a day or to, I rendered my X Windows system unusable by stuffing around with it. I uninstalled all fglrx drivers through Synaptic knowing it was probably going to cause trouble. Restarted and got the Xorg warning that it could not start. I counted on this and in TTY I installed the ATI propriety drivers. What I did not count on in my haste, is these drivers not being able to install!!!!! I've tried reinstalling all the packages I removed through apt-get. I think I'm missing one and then I'll get my system to work! In the installation log file it says something in the line of Kernel mismatch, no Kernel found, please consult read me. There is no read me. I'll check back on the ATI site and see what it says on Kernel mismatch but right now I'm writing exams.

If all else fails I'm, going to do a clean Install tomorrow(it's 23:00 this side of the world) and start form scratch with a clean system! Good luck and hopefully we can get something cooking! :)

EDIT: Just had to ask something, what variant card are you Running? I'm using an All-in-wonder make of the Radeon chipset. Is there even the remotest chance that this could make a difference?

---

### Post by genghis on 2006-06-12
Hey,

Good to hear you're still on board.  Yeah, I noticed that your posts say that you're in South Africa.  I'm over here in Virginia in the United States.  I had a friend from Botswana here at school but he returned to Africa after graduating.

Anyway, here is a link to the exact card that I bought.

[http://www.newegg.com/Product/Product.asp?Item=N82E16814102600](http://www.newegg.com/Product/Product.asp?Item=N82E16814102600)

I don't know if the all-in-wonder card difference is going to make a difference in the end, but since we both have a somewhat higher end ati card we should be able to at least install and actually use the same drivers.

Here is a list of a few threads regarding the xorg.conf files that I found interesting.
(although you have probably already read all these)  I'm just trying to make a more centralized collection of threads related to this problem.

[http://ubuntuforums.org/showthread.php?t=134624&highlight=dual+monitors+ati](http://ubuntuforums.org/showthread.php?t=134624&highlight=dual+monitors+ati)
[http://ubuntuforums.org/showthread.php?t=187011&highlight=dual+monitors+ati](http://ubuntuforums.org/showthread.php?t=187011&highlight=dual+monitors+ati)
[http://ubuntuforums.org/showthread.php?t=188189&highlight=dual+monitors+ati](http://ubuntuforums.org/showthread.php?t=188189&highlight=dual+monitors+ati)

This one is for kubuntu but the seems to be having a similar problem as I do with the mesa thing showing up.
[http://ubuntuforums.org/showthread.php?t=189874&highlight=dual+monitors+ati](http://ubuntuforums.org/showthread.php?t=189874&highlight=dual+monitors+ati)

Anyway, look over these when you get a chance and feel free to add any interesting threads that may prove useful.

Thanks!

---

### Post by genghis on 2006-06-12
Hey RudolfMDLT,

I think I may have gotten somewhere, but I'm not completely sure.  I was reading this thread:

[http://www.ubuntuforums.org/showthread.php?t=191651](http://www.ubuntuforums.org/showthread.php?t=191651)

jinx099 suggested trying:
```
sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev
```

So out of desperation I did.  Then I looked at my xorg.conf and noticed that the driver showed up as "fglrx" instead of "ati" or "vesa".  Here's my xorg.conf file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

Okay, so here's where it gets interesting.  So after rebooting, I run fglrxinfo get this output:
```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

Then I run glxinfo and get this output:
```
~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3

```

Notice how it says:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic

instead of

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect

like in my original post.  So I ran glxgears -printfps and got this output:
```
~$ glxgears -printfps
17085 frames in 5.0 seconds = 3416.822 FPS
16973 frames in 5.0 seconds = 3394.565 FPS
16973 frames in 5.0 seconds = 3394.406 FPS
16967 frames in 5.0 seconds = 3393.229 FPS
```

Which is a hell of a lot more that the 250 FPS you mentioned earlier with the mesa drivers.  The extended desktop still does not work but I feel a little closer at least.  Anyway, I just wanted to update you on what I've been working on, and good luck with your fresh install.

---

### Post by RudolfMDLT on 2006-06-13
genghis! Well Done! \\:D/

I will cerntainly give your advice a shot! 

O! and I had a look at your card, It looks just like mine! Theres hope!

Thank you very much!

In the meen time I'll try and see if I can get my card working and try to get some info on your duel display.

---

### Post by RudolfMDLT on 2006-06-13
Hi!

Got my card running! Not quite as fast as yours but good - 1800 fps! I'll do some fine tuning later!

Used a different approach though.

Had a look at the ATI control panel - You can spread or clone your desktop but I see no option for running dual head. In windows I remember using my Nvidia card, and this gave me an option to run a desktop manager - like the one in linux on the bottom right of the screen - and I could put desktop 1 on a monitor and desktop 2 on the second monitor. This ATI Control panel only allows spreading. If you go to the terminal, type aticonfig and a HUGE list of commands pop up. I still can't find any command that will make your system run two independent desktops.

But I'll keep looking!

Cheers!

---

### Post by genghis on 2006-06-13
Hey RudolfMDLT,

It's good to hear that you got your card to work.  Can you post how you were able to get it to work?  Anyway, I actually do not want to run two separate desktops on separate monitors.  I want to spread it horizontally so that I have one big desktop across both monitors.  However, when I the ATI Control panel to enable "Big Desktop Horizontal" and then reboot or restart xserver, nothing appears to happen.  It still just displays the same thing on both screens.

---

### Post by RudolfMDLT on 2006-06-13
[QUOTE=genghis]Hey RudolfMDLT,

It's good to hear that you got your card to work.  Can you post how you were able to get it to work?  Anyway, I actually do not want to run two separate desktops on separate monitors.  I want to spread it horizontally so that I have one big desktop across both monitors.  However, when I the ATI Control panel to enable "Big Desktop Horizontal" and then reboot or restart xserver, nothing appears to happen.  It still just displays the same thing on both screens.[/QUOTE]

Try this, in Gnome, in the terminal, find the text command that will do the same thing as the ATI control panel. type aticonfig into the terminal, do not configure anything in Gnome, just type aticinfig to get a HUGE list of possible commands. I think the command is: 
aticonfig --dtop=horizontal --overlay-on=1   =>copied directly from the sugested command

Then backup your Xorg config file and fglrx config file.

restart your machine, at the boot menu, choose recovery mode. This will put you into a text interface only, Xorg won't start. Configure the ATI card from here. when your finished, restart the machine - "shutdown -r 0 now", and this time boot normally. Hopefully this will work!

This is how got my card to work, not dual display, just to function, when X windows is not loaded you are free to do as you please with the graphics! I'll post my method later, I just need to make sure that my system is stable first.

EDIT: this is how i got my card to work:
[http://www.ubuntuforums.org/showthread.php?p=1133444#post1133444](http://www.ubuntuforums.org/showthread.php?p=1133444#post1133444)

---

