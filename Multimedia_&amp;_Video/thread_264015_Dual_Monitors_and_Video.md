---
title: "Dual Monitors and Video"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by Webspot on 2006-09-24
I have dual monitors which I set up and are working fine! 

Apart from playing video. When I play video, and have the window on my first desktop, it plays fine. 

But, when the video is playing and I move my mouse on to the second screen, the video slowly slides off to the left at the same rate as me moving my mouse to where I cannot see it.

I have tried using totem and vlc, but I get the problem on both.

I have attached my xorg.conf as xorg.conf.txt.

Hope you can help!!

---

### Post by dixonstalbert on 2006-09-24
same problem here!

I tried upgrading fglrx driver yesterday using this guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Method 1 didnt work so I tried Method 2 and that fixed the 'mesa issue' but now totem-xine, gmplayer, vlc all are behaving like you describe.

I tried switching driver in xorg.conf to ati, vesa, radeon but this prevented big desktop from loading and left me with clone displays- though with this I can watch movies on monitor 2!


here is  my xorg.conf

```

# If you have edited this file but would like it to be automatically updated
# again, run the following command: sudo dpkg-reconfigure -phigh xserver-xorg
#Section "Screen"
#	Identifier "aticonfig-Screen[0]"
#	Device     "aticonfig-Device[0]"
#	Monitor    "aticonfig-Monitor[0]"
#	DefaultDepth     24
#	SubSection "Display"
#		Viewport   0 0
#		Depth     24
#	EndSubSection
#EndSection
#Section "Device"
#	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
#	Driver      "ati"
#	BusID       "PCI:1:0:0"
#EndSection

Section "ServerLayout"

 #old has same but no []
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide
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
	Load  "i2c"
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

Section "Monitor"
	Identifier   "SyncMaster"
	DisplaySize  360	135
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

	#Option		"XaaNoOffscreenPixmaps"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	VideoRam    128000
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "HSync2" "30-81"
	Option	    "VRefresh2" "56-76"
	Option	    "UseFastTLS" "1"
	Option	    "Mode2" "1280x1024"
	#BusID       "PCI:1:0:0"	
EndSection

Section "Screen"
	Identifier "aticonfig-Screen [0]"
	Device     "aticonfig-Device[0]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"

		#Viewport   0 0
		Depth     24
		Modes    "2560x1024" "2304x1024" "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

here is my xorg.0.log (WW)s

```
(**) fglrx(0): Display dimensions: (360, 135) mm
(WW) fglrx(0): Probed monitor is 380x310 mm, using Displaysize 360x135 mm
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

```

the 360 135 line I put in months ago to fix screen ratio in totem which was messed up from using 2560 x 1024 virtual resolution

The only thing positvie I can give you for now is that if I watch dvd with gmplayer with command line switches of -vo x11 (i.e. type gmplayer -vo x11 in terminal)  I can watch movie on screen 2

hope this helps 
let me know if you find a solution...

---

### Post by dixonstalbert on 2006-10-02
well I spent hours on this and did not get anywhere :( 

something did not install correctly from the original instal in the OpenGL system and removing and re-installing all the GL stuff, gnome core, X-window-system-core did not fix it.

I had at one point installed Monodevelop, which has it own GL libraries and modifies stuff in /etc to point to them and I am very suspicious that this messed things up when I did a dist-upgrade to Dapper months ago... who knows, but I don't trust that damn monkey!!!

anyways, I did a clean install of dapper on another partition, used automatix to reinstall my applications, then used simple backup/restore and restored my home directory to the new partition from my last backup.

The whole process took less than 3 hours and when I was finished I had fglrxinfo reporting newest ATI drivers installed, fgl_glxgers was running at 600fps, and video apps were all working  properly.

finally after much googling I found out how to copy my new install partition back to my original partition.
While running in the new clean install I used this command:

```
sudo rsync -avHx --delete / /media/hda3
```

My understanding of the rsync options are -avHx handles things like maintaing permissions, handling symbolic links and keeping directory trees nice --delete tells rsync to delete anything in destination that doesnt appear in source. I opted for this because I was afraid some symbolic link or enviormental varible buried deep within my old install was the cause of my grief and better to get rid of it all then keep recycling the same error. I of course lost any data or changes that simple backup hadnt backed up. '/ (there is a space here) /media/hda3' tells rsync to use the root directory '/'  as the source and to send it to the target directory /media/hda3 which was now the mount point of  the root directory of my old install

I rebooted and the grub menu showed both my new and old installs. I booted into safe mode into my old partition and edited the /etc/fstab in my old partition (which now was a copy of the fstab in new partition) so the root partiton point ed to /hda3 

now my grub menu allows me to choose between a dapper install on partition 3 (/hda3 if you speak linux, (hd0,2) if you speak grub) or  new install on partition 7 ((hd0,6) in grub talk) 
I will use the old partition for day to day work and the new one for experimenting on evil monkies!

---

### Post by hungrybuddha on 2007-02-05
bump. i am still researching this to no avail. in due time, i'll probably find that there is no way around this...

if anyone has a similar problem, or knows the solution, please post...

---

### Post by dixonstalbert on 2007-02-06
hi hungrybuddha


do you have enough diskspace to set up a fresh install? you could use Qtparted to make a new partition then make a 2nd install to the new partition.

If your video looks okay then it is a configuration problem and not your particular hardware.

---

### Post by hungrybuddha on 2007-02-06
hello, and thanks..

i dont think it is a hardware problem. the playback is clear and crisp on whatever screen at video startup.  but no matter what, as soon as my mouse drifts to the secondary screen, the video also drifts off screen.

is another install really necessary? is this how you handled this?

---

### Post by Webspot on 2007-02-07
I personally found that I didn't get the problem after a new install. But after installing the updates, it all went wrong and I started getting this problem.

In the end though I just got used to it. Maximize video full to right screen move mouse all the way to left side of desktop, and just use the left screen.

---

### Post by dixonstalbert on 2007-02-07
> **hungrybuddha said:**
> hello, and thanks..

is another install really necessary? is this how you handled this?


yes. 

I reinstalled my old xorg.conf from the install that the monitors acted funny in and in the new install everything was fine; i.e. it wasnt my xorg.conf that was causing the problem.

As I mentioned before, I had previously installed Monodevelop from sources and not from ubuntu package, and then tried to manually remove it.

I only had the video problem on the 2nd screen after upgrading to Dapper, and when I started poking around, I found I hadnt removed an enviormental varible in .bashrc that pointed to monodevelops GLX libraries. I think when Dapper tried to upgrade GLX, things got messed and I dont know how you can totally erase GLX and reinstall without losing your gnome graphic enviorment...

Have you ever installed Monodevelop?

Could you post output of typing the following in a teminal?```
echo $PATH
echo $MANPATH
echo $PKG_CONFIG_PATH
```

Maybe like me, you had installed a non-ubuntu program at some point that left a little goody in your PATH that screwed up package management when you tried to upgrade.

---

### Post by hungrybuddha on 2007-02-08
> buddha@Home:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
buddha@Home:~$ echo $MANPATH

buddha@Home:~$ echo $PKG_CONFIG_PATH


have no idea what that says.

---

