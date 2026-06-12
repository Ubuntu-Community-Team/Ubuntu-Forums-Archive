---
title: "Ogg files do not play"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by lunamystry on 2007-09-18
I can't play any videos that are in .ogg format. Of all the players that I have (kaffeine, mplayer. totem, gxine, vlc) I only get a blue screen when i try to play the files. I thought the codecs for .ogg were there by default or is it only in ubuntu not Kubuntu?

---

### Post by vinutux on 2007-09-19
ogg vorbis (.ogg audio) and ogg theora (.ogm video) are opensource file format . it including almost all modern linux distrubustion including ubuntu..................

it is the only good codec come with ubuntu default....

1. it is possible problem to configure gstreamer pluging or somrthing else.....

uninstall all gstreamer plugins and its configuration and reinstalling with "synaptic" is a good solution.

...........................................

2. still the problem persist........... or problem in all other media players such as mplayer or xine ......... it is must be problem of u r graphic card or graphic driver..................:lolflag:

---

### Post by stmiller on 2007-09-19
Start vlc from a terminal, open the file to play back and then let us know what errors come in the terminal when it tries to play the file.

---

### Post by lunamystry on 2007-09-20
lunamystry@michelle:~$ vlc
VLC media player 0.8.6 Janus
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87
lunamystry@michelle:~$

That is what happens when I try to play with VLC after opening from terminal. I still have to try removing gstreamer. There is so many of them installed.

---

### Post by stmiller on 2007-09-20
Ok that is a X display error. You'll have to comment out lines in your /etc/X11/xorg.conf file that are for a wacom tablet. (Ubuntu includes those lines by default, if you have a tablet or not!) See this thread:

[http://ubuntuforums.org/showthread.php?t=212025](http://ubuntuforums.org/showthread.php?t=212025)

---

### Post by lunamystry on 2007-09-20
I  am  kinda afraid to play around with the reminal at the moment as I have exams coming up and I won't have time to fix things if they go wrong. So I'll probably try the thread after the exams but for interest sake, what is to comment out?

---

### Post by andrew.46 on 2007-09-20
Hi,

 If these are .ogg music files the best test is to play them with ogg123. If this is not on your system install:

```
sudo apt-get install vorbis-tools
```

 I have not come across theora files but my svn mplayer certainly plays them. Lots of info leading from this page:

[http://wiki.xiph.org/index.php/TheoraSoftwarePlayers](http://wiki.xiph.org/index.php/TheoraSoftwarePlayers)

             Andrew

---

### Post by lunamystry on 2007-09-21
well I have Mplayer and VLC which used to be my favorite player until I met Kaffeine and I also have the vorbis thing installed but they just show the blue screen when I try to play them. I think I will try the commenting out thing later on.  Just wanna know what exaclty it is first.

---

### Post by lunamystry on 2007-09-21
I need someone to confirm if this is how i should comment out the xorg.conf file. I did all this in Kate so that I hopefully don't mess up my PC. 

[INDENT]```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"	# Change to
								# /dev/input/event
								# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"	# Change to
								# /dev/input/event
								# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"	# Change to
								# /dev/input/event
								# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```[/INDENT]

Then further down

[INDENT]```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```[/INDENT]

I used tab for the spacing of what i added and single space before the #-sign in the first part.

---

### Post by vinutux on 2007-09-22
install correct display driver may solve ur problem or update those drivers

---

### Post by lunamystry on 2007-09-22
> **vinutux said:**
> install correct display driver may solve ur problem or update those drivers

uhm... okay. I can't seem to find and display drivers in adept. What do I look for?

---

### Post by vinutux on 2007-09-22
open adept and search fglrx for ATI driver or nvidia 4 nvidia driver

check u r enabled restricted drivers in restricted driver manager in system->administration

if u found a update for ur pakage install and try

uninstall the drivers and reinstall them (uninstall with configuration files) may helpfull

...........................

othervise u r xorg.conf currupted .....i think:lolflag:

---

### Post by lunamystry on 2007-09-23
> **vinutux said:**
> open adept and search fglrx for ATI driver or nvidia 4 nvidia driver

check u r enabled restricted drivers in restricted driver manager in system->administration

if u found a update for ur pakage install and try

uninstall the drivers and reinstall them (uninstall with configuration files) may helpfull

...........................

othervise u r xorg.conf currupted .....i think:lolflag:

I don't have Nvidia or ATI. My graphics card is the one that came with the PC I think it is intel. When I look at the system information under openGL it lists intel intel and tungsten graphics.

---

### Post by vinutux on 2007-09-23
Intel has opensourced its drivers.................. I think

so it came with xorg.................

and there is no need to install additional drivers..............................:guitar:

..............................................................

check other type of media files (ie mpeg wma mp4 mov) are running without probems

if the problem is persist all type of mediafiles ................... 

resolve u r xorg.conf ...............by hand

search in forums about configuring xorg...............

good luck             :lolflag:

---

### Post by lunamystry on 2007-09-24
My other files are playing fine. I just installed kubuntu Gutsy and I get the same problem. I will use the thread about commenting out some things in xorg.conf. Thanks

---

