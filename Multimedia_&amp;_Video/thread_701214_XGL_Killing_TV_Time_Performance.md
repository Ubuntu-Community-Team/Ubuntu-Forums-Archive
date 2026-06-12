---
title: "XGL Killing TV Time Performance"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by TZRick on 2008-02-19
Hello everyone,

I have just upgraded my Dell DImension 4100 (PIII 850Mhz) system with an ATI Radeon 9550 (Diamond Stealth) video card (originally nVidia GeForce II GTS).  I've installed XGL and Compiz, in order for it to work with the new card and TV Time.  I believe I read that there were issues using AIGLX, so I used XGL instead.

I am certainly one happy camper!  The 3D screensavers have all come to life and most of the desktop effects work (that cover flip app switcher rocks!!!)...all on a circa 2001 processor!  Vista: eat your heart out!!!

Anyway, the only thing I haven't been able to conquer is my TV Time's performance.  I am guessing, looking at other threads, that all video performance will be affected as well, but I haven't tested enough at this point.  Is there any way to 'exclude' video from being affected by XGL?  When I have TV Time running, the processor runs at 99%, which is where the bottleneck obviously lies.  If the processing can be handled by the video card instead, I am sure things will run much better.

Any ideas?  Thanks in advance!

Specs:
Ubuntu 7.10
Using Restricted Drivers
XGL/Compiz

---

### Post by Yellow Pasque on 2008-02-19
Unfortunately, XGL is a complete replacement for X.org and doesn't work with XVideo (accelerated video). It seems with ATI drivers, that when you sell your soul to the eye candy devil, you shouldn't expect good video performance. You might want to setup another small partition on your disk that has another Ubuntu install with X.org and the open-source radeion driver.

---

### Post by TZRick on 2008-02-19
Thanks for the response.  Is there any way to use AIGLX instead? I've uninstalled XGL but compiz from terminal produces:```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

Any ideas?

---

### Post by Yellow Pasque on 2008-02-19
What version of Catalyst/fglrx are you running? It has to be fglrx 8.42.3 or later to support AIGLX. If you have that installed then open up /usr/bin/compiz and edit like here [http://ubuntuforums.org/showpost.php?p=4169228&postcount=14](http://ubuntuforums.org/showpost.php?p=4169228&postcount=14)

Also, in that file you'll see a line that says WHITELIST="intel nvidia i810 ati ...." You need to add fglrx to the white list.

---

### Post by TZRick on 2008-02-22
Thanks for the guidance.  I installed Envy and that got me up to 8.45.4 as shown in the Catalyst Control Center.  Upon installation, Envy actually installed Compiz for me and it seems to have automatically configured /usr/bin/compiz as per your specs.

However, I have no window borders, title bars or even window listing on my panel.  I've seen this problem posted on many different sites, but most of what is there applies to nVidia users, or my settings already seem correct.  Also, and this is a minor annoyance, TV Time shows fine in fullscreen, but the screen is black when windowed.

FYI: Compiz does not seem to start on login, so I added the following to my Sessions to try to start it:
```
/usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --replace ccp
```

Any ideas?  Thanks again.  I really appreciate your help.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7276 Release
```

~/.xsession-errors:```

(process:6301): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6305): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/trinitron:/tmp/.ICE-unix/6298
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4153 (prog-if 00 [VGA])
Checking for texture_from_pixmap: Initializing gnome-mount extension
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
** Message: Not starting remote desktop server
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

(process:6569): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe Flash Player: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

** (gnome-system-monitor:6651): WARNING **: SELinux was found but is not enabled.
```

 ~/.gconf/apps/gwd/%gconf.xml:
```
<?xml version="1.0"?>
<gconf>
<entry name="metacity_theme_active_opacity" mtime="1169727168" type="float" value="0.86100000143051147">
</entry>
<entry name="metacity_theme_opacity" mtime="1169727168" type="float" value="0.50599998235702515">
</entry>
<entry name="metacity_theme_shade_opacity" mtime="1169727168" type="bool" value="true">
</entry>
<entry name="metacity_theme_active_shade_opacity" mtime="1169727168" type="bool" value="true">
</entry>
<entry name="use_metacity_theme" mtime="1161172811" type="bool" value="true">
</entry>
</gconf>
```

xorg.conf:
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"UseInternalAGPGART"	"no"
	Option		"UseFastTLS"	"2"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	# === Video Overlay for the Xv extension === 
	# === OpenGL Overlay === 
	# Note: When OpenGL Overlay is enabled, Video Overlay 
	# will be disabled automatically 
EndSection

Section "Monitor"
	Identifier	"DELL M781p"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"DELL M781p"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

/usr/bin/compiz:
```
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon fglrx i810"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T=""
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Set to yes to enable verbose
VERBOSE="yes"
```

---

### Post by TZRick on 2008-02-23
FYI: I uninstalled the proprietary drivers and am now using the open-source driver.  I had to remove much of my Gnome and Gconf directories from my profile and then switch the Window Manager option from Compiz to Metacity in gconf-editor to retrieve window borders, etc.

---

### Post by TZRick on 2008-02-23
Latest update:

Compiz is installed.  I had to add SKIP_CHECKS=yes in the compiz manager file, but I now have wobbly windows, etc.

The only problem now is that my screensavers do not work.  The screen simply goes blank.

---

### Post by TZRick on 2008-02-23
Yet another update:

The open-source driver seems to have been causing episodes of freezing where the mouse is responsive, but nothing else is.  I have reverted to the default restricted driver as provided by Ubuntu and will have to forgo Compiz...at least so it seems right now.

Any further suggestions?

---

