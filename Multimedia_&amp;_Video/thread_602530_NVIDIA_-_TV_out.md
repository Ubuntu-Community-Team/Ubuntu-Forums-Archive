---
title: "NVIDIA - TV out"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by flebber on 2007-11-04
I was following the how-to [http://ubuntuforums.org/showthread.php?t=98456&page=38]("http://ubuntuforums.org/showthread.php?t=98456&page=38")

On restart it does seem to work as I can see the whole boot process on both monitor and TV. However once it goes past login the screen stops displaying and goes to a grey background (where the desktop should be) I can still run the mouse on TV screen but vannot do anything.

Wasn't sure whether it wa related to the graphics card and xorg setup or whether its a user rights thing. Here is my stuff .

Interested to here any ideas as I have been trialling a few ideas from everywhere to see if it will work eg grom here [http://gentoo-wiki.com/TV-Out_with_GeForce]("http://gentoo-wiki.com/TV-Out_with_GeForce")
[http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV]("http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV")

User groups
[CODEflebber@flebber-desktop:~$ groups
flebber adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev mythtv
/CODE]

Xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "TV"
	Option     	"TVOverScan" "0.6" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Monitor" 
    	Identifier "Monitor[1]" #TV 
    	HorizSync 30-50
    	VertRefresh 60 
EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   	Identifier  "Simple Layout" 
       	Screen 0 "Screen[0]" 
       	Screen 1 "Screen[1]" RightOf "Screen[0]" 
   	InputDevice "Configured Mouse" "CorePointer" 
   	InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"

Section "Module"
	Load		"glx"
EndSection





```

---

### Post by MaX on 2007-11-04
> **flebber said:**
> I was following the how-to [http://ubuntuforums.org/showthread.php?t=98456&page=38]("http://ubuntuforums.org/showthread.php?t=98456&page=38")

On restart it does seem to work as I can see the whole boot process on both monitor and TV. However once it goes past login the screen stops displaying and goes to a grey background (where the desktop should be) I can still run the mouse on TV screen but vannot do anything.

Wasn't sure whether it wa related to the graphics card and xorg setup or whether its a user rights thing. Here is my stuff .

Interested to here any ideas as I have been trialling a few ideas from everywhere to see if it will work eg grom here [http://gentoo-wiki.com/TV-Out_with_GeForce]("http://gentoo-wiki.com/TV-Out_with_GeForce")
[http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV]("http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV")

User groups
[CODEflebber@flebber-desktop:~$ groups
flebber adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev mythtv
/CODE]

Xorg.conf


Use nvidia-settings instead to do these things.

---

### Post by flebber on 2007-11-04
Any part of "nvidia-settings" that I should particularly be using. I ran nvidia-settings from konsole but there doesn't seem to be many config options in what came up.

---

### Post by flebber on 2007-11-04
Cannot actually use nvidia-settings as when installing it removes nvidia-glx-new . I have found only one post where someone has actually got it working and that guy jagged it by installin mythbuntu and it had access to nvidia-settings options through there.

But me no luck installed mythbuntu and can't get it to run.

---

### Post by MaX on 2007-11-05
flebber: if you run nvidia-settings it should pop up a graphical interface for you to use.

Regarding the uninstalling of nvidia-glx-new, yes it did that for me too, but if you save the xorg file from nvidia-settings to your desktop you can install nvidia-glx-new again, replace the xorg.conf in your /etc/X11 directory and logout and login again and you should be set.

I think I have both nvidia-glx-new and nvidia-settings installed now btw, there was an update yesterday that I think fixed it.

---

