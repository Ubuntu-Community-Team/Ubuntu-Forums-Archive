---
title: "Desktop Effects only works with xserver-xgl which is too slow please help"
date: 2008-05-08
forum: Multimedia Software
---

### Post by ytsejam1138 on 2008-05-08
I'm using Ubuntu 8.04 on my laptop with an ATI IGP 320M graphics card.  I have read many posts about this card and it's quirks.  I believe my problem is somewhat isolated.  I have Direct Rendering enabled.  My problem is I would like to run Compiz. but I cannot enable Desktop Effects without having xserver-xgl installed.  However, when I do install xserver-xgl my direct rendering turns off which I believe causes my entire system to slow down to a crawl even scrolling webpages is a chore.  Can someone help me:

1.  Get desktop effects enabled without xserver-xgl
2.  Tweak xserver-xgl to run smoothly.

---

### Post by presston on 2008-05-08
tried ?
> skip_checks=yes compiz
and
> compiz -- replace


give log

---

### Post by dbcoolio on 2008-05-08
xserver-xgl isn't supposed to be required anymore with the Hardy kernel.  I was having the same problem as you (it not working without xserver-xgl, but really slow with it) and then I realized that since my grub was on a different partition, the dist upgrade didn't actually have grub load the new kernel.  once I fixed grub the problem went away.  I have the ATI xpress 200m on my laptop, fyi.

---

### Post by airbornemist6 on 2008-05-08
Have you tried reinstalling all of your compiz packages?

---

### Post by ytsejam1138 on 2008-05-08
I'm not at my laptop, I will upload all requested info as soon as I get back home.  

> **dbcoolio said:**
> xserver-xgl isn't supposed to be required anymore with the Hardy kernel.  I was having the same problem as you (it not working without xserver-xgl, but really slow with it) and then I realized that since my grub was on a different partition, the dist upgrade didn't actually have grub load the new kernel.  once I fixed grub the problem went away.  I have the ATI xpress 200m on my laptop, fyi.

I installed using the automatically use whole disk method.  I'm not sure if Grub is on a different partition.  How do I check that?  Also, how do I fix it if it is?

---

### Post by dbcoolio on 2008-05-08
hmmm, if you're using the whole disk method, then it's less likely that your grub would be messed up.  I have dual boot with windows, and then I had like 4 gb left over due to partitioning randomness that I wasn't using, so I installed a little secondary ubuntu so I could check out KDE and XFCE and Fluxbox and some other things and not mess up my main partition.  but it still messed it up a little, as it made a new grub on the new secondary partition.

Its possible that maybe it didn't update it quite right though.  put in the terminal:

```
uname -r
```

and if it's not 2.6.24-17-generic then that may be the issue.

---

### Post by ytsejam1138 on 2008-05-08
> **presston said:**
> tried ?

and



give log


skip_checks=yes compiz

yields:

```
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

and then the terminal window hangs.

Here is the log for compiz --replace

```
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Terminal window also seems to freeze after running compiz --replace

Here is my xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier      "ATI Technologies Inc Radeon Mobility U1"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "XAANoOffscreenPixmaps"
	Option 		"RenderAccel" "true"
	Option 		"XAANoOffscreenPixmaps"
	Option 		"DRI" "on"
	Option		"mtrr" "on"
	Option          "MergedFB"      "off"
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
	HorizSync 28-72
	VertRefresh 43-60
EndSection


Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies Inc Radeon Mobility U1"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "1024x768" "800x600"
	# Virtual 1528 1024
EndSubSection
EndSection


Section "ServerLayout"
	Option "AIGLX" "true"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "1"
EndSection 
```

---

### Post by ytsejam1138 on 2008-05-08
> **dbcoolio said:**
> hmmm, if you're using the whole disk method, then it's less likely that your grub would be messed up.  I have dual boot with windows, and then I had like 4 gb left over due to partitioning randomness that I wasn't using, so I installed a little secondary ubuntu so I could check out KDE and XFCE and Fluxbox and some other things and not mess up my main partition.  but it still messed it up a little, as it made a new grub on the new secondary partition.

Its possible that maybe it didn't update it quite right though.  put in the terminal:

```
uname -r
```

and if it's not 2.6.24-17-generic then that may be the issue.

I get 2.6.24-16-generic not 17.  Do I need to update to 17?  If so, how?

---

### Post by ytsejam1138 on 2008-05-10
bump

---

### Post by Rocket2DMn on 2008-05-10
Hey, I suggest reconfiguring X, then using this method to enable the workaround for using compiz on the open source ati drivers
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
^ this will give you a generic xorg.conf file which works for most since upgrading has tended to cause problems with xorg.conf configurations leftover from gutsy.
Restart X with CTRL+ALT+BACKSPACE, then follow this for the skip checks method: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by wrineha2 on 2008-05-10
I think I have much the same problem.  I am getting 2.6.22-14-generic
 

How might I be able to remedy this?

---

### Post by dbcoolio on 2008-05-14
if it is 22 instead of 24 then your problem is the same as mine was.

what you need to do is look in the /boot/ folder and make sure that the 24 kernels are installed there, and then ```
sudo gedit /boot/grub/menu.lst
``` first backup the current one, and then find where your list starts, and make a duplicate of the first entry, then change the numbers to match the right files in your /boot/ folder.  then restart.  if it doesn't work, use the entry you duplicated from to get back up again, and then look on here for help about editing grub.  also there is a bunch of comments in the menu.lst file that may be helpful.

---

