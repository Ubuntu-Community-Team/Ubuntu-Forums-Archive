---
title: "How to Rotate the Screen for a TX2000 Tablet PC"
date: 2008-11-29
forum: Multimedia Software
---

### Post by Favux on 2008-11-29
**TX2500, TX2z, TM2t & [SIZE="3"]other Tablet PCs[/SIZE]**

Last Updated: May 13, 2012

**[SIZE="3"]Preliminaries[/SIZE]**
The **Rotation HOW TO** assumes the Wacom digitizer is working on your tablet PC.  Either because the release default wacom.ko (the usb kernel driver/module) and xserver-xorg-input-wacom (the xf86-input-wacom X driver and xsetwacom) package work for your tablet PC (check Synaptic Package Manager or Software Sources) or you have successfully compiled and installed the Wacom drivers using the [LinuxWacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") or the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Configuration for Lucid is through the 10-wacom.conf and for Maverick and up it is the 50-wacom.conf.  Although you can still use the xorg.conf if you prefer.

There has been a **change** to the Wacom input tool **device naming convention**.  To get your devices to rotate enter ***xinput list*** in a terminal.  In the output find the "device name", e.g.:
```
&#9116;   &#8627; Wacom ISDv4 93 Pen stylus               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Finger touch             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Pen eraser               	id=16	[slave  pointer  (2)]

```
that correspond to the input tools you have.  For a tablet PC these would be stylus, eraser (if you have one), and touch (if you have it). Then substitute the longer more descriptive "device name" (with the quotes) in for stylus, eraser, and touch in the script's xsetwacom commands.  For example:
```
xsetwacom set stylus rotate ccw
```
becomes
```
xsetwacom set "Wacom ISDv4 93 Pen stylus" rotate ccw
```
You can also use the ID numbers if you are not hot plugging devices, otherwise the ID #'s can change.  Starting with xf86-input-wacom-0.11.0 the xsetwacom Rotate parameter has been made tablet wide so you need to only rotate the parent device.  This means for a serial (ISDV4) tablet PC the only xsetwacom Rotate command you need is for the stylus, and the others (eraser and touch) can be left out of the script.  For usb tablet PCs with touch you need both the stylus and the touch lines in the script because they are exported from the kernel as two separate devices.

There is a **bug** using the **Lucid default wacom.ko** (from linuxwacom version 0.8.4-1(?)). Stylus and touch are the same in the *xinput list* output, namely "Wacom ISDv4 93", for TX2500 & TX2000's. So for at least touch use the ID number. If you've compiled and installed linuxwacom 0.8.6-2 (or up) or the input-wacom wacom.ko this bug is fixed.


**[SIZE="3"]Summary[/SIZE]**
The first method below invokes the xrandr command line interface to find the screen orientation in the output of the server system's current state.  Then the script uses the appropriate xrandr and xsetwacom commands to rotate the screen and input tools.  Method 2 provides automatic rotation through a shell script if your tablet PC and the system software support it.  Method three does the same but through a Python gtk application that adds other features besides automatic rotation.  The fourth method relies on a C daemon and a shell command.  "Implementing a Script" describes how to make your script executable, how methods 1 & 4 can be implemented by a Launcher (which can be placed in a panel or a dock) or alternatively bound to a hardware key.  Appendix 1 has a little bit on enabling rotation in your video driver (if needed) and appendix 2 discusses how to enable tablet PC bezel buttons.  Appendix 3 shows you how to set up a HP Elitebook's thumb scroll bezel button.


**_[SIZE="3"]Method 1[/SIZE]_**:  "**xrandr -q --verbose**" & grep
This is a &#8220;general&#8221; script that works for both the TX2000 and TX2500 and other tablet pc's.  This script relies on the output of *xrandr -q --verbose*, which gives current screen state.  One line of the output includes current screen orientation.  They all seem, regardless of video chipset or driver, to have a common current screen orientation line which shares a common term and format.  This allows one script/command line to deal with all. 

So this script should work for any Tablet PC that has a line similar to the following in it's *xrandr -q --verbose* output:
```
default connected 1280x800+0+0 (0x1ad) normal (normal left inverted right) 0mm x 0mm
```
What you are looking for is "connected" and ") normal (".  Where "normal" is the current orientation (normal or left or inverted or right) bracketed by parenthesis ")" & "(".

***360 degree*** shell script:
```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
    # rotate to the left
    xrandr -o left
    xsetwacom set stylus rotate ccw
    xsetwacom set touch rotate ccw
    xsetwacom set eraser rotate ccw
    ;;
    left)
    # rotate to inverted
    xrandr -o inverted
    xsetwacom set stylus rotate half
    xsetwacom set touch rotate half
    xsetwacom set eraser rotate half
    ;;
    inverted)
    # rotate to the right
    xrandr -o right
    xsetwacom set stylus rotate  cw
    xsetwacom set touch rotate cw
    xsetwacom set eraser rotate cw
    ;;
    right)
    # rotate to normal
    xrandr -o normal
    xsetwacom set stylus rotate none
    xsetwacom set touch rotate none
    xsetwacom set eraser rotate none
    ;; 
esac
```
This will cause the screen to rotate through 360 degrees counter-clockwise in four 90 degree steps.

A TX2000  or TX2500 screen is hinged to swivel 180 degrees in only one direction before locking down in tablet mode. From landscape to portrait mode in other words. So the script only needs to rotate the screen orientation 90 degrees to portrait and then 90 degrees back to landscape mode. Since a right handed person holds the tablet in the left arm (most like the battery pointing to the right as a handle) the following simplified script serves.

***Right handed***  script:
```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
    # rotate to the right
    xrandr -o right
    xsetwacom set stylus rotate  cw
    xsetwacom set touch rotate cw
    xsetwacom set eraser rotate cw
    ;;
    right)
    # rotate to normal
    xrandr -o normal
    xsetwacom set stylus rotate none
    xsetwacom set touch rotate none
    xsetwacom set eraser rotate none
    ;;
esac
```

***Left handed*** script:
```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
    # rotate to the left
    xrandr -o left
    xsetwacom set stylus rotate ccw
    xsetwacom set touch rotate ccw
    xsetwacom set eraser rotate ccw
    ;;
    left)
    # rotate to normal
    xrandr -o normal
    xsetwacom set stylus rotate none
    xsetwacom set touch rotate none
    xsetwacom set eraser rotate none
    ;;
esac
```
You will need to place the script into a text file, name it, and make it executable.  See **a) Script** in **Implementing a Script with a Launcher or Key Binding** below.
* Thank you to martinjochimsen and manu7irl for helping to validate method 1 for the TX2500.


**_[SIZE="3"]Method 2[/SIZE]_**:  **Tablet PC Automatic Rotation** Script
Red_Lion got auto-magic rotation working.  He developed a script that uses the 'tablet' signal ('dock' for the original unpatched HP-WMI) of HP-WMI as a trigger to provide rotation.  While the following script was developed for HP tablet pc's, Lenovo ThinkPads (and very likely other tablet pc's) should be able to use it too with a minor modification.

Determine your "device names" with *xinput list* entered in a terminal. Then substitute them for stylus, eraser, and touch (if you have it) in the following shell script using the quotes around the "device name". Only use the xsetwacom commands for the devices you have.

Notice the script assumes you have CellWriter installed. You can substitute the onscreen keyboard of your choice or comment out or remove the lines.
```
#!/bin/bash

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/tablet ]]; then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
		if [[ $new != $old ]]; then
			if [[ $new == "0" ]]; then
				echo "Rotate to landscape, hide CellWriter."
				xrandr -o normal
				xsetwacom set stylus rotate none
				xsetwacom set eraser rotate none
				xsetwacom set touch rotate none
				cellwriter --hide-window
			elif [[ $new == "1" ]]; then
				echo "Rotate to portrait, show CellWriter."
				xrandr -o right
				xsetwacom set stylus rotate cw
				xsetwacom set eraser rotate cw
				xsetwacom set touch rotate cw
				cellwriter --show-window
			fi
		fi
		old=$new
		sleep 1s
	fi
done

# From Red_Lion post #576:  http://ubuntuforums.org/showthread.php?t=845911&page=58
```
Save it in "/home/yourusername/" as ".automagic_rotation.sh" (without the quotes), or whatever you want to name it. Make the file executable and add it to your Startup Applications.  See **a) Script** in **Implementing a Script with a Launcher or Key Binding** below.

For the ThinkPad all you should need to do is change the lines.
```
	if [[ -e /sys/devices/platform/hp-wmi/tablet ]]; then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
```
to
```
	if [[ -e /sys/devices/platform/thinkpad_acpi/hotkey_tablet_mode ]]; then
		new=`cat /sys/devices/platform/thinkpad_acpi/hotkey_tablet_mode`
```
Using these examples, if your tablet pc Brand & model also reports the swivel hinge state, you should be able to modify the script to work for you. 

See:
The original **Auto-magic Rotation Script HOW TO** at **[post #225]("http://ubuntuforums.org/showpost.php?p=7738673&postcount=225")**.
MisteR2's original instructions, the hp-wmi patch, and .fdi for it in posts [#104]("http://ubuntuforums.org/showpost.php?p=7189809&postcount=104") and [#106]("http://ubuntuforums.org/showpost.php?p=7191496&postcount=106") on this thread.
MisteR2's new instructions and attachments (with new files) at [post #206]("http://ubuntuforums.org/showpost.php?p=7637329&postcount=206").
Red_Lion's first post of the auto-magic rotation script in [post #576]("http://ubuntuforums.org/showpost.php?p=7732316&postcount=576") on the "Info and help for HP TX2500 Series".


**_[SIZE="3"]Method 3[/SIZE]_**:  The **Magick Rotation** application for Dell, HP, and Lenovo tablet pc's.  It automatically rotates screen orientation and devices/tools that use the Wacom or evdev drivers.  Versions have worked in Arch, Fedora, Gentoo, Mandriva, and openSUSE among others.

MisteR2 tracked down the swivel hinge signal to the HP-WMI kernel module, solving the mystery of no detectable signal.  This sits on top of WMI, which is the Windows Management Instrumentation mapper device.  WMI is a proprietary extension to ACPI that exposes parts of the ACPI firmware and is available for some BIOS's.  Matthew Garrett (the module maintainer) has separated out the swivel hinge signal from the docking event (on MisteR2's request) for us and provided a patch.  The patch is called hp-wmi.diff.txt and is in **[post #106]("http://ubuntuforums.org/showpost.php?p=7191496&postcount=106")**.  It creates a new event called 'tablet' as opposed to 'dock' and will be included in the hp-wmi kernel module for the 2.6.31 (Karmic).  Red_Lion then got auto-magic rotation actually working with his first script.  He also wrote the first version of the Magick Rotation applet in Python gtk.  Not only did it automatically rotate the screen orientation (along with the input tools) when you pivoted the screen to tablet mode it also allowed for handy shell commands.

**[SIZE="3"]Magick Rotation 1.5[/SIZE] applet** released (10-9-11) is **on Launchpad**:   [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  This version adds support for Oneiric (11.10) .  In addition to automatic rotation and selection of rotation direction it offers other features such as a touch toggle function and display of an onscreen keyboard when rotated.  Magick Rotation works for HP & Dell tablet pc's if they have auto-magic rotation in Windows (a swivel hinge switch sends a signal) and their bios supports WMI (and hence hp-wmi or dell-wmi).  It works for Lenovo tablets if they have the thinkpad_acpi and hence it's hotkey support.
**Note**:  Dell XT & XT2 users.  The dell-wmi from the kernel does not report the swivel hinge switch state.  To get a dell-wmi that works correctly see the MagickExtras folder in the magick-rotation folder.  Instructions are there or in a FAQ at the Launchpad site.  Or also see [post #1339]("http://ubuntuforums.org/showpost.php?p=10238515&postcount=1339").

***Advanced Setup*** command examples (note use of semi-colon to separate commands):
[**Run before switch to tablet:**]  killall -9 cairo-dock; gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 42
[**Run after switch to tablet:**]  cellwriter --show-window; cairo-dock -o
[**Exec. before switch to normal:**]  killall -9 cairo-dock; gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 24
[**Exec. after switch to normal:**]  cellwriter --hide-window; cairo-dock -o

CellWriter is included by default; the commands show it in portrait and hide it in landscape.  The Cairo (or Glx) Dock commands are to close the dock and restart it after rotation so it resizes correctly.  This is no longer necessary with recent versions.  The gconftool command resizes the top panel to a larger size (from the default 24) in portrait so it is more touch friendly.  For the bottom panel just substitute *bottom_panel_screen0* for *top_panel_screen0*.  To verify what your default panel size is use Configuration Editor (you may have to make it visible through System > Preferences > Main Menu).  Go to Applications > System Tools > Configuration Editor.  Then look in apps > panel > default_setup > toplevels, then top_panel or bottom_panel.


**_[SIZE="3"]Method 4[/SIZE]_**:  The **wacomrotate daemon**
Tom Jaeger, developer of EasyStroke, came up with an elegant solution.  He wrote a daemon in C called *wacomrotate* that detects current screen orientation and automatically rotates the Wacom input tools stylus, eraser, and touch to the same orientation.

Go to **[Tom's repository]("http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/")** and download the appropriate deb package that contains his C daemon for your release and install type i.e. 32-bit v.s. 64-bit.  For e.g., if you have a 64-bit install of Lucid it would be &#8220;wacomrotate_0.3.1_amd64.deb&#8221; dated 4-13-10.  For a 32-bit install of Maverick it would be &#8220;wacomrotate_0.3.1-0thjaeger1_i386.deb&#8221; dated 9-15-10, etc.  Save to desktop. Then double-click on it and let the deb package installer install it. It will automatically install itself into Startup Applications so that it is auto-started at boot.  If you grabbed the wrong deb by mistake the Debian Installer will tell you so and refuse to install the package.

He also supplied the following command line command to be used in conjunction with his wacomrotate daemon.
For ***right handed Portrait*** rotation use:
```
  xrandr -q | grep -q '+\w* (' && xrandr -o right || xrandr -o normal

```or for ***left handed Portrait*** rotation use:
```
  xrandr -q | grep -q '+\w* (' && xrandr -o left || xrandr -o normal

```
You'll want to put the command into a Launcher or create a Key Binding as described below.


_**[SIZE="3"]Implementing a Script[/SIZE]**_ with a **Launcher** or **Key Binding**
**a) Script**
1) Open Text Editor (gedit) and create a new .txt file.
2) Into it place the script of your choice.  Obviously if you're going to use the wacomrotate daemon you'll need Tom's command (or you can skip this and with his command go straight to the key binding method below).
3) Name the script and Save the script as *.yourscriptname.sh*.  The period in front of the name is makes it a hidden file.  This is useful if you place the file in your */home/yourusername* directory.  That will help prevent directory clutter.  If you decide to create a folder/directory bin (/home/yourusername/bin) for your scripts you probably won't want to make it hidden.
4) Now you need to make the script file executable.  Right click on the text file and choose Properties.  In the Permissions tab check the &#8220;Allow executing file as a program&#8221; and close.  Or in a terminal:
```
chmod +x ~/.yourscriptname.sh
```
5) The *Tablet PC Automatic Rotation Script* needs to be set up to auto-start.  Go to System->Preferences->Startup Applications and click on Add and for the command enter */home/yourusername/.automagic_rotation.sh*. And title it &#8220;Auto-magic Rotation&#8221; or whatever you like.

**b) Launcher**:  for methods 1 & 4
1) Next create a launcher on the desktop by right clicking on it and choosing *Create Launcher..*.  Give it a name and in the Command box type the path to the text file you made executable i.e. */home/yourusername/Desktop/.yourscriptname.sh*.
**Note**:  when you clean up the Desktop and move the script to say, /home/yourusername or /home/yourusername/bin directory, remember to change the path in the Launcher's command box to reflect the new path.
2) Double click on the launcher's icon and watch the screen rotate!  Check that your stylus, eraser, and touch are oriented and working correctly.  Double click again and rotate back.
3) If you want, move the launcher to a panel or to a dock, like Cairo-dock, and then a single click will rotate the screen.

**c) Button/key Binding**:  for methods 1 & 4.  To further integrate screen rotation into your tablet PC you can do a key binding to a key, preferably a bezel button.  A bezel button is one of the buttons on the edge of the screen still accessible in tablet mode.
While a HP TX2000 is used as an example on how to set up the bezel buttons, most of the information should generalize to other tablet PC's. For further explanation see **Appendix 2** below.  With the TX2000 only 2 bezel buttons ever worked, see *Miscellaneous Notes* below.  And starting with Lucid the DVD button also stopped working, leaving only the "Q" button.
1) To get the **DVD button** working again and launching the mediaplayer as it did before Lucid edit the *hewlett-packard* keymap in */lib/udev/keymaps* with:
```
gksudo gedit /lib/udev/keymaps/hewlett-packard
```
like so:
```
#0x08e dvd
0x08e media
```
2) To assign the **"Q" button** to the XF86Launch5 KeySym first edit the *hewlett-packard-pavilion* keymap in */lib/udev/keymaps* using:
```
gksudo gedit /lib/udev/keymaps/hewlett-packard-pavilion
```
And make the following change:
```
#0x88 media # FIXME: quick play
0x88
```
Now edit *rc.local* in */etc*:
```
gksudo gedit /etc/rc.local
```
and add:
```
setkeycodes e008 184
```
above the *exit 0* line and reboot.
3) Open the **CompizConfig Settings Manager** (CCSM).  You may need to install it first.  In **General** open **Commands**.  Make sure the *Enable Commands* box is checked.  In the *Commands tab* pick a command line and type in the name and path of the executable rotation script text file and close.  If you're running the wacomrotate daemon you can put in Tom's command directly instead of the path to the rotation script.
4) Next select the **Key Bindings** tab.  Pick the *Run command* line that has the same number as the *Command line #* you put the rotation script file name (and path) in.  Click on the *Disabled* button to the right of *Run command #*.  Click the *Enabled* box and then the *Grab key combination* button.  Press the Q button.  You should see XF86Launch5 appear.  Close CompizConfig.
5) Now press the "Q" bezel button and watch your screen rotate!


**[SIZE="3"]Miscellaneous Notes[/SIZE]**
With HP TX2000's we never got a signal, in xev or anything else, from the two blue led buttons on the bottom right edge of our screen, one of which is the original rotation button.  Starting with Karmic we lost the DVD bezel button too.  And the Q key (which we were using as a substitute rotation key) became the only active bezel button.  It now codes XF86AudioMedia and launches the mediaplayer like the DVD key used to and should do.  Presumably this is due to a bug(s) in hp-wmi.  Red_Lion looking at his DSDT thinks the "bezel buttons parsing via PNP0C09 method _Q16."  PNP0C09 is the Microsoft acpi-compatible embedded controller.  A summary of what we have learned so far is in [posts #273 & 274]("http://ubuntuforums.org/showthread.php?t=996830&page=28") on this thread.  There are similar problems with HP's TX2500 and TX2z bezel buttons, again presumably due to the same hp-wmi bug.
**Bezel Button Update:**  tipp98 is currently investigating the problem and has made progress!  He's provided a summary of his findings to date on [post #601]("http://ubuntuforums.org/showpost.php?p=11691208&postcount=601").  Even more information is available on this **linux-acpi** [mailing list thread]("http://www.spinics.net/lists/linux-acpi/msg34577.html").

For us HP TX2000, TX2500, & TX2z owners to get auto-magic rotation we needed to detect a signal from our swivel hinge.  Nothing came through on xev, or acpi_listen and in /var/log/messages either.  Then MisteR2 located the signal to the HP-WMI kernel module.

**Previous versions** of **Magick Rotation** (Red_Lion's applet for auto-magic rotation in pygtk):  0.5 is at [post #528]("http://ubuntuforums.org/showpost.php?p=9888796&postcount=528").  0.4 (first to support Lucid) is at [post #484]("http://ubuntuforums.org/showpost.php?p=9394701&postcount=484"); 0.3-3 is at [post #315]("http://ubuntuforums.org/showpost.php?p=8052613&postcount=315"); 0.2-5 is at [post #291]("http://ubuntuforums.org/showpost.php?p=8012056&postcount=291"); 0.2-4 is at [post #279]("http://ubuntuforums.org/showpost.php?p=7834835&postcount=279").  Also 0.2-3 at [post #272]("http://ubuntuforums.org/showpost.php?p=7805386&postcount=272") & 0.2-2 at [post #265]("http://ubuntuforums.org/showpost.php?p=7798703&postcount=265").

The **Auto-magic Rotation Script HOW TO** is at **[post #225]("http://ubuntuforums.org/showpost.php?p=7738673&postcount=225")**.

Both the Automatic Rotation script and Magick Rotation (they use the swivel hinge switch signal) work in Lucid, Maverick, and Natty for HP's TC4200, TC4400, TX2000, TX2500, TX2z, 2710p, 2730p, and TM2t.


**[SIZE="3"]Sources[/SIZE]**
Many thanks to the Tom Jaeger and the authors of the following excellent tutorials and associated threads among others:
by mirosol (alternative TX2000 rotation script):  [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
alternative TX2500 rotation script by Shm (typo corrected by Pietro Battiston:  [http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500]("http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500")):  [http://ubuntuforums.org/showthread.php?t=845911&page=35]("http://ubuntuforums.org/showthread.php?t=845911&page=35")
toobaz (Pietro Battiston) has updated his [**TX2500 wiki for Karmic**]("http://www.pietrobattiston.it/wiki/doku.php?id=karmic_on_hp_pavilion_tx2500#rotation_and_buttons").  He has an interesting take on setting up the rotation scripts there.
Toshiba M700 rotation script:  [https://wiki.ubuntu.com/SergioZanchetta/Old/ToshibaPortegeM700](https://wiki.ubuntu.com/SergioZanchetta/Old/ToshibaPortegeM700)


**_Appendix 1_:  enabling video driver rotation**
The **proprietary Nvidia** driver requires the following option in the xorg.conf:
```
	Option		"RandRRotation"  "on"
```
in *Section "Device"* with the *Identifier* labeled *"Configured Video Device"* or *"Default Device"*, depending on your Xserver version.

Most Intel MB chipsets using the **Xorg Intel** video driver don't require any extra configuration.  However some may require the same option, those chipsets that need a xorg.conf for proper configuration.

The **ATI proprietary "fglrx"** driver through Catalyst should work without any xorg.conf or option added to it.  If you have any video issues check out the [Unofficial Wiki for the AMD Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") site.

**_Appendix 2_:  Bezel Buttons; using mainly the HP TX2000 as an example**
First you want to check if the keys are emitting a keycode.  There are several diagnostic tests to look for a keycode among them *xev* and *evtest*.  Let's use xev.  In a terminal type:
```
xev
```
and hit enter.  A little box pops up.  Press one of the keys/buttons in question and then close the box.  The terminal will fill with output.  You are looking for keywords like **KeyPress**, **keycode**, and **keysym**.  You can copy and paste the output into gedit and then do a find for them.  You are looking for the keycode number and the little sections of output that contain it.  There should be two, one for the KeyPress event and one for the KeyRelease event.  Then repeat for the next key.  Remember the keycodes you get from xev are the X keycodes (hence the x in the name, xev = X event).  If there are keycodes you should be able to assign them through Xmodmap, xbindkeys, xdotool, etc.

Now if there is no X keycode that is another situation and there are several possibilities.
1)  Something is going wrong with the chain:  kernel keycode > udev key mapping (keysym assignment) > X keycode.  This is what the rest of appendix 2 deals with, a step by step guide to diagnose the chain.

Other possibilities include:
2)  The BIOS has changed key assignments and the kernel driver code that is reading the key assignment needs to be changed to reflect that.  Examples of that would be the code in hp-wmi.c or thinkpad-acpi.c.  The compiled versions of those are the hp-wmi.ko and thinkpad-acpi.ko (ko = kernel object i.e module/driver) you see in /lib/modules/yourcurrentkernel/kernel/drivers/platform/x86.  In which case you may need to work with the kernel source code of the appropriate kernel module/driver and change the hex/scan code assignments.  Then compile the module to test your changes.  Examples of that being done for the dell-wmi.c are in [post #1176]("http://ubuntuforums.org/showpost.php?p=9780095&postcount=1176") and [post #1587]("http://ubuntuforums.org/showpost.php?p=11439576&postcount=1587") of the N-Trig HOW TO.
3)  The final possiblity is either a kernel module/driver has never been written or, if one of the current modules is the appropriate driver, the code has never been written for it to support the buttons/keys in question.  **Fujitsu tablet PCs** "enjoy" a special case of this.  While the fujitsu-tablet.c (fujitsu-tablet.ko) module which supports the bezel buttons has been written and submitted to the kernel for unknown reasons it has never been accepted.  So to obtain the kernel module/driver (which comes in the fjbtndrv package) you need to use either Robert Gerlach's [fjbtndrv PPA]("https://launchpad.net/~khnz/+archive/ppa") or [SourceForge site]("http://sourceforge.net/projects/fjbtndrv/") and compile it.

**a) kernel codes** The first step is to find the bezel button's kernel scan codes.  Enter a console with <ctrl-alt-F1>; to get back to X enter <ctrl-alt-F7>.  Then enter ***showkey -s*** in the console and press the bezel buttons.  Only the scan code from the Q key (none of the other 3 do anything) appears:  0xe0 0x6d 0xe0 0xed.  Next find the kernel keycodes by entering ***showkey -k*** and press the buttons which shows (the two bottom buttons do nothing):  DVD button = 389 and Q button = 226.  So the bezel button assignments from the kernel are:
```

DVD button         scan code = ???                   keycode = 389
Q   button         scan code = 0xe0 0x6d 0xe0 0xed   keycode = 226
Rotation button    N/A
Brightness button  N/A

```
The keys and their corresponding key codes are defined in **input.h** at **/usr/include/linux**.

**b) udev codes** Now using the README at **/usr/share/doc/udev/README.keymap.txt** let's dump the current mapping and determine the udev scan codes and key codes.  To do this we need to know the input/event the keyboard is on.  Enter in a terminal ***/lib/udev/findkeyboards***.  The output shows the keyboard is on event 5.
> USB keyboard: input/event5
Or use ***ls -l /dev/input/by-path*** and look for -event-kbd.
> lrwxrwxrwx 1 root root  9 2011-06-01 16:05 platform-i8042-serio-0-event-kbd -> ../event5
Then using that event# dump the **current udev keymapping** into a text file for reference:
```
sudo /lib/udev/keymap input/event5 > /home/yourusername/orig-map.txt
**or**
sudo /lib/udev/keymap input/event5 > ~/orig-map.txt

```
To determine the udev codes run in a terminal the following command:  ***sudo /lib/udev/keymap -i input/event5***  Then press the bezel button(s) or multimedia/function keys of interest.  Use **esc** to exit.  If it shows a tendency to scroll away, use:  ***sudo /lib/udev/keymap -i input/event5 | less***  And after pressing the bezel buttons, again enter **esc** to exit, and you will see the scan codes and the associated udev key codes.  Enter **ctrl-z** to exit less.  The output shows:
```

scan code: 0x8E   key code: dvd
scan code: 0x88   key code: media

```
So now the **bezel button assignments from the kernel and udev** are:
```

DVD button   scan code = ???                   keycode = 389   scan code: 0x8E   keycode: dvd
Q   button   scan code = 0xe0 0x6d 0xe0 0xed   keycode = 226   scan code: 0x88   keycode: media

```
**Note**: to find the corresponding X keycode add 8 to the kernel keycode.  See e) below.

**c) udev rules and keymaps** 
In **/lib/udev/rules.d** you'll see the Hewlett-Packard rules in the **95-keymap.rules** file.  They will apply all the keymaps that the rules match.  The match is made to the Vendor and then the dmi id's product_name and board_version (**/sys/class/dmi/id**).  To determine the last two enter the following two commands:
```

sudo dmidecode --string system-product-name

sudo dmidecode --string baseboard-product-name

```
The results being:
> 
HP Pavilion tx2000 Notebook PC
30E5

So the rule matches cause the following hewlett-packard keymaps in **/lib/udev/keymaps** to be applied:  hewlett-packard, hewlett-packard-tablet, hewlett-packard-pavilion, and hewlett-packard-tx2.  Looking in them we discover that **hewlett-packard** contains **0x08e dvd** and **hewlett-packard-pavilion** has **0x88 media**.  Now we know where the udev codes are coming from.

**c) changing udev keymaps**
Clearly we can edit and change the rules or the keymaps.  While the DVD button seems to be recognized by udev it appears to do nothing and acts broken.  Can we get it to do anything?  Editing the hewlett-packard keymap in **/lib/udev/keymaps** like so:
```

#0x08e dvd
0x08e media

```
Results in, after a reboot, the DVD bezel key suddenly working again!  And it launches the mediaplayer like it used to do and just like the Q key does now.  So we are back to two working bezel buttons.  But we don't need both assigned to media so let's remove the media assignment from the Q button.  Edit the hewlett-packard-pavilion keymap in /lib/udev/keymaps using:
```
gksudo gedit /lib/udev/keymaps/hewlett-packard-pavilion
```
And make the following change:
```
#0x88 media # FIXME: quick play
0x88
```
After a reboot if you check the keymap:
```
sudo /lib/udev/keymap input/event4 > /home/username/mod-key-map.txt
```
You'll find *0x088 media* changed to *0x088 reserved* indicating the Q button is unassigned.

**d) assign the Q button to the XF86Launch5 KeySym with setkeycodes in rc.local**
To find the usable form of the kernel scan code needed by setkeycodes press the Q button and run:
```
dmesg | grep atkbd
```
You should see:
> [  109.500951] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[  109.500956] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[  109.502910] atkbd serio0: Unknown key released (translated set 2, code 0x88 on isa0060/serio0).
[  109.502914] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
Dmesg has kindly done the conversion for us and **e008** is what we want to use.

Now we need to assign the "Q" button to XF86Launch5 in order to bind it into a rotation script.  We've been traditionally using XF86Launch5 to avoid conflicting with any other key assignment.  To determine the keycode for XF86Launch5 run this command:
```
xmodmap -pke | grep XF86
```
In the output we see:
> keycode 192 = XF86Launch5 NoSymbol XF86Launch5
Notice as the command name *xmodmap* implies 192 is a X keycode.  Recall to get the kernel keycode you need to subtract 8 from the X keycode.  So *192 - 8 = 184*.  Now using ***184*** enter in rc.local in /etc the following:
```
setkeycodes e008 184
```
above the ***exit 0*** line and reboot.  By adding it to rc.local we avoid prefacing it with *sudo* since rc.local runs before X starts.  Now the Q button is assigned to XF86Launch5 and is ready to be bound in CCSM to a rotation script (see "Implementing a Script" c) above).  You can verify this by opening up a terminal and running &#8220;xev&#8221;.  A box will pop up.  Press the Q bezel button and then close the xev box.  In the ouput you will see for the bezel key press XF86Launch5.

**TA DA!**  We're back to where we were pre-Lucid (well OK, Karmic).  Two working bezel buttons with DVD calling the music player and Q the rotation script.

Another example of using setkeycodes is the **Thinkpad X201t** script "**setX201tKeys.sh**" by linuxd00 from "[[HOW TO]Lenovo X201 tablet. Enable your Tablet buttons and some little surprises]("http://ubuntuforums.org/showthread.php?t=1656632")".
```
#!/bin/bash

sudo setkeycodes 0x67 148 # unlabeled(rotating arrow) button mapped to KeySym:	XF86Launch1 - X keycode is 156
sudo setkeycodes 0x6c 120 # Rotatebutton button mapped to KeySym: 		XF86LaunchA - X keycode is 128
sudo setkeycodes 0x68 204 # Toolbarbutton button mapped to KeySym: 		XF86LaunchB - X keycode is 212
sudo setkeycodes 0x66 149 # Padlock button mapped to KeySym:  			XF86Launch2 - X keycode is 157
```
The Thinkwiki.org has more on Thinkpad bezel buttons.

**e) X keycodes**
The Xserver currently doesn't process keycodes greater than 255 due to core protocol limitations.  This is why some keys don't generate any events.  X also requires an offset of 8 from the kernel key code.  Recall there is a list of kernel key values in input.h.  To get the corresponding X keycode simply add 8 to the kernel keycode:
```
X keycode = kernel keycode + 8 (provided the new X keycode is not greater than 255)
```
So for example the Q button's X keycode would be:
```
X key code = 234 = 226 + 8
```

**f) Xmodmap (method used prior to Lucid)**
1) Open up a terminal.  Type &#8220;xev&#8221; and enter.  A box will pop up.  Press the bezel button and then close the xev box.  Then look for the returned keycode value for the bezel key press.  (For a HP TX2000 it was keycode 201 for the &#8220;Q&#8221; key in Intrepid (205 in Hardy)).
2) Open a text file on the desktop.  In it enter the keycode e.g. 201:
```
  keycode 201 = XF86Launch5
```where in this example XF86Launch5 is a key label not being used by any other key code.  Save the text file as &#8220;**.Xmodmap**&#8221; in your home/user/ directory.  The Xmodmap will become active on reboot.
After restart open up a terminal and run &#8220;xev&#8221;.  Press the bezel key.  You should see the keycode number as before now associated with in our example XF86Launch5.
*thanks to Ayuthia for his assistance

**_Appendix 3_:  HP Elitebook Tablet PC Thumb Scroll Bezel Button**
Sometimes the showkey command in appendix 2 a) doesn't yield a scan code.  In this example this Elitebook's thumb scroll scan codes were found in the **kern.log**.
```

    Mar  6 12:30:22 MisfitToy kernel: [13086.240796] atkbd serio0: Unknown key released (translated set 2, code 0x86 on isa0060/serio0).
    Mar  6 12:30:22 MisfitToy kernel: [13086.240806] atkbd serio0: Use 'setkeycodes e006 <keycode>' to make it known.
    Mar  6 12:30:22 MisfitToy kernel: [13086.531892] atkbd serio0: Unknown key pressed (translated set 2, code 0x87 on isa0060/serio0).
    Mar  6 12:30:22 MisfitToy kernel: [13086.531902] atkbd serio0: Use 'setkeycodes e007 <keycode>' to make it known.

```
Looking in the:
```

xmodmap -pke > xmodmap-pke.txt

```
output shows these X keycodes which are of interest.
```

keycode 111 = Up NoSymbol Up
keycode 112 = Prior NoSymbol Prior

keycode 116 = Down NoSymbol Down
keycode 117 = Next NoSymbol Next

```
To get the thumb scroll button to work we'll elect to use Prior and Next.  Remembering to subtract 8 from the X keycodes, enter in rc.local:
```

    setkeycodes e006 104
    setkeycodes e007 109

```
above the ***exit 0*** line and reboot.  **TA DA!**  Your thumb rocker switch now scrolls.
*thanks to robbyb413 on Mint forums for his assistance

---

### Post by stringy-jb on 2008-12-05
Awesome post .... you folks are wonderful!!

---

### Post by martinjochimsen on 2008-12-08
Hi favux

Can you change the "sudo gedit etc/x11/xorg.conf" to "sudo gedit /etc/X11/xorg.conf"? I think there is missing a "/" and a capital "X" in that line. Of course both without the quotes!

Martin :-)

---

### Post by Favux on 2008-12-08
Hi martin,

You are correct.  Thanks for pointing it out.  It's fixed.

---

### Post by fbdelivers on 2008-12-13
Thanks for the post.  The only thing that I can't get to work is the stylus calibration when I rotate.

Touch screen works.
Key binding is working with 'Q'

But when I try to use the stylus everything is crazy.  Any ideas on what may be causing this?

using tx2500.

Thanks

---

### Post by Favux on 2008-12-13
Hi fbdelivers,

The first thing that comes to mind is that your name for "stylus" in xorg.conf is different from "stylus" in the scripts.  Check your xorg.conf and look at the stylus name in the "InputDevice" stylus section and in the "ServerLayout" section.

And remember in xorg.conf it's case specific.  In other words "Stylus" is not the same as "stylus".  Probably best to change the script name unless you want to get into checking your .xinitrc's.

Let me know.

---

### Post by martinjochimsen on 2008-12-13
Hi Favux

How is the calibration for the stylus working when you have rotated your screen?
Mine is off with at least half a centimeter, but is perfect when the screen is normal.
Did you also use Xournal? Do you have pressure sensitivity in that program (or in any programs)?
Mine is the same in both GIMP and Xournal meaning NO sensitivity. It would be great to have some kind of sensitivity when I fx. is using the onscreen keyboard in Cellwriter. As it is now, it is impossible to use. You can only wright reeeaaalllllyyyyy sssslllloooowwwwwllllyyy to be sure you hit the right letter!!!

Martin :-)

---

### Post by Favux on 2008-12-13
Hi martin,

My calibration is the same rotated or unrotated.  Have you tried calibrating when rotated?  I added wacomcpl the my System>Preferences menu using System>Preferences>Main Menu.  I called it Wacom Tablet Calibration and in the command box put "wacomcpl".  This way it is easy to calibrate it rotated.  But to be honest I haven't needed to do this.  Hopefully that's all you need to do, and we haven't found a problem with "radeon"!

Yes I have pressure sensitivity in Xournal, Gimp, and Inkscape.

First I'd suggest you go to the Linux Wacom Project's _Using Xsetwacom_ HOWTO at:

   [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom")

if you haven't already.  Lots of good info., esp. on using terminal to check your pressure sensitivity, etc.  Remember the tool names are case sensitive so stylus is not the same as Stylus.  Check your xorg.conf if you don't remember.  This gives you access to settings that aren't necessarily in wacomcpl.

Xournal:  in Options do you have Xinput checked?  Do you have pressure sensitivity checked?

Inkscape:  Have you gone to File>Input Devices and configured stylus, eraser, and touch?

Gimp:
You probably want to check out Drawing Tablets-Wilber's Wiki at:
   
   [http://wiki.gimp.org/gimp/DrawingTablets]("http://wiki.gimp.org/gimp/DrawingTablets")

Lots of good info. but to set up Gimp you want the hotlink Pressure Sensitivity under Enabling Gimp Pressure Sensitivity.  When it says File>Preferences it means Edit>Preferences.  Also the Device Status dialog is located in Windows>Dockable Dialogs>Device Status.  Just follow the steps and you should have your stylus, eraser, and pressure working in short order.  Hope this helps.

---

### Post by Favux on 2008-12-13
Hey martin,

Another thought.  I have noticed occasionally, if I've opened a program in one orientation and then rotate to another orientation, things can be off.  It mainly, or exclusively, happens in Gimp.  So I guess I just have developed a habit of only opening the program once I'm in the orientation I want.  I really wasn't aware I was doing that until just now.

---

### Post by martinjochimsen on 2008-12-13
No, i didn't have pressure sensitivity checked in xournal - and now it works! Thanks.
I now remember that you earlier gave me the links for the Wacom sites. I only remember that I didn't understand much! :-) I'll take another look.
Have you tried the keyboard in Cellwriter (or the keyboard in Onboard)? Is it easy to write with?
I will try to calibrate the stylus when the screen is rotated and see what happens.
Thanks for the quick reply.

Martin :-)

---

### Post by Favux on 2008-12-13
Hi martin,

I just use Cell Writer.  It has the key board and the letter recognition feature too.  It's as good as the MS input panel.  I have it set in Sessions so it's available at boot.

---

### Post by martinjochimsen on 2008-12-13
I also made a startup-session for Cellwriter. 
Great minds think alike! :-D
How is the keyboard working for you. Is it sensitive enough for writing?

---

### Post by Favux on 2008-12-13
Hi Martin,

I'm writing this with Cell Writer's keyboard!  Does this answer your question?  It's slower than typing though.

---

### Post by martinjochimsen on 2008-12-13
Aha!
I just found this lines from the Wacom howto:


```
If you want to know what the current (or default) pressure sensitivity setting is, then:

    [jej@ayukawa linuxwacom]$xsetwacom -s get Stylus PressCurve (output in xsetwacom format)
    xsetwacom set stylus PressCurve "0 15 85 100"
    or
    [jej@ayukawa linuxwacom]$xsetwacom -x get Stylus PressCurve (output in xorg.conf Option format)
            Option  "PressCurve"    "0,15,85,100"

    [jej@ayukawa linuxwacom]$xsetwacom -x getdefault Stylus PressCurve 
            Option  "PressCurve"    "0,0,100,100"

If you want to set the pressure sensitivity a bit softer, then:

    [jej@ayukawa linuxwacom]$xsetwacom set Stylus PressCurve 0 15 85 100
```

and

```
PressCurve    i1 i2 i3 i4  sets the pressure bezier curve, where i1+i4=100; i2+i3=100
```

The question is then: How do I get it to be more sensitive than the example (0 15 85 100).....beside just trying and trying?

---

### Post by Favux on 2008-12-13
Hi martin,

As far as I know that's what you do.  Apparently it's an individual preference.  I have seen settings like:  5 15 85 95 and 5 20 80 95.  But I don't know what the "standard" settings are.  I'm not a graphics artist, I just mess around.

---

### Post by tekrytor on 2008-12-13
> **Favux said:**
> **Re: TX2500 Tablet PC**

Note:  TX2500 users.  The ATI propietary driver "flgrx" (up to and including Catalyst 8.11) does not support rotation.  For rotation you will have to use Xorg's "radeon" driver.

I can't get rotation to work, but I just "got it" that the proprietary drivers might be the problem. Guess I should have read the first line of the instructions. Everything else is working in my tx2500. Backing off the ATI driver next. I'll be back. ;(

---

### Post by fbdelivers on 2008-12-14
> **Favux said:**
> Hi fbdelivers,

The first thing that comes to mind is that your name for "stylus" in xorg.conf is different from "stylus" in the scripts.  Check your xorg.conf and look at the stylus name in the "InputDevice" stylus section and in the "ServerLayout" section.

And remember in xorg.conf it's case specific.  In other words "Stylus" is not the same as "stylus".  Probably best to change the script name unless you want to get into checking your .xinitrc's.

Let me know.

Thanks for the response.  I double checked my script and xorg.conf file and they are using the same name.

Here is my xorg file and script I'm using if that helps.  I may be just missing something.

On a side note when I run wacomcpl it doesn't show any devices available.  So maybe I should start from scratch with my wacom configuration.

---

### Post by Favux on 2008-12-14
Hi fbdelivers,

I think we have you sorted out now.  The clue is that in wacomcpl you don't see stylus, eraser, or touch.  That means the linuxwacom kernel module is not detecting any usb inputs.  You do have a TX2500, correct?  I think that means your stylus is working through HAL.  You do have it unrotated right?  My stylus didn't work through HAL.  I wonder if Tom Jaeger's wacomrotate daemon would rotate your stylus which is working through HAL?  But you don't have eraser, side button or touch, right?

Your xorg.conf is a TX2000 xorg.conf, not a TX2500 xorg.conf.  Look at the difference in usb input:
TX2000(yours)
```
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
```
TX2500
```
Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
```
So I have attached a TX2500 xorg.conf from a laptop that has working tablet features.

You can modify it some, using your video section for example.  Notice how Synaptic Touchpad is commented out.  HAL handles it fine.  I notice you have some extra configuration on yours.  I think HAL will handle that to.  Notice the mouse is handled through HAL.  The keyboard could be handled through HAL, but HAL breaks single key key bindings. So we wouldn't be able to use your "Q" key for screen rotation if we used HAL.

Try replacing your xorg.conf with the TX2500 xorg.conf (with changes you feel appropriate).  Of course back up your xorg.conf first.

---

### Post by fbdelivers on 2008-12-14
Awesome.  You had my xorg.conf figured out.  Using your updated tx2500 did the trick and rotation works as per the script I was using before.  Very cool.

---

### Post by Favux on 2008-12-14
Hi fbdelivers,

Great!  Isn't being able to use a tablet pc as a tablet nice!

---

### Post by fbdelivers on 2008-12-14
> **Favux said:**
> Hi fbdelivers,

Great!  Isn't being able to use a tablet pc as a tablet nice!

Yes. With full rotation support I can finally say goodbye to the vista partition.

---

### Post by fbdelivers on 2008-12-14
> **Favux said:**
> Hi fbdelivers,

Great!  Isn't being able to use a tablet pc as a tablet nice!

Yes.  With full rotation support I can now say goodbye to my vista partition.

---

### Post by fbdelivers on 2008-12-14
> **Favux said:**
> Hi fbdelivers,

Great!  Isn't being able to use a tablet pc as a tablet nice!

Yes.  With full rotation support I can now say goodbye to my vista partition.

---

### Post by Favux on 2008-12-14
Wow!  fbdelivers, a triple post.  A new record!  The forums been flaky tonight.

Hi Riverhed and DrakeGis,

Drew,

Did you run gali98's 11-3-08 tutorial?  Why don't you post your xorg.conf.

DrakeGis,

The output of dmesg | grep Wacom :
> [ 18.048515] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.0/input/input10
[ 18.292550] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input11
[ 18.354005] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
seems to indicate you have the wacom module correctly loaded and you should be seeing stylus and touch activity.  So it is probably a xorg.conf problem or in .xinitrc or xinitrc.  I don't know for sure if "radeon" supports compiz.  I guess we'll have to find out.  Xorg is promising to add 3d to "radeon" so compiz should be supported soon, if it isn't already.

---

### Post by fbdelivers on 2008-12-15
> **Favux said:**
> Wow!  fbdelivers, a triple post.  A new record!  The forums been flaky tonight.

The embarrassment of creating a new record is all worth it with rotation working now :p

I don't know what was going on last night.

---

### Post by Favux on 2008-12-15
Hi everybody,

I thought I'd mention that I went through gali98's tutorial and installed linuxwacom 0.8.2.  I read through all the release notes and it seemed like a worthwhile thing to try.  It works fine.  I just changed 0.8.1-6 to 0.8.2 in the tutorial.  The notes talked about more features for wacomcpl.  I don't really see anything new though.

---

### Post by DrakeGis on 2008-12-15
Favux, thanks !!!!. I figure out that there was a problem in the xorg.conf. I was able to fix it. I would like to know more about the calibration process. It seems to me that it is very hard to get the touch correctly calibrated...  
I haven't try the rotation. I guess it will have to wait until next weekend. Does anyone has compiz and rotation  working ?

Thanks again.

D.


> **Favux said:**
> Wow!  fbdelivers, a triple post.  A new record!  The forums been flaky tonight.

Hi Riverhed and DrakeGis,


DrakeGis,

The output of dmesg | grep Wacom :

seems to indicate you have the wacom module correctly loaded and you should be seeing stylus and touch activity.  So it is probably a xorg.conf problem or in .xinitrc or xinitrc.  I don't know for sure if "radeon" supports compiz.  I guess we'll have to find out.  Xorg is promising to add 3d to "radeon" so compiz should be supported soon, if it isn't already.

---

### Post by tekrytor on 2008-12-16
> **Favux said:**
> **and a TX2500 Tablet PC**
:::
9)Go to System>Preferences>CompizConfig Settings Manager.

Favux,

I got rotation working on my HP tx2510 running Ubuntu 8.10 using your instructions. Thank you!

Feedback:
I would possibly add one update to your instructions though. Step 9) describes using Compiz, which was not installed by default on my system, which you might mention in your instructions, that it might need to be installed. I had to install it before I could proceed. That said, it's a pretty cool tool. Thanks for introducing me to it too. 

The only thing left for me to fix now is that the touchpad/mouse/pen/eraser do not rotate. Almost there.

Cheers!
Steve

---

### Post by Favux on 2008-12-16
Hi DrakeGis and Tekrytor,

DrakeGis,

You're right, touch isn't as sensitive as on Vista.  That's one of the reasons I moved to 0.8.2, especially when I saw the stuff about wacomcpl.  But if improved touch is in there I haven't figured it out.

Tekrytor,

> The only thing left for me to fix now is that the touchpad/mouse/pen/eraser do not rotate.
That's what my rotation HOW TO is for.  The scripts are not just suppose to rotate the screen, they are suppose to rotate stylus, eraser, touch, etc..  That's what I mean by working rotation.  So something is not right.  Which method (script) are you using?  Please post your xorg.conf.

I'm still not sure if TX2500 owners with the ATI video chipset can use Compiz with Xorg's "radeon" driver (right now I'm thinking they can't).  I know they can with flgrx, but it doesn't allow rotation.  So I feel I can't just tell folks to install it.  If Compiz works with "radeon" I could add that.  Someone please let me know.

If you don't have Compiz installed then you have metacity, and it's my understanding the keybinding commands on metacity are essentially the same.  Since I haven't used them I'd appreciate input on how to.

So I'm clear.  You are able to use Compiz with "radeon" as your video driver?  Do you know if this is the latest "radeon" driver?


Talk to you soon.

---

### Post by Favux on 2008-12-16
Hi DrakeGis,

If the touchscreen on the TX2000 and TX2500 is capacitive, which I believe it is, I have touchscreen calibration.

 The xsetwacom parameter "Capacity   integer (1 -5)" sets the touch sensitivity level for capacitive touch device (default is 3 for capacitive tools, -1 for none capacitve tools).  Add it to your /home/username/.xinitrc like so:
```
xsetwacom set touch bottomy "3969"
xsetwacom set touch bottomx "4028"
xsetwacom set touch topy "215"
xsetwacom set touch topx "140"
xsetwacom set touch Capacity "1"
etc. . .
```
I just tried the numbers between 1 and 5, restarting X in between.  Not quite as much variation as I would have expected, but 1 seems the most sensitive.

Give it a try and let me know.

---

### Post by DrakeGis on 2008-12-17
Thanks again for your help !!!! I'm flying tomorrow, so probably I will try to do some testing with the touch calibration, while bored at the airport (Actually, I want to play Battle for Wesnoth with my finger :D ). 

I do have some questions:
 
1) Where did you get the numbers (for bottomy,bottomx, topy and topx) ? from wacdump ?

2) I can't get xev return a value for the "Q" key. BUT, I don't originally have a "keyboard" section in my /etc/X11/xorg.conf. 

3) I had some problem with the ATI drivers, when reproducing video the are where the video is reproduced 'flash' or 'blink' (I'm not sure how to decribe this). Has anyone found a similar problem ? Because of that I guess I'm running radeon drivers (how can I verify this ? Again no information in xorg.conf ) . I any case I'm not running Compiz, so where/how can I specify the link between the key value (once I have one) and the command-to-run (I see that System->Preferences->Keyboard Shortcuts allows me to edit setting but no to add )

4) If I'm reading correctly the xorg.conf file specify the same event for stylus and for eraser. Can you set up the eraser (the back of the stylus) to trigger a right-click and the stylus to trigger a left-click and activate the rotation script with the button of the stylus ? 

  

> **Favux said:**
> Hi DrakeGis,

If the touchscreen on the TX2000 and TX2500 is capacitive, which I believe it is, I have touchscreen calibration.

 The xsetwacom parameter "Capacity   integer (1 -5)" sets the touch sensitivity level for capacitive touch device (default is 3 for capacitive tools, -1 for none capacitve tools).  Add it to your /home/username/.xinitrc like so:
```
xsetwacom set touch bottomy "3969"
xsetwacom set touch bottomx "4028"
xsetwacom set touch topy "215"
xsetwacom set touch topx "140"
xsetwacom set touch Capacity "1"
etc. . .
```
I just tried the numbers between 1 and 5, restarting X in between.  Not quite as much variation as I would have expected, but 1 seems the most sensitive.

Give it a try and let me know.

---

### Post by Favux on 2008-12-18
Hi DrakeGis,

No the numbers were in /home/user name/.xinitrc where I was telling you to add "xsetwacom set touch Capacity "1"" to the touch section.  They should have been generated when you did the wacomcpl part of gali98's tutorial.  I just included them so you could see what the touch section looked like and where to put Capacity.

Did you see the addendum in the Rotation HOW TO where I talked about activating the keys?  This is the xorg.conf keyboard section for a TX2500:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection
```
You could just add this to your xorg.conf and reboot.

If in System>Administration>Hardware Drivers you don't have the ATI proprietary driver activated then you're running on Xorg's "radeon".  Also the video section in xorg.conf would have "fglrx" in it (the proprietary ATI driver).  If you're not running Compiz then you should be running metacity.  I think you can do the same keybinding stuff with it, and like Compiz metacity's editor would be in System>Preferences.  But since I'm not using it I'm not sure.

As to the rescripting/redirecting of the stylus etc., I don't know.  I never thought to try that.

---

### Post by Favux on 2008-12-25
Hi,

I thought I'd add another rotation script.  Might be useful to those with other types of tablet pc's.
```
# Simple rotation script

if [ -f /tmp/rotated ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate none
        xsetwacom set "touch" Rotate none
        xsetwacom set "eraser" Rotate none
        rm -f /tmp/rotated && exit 0
else
        xrandr -o right
        xsetwacom set "stylus" Rotate CW
        xsetwacom set "touch" Rotate CW
        xsetwacom set "eraser" Rotate CW
        echo 1 > /tmp/rotated && exit 0
fi
```

Also stuck it on as an attachment.

---

### Post by Docaltmed on 2008-12-31
Hi Favux (and anyone else who wants to chip in),

I've almost gotten the rotate thing working, with one problem. After rotation, although the stylus behaves appropriately, it is about 2 cm off. 

I tried to calibrate it with the screen rotated, but the lower right calibration box is off of the actual screen.

And application windows, when maximized, also flow off the screen.

So it appears that when rotation occurs, something isn't recognizing the the new screen dimensions.

I'm running a clean Kubuntu installation, 8.10, on an HP TX2510us. I'm using the same xorg.conf file that I was using previously in Ubuntu 8.10, which worked correctly.

I am using XRandR to rotate the screen, and the daemon to rotate the stylus. I'm attaching my xorg.conf file, in case that is of help to anyone.

Thanks for everyone's help. This is the last stage in what has turned out to be an interminably long conversion process (but then again, aren't they always?)

---

### Post by Favux on 2008-12-31
Hi Docaltmed,

I'm not sure what the poblem is.  You could run more of your stuff through HAL, commenting it out in xorg.conf.

Adding "radeon" to your video section instead of "ati" might be worth trying to fix the rotation problem.  I'm going to attach a TX2500 xorg.conf.  Compare it to your current xorg.conf side-by-side in a text editor.  Maybe you'll spot something.

For future reference I have xorg.conf's attached to the bottom of the rotation HOW TO.

---

### Post by Favux on 2009-01-01
Hi Docaltmed,

I thought I'd mention KDE does not use Compiz-Fusion like Ubuntu/Gnome does.  It uses kwin it's own aiglx/compositing tool integrated into it's window manager.  This may be part of your problem.

ATI on 12-31-08 released a bunch more 3-D driver stuff to open source.  Hopefully this will make for rapid advancement of Xorg's "radeon" drivers.  Also I've seen folks mention a "radeonhd" and "radeonhd-c" driver for r5xx and r6xx chipsets.  I'm not sure that applies to you, but it's worth checking out.

---

### Post by Favux on 2009-01-14
Hi everybody,

Since gali98 hasn't updated his tutorial in two months I took the liberty of posting my "version" with the latest Linux Wacom Drivers.  If there are errors please let me know (and be kind).  It's at:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

---

### Post by yurtboy on 2009-01-21
latitude radeon driver working well.
i used the xrand command from the first post.
i will try the scripts later.
thanks!

cellwriter is nice....

---

### Post by Favux on 2009-01-21
Hi yurtboy,

Good!  If one of the scripts or Tom Jaeger's wacomrotate work for you could you please post back.  I would greatly appreciate it.

Is that a Dell latitude with multitouch?  A N-trig digitizer?

---

### Post by yurtboy on 2009-01-24
Here is the script that is working well.
```

#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "st$

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) $

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
#    -rotate to the left
    xrandr -o left
    xsetwacom set stylus rotate CCW
    xsetwacom set touch rotate CCW
    xsetwacom set eraser rotate CCW
    ;;
    left)
#    -rotate to inverted
    xrandr -o inverted
    xsetwacom set stylus rotate HALF
    xsetwacom set touch rotate HALF
    xsetwacom set eraser rotate HALF
    ;;
    inverted)
#    -rotate to the right
    xrandr -o right
    xsetwacom set stylus rotate  CW
    xsetwacom set touch rotate CW
    xsetwacom set eraser rotate CW
    ;;
    right)
#    -rotate to normal
    xrandr -o normal
    xsetwacom set stylus rotate NONE
    xsetwacom set touch rotate NONE
    xsetwacom set eraser rotate NONE
    ;;
esac

```

I did nothing to alter it and it works fine.

I did have a question thought, I do not see a screen calibration tool.  I tried wacomcpl but that just gives me a control panel to change some settings not a place to calibrate the pen to the screen. The reason I ask is cause when I wake from suspend the point is usually off by an inch or so and worse as you get to the top of the screen. I noticed others had this problem too.
Thanks again for all your work making the script.

---

### Post by Favux on 2009-01-24
Hi yurtboy,

Great!  You're the first non-HP user to post back that that script works for you.  Thank you!  You have a Dell Latitude XT, correct?

As to calibration.  It sounds like your stylus is working through HAL (hardware abstraction layer).  There is a .fdi file somewhere controlling your stylus.  I stopped trying to learn how to edit .fdi files when it became clear that HAL would only offer stylus and not the rest of my tablet features.

The quick and dirty way I use to recognize that HAL is running things is that my side-switch doesn't work.  It doesn't act as a right mouse click.  Also when I type "wacomcpl" in a terminal and the gui pops up "stylus", "eraser", and "touch" are absent on the left.  I can't click on them to highlight them and so the calibration, screen mapping and other settings don't pop up.

To figure out what's going on I need some more information.  How did you install the LinuxWacom kernel driver (which tutorial did you follow)?  Is your Tablet PC usb or serial?  What tablet features do you have, eg. "sylus", side-switch, "eraser", and "touch"?  I probably need to see your xorg.conf.  Could you please attach it to your next post.

---

### Post by yurtboy on 2009-01-24
Hello,
I started here
[http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77](http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77)
It it got the tablet to do touch but no rotate.
When I came to this thread i realized I could not use the ati driver but the radeon if I wanted to rotate.
Now that I got the script (the one posted above) to work things seem a bit better but.
1. As noted no calibrate option
2. When I shift into the rotate mode the pen works okay but it is Xournal for example scrolls endlessly if I go beyond a certain point from the right of the screen. Like if I could draw an imaginary line down the middle of the screen when I am in vertical mode, the right works great and the left does funny things like not write but scroll.
But I can draw fine on the right side of the screen so for now I figured that was good enough ( -:
3. When I am in horizonal mode the pen is off by 2-4 inches and basically of no use.
4. Lastly (other then the dream of making the touch screen work) waking from suspend seems to leave the pen off by 2-4 inches in either mode.

I am using intrepid
the xorg is attached
and on the link above the wacom is
[http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb](http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb)
I got it from this secion
> Update: Starting 2008-11-14, the integrated N_Trig touch screen works partially. That is, I can use the stylus to move the cursor and for left- (tapping) right- (the larger button on the stylus), and middle-click (the smaller button on the style), but direct finger touch does not work right now. (K)Ubuntu 8.10 already includes kernel 2.6.27 which supports the N-Trig USB device with HID events. Using the xserver-xorg-input-wacom package, the cursor can already be moved, although quite erratically. To make it usable, get the patch linuxwacom-0.8.1-3.ntrig_hack.patch from here. It applies cleanly to the Kubuntu 8.10 wacom-tools package version 0.8.1.4-0ubuntu3. I suggest to get it using "apt-get source wacom-tools", apply that patch, update the package version to something akin to a NMU release, recompile and install the new driver. Alternatively (if you trust me and my security measures for this page), you can just install my patched and pre-compiled version for x86-32 and x84-64. Note that the wacom-tools binary utilities package doesn't need to be patched (the standard Ubuntu package works).

---

### Post by Favux on 2009-01-24
Hi yurtboy,

That was helpful.  Basically N-trig needs a patch to the linuxwacom driver.  So far the patch you have only works on an older linuxwacom driver.  Bugs in that driver have been fixed in the newer versions.  But we can't do anything about that because the patch doesn't work on them.

But it looks like we can do some stuff with the xorg.conf before we get into the more complicated driver questions.

First what I did is reorganize and clean up your xorg.conf.  This is somewhat arbitrary.  I'm trying to get it as close to the Xorg's default format as I understand it, and it also helps me visualize it better.

Next I turned off compiz.  It isn't clear to me how well the "radeon" driver supports Compiz, so it's a complication we can eliminate.  Be sure to turn off any Compiz theme you have enabled!  This may help with Xournal.

The "ServerFlags" section is probably unnecessary.  Back when HAL was first introduced some people thought it and xorg.conf would conflict.  Since it turned out they didn't I hope we can lose it.

Next I turned off, commented out, your mouse and touchpad section.  This is because HAL (hardware abstraction layer), introduced with Intrepid, should be able to run them.  Also us TX2000 users had a problem where X confused "Touchpad" with "touch".  So we renamed "Touchpad" "Pad" to get around it.  By commenting out "Touchpad" we get the same thing.  Since your mouse is different from mine I'm not entirely confident it will work through HAL.  But it should.

Your Wacom "InputDevice" sections look like they have some problems.  Let's save that for the next iteration of xorg.conf.

So back up your xorg.conf!  I suggest you compare this xorg.conf to yours and study the changes and also make sure I didn't make an obvious goof.  And if you're brave try this edited xorg.conf!

Good luck!

---

### Post by yurtboy on 2009-01-25
So far the Xournal does work better.
The left side seems to have more response!
Thanks!
Do you think it is worth trying to build that patch against the newer wacom?

Other notes
1. Suspend still leaves pen out of alignment
2. compiz is off

I had a nokia n800 for a bit, wonder what they use.

---

### Post by Favux on 2009-01-25
Hi yurtboy,

Good, we're making some progress!  Keep Compiz off for now.

The suspend causing misalignment may be due to not having a .xinitrc file.  X doesn't restart when you come out of suspend, does it?  See right now your calibrations are all in xorg.conf, and if you're loosing them during suspend they would only be reapplied after an X server restart.  I'm not sure how suspend works, so I don't know for sure if a .xinitrc file would be kept or reapplied.  So does wacomcpl work for you yet?  Hopefully the patch is not blocking wacomcpl in wacom-tools.  Maybe the next edited version of your xorg.conf below will let you use wacomcpl.

You used his deb, right?  The problem is we don't know exactly what he compiled on what.  Or maybe you do.  Xorg warns against using a wacom-tools that isn't the same version as the wacom driver.  They say it can crash X!

If the patch works on a later version I would say go for it.  Wacom-tools 0.8.1-4 has known bugs that the later versions, like 0.8.1-6, fixed (currently on 0.8.2-2).  Unfortunately he says the patch is for kernels before 2.6.27.  But Intrepid comes with 2.6.27.  Then he says whichever version of 2.6.27 he's using, which he doesn't specify(!), now partially supports N-trig HID!  So I am very confused.  I think Intrepid is currently on 2.6.27-9 and I'm using 2.6.27-11.  Back when he posted it was 2.6.27-7!  What I'm saying is you may not even need the patch anymore.  The newer kernels may have more N-trig support built in.  What I'd like to do is see if the Linux Wacom Project says anything about N-trig support.  In it's change-logs or something.  So don't do anything about recompiling now, but maybe start researching the question.

Now on to the new xorg.conf.  What I did was remove lines from the "InputDevices" sections that I don't think should apply to a usb tablet.  But since it's N-trig, I can't be sure.  The lines are:
```
#	Option "Mode" "Absolute"
#	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
```
Also notice that stylus and eraser have the same input so eraser shouldn't need the calibration lines.  By the way have you enabled eraser in Gimp or Inkscape?  Does it work?
```
#	Option "TopX" "0"
#	Option "TopY" "0"
#	Option "BottomX" "9600"
#	Option "BottomY" "7200"
```
Does touch work right?  I ask because it has the same calibrations as the stylus.  On my TX2000 they aren't even close!

According to his xorg.conf I think I'm counting four buttons.  Really?  You have four buttons on the stylus?

Like I thought you don't seem to need the ServerFlags section so I deleted it.

I want to point out that you could comment out the keyboard section and let HAL run that too.  But HAL breaks single key key bindings.  So if you have a bezel button we can get a key code on we could bind it to your rotation script.  Do you want a rotation button?  If so leave the keyboard active.

As before back up your xorg.conf and proceed at your own risk.  Good luck!

---

### Post by Favux on 2009-01-27
Hi yurtboy,

At the LWP's bulletin board/forum on 7/30/08 Rafi Rubin volunteered to add N-trig code to the LWP's drivers.  He had some sample code and seemed to think it would be relatively simple.  He asked if there was any interest in supporting a non-wacom tablet.  Ultimately he wanted to support multi-touch.

There wasn't any follow-up I could see.  But that doesn't necessarily mean anything.  They could have continued the discussion over private channels.

So if there is more support in the kernel (honestly I don't know how to determine that exactly) so far as I can tell there may be more support through LWP too.

---

### Post by yurtboy on 2009-01-27
Okay here are the results

1. I put in the new xorg file and restarted X. All seems to be working still (though I have yet to gotten scroll to work on the mouse maybe it is not there?)

2. Touch worked fine though, Xournal seemed less sensative on the top left side so that was good, more testing later.

3. I then tried to remove the wacom deb I downloaded (noted in previous message) and use the one in the ubuntu repositories. I did this rebooted and the pen did not create and action. I could click on things and watch the X or button sink in but no reponse. Like File --> Save but I would click File in the menu and it would not open.
Oh well, went back to the other one and it works again.
aptitude remove xserver-xorg-input-wacom
Went back to
xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb

4. Touch (finger) does not work yet

I did look on the threads and wrote that person back about the n-trig.
I wanted to know how to install those patches?
Or do I need to build (which would be fine is someone told which packages)


5. Attached is what I have always seen with wacomcpl
I guess what I meant before is there are no real calibration tools from what I was use to w say a Nokia n800 ie X marks on the screen to poke at to calibrate.

Alright getting closer.
Thanks!

---

### Post by Favux on 2009-01-27
Hi yurtboy,

1. I think lack of scroll in the mouse and mouse jitters were two of the bugs in 0.8.1.4.  Do you mean trackpad mouse?

2. When you say touch worked what do you mean?  By touch I mean the touch screen recognized my finger or fingernail.

3. OK, stuck with the patched deb of 0.8.1.4.  LinuxWacom is up to version 0.8.2-2 currently.

4a. Touch (finger) doesn't work.  So in 2. you're talking about the touchpad, right?  And the "mouse" associated with it?

4b. I hope he contacts you.  We need to know more.

5.  Above tracking in the blank spot is suppose to be the calibration button/tab.  Since wacomcpl is showing stylus and eraser but not touch it looks like touch data is not being sent to Xinput.  If you get a reaction at all to your finger does the pointer do something weird like immediately head to the right corner of the screen?  We might want to comment out the "touch" section of your xorg.conf at some point if touch isn't working.  If it isn't working why not?  Also it would let us see, if by removing touch as an input (remember you have to remove it in server layout too), it is interfering with calibration for the stylus.  But remember touch has the same calibration as stylus.  That wouldn't be true in a Wacom tablet, so maybe the coordinates for touch are just way off?

The fact there is no calibration for the stylus for wacomcpl implies the patch isn't perfect.  You could manually experiment with the settings on stylus in xorg.conf.  Bit of a pain to be constantly restarting X.

What would be nice is if you'd just be a able to configure the linuxwacom kernel driver 0.8.2-2 and it would work for you.  This seems unlikely at this point.  Other than Rafi Rubin's two posts I haven't seen anything on the LWP's site re N-trig.  All the folks claiming a working tablet seem to be getting their drivers from the same place you are.

---

### Post by Docaltmed on 2009-01-28
Here's a TX2500 data point for anyone who can make use of it. I can't.

I tried for several weeks to get the calibration right when rotating the screen using the rotate daemon. And although the screen would rotate properly, and the touch and stylus functions would also rotate their behavior appropriately, both touch and stylus had a gradually increasing calibration offset moving from the left of the screen to the right. The offset increased to the right. Wacomcpl calibration was of no help, as the right lower crosshairs were off the screen in portrait mode. Messing about with xorg.conf was of no help, although it did produce some spectacularly dysfunctional results from time to time.

Tonight, on a wild hair, I used one of the scripts that Favux demonstrated in his tutorial, and voila! Perfect calibration.

I have no idea why one method would work and the other does not, but I thought the information might help you guys with the binary brain cells.

And, by the way, thanks to all of you who help the rest of us out. I hope to be able to contribute my share one of these days.

---

### Post by adamsu on 2009-02-06
I have gotten rotation to work on a tx2500 in Intrepid using the newest ATI driver, which can be downloaded [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-9-1-x86.x86_64.run"). Installation is easy, just run the script as sudo in a terminal and follow the directions. After restarting, the scripts from the first post (or at least the first script, that's the one I use) work for rotating the screen as long as it is not composited. I use compiz, so I just switch to metacity using the compiz icon (fusion-icon) in the dock when I want to rotate, then switch back to compiz when the screen is returned to the normal position. This is a small compromise to get everything working!

---

### Post by Favux on 2009-02-06
Hi adamsu,

Good job!  Thanks for posting.  Don't give up on the compositing, ATI has released a bunch of new stuff to open source.  If "fglrx" doesn't support it soon (with rotation) "radeon" might.  And the Compiz developers have got their act together now, so improvements in Compiz are coming.

---

### Post by zikook on 2009-02-10
hi adamsu,
I've tried the latest ATI drivers but I see there's still no rotation support. 
running this command with ATI's drivers (this command works with the open source driver)-
xrandr -o inverted
I get the following output-
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
Which is consistent with the previous version of the ATI driver.
Can you tell me what output you get?
Can you post your 'fglrxinfo' output?
Thanks,
-Aharon

---

### Post by GrooveTherapy on 2009-02-12
Hi all

I'm running intrepid on my TX2000, stylus (minus the eraser) with pressure sensitivity and touchscreen both work. 

I've managed to bind the rotate script to the 'Q' LED button, however the Q and DVD buttons only work when the screen is lifted up.  I've tried the omke script that microsol linked to on his howto page (located as #7 here: [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)) but it doesn't allow the buttons to work in tablet mode.  Has there been any progress on this?

---

### Post by Favux on 2009-02-12
Hi GrooveTherapy,

Glad you have pretty much everything working.

Right now I have my "Q" button set to Tom Jaeger's wacomrotate daemon and script.  The "Q" button works fine with the screen locked down in tablet mode.  As does the DVD button.  When I was using one of the rotation scripts it also worked.  Have you checked your bezel buttons while in tablet mode in Windows?

Regarding your eraser questions please see post #8 and the posts around it at the beginning of this thread.  And in Xournal the side-switch should be the eraser.

---

### Post by GrooveTherapy on 2009-02-12
Hi Favux

I tried Toms script (I had to use the i386 package) and added the -f and -t lines to the command in System->Preferences->Session and restarted X, but no luck.  The Q and DVD buttons are recognized by xev, but only when the lid is up.  These two buttons don't work for me in windows (even when they are up) but I always thought this was because I did not have the proper drivers for them (I reformatted the factory vista settings the day I bought my tx2000)  The rotate and 'gears' button work for me in windows, even while in tablet mode.  

I have the side switcher working as the eraser (it is programmable through Options->Button 3 mapping in Xournal) but the eraser is not...it defaults to the pen instead.  It sounds like you're saying that the eraser input is detected, its just applications like xournal aren't programmed to do anything useful with it.  Am I reading this correctly?

---

### Post by Favux on 2009-02-12
Hi GrooveTherapy,

Your right about Xournal.

> The rotate and 'gears' button work for me in windows
We can't get them to work in linux, can't detect a signal.

It sounds like a hardware failure with the DVD and Q buttons.  If your lucky it might be firmware, since it's positional in linux.  Have you updated your bios?  Check the HP site and see if there are bezel button drivers.  It's been a while since I went there.  I just use HP update, which seems to miss things like bios updates.  Otherwise I hope you're still under warranty.

Edit:  On Tom's daemon, the new version doesn't use the -f and -t switches.

---

### Post by GrooveTherapy on 2009-02-12
Hey Favux

I just tried the bios update and now the buttons work in tablet mode!  This tx2000 is the first computer I've ever bought with my own money and I've been extremely diligent about taking care of it, so I'm glad nothing on it is broken!  I assumed anything that didn't work in vista was due to the reformat...With the working DVD button, I plan to write a script that will turn off the LCD display (to save battery life while in lectures)

Between the working tablet/keys and xournal, I can finally use linux for the classroom.  Thanks for the great guide!

---

### Post by Favux on 2009-02-12
Hi GrooveTherapy,

Great!  Nice work.

Thanks for the thanks.

If you get the script up and running please share.

---

### Post by GrooveTherapy on 2009-02-17
Hey all


The command: 

```

xset dpms force off

```

Will turn off the display.  Any input will turn it back on.  I find this useful for lectures, so those who use their tablet for taking notes like I do might appreciate it.  If the prof steps out of the room or does anything not worthy of writing down for an extended period, this button will save you the 6-8 watts required to run the display.  All you need to do is bind it to a button, which you should be able to do in the same way Favux explains in the first post.  For some reason though, gconf-editor wouldn't let me do it :confused:  I'd rename the DVD key in .Xmodmap, xev would recognize it, but every time I bound any command to it in gconf-editor, it wouldn't execute.

I've had problems with gconf in hardy as well, so if anyone else is having problems, here's an alternative method for keybinding:

In terminal, run:
```

sudo apt-get install xbindkeys && apt-get install xbindkeys-config

xbindkeys --defaults > ~/.xbindkeysrc

```

Run xbindkeys-config to get to the GUI.  A few default commands should be listed.  If there are none, try loading the .xbindkeyrc file created above by going file -> open default file.  From here, select 'New' to create a new keybinding.  In the 'Key' field, hit 'Get Key' and press the key you want to bind the action to.  In action, simply type the action or path to the script you want to run, such as ~/.rotation.sh or xset dpms force off.  Hit apply/save apply and exit, then your new key should be ready.

These setting disable after restarting X, so one last thing is required: to start xbindkeys at login.  To do this, go system->preferences->sessions.  Click 'Add' and under name type 'Start xbindkeys at login' or whatever you prefer.  Under command, simply type 'xbindkeys'  Restart X by hitting ctrl alt del, login, and see if your key binding is still enabled.

---

### Post by cak3 on 2009-02-20
First of all, thanks, this was really helpful and allowed me to nuke vista (though ironically I "replaced" it with a small xp install in virtualbox). Everything seems to be working (though I miss compositing...*sniffle*), but I am having the same issue groove had (the 'Q' button does not work when the screen is in tablet mode). Xev detects nothing from it then. I would just use the same solution, but I have a tx2500z, and I can't find a bios update for it.

Any ideas?

---

### Post by Favux on 2009-02-20
Hi cak3,

The HP site should have bios upgrades if you go to support drivers and downloads and put in your exact model number.  If that doesn't work did you check out the Key code Addendum at the bottom of the Rotation HOW TO?

---

### Post by cak3 on 2009-02-21
My exact model is the TX2500z, and unfortunately HP has no bios downloads available for it on the site ([http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&os=2093&product=3744020&](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&os=2093&product=3744020&))

I did use the key-code thing, thats how I got it working initiall. The 'Q' button works just fine, rotates and everything, when the screen is up, but it does nothing when it is in tablet mode.

xev detects nothing from the button (or the DVD button) when the machine is in tablet mode, and both work fine and are detected fine when the laptop is up. They worked fine in vista (though I dont have it any more) so I don't think its a hardware issue, but i suppose it could be, given that it has beem a bit since I used them in vista.

---

### Post by Favux on 2009-02-21
Hi cak3,

If you still have Vista installed you should boot into it and check it out, see if the bezel keys are working.  If they are position sensitive in Vista also it would seem to suggest to me some sort of hardware problem.  If they work ok and you have the latest bios I don't know what else to tell you.  They updated the bios for the TX2000 like 3 to 5 times, but there hasn't been a new update in months.

---

### Post by martinjochimsen on 2009-02-21
Hi there

I finally got the "Q"-key to rotate the screen. I did it with xbindkey-config. But when I reboot the "Q"-key, the computer, the program have forgotten the command to rotate. Does enyone know how I can make it work after a reboot?

By the way Favux. Did you know there is a rotation-script in /etc/acpi? It rotates the screen 90 degrees clockwise and back again.

I also got suspend and hibernate to work. Take a look at this thread:
[http://ubuntuforums.org/showpost.php?p=5220536&postcount=19](http://ubuntuforums.org/showpost.php?p=5220536&postcount=19)


```
Create the following file: sudo nano /etc/pm/sleep.d/25i8042

Code:

#!/bin/bash

case "$1" in
	hibernate|suspend)
		# Unbind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
		fi
		;;
	thaw|resume) 
		# Rebind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
		fi
		;;
	*)
		;;
esac

exit $?

Make sure this file is executable. There is no need to reboot your computer - your next suspend should work.
```

and finally the mics in the screen are working. I made a clean install of the system (8.10) yesterday and after all the updates I just for fun tried the Sound Recorder.....and the mics recorded - but I don't now why. They also work in fx Skype I just had to change some of the preferences for the ingoing sound.

Martin :-)

---

### Post by martinjochimsen on 2009-02-21
To answer myself...

How to get the "Q"-key to remember the action in xbindkeys-config after a reboot.
Go to System->Preferences->Sessions
Make a new action fx. Xbindkeys
add the command: /usr/bin/xbindkeys
save and exit.

Now the "Q"-key should remember what it is told!!! :-D

Martin :-)
tx2590oe

EDIT:
DUH!!!
I just read GrooveTherapy's post #59
He (she?) must be a GENIUS!!! :-D
Well I can then confirm it worked for me as well.

---

### Post by Favux on 2009-02-21
Hi martin,

Good couple of posts.  I thought GrooveTherapy's screen dimming was clever.  Hopefully between you and GrooveTherapy TX2500 users with problems can get their Q key working using xbindkeys.  When did you folks start running into Q key problems?  Was it a kernel update?  Do I need to update the HOW TO?

Good news about the mikes, somewhere in there updates must have fixed it?

Early on I think I remember reading in a wiki or a thread about the included rotatescreen.sh.  Was it for one of the early Thinkpad tablets?  The X40 or 41?  Anyway since I didn't have a screen-rotation in /var/lib/acpi-support, it didn't seem to apply.  Especially since acpi_listen doesn't pick up anything from our hinge or rotation button.  Thanks for reminding me about it, I had forgotten it was there!

---

### Post by GrooveTherapy on 2009-02-22
For sound, check out this thread: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Or go straight to the quick guide here:
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

That was able to get my sound issues ironed out (before, multithreaded playback and recording didn't work, now both do :D)



For TX2500 users, I'm not sure.  My TX2000 hardware buttons didn't work in tablet mode until I ran the BIOS update.  Enter your bios settings and see if there are any settings for it (press F2 during the phoenix splash screen at startup)  I don't have a lot of confidence in this producing any useful results though.

My advice would be to contact HP and ask them about it.  You could ask them if running the TX2000 bios update would help - I believe the only major hardware difference between the TX2000 and 2500 is the switch from the NVidia Geforce 6150 mobile to the ATI 3200 HD mobile.  So hopefully, if that doesn't have too much bearing on the motherboard design, the bios update could work.  My sister got the TX2500, so if I can talk her into installing ubuntu, I'll actually have a system to play around with and I might be able to find a fix.

---

### Post by martinjochimsen on 2009-02-22
Speaking about BIOS updates.
I'v got the tx2590eo with BIOS version F.05. Somewhere around I read, that there should be a F.08 or even a F.09 version for the tx2500 model. Does anybody now anything about that - maybe a link??? I can't find any link or anything.
Anybody...?

Martin :-)

---

### Post by cak3 on 2009-02-22
Well, I did not fix my problem with the 'Q' key, but I have some more info on the problem. It seems that, after pressing the button above the touchpad (to disable the touchpad) the 'Q' and 'DVD' keys cease to work, but that, upon pressing that button again (reenableing the touchpad) the screen rotates (and the 'Q' and 'DVD' buttons work again). So, it would seem that when the button to disable the touchpad is pressed, it takes the keycode of the 'Q' key.

Weird.

I am not sure what could cause this... it could be hardware, or some bizarre phenomenon with how linux is handling the keys. I don't have a windows install on the laptop now, so until I put one on and test it, I am just going to stick with a launcher and ordinary keyboard command to rotate screen. I'll post whatever I find out after testing it in windows.

Also, @martin : As far as I know, it would be here ([http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=3758333&lc=en&cc=us&dlc=en&lang=en&cc=us&submit=Go%20%BB](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=3758333&lc=en&cc=us&dlc=en&lang=en&cc=us&submit=Go%20%BB)) but I suspect you already looked there and, as in the case with mine, I dont see any bios updates there.

---

### Post by martinjochimsen on 2009-02-22
Thanks for the link cak3, but I'v seen it already, and there is no BIOS upgrade for my model. Does everybody else on this forum who's got a tx2500 model have BIOS ver. F.05?

Sounds weird whit the button above the touchpad. My "Q"-button works fine when that button is pushed, and it still works after the touchpad has been enabled again. I'm afraid I can't help you there.

Question:
I'm using xbindkeys to let the "Q"-button flip the screen, and it also works after a reboot - thanks to Groovetherapy. My problem is, that it doesn't work after suspend or hibernate. What can I do to make it work?

Martin :-)

---

### Post by Favux on 2009-02-22
Hi,

On my TX2000 I have bios v. F.08 which is the latest.  Released in May of '08.

> **by cak3**
It seems that, after pressing the button above the touchpad (to disable the touchpad) the 'Q' and 'DVD' keys cease to work, but that, upon pressing that button again (reenableing the touchpad) the screen rotates (and the 'Q' and 'DVD' buttons work again). So, it would seem that when the button to disable the touchpad is pressed, it takes the keycode of the 'Q' key.
Now that is interesting.  Could that imply our bottom bezel buttons and swivel hinge also go through the same "drivers" as the Synaptic Touchpad?  And our problem with them is that we have an idiosyncratic version of Synaptic Touchpad that Ubuntu doesn't support.  Through HAL's .fdi files or whatever?

Martin, I think there's a file or script that runs after suspend/hibernate to reconfigure the system.  I can't remember it's name or where it is, but I have seen people edit it to make sure something restarts.  Also I found this in a serial tablet user's xorg.conf:
```
Section "Module"
	Load		"wacom"
EndSection
```
Located above the beginning of the Wacom entries.  I'm wondering if this would do the same thing as your "fix" with nano to /etc/modules?  Are you in the mood to experiment?

---

### Post by MisteR2 on 2009-02-23
Hey everyone. Just wanted to chime in and say I've just had the same thing happen to my tx2500z that cak3 had happen to his with respect to the mousepad disable button. Everytime it reconnected (push to disable, push again to re-enable/reconnect) it would flip the screen. 

I wonder, if in Vista it disables the touchpad when in tablet mode (would make sense) and re-enables it when in laptop mode.

I'll take a look in Vista and see if I can trace what does what at some point (probably not today).

Later all.

---

### Post by GrooveTherapy on 2009-02-23
Hey MisteR2

Are you running hardy?  I had the same problem before I upgraded to intrepid

---

### Post by cak3 on 2009-02-24
Ok, so I reinstalled vista (enterprise, actually, since I have a liscence for it from MSDNAA), and the 'Q' and 'DVD' buttons function properly (even when the laptop is in tablet form or when the touchpad is disabled, the two things that caused problems in linux). So it would seem that it is a driver or related issue more than hardware.

And, I am running intrepid, so that that can't be the problem.

---

### Post by Favux on 2009-02-24
Hi cak3,

It feels like we're teetering on the brink of a "breakthrough" in understanding some of this stuff.  I'm just not bright enough to get it.  So now I'm wondering if this has something to do with the laptop "hotkey-setup" program.  It's v. 0.1-23 in Intrepid.  And with a default install the hotkeys daemon isn't running.

---

### Post by martinjochimsen on 2009-02-24
Hi Favux

It didn't work with
```
Section "Module"
	Load		"wacom"
EndSection
```
in xorg.conf

But it was a good idea.
I put it in here
```
# Removed HAL comments to enable single key key bindings.
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "dk"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Synaptics Pad"
#       Driver          "synaptics"
#       Option          "SendCoreEvents"  "true"
#       Option          "Device"        "/dev/psaux"
#       Option          "Protocol"      "auto-dev"
#       Option          "HorizEdgeScroll"  "0"
#EndSection

#Section "Module"
#       Load            "wacom"
#EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
        Option          "Type"          "stylus"
.
.
.
snip
```

---

### Post by Favux on 2009-02-24
Oops!  Dbl. post.  Sorry!

---

### Post by Favux on 2009-02-24
Hi martin,

Right, exactly the right place.  And of course it wasn't commented out ;)  Oh well, why make it easy?  Thanks for trying it out!

Edit:  Script(s) in /etc/acpi/  like resume.sh and then /resume.d and /suspend.d .

---

### Post by martinjochimsen on 2009-02-24
Of course no "comments"!

:-D

---

### Post by cak3 on 2009-02-24
I don't have any more information regarding the keys or anything, but I just ordered a SSD I got a killer deal on from newegg, and am planning to replace my lappy's HDD with it and then try out Jaunty Alpha 5 (should be out on the 26th) on it, so I will see if a fresh install and/or changes in jaunty affect it (assuming I dont have too many problems with the alpha).

Since im going to do a fresh install anyway, would you reccomend doing anything or experimenting with the laptop hotkeys package? 

though, come to think of it, that package might be updated for jaunty -- Ill have to look into it.

EDIT:

Just did a bit more messing around. When the touchpad is enabled, pressing the button above it to disable it has a keycode of 200, but pressing it again to re-enable it has a keycode of 201, the same the the 'Q' button had. I say "had" because now it seems that the Q and DVD buttons are not recognized at all by the event manager whether or not the touchpad is enabled. The only change I can think of that might have affect this was uncommenting the Synaptics stuff in my xorg.conf (to see if it changed anything). Undid that, and nothing changed, so that wasn't it.

---

### Post by Favux on 2009-02-24
Hi cak3,

> pressing it again to re-enable it has a keycode of 201, the same the the 'Q' button had
Weird.  Mine is 201 and it was 205 in Hardy before it disappeared with Intrepid.  Did you run the Key code Addendum at the bottom of the HOW TO?

I'm assuming the "hotkey-setup" program will be a different version in Jaunty.  I thought it was a version change that disabled my Q key in Intrepid.

The SSD sounds very kewl.  And I think we're all very interested in Jaunty.  Especially with the new version of X breaking the video drivers and all.  What does it do to linuxwacom?  They say they've updated 0.8.2-2 to support it.  I guess you'll find out.  Should be exciting!

---

### Post by cak3 on 2009-02-25
Yea, thats how I got the buttons working initially (using the addendum). Ill try running it again to see if it will get them working at all again, I could have reset that with all the messing around I did.

---

### Post by MisteR2 on 2009-02-26
Hey everyone. 

To answer a previous question, yes I'm running Intrepid.

Jumped back into vista not too long ago. Tried a few USB sniffing programs, SniffUSB seemed to work best ( for free at least :) ). Nothing on the log when sniffing wacom for the button activity. I tried to get it to sniff the keyboard, but for some reason it was saying the USB HID item was disconnected...

Aside from that I took a look at the keyboard driver. Apparently it's set up with support for quick keys. And in Device Manager where it normally gives information about USB manufacturer and model numbers, I saw something that looked like the keyboard had some ACPI stuff hooked into it (pnp0303?).

Maybe if someone can dig around in the windows keyboard driver specific to this model that may provide some clues (I can't at this time due to other obligations).

That's what I've got for now.

Later all!

---

### Post by Favux on 2009-02-26
Hi MisteR2,

Thanks for keeping us posted.  Sounds like a good first pass.

---

### Post by MisteR2 on 2009-02-28
Hello again.

Sooooo.. started playing with i8042 debug mode (apparently the chip that all keyboard presses pass through) and got activity from dvd and media key, none from the rotate or gear key.

So now I'm going down the acpi path, using acpidump and related tools, with no idea how to use them. :)

I'll let you all know if anything else pops up.

Lat.

----------------------------------

EDIT:

After digging around in the ACPI dumps, there is a Tablet LID Switch Event. Found button presses for brightness, etc. but nothing directly pointing to the other two buttons that currently don't work.


2nd EDIT:

Started checking into /proc/interrupts. The count for acpi increases when laid into tablet mode, but it doesn't increase when buttons are pressed. Not discouraging, but doesn't help on the button issue. Also, does anyone here know how to add another ACPI event? (for the tablet switch)

3rd EDIT:

Anyone know about keycode 465? Highest one I could find, and may explain something.

---

### Post by Favux on 2009-02-28
Hi MisteR2,

The keycode 465 is paired to e001 in "/var/run/hotkey-setup".  The next two highest are e008 387 and e00e 389.  You're right, that's interesting.  Two other hotkey-setup files are "/usr/share/hotkey-setup/hp-tablet.hk" and "/etc/init.d/hotkey-setup".

As previously mentioned I've checked xev and acpi_listen and looked in "/var/log/messages".  I also installed "discover" and looked with that.

Two commands:
```
lspci -v -nn
```
may want to put "sudo" in front of lspci, and:
```
lsusb -v
```

I want to emphasize that just because I couldn't find anything doesn't mean it isn't there.  I could have been looking right at the critical info and not recognized it!

Good work.  I do not know how to add another acpi event.  Keep looking!

---

### Post by MisteR2 on 2009-03-03
Took a bit deeper of a look recently. Something called Windows Management Instrumentation. There's a kernel module for it's support (WMI), but I don't know if the module has support for the buttons we have. It's description up on MS's website [Link]("http://www.microsoft.com/whdc/system/pnppwr/wmi/wmi-acpi.mspx") fits what the button does in vista. 

Lat.

EDIT:

Module called hp-wmi. Modprobed it and nothing so far.

EDIT2:

Okay. Decompiled the DSDT for this computer. The screen swivel signal is definitely sent through WMI, The regular lid switch has no reference to WMI. This is where I say things need to be pushed further. At this point do we file a bug or ...?

EDIT3:

A possible starting point may be the TC1100 WMI driver included in the kernel. Only problem is it doesn't show up in the menuconfig for the kernel because it appears to be restricted to x86.

---

### Post by Favux on 2009-03-03
Hey MisteR2,

Great thread on the TC1100 by phenest and Aearenda:

[http://ubuntuforums.org/showthread.php?t=563736&highlight=tc1100]("http://ubuntuforums.org/showthread.php?t=563736&highlight=tc1100")

As far as I know they use a rotation script bound to a button also.  No automagic rotation.  They do have some code that gives them all their buttons.

---

### Post by Favux on 2009-03-09
Hi MisteR2,

I was wondering if this makes any sense to you.  In the Side Buttons section (i.e. the bezel buttons) of this link:
[http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000]("http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000")
Is another link to quickstart the ACPI Direct Application Launch driver for Linux:
[http://quickstart.sourceforge.net/]("http://quickstart.sourceforge.net/")

---

### Post by MisteR2 on 2009-03-15
Hey everyone. Sorry about the absence. School stuff has been ramping up lately. :)

Anyways, Favux, thanks for the links. The quickstart application would be useful, for booting into different distros, say hit the DVD or quickstart button (backwards rotating circle) to boot into netbook remix or whatever you feel like. It actually deals with another ACPI "feature" introduced by Vista, known in ACPI-land as PNP0C32. 

Unfortunately, the buttons and hinge switch we have deal with PNP0C14.

But the quickstart app may be a more reliable way of reading button events. I still have issues of the quickstart button I use going out after the computer is put to sleep (I had bound it to a rotation script).

I'll look into it.

Also, I'm still looking into making a request for help to get the switches into the hp-wmi module. if anyone has any ideas on who to contact about that it would be greatly appreciated!

Lat.

---

### Post by Favux on 2009-03-15
Hi MisteR2,

No problem re the links.  Thanks for elucidating quickstart, I still haven't had a chance to look it over.  I don't know how to go about getting someone to look at the hp-wmi module for us.  It is probably to late for Jaunty.  Actually a quick and dirty way to get attention might be posting in the Jaunty testing thread.  That might be abusing the thread a little, but if you worded it right?  They probably want things like that posted on Ubuntu Brainstorm.

---

### Post by MisteR2 on 2009-03-17
I'll give brainstorm a shot. I'm not too worried about the needed changes making it into Jaunty. Personally I don't have too much of a problem playing with things outside of major releases (my desktop still runs gentoo :) ).

I will admit it would be nice if the debug kernels were a bit more accessible. Last I checked they still didn't have one for 2.6.27-11.

Lat.

EDIT: Bug's up. [https://bugs.launchpad.net/bugs/344141](https://bugs.launchpad.net/bugs/344141)

---

### Post by adamsu on 2009-03-18
Zihook,
Sorry for not replying sooner, it has been a while since I have been on the forums. I actually saw your post because I reinstalled my system and then ran into the same error you describe when trying to rotate. So I retraced my steps, and found the answer. 
After installing the new driver, you need to run the command *sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"*, then logout.
After that, rotation works for me as long as the screen is not composited.
Hope this helps!
adamsu

---

### Post by Favux on 2009-03-24
Hi MisteR2,

Matthew Garett is listed as the HP-WMI module author on the module info dump that Leann Ogasawara did on your bug report.

He's active on the linux kernel lists and the kernel bug tracker.  On this link he directly supplies a HP-WMI patch to a user reporting a key related bug:

[http://bugzilla.kernel.org/show_bug.cgi?id=11424]("http://bugzilla.kernel.org/show_bug.cgi?id=11424")

---

### Post by Trevski13 on 2009-04-06
Hey, I was wondering what exactly is happening with the commands for getting the Q/DVD buttons to work (the hotkey-setup) it works... but I'm not quite getting what it's doing to fix it.

---

### Post by Favux on 2009-04-06
Hi Trevski13,

That's my question.  Gali98 says it resets the keymap.  Maybe you can give me a sanity check.  I don't know where you're starting from so forgive me if I get too basic.

Basically we're dealing with the initialization scripts in init.d.  So rc refers to run command which have multiple run levels with I think 2 being the Ubuntu default.  Now update-rc.d is a Debian utility.  So to learn more about it:
```
man update-rc.d
```
and  [http://wiki.linuxquestions.org/wiki/Update-rc.d](http://wiki.linuxquestions.org/wiki/Update-rc.d)

as an aside in Intrepid they added:
```
sudo service hotkey-setup restart
```
which means the same thing as:
```
sudo /etc/init.d/hotkey-setup restart
```
So we are removing and installing a System-V style init script link (ok really Upstart) with hotkey-setup.  With the -f forcing removal of the symlink.  Some more background:  [http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html](http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html)

But what is the "99 1 2 3 4 5 6 ."?  That's our question, correct?  I don't follow it from the man page and googling doesn't give anything.  I see some code with 99 followed by some numbers (not the same ones) but no context I can follow.  I assume it's modifying hotkey-setup somehow.

A couple more links, but not so relevant.
[https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch)  -see method 2
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

If you figure it out I would appreciate you letting me know!

Edit:  Oh wait a minute.  The 99 is the order to start the daemon?  And 99 presumably is after every other daemon.  And then run the daemon on levels 1 through 6 (Upstart's pseudo runlevels)?  And the . is just part of the syntax, in case you want to follow it by another commmand?  Hmmm.

---

### Post by Favux on 2009-04-07
Hi everyone and Trevski13 and Mark,

I think this is how the story goes.  With Intrepid the new evdev input driver in X.Org 1.5 generated X keycodes that were different from Ubuntu 8.04 LTS (Hardy) and before.  This resulted in non-functioning hotkeys, because keybindings (through a ~/.Xmodmap file or whatever) were no longer valid.  My "Q" key keycode changed from 205 in Hardy to 201 in Intrepid.

This also meant that the previous keymap symlinks of hotkey-setup in the initization scripts of init.d were not valid.  This may be why xev wouldn't work for some keys where it had previously worked.  Now why were those previous symlinks present?  I don't know.  I upgraded, so that could explain it in my case.  A failure of the upgrade process to reconfigure the symlinks.

What the commands:
```
sudo update-rc.d -f hotkey-setup remove
sudo update-rc.d hotkey-setup start 99 1 2 3 4 5 6 .
```
are doing is first stopping the hotkey-setup service/daemon.  It has to be stopped to modify it.  The "-f" is forcing the removal of the old, erroneous symlinks.  The hotkey-setup daemon is restarted making new appropriate symlinks.  The:
```
99 1 2 3 4 5 6 .
```
starts the service (after allowing 98 other daemons to start) and applies it to run levels 1-6.  Which makes sense, because we're dealing with basic hardware that we want working on every run level.  And presto keys work again and xev can now detect the keycodes it couldn't before.  The DVD key and the new 201 keycode I had for the "Q" key in Intepid weren't detected by xev until I ran the "update-rc.d" commands and reset my symlinks.

I'd appreciate feedback.  Am I on the right track here?

Mark, if I have this right, it should probably work for you too.  I'm still waiting for gali98 to get back on it.

---

### Post by Trevski13 on 2009-04-08
ok, so it makes perfect sense that the 99 is the start position. the run levels make sense too (although any clue why 6 is needed? I honestly don't understand the details of the run levels so that may be simple... so let me break this down and see if I've got this right...

If we take the code
```
sudo update-rc.d -f hotkey-setup remove
sudo update-rc.d hotkey-setup start 99 1 2 3 4 5 6 .
```
and break it down, we first have:
```
update-rc.d -f
```
this is our command says we want to update a run command (and that we want to force it). 
then we have:
```
hotkey-setup
```
which indicates the daemon/run command(?) we wish to modify, 
and this is followed by:
```
remove
```
which is the option for our command, stating we'd like to remove said daemon/run command
first line done wooo!
what have we done? removed hotkey-setup from the run commands.

we then have:
```
update-rc.d
```
this is our update command again but this time no forcing

```
hotkey-setup
```
once again we are modifying the hotkey-setup

```
start
```
here we have an option but now it's to start the daemon/run command, 
for which we are then given the parameter:
```
99
```
which is the position in the execution order the daemon/run command is to be placed(?), 
this is followed by:
```
1 2 3 4 5 6
```
which are the run levels the daemon is allowed on, 
and FINALLY we have:
```
.
```
which... does... something........ or rather *doesn't* do *anything*, except, of course, make the command happy ^_^
what have we done? we've (re-)added the hotkey-setup daemon to the run commands in position 99 and on run levels 1-6...

So... all in all... all we've done is modified (I assume, since we don't know the original parameters) the daemon to run 99th and on levels 1-6...

My question is this... how does doing *that* allow me to use my media keys... if anyone has an answer for me I'd love to hear it.

sorry if I went a little over-board with the "CODE" tags :D

And one last thing, if you or anyone else knows the original parameters (aka what I can use to put it back to how it was (media keys not working)) for the hotkey-setup daemon, I'd love to know what those are.

P.S. although we don't seem to be at that point yet, I, unfortunately, am unable to try/test much out on my laptop at the moment, I...er... killed the graphics (and the touch screen and rotation along with it)... somehow... so most of my attention is on fixing that. hopefully won't take long to fix, but just thought I'd mention it.

P.P.S. never mind, got the video fixed :D

---

### Post by Favux on 2009-04-08
Hi Trevski13,

I don't think you quite have it.  We are pretty deep in the boot process.  The key thing is the -f and everything else is window dressing.  If you look at:
```
ls -l /etc/rc2.d
```
You see the symlinks between /etc/rc2.d and /etc/init.d/.  Note the S infront.  S(start), K(kill).  And the numbers.  Looks like I was wrong and hotkey-setup is 99 just because that's it's assigned number.  But in that listing you'll see the symlink:
> S99hotkey-setup -> ../init.d/hotkey-setup

So what we have to do is stop the hotkey-setup service/daemon so we can modify it.  The modification we are making is breaking the symlink, -f, and then we are restarting the hotkey-setup daemon.  Which apparently reforges a new corrected symlink.  Don't ask me how, I assume that's some other initialization script tool.

So presumably there was a /etc/init.d/hotkey-setup with Hardy and then a new hotkey-setup in /etc/init.d/ with Intrepid.

Another way to look at the services would be using a CLI utility sysv-rc-conf.  A gui front-end would be "bum", Bootup-Manager.

Another point is that the SystemVinit daemon and run levels don't really exist anymore.  In Feisty they started deprecating it in favor of Upstart.  This was to allow more modern stuff like hotplugging (shades of HAL).  So Upstart is impersonating  SystemVinit.  Upstart also emulates the runlevels.

Anyway that's my current best guess.

---

### Post by Trevski13 on 2009-04-08
alright, I get it. (in an, I-get-it-but-I-don't, kind of way](*,)) The boot process for the Linux kernel is somewhat of a dark corner for me, as are things like run levels and such doo-dads Lol. Now don't get me wrong, I'm sure I'll come to understand it as I troubleshoot problems. But that is neither here nor there. Anyway, at least now I understand enough to know that it won't get me where I want to go :cry: oh well... 

Totally random do you know if anyone (besides myself) has come up with the solution for the touchpad on/off button on the tx2000 indefinitely launching gnome help? I saw some people complain about it, but never saw a solution, so if no one has, I'll make a post telling how to fix it ^_^

---

### Post by Favux on 2009-04-08
Hi Trevski13,

That sounds worthwhile.  I've never had that problem before, but then I almost never turn off the touchpad.  I haven't seen a solution posted that I can remember.

---

### Post by cak3 on 2009-04-13
> **Favux said:**
> **a TX2500 Tablet PC, and other Tablet PC's**

This doesn't apply to you with ATI proprietary "fglrx" through Catalyst.  After configuring your card as usual you may need to type the following command into a terminal:
```
aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
```
I'm not sure if you need to use sudo.
This applies to Catalyst drivers 8.9 and later and is from:  [http://wiki.cchtml.com/index.php/Features#Screen_Rotation]("http://wiki.cchtml.com/index.php/Features#Screen_Rotation")
*Thank you farmercyst and Vincent_Lin and adamsu for pointing this out.


* Thank you to martinjochimsen and manu7irl for helping to validating methods 1 & 2 for the TX2500.

Thanks for that. A couple notes -- it does need to be run as root, so you can modify it to have sudo. 

The fglrx drivers in Jaunty's repos are new enough that this will work, you dont need to compile them yourself. In fact, I think that jaunty's fglrx (8.600) is newer than the drivers on ati's page, they include the unrealeased Catalyst 9.4.

---

### Post by Favux on 2009-04-13
Hi cak3,

Thank you for the information.  I'll modify the HOW TO.

---

### Post by MisteR2 on 2009-05-01
So... progress has been made on the tablet swivel front. Been talking to Matthew Garrett (HP-WMI author) and apparently the tablet swivel was sharing the signal with the docking function. Thanks to him, there is now a seperate signal for the tablet swivel switch. I'm still trying to get it to work through hal (which is a beast of a thing to try to learn).

I'll should be able to post up a patch for hp-wmi.c soon. I'll put up a makefile so all you will compile is the module itself. One thing though. You'll need 2.6.30-rc kernel source to do this. I got mine from [http://kernel.ubuntu.com/~kernel-ppa/](http://kernel.ubuntu.com/~kernel-ppa/) and was able to apply the patch.
The makefile I'll post up later should build against 2.6.28 headers. I'll also post up the fdi that I'm playing with.

Later all.

---

### Post by Favux on 2009-05-01
Hi MisteR2,

Great!  Outstanding work.  Glad you got in touch with Matthew.  So Jaunty will have automagic rotation!

Will this get are two non-functioning bezel buttons working also?  And would the modified module work for other HP tablets, like the TC4200?

---

### Post by MisteR2 on 2009-05-01
I haven't gotten any response from the bezel buttons yet. As to whether it will work for the TCs, I'm not sure. ill this get are two non-functioning bezel buttons working also? And would the modified module work for other HP tablets, like the TC4200? Not sure. Worth a shot though.

Alrighty then. Here we go. 

**REMEMBER!!** Apply the attached patch to 2.6.30-rc sourced hp-wmi. I used 2.6.30-rc2. 

The makefile here uses the headers for your current kernel. This is something intended to be used in a separate directory ie, /home/whoever/blah. Just take it and stick it into a text file in the same directory as your hp-wmi.c and call it Makefile.

```

obj-m := hp-wmi.o
 all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

```

Now the fun part. The FDI file. I have killed way to much time trying to track this information down. :) And I'm not even sure if it works yet.

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.udi" contains="/org/freedesktop/Hal/devices/computer_logicaldev_input_3">
	<append key="input.switch" type="strlist">0x05:TABLET_MODE</append>
    </match>
  </device>
</deviceinfo>

```

Make sure you have input-utils, so you can see if your hal device may be something different.

Using input-event(s?) shows that the tablet swivel is a switch. Although in some fdi files, I've seen switches, such as the regular tablet lid switch referred to as a button. 

That should be about everything. If I've forgotten anything, I'll be back.

Later.

---

### Post by Favux on 2009-05-02
Hi MisteR2.

In Device Manager I do have an "unknown button".  Unfortunately Device Manager won't let me copy out some key lines.  But basically it refers to keyboard, input.keys, and button.  And the sysfs_path refers to PNP0A08:00.  But it does not contain input.switch.

So even if I apply the patch to 2.6.30-rc sourced hp-wmi I can build against the 2.6.28 headers and use the resulting patched HP-WMI module in Jaunty?

What are the chances of doing the same against 2.6.27 headers in Intrepid and using it in Intrepid?  Slim to none?  And of course the same question in Hardy, which I think was 2.6.24.

Thank you very much for the .fdi.  I know getting that together wasn't trivial.  And if you get a chance thank Matthew for us.

---

### Post by Favux on 2009-05-08
Hi everyone,

fr34k4d3113 has a Asus R1E tablet pc.  He modified the method 1 script and put it into gnomes 'startup applications' to automatically change the wacom-rotation when he rotates the display.  I thought I would share it:
```
#!/bin/sh 

while [ 1 ]
 do
  sleep 2
  rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

  case "$rotation" in 
    normal) 
### rotate to the normal ###
    if [ `cat /home/user/.rotate/rotatestatus` = "right" ]; then
      compiz &
      xsetwacom set stylus rotate NONE 
      xsetwacom set eraser rotate NONE
      echo "normal" > /home/user/.rotate/rotatestatus
    fi
    ;; 
    right) 
### rotate to right ###
    if [ `cat /home/user/.rotate/rotatestatus` = "normal" ]; then
      xsetwacom set stylus rotate CW 
      xsetwacom set eraser rotate CW
      echo "right" > /home/user/.rotate/rotatestatus
    fi
    ;; 
  esac
 done
```
It turns out he is one of the lucky few.  His Asus tablet works with the "rotatescreen.sh" in "/etc/acpi".  So he then went on to rewrite "rotatescreen.sh" to also rotate his wacom devices:
```
#!/bin/sh

user="yourusername"

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/scredrittelen-rotation`
fi

case "$ROTATION" in
        right)
        NEW_ROTATION="normal"
        ;;
        *)
        NEW_ROTATION="right"
        ;;
esac
echo $NEW_ROTATION

for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXconsole;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum.0"
        fi
        /usr/bin/xrandr -o $NEW_ROTATION
        echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation

        if [ $NEW_ROTATION = "normal" ]; then
            xsetwacom set stylus rotate none
            xsetwacom set eraser rotate none
            su $user -c "compiz &"
        fi
        if [ $NEW_ROTATION = "right" ]; then
            xsetwacom set stylus rotate CW
            xsetwacom set eraser rotate CW
            su $user -c "metacity --replace &"
        fi
done
```
As you can see he also had a problem with Compiz on rotation.  So he put in the script the change to metacity on rotation.

Enjoy.

---

### Post by cak3 on 2009-05-11
MisteR2 (or anybody who has figured it out):

Would it be possible to clarify the process needed to get it all working? I mean, I can patch the file and run the makefile, but as far as I can tell that doesn't get me anywhere.

Thanks

EDIT: Basically, I need to know 2 things. Do I need to run the makefile with only that patched file in the directory, or with the entire extracted contents of the directory, and also, once run, where do I find and then put the .fdi

---

### Post by MisteR2 on 2009-05-17
The way it worked for me was with hp-wmi.c in the same directory as the makefile. For me it was /home/*username*/hp-wmi that I did my work in.

The .fdi file should go in /usr/share/hal/fdi/policy/20thirdparty or something along those lines. The /usr/share/hal i'm positive about.

By the way, I should be able to devote some more time to this now that I've graduated from SMU. (WooHoo!)

Lat.

---

### Post by Midnight_Sun on 2009-05-21
Dear All,

I'm quite new to Ubuntu, but I was brave, and bought a TX2z, and try to run Ubuntu on it. First test was Jaunty - for the sake of ext4 - but with that kernel the activation of wacom was impossible.
Now I'm back to Intrepid 8.10.
With the help of 
[http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)
I was able to activate stylus. (many THX!)
FGLRX up and running, Compiz effects turned off. Use Mayerhoffer patched package and a the xorg.conf of Favux. (as far as I remember.)  

All is fine in normal mode, stylus is ok and calibrated, button works.

Tried the rotation script, and there came the problem.
If I rotate the screen, the stylus gets crazy, as far as I can tell in portraz mode top right movement becomes something like bottom left or bottom right direction, so it's a pain.

Tried to change CV to CCV in the script, no joy.
Tried to edit xorg.conf to add topx topy bottomx bottomy to stylus, but the only effect was that the default state became also worse.

I'm getting lost in messing around, and I don't want to destroy the the results - even they were hard to get for me...

Please, if You can, give me some direction!

THX!

---

### Post by Midnight_Sun on 2009-05-21
oh!

Forgot to post my xorg.conf... sorry.

Here it goes:

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen "Default Screen"
        InputDevice    "Trackpad"
        InputDevice    "stylus"
# I've commented out the eraser because it either doesn't exist or doesn't work
#        InputDevice    "eraser"  # "SendCoreEvents"
        InputDevice    "touch"
EndSection                                 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Load	"dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "InputDevice"
	Identifier  "Trackpad"
	Driver      "synaptics"
	Option	"Device" "/dev/input/by-path/platform-i8042-serio-1-event-mouse"
EndSection

Section "InputDevice"
	Driver "wacom"
        Option "Mode" "Absolute"
        Identifier "touch"
	Option "Touch" "on"
        Option "Type" "touch"
 	Option "ForceDevice" "ISDV4"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#        Option "USB" "on"
	Option "TopX" "225"
	Option "TopY" "225"
	Option "BottomX" "26300"
	Option "BottomY" "16375"
	Option "DebugLevel" "8"
 	Option "Button1" "1"
 	Option "Button10" "1"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "stylus"
        Option "Mode" "Absolute"
        Option "Type" "stylus"
 	Option "ForceDevice" "ISDV4"
 	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
 	Option "TPCButton" "on"
        Option "USB" "on"
        Option "Button2" "3"
#        Option "Button3" "core key alt F2"
#	Option		"TopX"		"225"
#	Option		"TopY"		"225"
#	Option		"BottomX"	"26300"
#	Option		"BottomY"	"16375"

EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option "Mode" "Absolute"
	Option "Type" "eraser"
	Option "ForceDevice" "ISDV4"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
 	Option "TPCButton" "on"
	Option "USB" "on"
	Option "Button1" "2"
EndSection

---

### Post by Favux on 2009-05-21
Hi Midnight_Sun,

Did you do the "aticonfig" command from appendix 1 on the HOW TO up front?

---

### Post by cak3 on 2009-05-21
> **MisteR2 said:**
> The way it worked for me was with hp-wmi.c in the same directory as the makefile. For me it was /home/*username*/hp-wmi that I did my work in.

The .fdi file should go in /usr/share/hal/fdi/policy/20thirdparty or something along those lines. The /usr/share/hal i'm positive about.

By the way, I should be able to devote some more time to this now that I've graduated from SMU. (WooHoo!)

Lat.

Thanks. Got the module, but its still in not working (x event viewer sees nothing). Is there a specific name I have to give the .fdi? ALso, how would I go about using input-utils to figure out the correct device or whatever.

Thanks.

---

### Post by Midnight_Sun on 2009-05-22
Yes I did.

Besides I've tried out Method 3 with the Tom Jaeger deb installed. Still no joy... :-(

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun, 	

Try commenting out:
```
#Section "Module"
#Load "glx"
#Load "dri"
#EndSection

```
And see if it behaves on a reboot.  I hope you don't need "dri".  Otherwise what does:
```
xsetwacom list
```
and
```
xinput --list
```
look like.

---

### Post by Midnight_Sun on 2009-05-22
thx, givin a try.

xinput --list
```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Trackpad"	id=2	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"stylus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 11
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"touch"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 11
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 225
		Max_value is 26300
		Resolution is 0
	Axis 1 :
		Min_value is 225
		Max_value is 16375
		Resolution is 0
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 1b96:0001"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 11
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Video Bus"	id=9	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

xsetwacom is not yet installed. Gee! Missed something?

---

### Post by Midnight_Sun on 2009-05-22
Commented out. No change.

Try to install wacomtools.

---

### Post by Midnight_Sun on 2009-05-22
Oh My!  What an as* I am!

Installed wacomtools and works like a charm!

Thanks a lot Favux! Life saver! :-)

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun,

Excellent!  Nice work.

Say would you be interested in optimizing your xorg.conf?  So far no TX2z user has stuck with it more than one test or so.  I think we may be able to improve it some.

---

### Post by Midnight_Sun on 2009-05-22
Cool!

Open to everything!

Let's give it a go!

(Basically I now quite few about xorg, but will try to learn...)

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun,

Great!  First test in a few minutes.

---

### Post by Midnight_Sun on 2009-05-22
ok. 

Till then: kezbindings work to a custom key of my choice, it's nice!

The official rotate key is dead for xev, but that's what You were talkin about...

I add some Compiy efects and will see what happens with rotation.

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun,

Basically have the test xorg.conf done.  But I want to back off and read the stuff I did with xorg.conf on the TX2z thread.  Make sure I'm not missing anything.  So I'll post it tomorrow.

Meantime have fun.

---

### Post by Midnight_Sun on 2009-05-22
ok.

I'll wait.

Besides: in portray mode the stylus is miscalibreted some 10 millimeters, but i'll review the thread since it has been some solution for that.

cheers!

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun,

Good deal.  I'll see you later.

Say just to make sure I'm remembering correctly the TX2z doesn't have an eraser does it?  I checked it out in a store and I didn't see one on the display unit.  The eraser is a eraser-shaped button on the top of the stylus that retracts into the barrel of the stylus when depressed.

Also do you need help with backup and editing commands for xorg.conf or do you have that handled?

---

### Post by Midnight_Sun on 2009-05-22
You remember well. TX2z has no eraser.
Backup and editing is no problem.

I will have some hectic dazs, but await Your ideas, and test them as quickly as possible...

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun,

I appreciate you helping lock down an xorg.conf for the TX2z.

So we are on the same page you are using the patched linuxwacom 0.8.1-4 amd-64.deb that Rene Mayrhofer provides?

Although it might look like I made a lot of changes I actually haven't.  I added the header and rearranged things.  I deleted the eraser stuff.  I indented the lines I'm sure of.  There shouldn't be much risk of X breakage with this.  But be sure to back up your current xorg.conf and be prepared to restore it.

Now onto the changes:
1)  In Intrepid HAL with the Synaptic .fdi file should be able to handle your trackpad so I commented it out.  Let's find out for sure.
2)  The stylus section is usually considered the more important one so I made it first and put the coordinates in it.  Let's see if that works.
3)  None of these seems to contribute anything so I commented them out:
```
#Option "DebugLevel" "8"
#Option "Button1" "1"
#Option "Button10" "1"
```
You're not debugging, Button1 1 should be default, and I don't know what Button10 1 is.

Give it a shot.  Good luck!

---

### Post by Midnight_Sun on 2009-05-22
Hi!

Test went quite ok. X still alive.
Touchpad is working nicely, but the stylus is miscalibrated some 15cm-s (!) top lett direction in all views. (moving direction is ok, movement is consequent, but the pointer is far from the stylus.) Rotation still ok with keybinding.

Ideas?

---

### Post by Midnight_Sun on 2009-05-22
Hi!

Test went quite ok. X still alive.
Touchpad is working nicely, but the stylus is miscalibrated some 15cm-s (!) top lett direction in all views. (moving direction is ok, movement is consequent, but the pointer is far from the stylus.) Rotation still ok with keybinding.

Ideas?

---

### Post by Favux on 2009-05-22
Hi Midnight_Sun,

Oops!  Try substituting in glurgle's calibration first:
```
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
```

If that doesn't work try commenting out (#) the four lines with the coordinates.  And if that doesn't work try moving them back to touch.

---

### Post by Midnight_Sun on 2009-05-23
So, I've corrected the numbers, and things got better.
 It is still a bit miscalibrated, but far less than before.
The funny is, that the pointer gets more and more correct when I move towards the top left corner, and less and less accurate in bottom right direction.
Rotation still ok.

---

### Post by Favux on 2009-05-23
Hi Midnight_Sun,

Alright!  This next step should also be low risk.  Try commenting out in stylus and touch sections:
```
Option "ForceDevice" "ISDV4"
```
like so:
```
#Option "ForceDevice" "ISDV4"
```
This line is for serial tablets and I don't think it is doing anything.  Keeper of the Keys and I think someone else said things still worked with it removed.

When we get finished with xorg.conf we should be able to improve your calibration and make it spot on.

---

### Post by Midnight_Sun on 2009-05-24
Cool!

Commented out, and still alive.
Stylus quite well calibrated!  Completely usable!

Besides: IÍve forgot to mention: touch is absolutely not working ever since. (Not since the last change, but since the beginning, but I've did not pay much attention to it.)

---

### Post by Favux on 2009-05-24
Hi Midnight_Sun,

Good deal.

So your saying that touch went out with the test 1 xorg.conf?  Not sure why but I have a few ideas.  Rather than backtracking let's keep going.  Maybe we can get it back.

Again these should be low risk.  But we're starting to get into the uncertain area.  This line should be default:
```
Option "Mode" "Absolute"
```
in both the stylus and touch sections.  As should this line in stylus:
```
Option "TPCButton" "on"
```
So let's comment them out also.  If that works...

Now we get into the exciting area of real breakage risk!

---

### Post by Midnight_Sun on 2009-05-24
Seriously miscalibrated (nearly a whole screen) but still works ok.

---

### Post by Favux on 2009-05-24
Hi Midnight_Sun,

Interesting, that shouldn't have happened.  Let's ignore it for now and forge on.

So now real risk of breakage.  In the touch section remove the comment from:
```
# Option "USB" "on"
```
to
```
Option "USB" "on"
```
and comment out:
```
Option "Touch" "on"
```
to
```
#Option "Touch" "on"
```

My fingers are crossed.

---

### Post by Midnight_Sun on 2009-05-24
:-)
You've crossed well.
NOTHING had happened. Not a single change... (besides I'm available under Skype or Gtalk if YOu find that better. More speedy I think...)

---

### Post by sha.goyjo on 2009-05-24
Okay, Mister2, I've followed your advice....cept what do I do with the files the make command created? I patched the 2.6.30 hp-wmi.c with your patch, then used your makefile....I just don't know what to do with it now.

EDIT:

I apologize. I just had to do a search to find where the original hp-wmi.ko was located, then switch them out.

---

### Post by Midnight_Sun on 2009-05-24
And an other thing - might be of interest. People were looking for the possible keykodes of the sidebuttons beside the screen of tx2z. 
The buttons do not give a sign under xev, but if You use the remote control thingy, the middle "wave" formed button gives the following keykode:

```
KeyRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x9d, subw 0x0, time 1296358, (358,203), root:(368,300),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by Favux on 2009-05-24
Hi Midnight_Sun,

OK, now for the penultimate.  The heart of the mystery.  Breakage City here we come.

Why in "ServerLayout" isn't stylus and touch followed by "SendCoreEvents"?  In other words is the patch really able to use the linuxwacom drivers through xorg.conf?  Or is it of necessity some very idiosyncratic kludge?

Here we go.  Fingers and toes crossed now.

---

### Post by sha.goyjo on 2009-05-24
next question. what should I name the fdi file?

EDIT: Also, I have the same problem as favux with regard to the output of input-events. This is what I get

```

/dev/input/event3
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

```

---

### Post by Midnight_Sun on 2009-05-24
Wonders, wonders! :-)
Things are workin, Stylus far awaz but ok, touch still disabled.
All other things equal.

---

### Post by Favux on 2009-05-24
Hi Midnight_Sun,

Wow! :p  Let's see what happens when you try to use wacomcpl.  Go to Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  In wacomcpl is stylus and touch present?  Can you calibrate them?  How about the stylus button?  It'll be button 2.  To make it a right mouse click it should say button 3.  2 would be middle click.

---

### Post by Favux on 2009-05-25
Hi Midnight_Sun,

Before trying wacomcpl see how this xorg.conf works for you.  Is touch working now?

---

### Post by Midnight_Sun on 2009-05-25
Works fine. Correct calibration. Like a charm.
Let's see wacomcpl.

---

### Post by Midnight_Sun on 2009-05-25
Well, the data are correct regarding the stylus in wacomcpl. The only funny thing is that there are to touch devices with the same name. Quite consequently touch is still not working.
Should I change something for the stylus? (It is quite ok now...)

---

### Post by Favux on 2009-05-25
Hi Midnight_Sun,

Interesting.  Wacomcpl shows you two instances of touch under stylus?  My tablet uses two usb paths, one for the stylus and the other for touch.  But yours, since it is a N-trig instead of a Wacom, uses only one path.  So let's see what happens if you change in "ServerLayout":
```
	InputDevice	"touch"		"SendCoreEvents"
```
to
```
#	InputDevice	"touch"		"SendCoreEvents"
```
In other words comment touch out.

---

### Post by Midnight_Sun on 2009-05-25
Ok. I'll comment it out.

Yet an other funny experience:
Stylus is working correctly in Cellwriter, but after suspend it gets strongly misplaced.
Seems like something refuses to start egain after suspend.
Quite annoying.

---

### Post by Midnight_Sun on 2009-05-25
Commented out.
No touch sensitivity and no touch in wacomcpl. 
(This is not a too big problem for me, since touch annoys me while using stylus, but anyway, let's keep on testing. At the and We will see.)

On the other hand: Were You able to figure out a way to get Compiz effects and wacom rotation working at the same time? (or if not, do You have an idea to turn Compiz on and off simlpy from the command line?)
THX

---

### Post by Favux on 2009-05-25
Hi Midnight_Sun,

So instead of touch present twice in wacomcpl now there is no touch at all.  Try the attached xorg.conf and let me know if touch is back in wacomcpl and if it works.  I'm beginning to think the guy who came up with the xorg.conf that let's touch work was an (evil) genius.

There is a Compiz switch (Compiz Icon) you can install from Synaptics that can turn it off and on.  On post #108 page 11 of this thread fr34k4d3113 has a rotation script that turns Compiz off on rotation and back on when unrotated.  So it is doable.  So I took a stab at it and have attached the script below.

Loosing calibration after suspend means that the .xinitrc isn't reapplied or rerun at the end of suspend.  You can make a launcher to rerun the .xinitrc after a suspend where you loose calibration.  Just tell the launcher to run .xinitrc.

Some folks have various scripts they run before entering a program, say Gimp.  They apply the changes they find convenient in Gimp before starting it and then rerun .xinitrc after they exit Gimp.

We can try adding something to get it to run automatically after suspend later.

Edit:  Fixed the xorg.conf.  Please try the new test 5.
Edit 2:  Hopefully fixed the rotation script, please try and let me know.  Oh, and I forgot to mention that for the TX2z you may need to delete or comment out the two "xsetwacom set eraser rotate etc." lines.  I left it the general case so any ATI (ie the TX2500) can use it too.  It depends on if Xorg complains, which it might.

---

### Post by Midnight_Sun on 2009-05-26
Hi there,

Thanks for the script, I'll check it.
Problem: xorg made my system crash.
Anyway I think it's just a syntax problem.

While bootup it said:

> Parse error on line 59... "OPTION" is not a valid keyword in this section

So if You can correct it, we will give a try again...

---

### Post by sha.goyjo on 2009-05-26
I'm only asking because for those of us who aren't used to messing with .fdi files by hand the procedure is confusing. If not completely impenetrable. But that doesn't mean we don't want to help with the dev process by attempting the procedure and finding errors on different system configurations.

---

### Post by cak3 on 2009-05-31
> **sha.goyjo said:**
> I'm only asking because for those of us who aren't used to messing with .fdi files by hand the procedure is confusing. If not completely impenetrable. But that doesn't mean we don't want to help with the dev process by attempting the procedure and finding errors on different system configurations.

I second this motion. I got the hp-wmi.ko module patched and compiled, and I found out where the original was and replaced it, like sha.goyjo. I inserted the .fdi file, but I think that I probably need to know what to name it, as xev is certainly not seeing anything when I rotate the screen. 

If the .fdi file name isn't the problem, then I still need help... I am kind of lost here. I kinda knew what I was doing when I was futzing around with the xorg.conf, but I have no idea how hal or this .fdi stuff works...

---

### Post by cak3 on 2009-06-06
anyone?

---

### Post by Midnight_Sun on 2009-06-24
Hi there!

Long no seen. Sorry for the silence, but was elswhere engaged.
So. I've tried the script of Favux with Compiz deactivation, but I'm stuck.
Metacity is in itself a problem, since after metacity --replace things go well for 30 seconds, and then the window dorders start disappearing and all is unresponsive. 
What to do with this?
I'm not up to using meaticty at all, but I don't know a way to replace - or more better simply deactivate - compiz from the command line. In normal alignment Compiz and wacom work like charm.
Any ideas?

Besides: still up to testing xorg if it's needed!
cheers!

---

### Post by Favux on 2009-06-24
Hi Midnight_Sun,

Good to hear from you again.

Sorry to here about problems with the rotation script.  I'm not sure what's going wrong.  Metacity is the default windows manager for gnome.  When you deactivate Compiz it has to be replaced with Metacity.  You can deactivate Compiz with the Compiz-fusion icon in Synaptics.  So I don't understand why Metacity in portrait mode isn't working for you.  I think it must be something else, not metacity.

Since we last talked I've found out touch won't work in Jaunty unless some modifications are made to the kernel or a new kernel and/or the linuxwacom drivers.  Ayuthia has figured out probably the best way to get things working.  See Appendix 2 on the first post first page of this thread.  I did use what we learned about the xorg.conf to optimize Rafi Rubin's Wacom sections for Ayuthia.  So our experiments were valuable.

---

### Post by Midnight_Sun on 2009-06-24
Problem solved.
Installed xfwm4 and the solution is brutely but simply

```
killall compiz.real & xfwm4 

```

and then backwards

```
compiz --replace
```

I'll try to integrate it into the rotate script, and post it here.

---

### Post by Midnight_Sun on 2009-06-24
Edited.
Works. :)

---

### Post by Favux on 2009-06-24
Hi Midnight_Sun,

Wow!  Nice work!  I never thought of that.  And killing Compiz before starting metacity doesn't work for you when rotated?

---

### Post by Midnight_Sun on 2009-06-24
Left out ```
exit;;
```
from the end of it.
Made a bit of a problem while switching back to compiz if ran from a launcher.

Corrected.

---

### Post by Midnight_Sun on 2009-06-24
Well, I did not hessle much with Metacity. Frankly I don't use it. Maybe kill would do it, but in the version before it froze in a quite funny manner after some secs of work. Last solution is ok now. :)

---

### Post by knipp21 on 2009-07-02
ok so i ran method one step by step..and when i click where i have the launcher...nothing happens

---

### Post by Favux on 2009-07-03
Hi knipp21

Did you add:
```
Option		"RandRRotation"  "on"
```
to the Nvidia section of your xorg.conf (see Appendix 1)?  You can download one of the TX2000 xorg.conf's at the bottom of the HOW TO to see where it goes.

To edit xorg.conf use in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
But first back it up with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
The cp is copy.

---

### Post by knipp21 on 2009-07-03
> **Favux said:**
> Hi knipp21

Did you add:
```
Option		"RandRRotation"  "on"
```
to the Nvidia section of your xorg.conf (see Appendix 1)?  You can download one of the TX2000 xorg.conf's at the bottom of the HOW TO to see where it goes.

To edit xorg.conf use in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
But first back it up with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
The cp is copy.

can i use the one i downloaded and just paste it into mine? i have made the backup so i was just wondering

---

### Post by Favux on 2009-07-03
Hi knipp21,

No, that's for Intrepid and earlier.  You don't need most of what's in there.  In Jaunty things change because they're deprecating xorg.conf for HAL/.fdi.  Just add the one line, or show me your Jaunty xorg.conf and I'll show you where to put it.

---

### Post by knipp21 on 2009-07-03
> **Favux said:**
> Hi knipp21,

No, that's for Intrepid and earlier.  You don't need most of what's in there.  In Jaunty things change because they're deprecating xorg.conf for HAL/.fdi.  Just add the one line, or show me your Jaunty xorg.conf and I'll show you where to put it.

ok here it is

Section "Screen"
	Identifier	"Configured Screen Device"
	DefaultDepth	24
EndSection




Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option        "Type"          "stylus"
	Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option        "Type"          "eraser"
	Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option        "Type"          "cursor"
	Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "pad"
	Option        "Device"        "/dev/input/wacom"    # USB ONLY
	Option        "Type"          "pad"
	Option        "USB"           "on"                  # USB ONLY
EndSection
Section "ServerLayout"
Identifier "Default Layout"
	InputDevice   "stylus"  "SendCoreEvents"
	InputDevice   "eraser"  "SendCoreEvents"
	InputDevice   "cursor"  "SendCoreEvents"	# For non-LCD tablets only
	InputDevice   "pad"  "SendCoreEvents"	# For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection

---

### Post by Favux on 2009-07-03
Hi knipp21,

Did you add all those wacom entries?  Or did Mint 7?

---

### Post by knipp21 on 2009-07-03
good question..i havent opened this before, could this be from my setup from one of the how-tos? i just opened this for the first time when you told me to..mint 7 could have im checking on google right now

update: this link shows the default file as opposed to mine [http://forums.linuxmint.com/viewtopic.php?f=109&t=10434](http://forums.linuxmint.com/viewtopic.php?f=109&t=10434)

---

### Post by Favux on 2009-07-03
Hi knipp21,

Well whatever, it doesn't look right.  I removed the wacom entries that apply to an external graphics tablet and commented the others out.  Notice touch isn't in there like it is in the TX2000 xorg.conf you downloaded.

Hopefully things aren't too different and the "RandRRotation" won't break anything.

```
Section "ServerFlags"
	Option		"DontZap"	"False"
EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "stylus"
#Option "Device" "/dev/input/wacom" # USB ONLY?
#Option "Type" "stylus"
#Option "USB" "on" # USB ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "eraser"
#Option "Device" "/dev/input/wacom" # USB ONLY?
#Option "Type" "eraser"
#Option "USB" "on" # USB ONLY
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"RandRRotation"	"on"
EndSection

Section "Screen"
	Identifier	"Configured Screen Device"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#	InputDevice	"stylus"	"SendCoreEvents"
#	InputDevice	"eraser"	"SendCoreEvents"
EndSection
```
This is more what things should look like.  Minus the touch entries which I didn't add since you are using HAL/.fdi.  This one you can copy and paste in.

Edit:  That's from 3/08, way before the Jaunty xorg.conf changes.

---

### Post by knipp21 on 2009-07-03
> **Favux said:**
> Hi knipp21,

Well whatever, it doesn't look right.  I removed the wacom entries that apply to an external graphics tablet and commented the others out.  Notice touch isn't in there like it is in the TX2000 xorg.conf you downloaded.

Hopefully things aren't too different and the "RandRRotation" won't break anything.

```
Section "ServerFlags"
	Option "DontZap" "False"
EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "stylus"
#Option "Device" "/dev/input/wacom" # USB ONLY?
#Option "Type" "stylus"
#Option "USB" "on" # USB ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "eraser"
#Option "Device" "/dev/input/wacom" # USB ONLY?
#Option "Type" "eraser"
#Option "USB" "on" # USB ONLY
#EndSection

Section "Device"
	Identifier "Configured Video Device"
	Driver		"nvidia"
	Option		"RandRRotation"  "on"
EndSection

Section "Screen"
	Identifier	"Configured Screen Device"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#	InputDevice	"stylus"	"SendCoreEvents"
#	InputDevice	"eraser"	"SendCoreEvents"
EndSection
```
This is more what things should look like.  Minus the touch entries which I didn't add since you are using HAL/.fdi.  This one you can copy and paste in.

ok but before i do so..i copy this over everything right?

and why are there no touch entries? will touch still work?

---

### Post by Favux on 2009-07-03
Hi knipp21,

Right clear everything out and replace it with this.  The only difference is the rotation line and commenting out the wacom lines.  So if it breaks X it's the rotation line.  To restore things just reverse the copy (cp) line at a command line (which you should be able to reach) like:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by knipp21 on 2009-07-03
ok i did that..now i need to redo the launcher? i say that cause when it wasnt working i just deleted it

---

### Post by Favux on 2009-07-03
Yep, going to need to redo it and makes sure it points to the rotation script you chose.  You rebooted correct?

---

### Post by knipp21 on 2009-07-03
just finished and it works!

---

### Post by Favux on 2009-07-03
Hi knipp21,

Outstanding!  Nice job.  I think this is the first time I've worked with Mint.

---

### Post by knipp21 on 2009-07-03
> **Favux said:**
> Hi knipp21,

Outstanding!  Nice job.  I think this is the first time I've worked with Mint.

cool, i like it, it come prebuilt with flash and all that stuff in it...it just seemed a little less buggy..btw trying to set the q key doesnt go with your how-to because the file you gave me had nothing commented out like it says..and when i ran xev and pressed the key nothin happened

---

### Post by knipp21 on 2009-07-03
not sure if this works for everyone but you can set the Q key to rotate your screen w/o all the comand line...go to system->preferences->keyboard shortcuts...then choose add and basically create a launcher...for command just set it wherever your .name.sh is at...maybe this helps maybe it doesnt..just offering some info i found

---

### Post by Favux on 2009-07-03
Hi knipp21,

That's useful info.  So that works even though xev wasn't returning a key code?  Things have changed once again with Jaunty/Mint 7.

What you were asking about earlier.  You could probably use the TX2000 xorg.conf's keyboard section and add it yours to get what I was talking about.  But it doesn't look like you need to anymore.  From what you are saying sounds like Jaunty/Mint 7 has fixed the bug and now HAL doesn't break single key key bindings!

If you can give me a little more detail and someone else can verify it I could add it to the HOW TO.

---

### Post by knipp21 on 2009-07-03
well it was working..but it stopped...when i go through and reset it, it works again..it stops after i have logged out or restart my comp..i just set it to alt+right arrow and it works fine for me...but if the above info help please let me know ;)...umm one thing did happen today though...when i restart my computer, screen is calibrated, but when i hibernate it by closing screen, it loses calibration..any thoughts?


update:i have Q key set right now and is working...will continue to toy with it..if anyone figures it out just post it please so Favux can get this to the how-to

update 2: ok so this is different...i set it as my shortcut and it works...i restart and its still shown as the shortcut, but wont rotate screen..i dont know enough to persue this further so i will leave this to yall :)

---

### Post by Favux on 2009-07-03
Hi knipp21,

Maintaining your settings through suspend or hibernate is what the monitor_wacom.c script is for in Section 4 of gali98's post #104 on the other thread.

I don't know why your assigned rotation button (or key combination) keeps stopping.

---

### Post by knipp21 on 2009-07-04
> **Favux said:**
> Hi knipp21,

Maintaining your settings through suspend or hibernate is what the monitor_wacom.c script is for in Section 4 of gali98's post #104 on the other thread.

I don't know why your assigned rotation button (or key combination) keeps stopping.

well i have just opened my computer, and all works so ill let this play through and just let you know what happens over time...i hope ppl try the Q key my way so we know if this is a valid method

---

### Post by galenwilcox on 2009-07-08
):Phello everyone, i am very new to linux and very new to forums i hope i an in the right place. WELL here is my question: how do i "install the screen rotation script in the screen rotation tutorial & how do i attach it to the buttons on the monitor. also i tried to install the wacomrotate download and i keep getting the error saying " Error: Dependency is not satisfiable: libxi6" COULD anyone tell me how to get around this. FYI i am on a tx2510us running hardy 8.04 i now have the stylus touch and eraser all working and they show up in the wacomcfg box when the tool pops up. i am BRAND new to this so please do think i would be offendend by the simplest of instructions. I am using the ATI propietary driver becasuse it looks so much better with that one, is their a way to use the other ubuntu video drive and make the screen look great. Just wondering.
 
Also, i was on jaunty and had a hard time getting the stylus and eraser to show up in wacomcfg. also if i have to edit any files could you please tell me the commands to get the pages to pop up. THANK YOU SO MUCH FOR ALL OF YOUR HELP AND HARD WORK.

---

### Post by Favux on 2009-07-08
Hi galenwilcox,

I answered you on the other thread you posted on.  Let's continue here though if you have more questions.

By the way what you've done is called double posting.  It violates forum etiquette.  Doing that can start multiple threads with different people answering the same question duplicating effort.  That's why it is a no no.  Don't worry about it, just letting you know.

---

### Post by galenwilcox on 2009-07-08
i am sorry about that, i tried to delete the other post when i relized this was the correct place but i couldnt. I have read your stuff so much you are sort of famous to me. Well i am sure you can help. i have a tx2510 and am unsure  how to do  screen rotation and key binding. i have been trying to install wacomrotat but i keep getting a error.
 
What are the details you need from me and i will get them to you .som things i might need help to fugure out how to tell you.
THank you and sorry again.

---

### Post by Favux on 2009-07-08
Hi galenwilcox,

Don't worry about and don't bother to try and erase it.  Did you read my answer to you on the Kernel Driver thread?

My advice is to first set up a launcher to get rotation.  Then worry about key binding later.  I'm not real sure where you are getting stuck.  Just read things through a few times.  I think it will start making sense.

Remember with the ATI proprietary driver "fglrx" you have to do the aticonfig command at the bottom of the HOW TO in appendix 1.

---

### Post by galenwilcox on 2009-07-08
yes i did read the other post i am working on it now i will post questions or results shortly. and i will post wher i was getting hung up and the solutions for other newbies like me who after 4 nights of trying are addicted to ubuntu tablets. THANKS

---

### Post by galenwilcox on 2009-07-08
favux, i ran the command in apendex 1 just by copying and pasting and it gave me "Set Key DDX, Enablerandr12" I believe that is what it was supposed to do. Now as we go i just simply copy and paste the context of the script i choose ie. general right or left.
 
This is what i did.
1 - ran the command in apendix 1 because i have the ati video driver. results above.
 
2 - ran the " xrandr -q --verbose" in terminal and checked for the output which looked close to the one posted.
 
3 - created a text doc by rightclicking on destop nemed it .rotation.sh made it exicutable as a program in properties.
 
4 - copied all of the script from bottom to top in the "right handed script code box" and pasted it in my .rotation.sh file.
 
5- double clicked .rotation.sh choose run in terminal. the terminal flashed but nothing happend.
 
THANK YOU.

---

### Post by Favux on 2009-07-08
Hi galenwilcox,

My bad.  I forgot you are on Hardy.  You're basically there.  Use the equivalent method 2 script.  Right click on the .sh file and tell in to open in Text Editor.  Substitute it for the method 1 script.  Follow the instructions about commenting out (#) the TX2000 line and removing the comment (#) for the TX2500.

You can choose Run after dbl. clicking rather than run in a terminal.  Then you can use a launcher to run the script.

If you could post the xrandr -q etc. output I suppose I could see if I could get a method 1 script working in Hardy.

---

### Post by galenwilcox on 2009-07-08
hi favux, 
thank you for the help i do understand now however its not working. i think it is because i am using the ati propetary driver but im nor sure. when commenting out the line and uncomenting the new one i noticed it said somthing about xorgs driver. maybe you could tell me is their a way i dont care which version i use i am just wanting to use compiz to amaze my friends and linux is a cool hobby do you think i should switch versions. the things i would like to work are touch, stylus eraser, and screen rotation with the buttons on the screen. i your opinion with my tx2510us which should i use. hardy just seemed the easiest to me with the xorgs and all insted of the fdi files. i was on jaunty and followed the tut on pg 11 post 104 and could only get the touch to show up in the wacomcpl box. and is their any way to do the magic screen rotate on the tx2510us because of the swivil on hardy or do i have to use jaunty or intrepid. THANKS FAUX ps. if i have to remove this video driver and install the xorg one could you post me the commands. thanks again.

---

### Post by Favux on 2009-07-08
Hi galenwilcox,

You've accomplished quite a lot.  You installed Jaunty and then Hardy.  You got Wacom working by configuring xorg.conf.  So taking a break, read things over again, making some notes of what you've done if you haven't already.  Giving yourself a little time to digest and process the information you've acquired seems like a reasonable thing to do.  You probably have a little bit of information overload.

But a question.  What Catalyst is currently in Hardy?  If it's 8.9 or higher it supports rotation like it says at the top of the HOW TO.  Maybe you need to repeat the aticonfig command?  Copy and paste it in a terminal.  Or check out the wiki it is linked to.

To get Xorg's Radeon just go to Hardware Drivers and deactivate the ATI driver.  Reboot or restart X (ctr-alt-backspace).  Radeon should install automatically.  You may have to check on xorg.conf to see if things have been changed.  So back it up first.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by galenwilcox on 2009-07-08
Favux or ANYONE else with a answer, 
i know their is a very simple solution to this and usually i am pretty good at this sort of thing but i am having a hard time. could you or anyone please tell me how to see what  version of flgxr i have installed? when i go to system>admin>hardware drivers it just says "ATI graphics accelerated driver" also when i run the aticonfig or the other "aticonfig --initial --input=/etc/X11/xorg.conf" it says "Found fglrx primary device section
Nothing to do, terminating." also when i uninstall the "ATI graphics accelerated driver" my screen looks terible.. PLEASE HELP ME GET THIS THING ROTATING. if somone else is going to jump in to help if you look at post #188 in this thread and thier is a list of what ive done.

THANK you, also i am so new to linux that even simple things confuse me like where to find files to edit and simple things like that so please a little help with commands and stuff is appreciated.

THANK YOU

---

### Post by Favux on 2009-07-08
Hi galenwilcox,

Try in a terminal:
```
dpkg -l | grep ati
```
and
```
dpkg -l | grep fglrx
```
and
```
dpkg -l | grep [Cc]atalyst
```
or maybe:
```
dpkg -l | grep ATI
```
and see if it tells you the version number etc. in the output.

I don't think the radeon driver is suppose to look that bad.  It may need some lines in the video "Device" section in xorg.conf to specify some settings.  I don't know what those are.  So maybe a little research.  Are there some optional video settings you made when using "fglrx"?  To the fonts or whatever.  What happens when you go to System>Preferences>Appearance>Visual Effects.  Have you tried changing the setting there?

---

### Post by galenwilcox on 2009-07-08
hi favux here is the output.
thank you. in the meantime i will try to disable driver, restart and configure the way you said.

Thanks

edit: i just disabled the ati driver, restarted then when i go to visual effects it will not let me enable any iy says "desktop effect could not be enabled when i click on extra or mix.

Thanks again

---

### Post by Favux on 2009-07-08
Hi galenwilcox,

Mystery solved.
```
ii  xorg-driver-fglrx                          1:7.1.0-8-3+2.6.24.18-24.1                                 Video driver for ATI graphics accelerators

```
Nearly impossible to decipher but I  think "1:7.1.0-8-3" means "fglrx" 7.1.0 in Catalyst 8.3.  And I confirmed on the ATI wiki that Hardy's repository is only up to Catalyst 8.3.  And 8.3 doesn't allow rotation!

ATI wiki:  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
Ubuntu page:  [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Hardy page:  [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
Which shows you how to install Catalyst 9.6, which does allow rotation!  But fairly intricate for a newbie, so you'd have to study it carefully and proceed cautiously.

```
ii  xserver-xorg-video-ati                     1:6.8.0-1ubuntu1                                           X.Org X server -- ATI display driver
```
I think ati is another name, or alias, for radeon.  I don't remember the details.

You may be on a VESA driver, which is why things look so bad.  So maybe the video section in xorg.conf should look like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
#	Driver		"fglrx"
EndSection
```
instead of?:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
#	Driver		"fglrx"
EndSection
```
But why don't you see if addition to Xorg's ati you have their radeon:
```
dpkg -l | grep radeon
```
or in Synaptic Package Manager search ati, radeon, and xorg.  See what's available.

---

### Post by galenwilcox on 2009-07-09
Hi favux, scince we last spoke i have managed to crush everything had had acomplished on 8.04 by trying to update the drivers. no matter how hard it tried i could not get rid of mesa. well i decided to just start all over on jaunty because it seems like once i get the fdi files undestood and with you help i will be able to get things going and have the best final resuts. with magic screen rotation and compiz with touch and all. 
 
PLEASE before i get to far could you give me ANY advice to help. on 8.04 i was having no problems except upgrading the vide driver.
 
on 8.10 after i followed this -> 
[http://ubuntuforums.org/showthread.php?t=1038949&highlight=wacom+tx2500](http://ubuntuforums.org/showthread.php?t=1038949&highlight=wacom+tx2500)
 
and when i get to part 5 i get errors such as file not found or similar. then when i try to copy in step 7 it doesnt work no such directory or somthing like that. 
 
same thing when i use the other tutorial on post 104 but if i use your command to see if the wacom kernel is present it is.
 
well anyway i am installing jaunty right now, i do have pretty good grip on configuring xorg. and when i was on jaunty last time the only proble was when i used the command "dmesg | grep wacom" i only had 1 device i think i know how to plug my numbers into fdi. sort of like the "pci blah blah....usb 14.5 event mouse" thing nut i only had touch show up last time.
 
HOPEFULLY now things go smoother for me i am sick of working on it and want to play with it. ps does compiz work good on jaunty with the propitary video drivers"):P
 
THANKS A MILLION

---

### Post by Favux on 2009-07-09
Hi galenwilcox,

Well it you are having a problem with files not found on step 5 what probably happened is you forgot one of the lines in step 2) or didn't copy the really long line.  Notice how you have to use the slider at the bottom of the code box that contains it to see the whole thing.  You probably cut it off short.

In gali98's Jaunty HOW TO on #104 you don't need the usb 14.5 event mouse line.  That's for the xorg.conf not the 10-wacom.fdi you use in Jaunty.

Compiz works fine with the proprietary ATI driver except when you try to rotate.  It messes things up when you are rotated.  That's why I have the "Compiz off Rotation" script attached to the HOW TO up front.  I think it works.

Good luck.

---

### Post by galenwilcox on 2009-07-09
Favux, i just got the stylus, touch and eraser working now i want to make the screen rotate and get it key bound or on auto rotate when i swivel the screen, i am on jaunty i have the ATI/AMD proprietary FGLRX graphics driver enabled.. which method should i use to get the best end results 1 2 or 3 . 

remeber i would like to use compiz, key binding and the auto rotate..

Thanks for you advice and all of your help. 

Shawn

---

### Post by Favux on 2009-07-09
Hi Shawn,

Ok, you've got the important stuff.  You should be able to get rotation going, just maybe without all the eye candy you're hoping for.

I don't think you can use Compiz when rotated with "fglrx" yet.  That's what the Compiz_off_Rotation script is for attached to the bottom of the HOW TO on the first page of this thread.  It turns Compiz off before it rotates and then back on when it rotates back to landscape.  It's worked for several folks so far, only one said it didn't work when rotated.  If you want to try it set it up in a launcher first.  When you drag a launcher into the top panel it only needs a single click.

I don't know about the auto rotation.  If you're talking about the swivel hinge MisteR2 was doing that, but he hasn't posted in a while.

For key binding you have to see what bezel keys respond with xev.

---

### Post by galenwilcox on 2009-07-09
Favux,

I got the compiz off rotation working in a launcher on the top panel, it works perfect the calibration is just off a little rotated other then that it is perfect.

the only bezel button i get response from is Q but it is mapped to music player, do you know how to remap that button. if not thats ok.

THANKS a million, SHAWN:guitar:

---

### Post by Favux on 2009-07-09
Hi Shawn,

Fantastic!  You're there.  And the script works?  Cool.

Every time they update Ubuntu the button mapping changes.  I guess because there's a new Xorg Xserver (v. 1.6 in Jaunty).  What we were able to do is the key code addendum near the bottom of the HOW TO.  That gave us back the two buttons that disappeared going from Hardy to Intrepid.  2/4 we could never get.

But don't do that!!  No one has reported that it works in Jaunty.  Don't be the first to try it!

If after a few weeks, when you know more, you want to do some research and look into it that'd be great.

---

### Post by gothgirl on 2009-07-16
Hi all,

Perhaps I have overlooked something here or a difference between distros. But I figure it can't hurt to ask you guys for a little help.

I've recently purchased an HP tx2510us and am trying to get the rotation to work properly. I've tried all of the scripts listed in the first post and they mostly work. The only problem is that when I have this in tablet mode, the bottom portion of the screen is unusable. It is just a stretched out blur and anything placed into that area is completely unreadable. I am running a new install of Gentoo and do not use Compiz at all. I am using the fglrx driver. I have tried each script with Fluxbox, Gnome, and Kde4, each resulting in this same unusable area equaling about 1/3 of the screen. 

If you need anything from me system wise to help you assist me I'll be more than happy to post it. And thanks in advance for any possible help you can give.

---

### Post by Favux on 2009-07-16
Hi gothgirl,

Welcome to Ubuntu forums.

That's a weird one.  Like you said it may be a distro thing.

Can you tell me what version of Catalyst your "fglrx" is from?  
Also which version of linuxwacom do you have installed?  And which version of Xorg's Xserver?

Edit:  By the way did you run the aticonfig command in Appendix 1 at the bottom?

---

### Post by Ayuthia on 2009-07-17
It does not appear to be a distro thing.  I am able to get it to work on Gentoo with the 2.6.30 kernel (64-bit) and the catalyst 9.6 (ati-drivers 9.6).  However, I am using the tx2-1025dx.  If you are not using the 9.6, then it could be missing a patch.

I can also confirm that it does not work for me when I use compiz, but it does work fine using kwin (under KDE4).

---

### Post by synace on 2009-07-18
i can solve that one.. turn off compiz :)

that's the 'blur' issue.

system > prefs > appearance > visual effects > none

the scripts are supposed to toggle compiz vs metacity, but something must not be working on your implementation.

---

### Post by MisteR2 on 2009-07-18
Hello again. Sorry about my last post not being very clear on how to get to where I was at that time. I've made some more progress, and I'll try to be a little clearer. :)

So. It works.

Automatic rotation.

Make sure you have the kernel headers for your system (apparently 2.6.28-14 is the latest, which means I have to rebuild also...).

Apt-get install inotify-tools. This includes a program that will monitor a file for a state change.

Make a folder and place hp-wmi.c (with the ".txt" removed, it's already patched) and the Makefile in there.

Run the makefile and place the resulting .ko (there will be more files generated, but that's the one we're interested in) inside of /lib/modules/*kernel_version*/kernel/drivers/misc.

Take the rotate_screen_inotify_v2 script (a modification of something I found here earlier, sorry for not being able to give proper credit) and open it. The secret sauce here is inotifywait, which monitors the tablet switch input device created by the driver. You'll have to change the input event to your proper one that's watched in one of the line that runs inotifywait. Hopefully I can get something in there to automatically detect which one it is at the first running of the script. 

If you want to test out the script, comment out all lines dealing with xrandr and wacom rotation. Uncomment the lines that place the text file in /tmp. You can open up two terminals: one to run the (modified) script and one to monitor the file created in.

I've learned a little bit more about how to play with HAL and udev through this, but I still have yet to get HAL to recognize the tablet switch. The actual node is part of the hp-wmi platform device, and not something "under" it like the rfkill switches (bt, wifi, etc). And if hal doesn't see it, udev doesn't know or care if it exists, and dbus can't tell you when something's changed. So that's the next step to get this working "properly". But for right now, we have this. 

Eventually, I'm going to get this put into an init script.

Good Luck and have fun.

DT

---

### Post by Favux on 2009-07-18
Hi MisteR2,

Welcome back.  Thanks, your explanation clears things up a bit.

Do you have any thoughts on getting HAL onboard?

---

### Post by MisteR2 on 2009-07-18
I'm not sure exactly how to go about it. When I use "udevadm info -ap /sys/devices/platform/hp-wmi" this is what I get:

```
  looking at device '/devices/platform/hp-wmi':
    KERNEL=="hp-wmi"
    SUBSYSTEM=="platform"
    DRIVER=="hp-wmi"
    ATTR{modalias}=="platform:hp-wmi"
    ATTR{display}=="1"
    ATTR{dock}=="0"
    ATTR{tablet}=="0"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""
```

I'm still unsure on how to get sysfs values to work within HAL. I think it's something to do with the platform device. When I was playing with HAL to get the other device to play nice (the one I mentioned earlier in the thread deals with hotkeys, unfortunately not the bezel keys) I was able to add things to it via "append" tags in an FDI file. I haven't been able to do that with this platform device. 

DT

---

### Post by Favux on 2009-07-18
Hi DT,

You are definitely beyond me.  A couple of links you may want to glance at:

Think wiki on docking and un-docking (with reference link):  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61)

kernel modules keymap:  [http://people.freedesktop.org/~hughsient/quirk/quirk-keymap-modules.html](http://people.freedesktop.org/~hughsient/quirk/quirk-keymap-modules.html)

LaptopSpecialKeys wiki:  [https://help.ubuntu.com/community/LaptopSpecialKeys](https://help.ubuntu.com/community/LaptopSpecialKeys)

Hopefully something in there you can use, and I'm not wasting your time.

---

### Post by MisteR2 on 2009-07-18
I've been past a lot of those links, and unfortunately many of them depend on acpi signals to run programs. Right now, this doesn't send any ACPI signals. Which is why HAL is (right now) pretty important. Maybe I'll try to get in touch with Matthew again and see if he has any ideas on how to access it. 

So did everything work out for you? Anytime I have the script running in a xterminal (or whatever), I can swivel the screen and it switches.

DT

---

### Post by gothgirl on 2009-07-19
> **synace said:**
> i can solve that one.. turn off compiz :)

that's the 'blur' issue.

system > prefs > appearance > visual effects > none

the scripts are supposed to toggle compiz vs metacity, but something must not be working on your implementation.

I do believe I stated in my original post I do not run compiz. I've never installed it on this machine actually so that can't be the issue with mine.

---

### Post by gothgirl on 2009-07-19
> **Favux said:**
> Hi gothgirl,

Welcome to Ubuntu forums.

That's a weird one.  Like you said it may be a distro thing.

Can you tell me what version of Catalyst your "fglrx" is from?  
Also which version of linuxwacom do you have installed?  And which version of Xorg's Xserver?

Edit:  By the way did you run the aticonfig command in Appendix 1 at the bottom?

1> I'm guessing my catalyst is 9.6 as like Ayuthia I have ati-drivers-9.6 installed.
2> linuxwacom is 0.8.3
3> xorg server is 1.6.2

I haven't yet run the aticonfig will do that though and let you know the result.

---

### Post by Favux on 2009-07-23
Hi gothgirl,

Good deal!  So the aticonfig fixed it.

I think that's the best rotation functionality a straight "fglrx" has managed.  So Catalyst 9.6 seems to be an advance, rotation-wise.

---

### Post by Zuke24 on 2009-07-28
OK, I used Tom's deb package, wrote the script into ~/Desktop/.rotate.sh, made that executable, assigned the "Rotate Screen" key the command, and it works! :)

Only I lose calibration when it switches to the right. :confused:

I've added the -t to the wacomrotate in my startup apps, rebooted, and no change.  I've added -f -t to it, and no change.

Any other place I should look?

---

### Post by Favux on 2009-07-28
Hi Zuke24,

You don't need the -f and the -t, that was for an older version of the rotation daemon.

What do you mean you lose calibration?  You have Intel graphics,correct?
```
lspci | grep VGA
```
Are you using Compiz?

---

### Post by Zuke24 on 2009-07-28
I'm fairly certain I am, how do I tell?  Yes, I have Intel graphics, though that command you gave me didn't do anything.

I guess I shouldn't say I'm losing calibration; rather, the touchscreen isn't rotating with the display.  The display thinks it's turned 90 degrees, but the input has not.  Again, I used Method 3

---

### Post by Favux on 2009-07-28
Hi Zuke24,

Hmmm, it should give your video card.

OK, that's different.  That means the xsetwacom commands aren't applying to stylus, eraser and touch.  Sounds like the daemon didn't start up with reboot.  Step 9) is still written for Intrepid or earlier.  So like in Section 3 in the Kernel Driver HOW TO and the method it recommends for Jaunty I guess it would be:

In Jaunty go to System->Preferences->Startup Applications and click on add and for the command write
"/usr/bin/wacomrotate" (without the quotes).

I would have thought just "wacomrotate" would work since it's in "/usr/bin".  Let me know if it works and I'll change the HOW TO.

---

### Post by Zuke24 on 2009-07-28
Well, hell if I know what just happened!  I restarted a few more times, and suddenly my button mapping was gone.  Went back into compiz config, and the button mappings weren't enabled anymore.  Enabled them, back, close, and suddenly it all works!

I've restarted twice since, just to make sure it stays working!  Bizarre.  Also, I never did put in the /usr/bin/" path in the startup.  It works just with "wacomrotate".

---

### Post by Favux on 2009-07-28
Hi Zuke24,

Good!  So for some reason the Compiz key binding didn't kick in the first time.  And all you need is "wacomrotate", which is the one part of it that makes sense.

---

### Post by Zuke24 on 2009-07-28
No, the key binding was working (hitting the key DID rotate the screen).  It just seems that part of the actual script wasn't working.  Oh well, for whatever reason it works now.  I'm not going to overthink it!

Now for the challenge of getting the fingerprint reader to work correctly!  Does this ever stop?

---

### Post by Zuke24 on 2009-07-29
OK, this might be a bug, it might be my own model being wonky, so I'll try and be as detailed as I can.

Lenovo X61 Tablet (7764-CTO) 
Jaunty 9.04 amd64
Used Tom's deb from Method #3

4 out of 5 times, everything works fine!  That 5th time, however, calibration is suddenly lost after rotating.  When this happens, half the time the tablet thinks it's still in Landscape mode, the other half it goes to portrait but my input is about an inch off.

Opening wacomcpl and recalibrating fixes everything, and it holds its calibration through rotations for the next 4 out of 5 times.

Just seems to be a random glitch.

---

### Post by Favux on 2009-07-29
Hi Zuke24,

Rather than redoing wacomcpl you could set up a launcher to rerun the "/home/username/.xinitrc" of wacomcpl.

I think the problem is probably your Intel graphics, which is why I wanted to identify it.  You should be able to pull it out of "lspci".  Or it's interaction with Compiz.

You could try turning off Compiz and just using Metacity.

Or you could look into the Intel issue.  Some links:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

[http://www.linuxpromagazine.com/Online/News/Ubuntu-9.04-New-Intel-Graphics-Drivers](http://www.linuxpromagazine.com/Online/News/Ubuntu-9.04-New-Intel-Graphics-Drivers)

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver)

---

### Post by akand074 on 2009-08-02
Hello,

I myself am using the HP Touchsmart tx2z and I went straight to the Appendix 2 and did some reading. I understand you have to edit the xorg.conf file which I have already done but I have gotten really confused on the rest of it. I tried installing the kernels on another thread which wouldn't install. Another thread led me to install all the source files for custom kernels which I ended up in a dead end. in Is there no thread which explains the steps more thoroughly without sending me from thread to thread because I have been trying to get this for over an hour unsuccessfully. If I can get any help it would be greatly appreciated. Thank you very much.

---

### Post by Favux on 2009-08-02
Hi akand074,

Welcome to Ubuntu forums!

No, Ayuthia hasn't done a HOW TO.  You should just need the xorg.conf and install the deb.s.  Just download them and dbl-click them.  Did you choose the correct ones for your cpu architecture?  There's probably a little more information on his first post with the older deb.s  You're better off posting on the thread where the deb.s are.  What error message did you get?

Another thread where folks got things going:  [http://ubuntuforums.org/showthread.php?t=1206355&page=2](http://ubuntuforums.org/showthread.php?t=1206355&page=2)  But you'll have to skim through a bit and no one has had problems installing the deb.s I'm aware of.

---

### Post by Favux on 2009-08-05
**Auto-magic Rotation HOW TO:  for Intrepid, Jaunty, Karmic, and Lucid** brought to us courtesy of Red_Lion [post #576]("http://ubuntuforums.org/showpost.php?p=7732316&postcount=576") in the "Re: Info and help for HP TX2500 Series" thread.

Red_Lion supplied the "hp-wmi.c" source code and his custom Makefile.  The makefile was for 2.6.30 (in Jaunty) but works fine in 2.6.27 (Intrepid).  Actually as far as I can tell the "hp-wmi.c" source code is the same from 2.6.27 to 2.6.30.  If you want to verify this or get the source code directly use the links below.

The following assumes you have your video set up for rotation.  See Appendix 1 in the Rotation HOW TO on the first page, first post of this thread.

First check to see if you already have HP-WMI installed:
```
modprobe -l | grep hp-wmi
```
If it is there, and it should be in Jaunty, Karmic, and Lucid, no need to compile it (thank you Red_Lion for pointing this out).

Next check 'lsmod' in a terminal:
```
lsmod
```
In Intrepid you should see wmi.  You should also see hp-wmi after you compile and install it, and then add it to the 'modules' file in "/etc/" as described below.  In Jaunty, Karmic, and Lucid you should see only hp-wmi.  If you don't you'll need to add it to 'modules' as below.  The difference is due to the Ubuntu kernel team adding wmi to the kernel starting with Jaunty.  So it's now wmi.h in "linux-headers" rather than wmi.ko in "linux-images".

For Intrepid download the hp_wmi.tar.gz onto your desktop.  Extract it.  In a terminal enter:
```
cd ./Desktop

cd hp_wmi

make

sudo make install
```
The "hp-wmi.ko" will be installed in "/lib/modules/`uname -r`/extra/".

To make hp-wmi active (i.e. present in lsmod) add "hp-wmi" (without the quotes) to the end of the "modules" file using:
```
gksudo gedit /etc/modules
```
Save and close.

Using Text Editor (gedit) open and place in an empty file the following script:
```
#!/bin/bash

# From Red_Lion post #576:  http://ubuntuforums.org/showthread.php?t=845911&page=58

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/dock ]]; then
		new=`cat /sys/devices/platform/hp-wmi/dock`
		if [[ $new != $old ]]; then
#			-Close and restart Cairo Dock so it resizes on rotation.
#			killall -9 cairo-dock &
#			sleep 2s
			if [[ $new == "0" ]]; then
				echo "Rotate to landscape, hide cellwriter."
				xrandr -o normal 
				xsetwacom set stylus rotate NONE 
				xsetwacom set eraser rotate NONE
				xsetwacom set touch rotate NONE 
#				cellwriter --hide-window
			elif [[ $new == "4" ]]; then
				echo "Rotate to portrait, show cellwriter."
				xrandr -o right 
				xsetwacom set stylus rotate CW 
				xsetwacom set eraser rotate CW
				xsetwacom set touch rotate CW 
#				cellwriter --show-window
			fi 
#			cairo-dock -o &
		fi
		old=$new
		sleep 1s
	fi
done
```
**Note**:  In **Lucid** there has been a change to the device naming convention (actually true in Jaunty and Karmic also, but you can ignore it if using one of the modified wacom.fdi's).  To get your devices to rotate enter 'xinput --list' in a terminal. Find the device names that correspond to stylus, eraser (if you have one), and touch. Then substitute the longer more descriptive device names (with the quotes) in for stylus, eraser, and touch in the script's xsetwacom commands.  You can also use the ID numbers.  There is a bug using the Lucid default wacom.ko (from linuxwacom version 0.8.4-4(?)). Stylus and touch are called the same, namely "Wacom ISDv4 93", for TX2500 & TX2000's. So for at least touch use the ID number. If you've compiled and installed linuxwacom 0.8.5-12 or 0.8.6-2 (or up) wacom.ko this bug was fixed.

Save it in "/home/yourusername/"  as ".automagic_rotation.sh" (without the quotes), or whatever you want to name it.  Close Text Editor.  Back in the terminal:
```
cd ~/

chmod +x ~/.automagic_rotation.sh
```
Then in Intrepid go to System->Preferences->Sessions and click on Add and for the command enter "/home/yourusername/.automagic_rotation.sh" (without the quotes). And title it &#8220;Auto-magic Rotation&#8221; or whatever you like.  Remember ".automagic_rotation.sh" will be a hidden file and to view it you'll have to check Show Hidden Files in View.

In Jaunty, Karmic, & Lucid go to System->Preferences->Startup Applications and click on Add and for the command enter "/home/yourusername/.automagic_rotation.sh" (without the quotes). And title it &#8220;Auto-magic Rotation&#8221; or whatever you like.

As you can see from the commented out lines Red_Lion likes to have CellWriter show itself when in portrait/tablet orientation.  I have Cairo Dock which needs to be restarted on rotation so that it correctly resizes.  I left the lines in to demonstrate what you can do.  For example you could integrate the Compiz_off_Rotation script into it if you have ATI video but want Compiz in landscape as I do in [post #284]("http://ubuntuforums.org/showpost.php?p=7954654&postcount=284").

Reboot.  You should now have auto-magic rotation when you rotate your screen on the swivel hinge!


If you have used, or are planning on using, the patch Matthew Garrett (HP-WMI module maintainer) supplied to MisteR2 first you need to change 'dock' to 'tablet' on the "trigger line" according to Ayuthia.  The patch separates out the swivel hinge signal from the "dock event" and calls it 'tablet'.  This is obviously more technically correct and probably necessary for those of you with docks.  Otherwise docking may trigger rotation.  The patch, called "hp-wmi.diff", is attached to MisteR2's [post #106]("http://ubuntuforums.org/showpost.php?p=7191496&postcount=106") in this thread.  The patch is included in the HP-WMI for kernel 2.6.31.  So in Karmic you will also need to make these changes.

So in the script change:
```
/sys/devices/platform/hp-wmi/dock
```
to
```
/sys/devices/platform/hp-wmi/tablet
```
Which is how MisteR2 has the line in his "rotate_screen_inotify_v2.sh" script in [post #206]("http://ubuntuforums.org/showpost.php?p=7637329&postcount=206") in this thread.

Additionally the '4' needs to be changed to a '1' in the 'elif' portrait rotation line (per Ayuthia).  So:
```
elif [[ $new == "1" ]]; then
```


Note:  In Karmic cak3 has another take on automatic rotation.  He wrote a little bash "daemon" and uses Tom Jaeger's WacomRotate daemon (method 3).  See [post #374]("http://ubuntuforums.org/showpost.php?p=8764779&postcount=374").

_**Appendix 1:  hp-wmi.c source code blobs in the kernel git trees**_

kernel 2.6.27:  [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.27.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.27.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220)

kernel 2.6.30:  [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.30.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.30.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220)

_**Appendix 2:  Explanation of WMI**_
For those who are curious about the WMI BIOS interface here is a brief explanation:
> This driver adds support for the ACPI-WMI (Windows Management Instrumentation) mapper device (PNP0C14) found on some systems.

NOTE: You will need another driver or userspace application on top of this to actually use anything defined in the ACPI-WMI mapper.  ACPI-WMI is a proprietary extension to ACPI to expose parts of the ACPI firmware to userspace - this is done through various vendor defined methods and data blocks in a PNP0C14 device, which are then made available for userspace to call.

The implementation of this in Linux currently only exposes this to other kernel space drivers.

This driver is a required dependency to build the firmware specific drivers needed on many machines, including Acer and HP laptops.  *[i.e. HP-WMI]*

It is safe to enable this driver even if your DSDT doesn't define any ACPI-WMI devices.
From:  [http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg11962.html](http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg11962.html)

---

### Post by Red_Lion on 2009-08-06
Favux, tnx for post information here.

BEFORE you make hp_wmi compile - check what it not present in you system:
```

modprobe -l | grep hp_wmi

```

If resulf of command is empty - need to compile hp_wmi module.

---

### Post by martinjochimsen on 2009-08-07
Hi Red_Lion and Favux

I have been away from this list for a loooong time, but today I suddenly got an email from another list, that I should take look on this rotationlist.....and I must say you guys have been WORKING!!! :-D
WAUW....the guide in #225 from Favux worked out-the-box first time. Thanks!!!
When I rotate my screen I usually wants the screen to rotate 180 degrees, so I just changed the xrandr command from "right" to "inverted".


```
elif [[ $new == "4" ]]; then
				echo "Rotate to portrait, show cellwriter."
				xrandr -o right 

```

to

```
elif [[ $new == "4" ]]; then
				echo "Rotate to portrait, show cellwriter."
				xrandr -o inverted
```

...if somebody else wants to rotate 180 degrees?!

And by the way I have a tx2510eo with Ubuntu 9.04 and kernel 2.6.28-15-generic

Martin :-)

EDIT:
..too fast! I now have to work on the calibration. When the screen is rotated the mouse is off by at least 10 cm. I probably will come back soon! :-)

EDIT:
...and when the screen is rotated only 90 degrees (xrandr right) calibration works fine!

---

### Post by Red_Lion on 2009-08-07
For normal calibration need to rotate aslo stilys, eraser and touch.
```

				xrandr -o inverted
				xsetwacom set stylus rotate HALF
				xsetwacom set eraser rotate HALF
				xsetwacom set touch rotate HALF

```

---

### Post by martinjochimsen on 2009-08-07
to Red_Lion

```
xrandr -o inverted
xsetwacom set stylus rotate HALF
xsetwacom set eraser rotate HALF
xsetwacom set touch rotate HALF
```

Works perfect. Thanks!

Martin :-)

---

### Post by TomtheWombat on 2009-08-07
This makes me wish that I still had my tx2000z!  :(

---

### Post by Ayuthia on 2009-08-07
One other item that I did not see at first:
```
elif [[ $new == "4" ]]; then
```
should be:
```
elif [[ $new == "1" ]]; then
```
when you are checking for /sys/devices/platform/tablet.

---

### Post by Favux on 2009-08-07
Hi Martin,

Good to hear from you again.  Glad it worked for you!  Cool, huh?

Hi Red_Lion,

Thanks for helping Martin out.  And thanks again for the auto-magic rotation script.

Hi TomtheWombat,

Thanks for the affirmation.  Go get one!  Or heck, I saw a TX2z at Best Buy for $850 the other day.

Hi Ayuthia,

Thanks.  Added it to the HOW TO.

---

### Post by Red_Lion on 2009-08-07
Now i start write normal utility for "magic-rotation". It will be wrote on pygtk, will support patched and native hw_wmi. I will comlete it in few days (it's simple programm, but i busy on job now and not have few hour :) )

---

### Post by Favux on 2009-08-07
Hi Red_Lion,

That sounds good.  Looking forward to it.

---

### Post by joutsen on 2009-08-08
Hey guys, thanks for the hard work. Couple of points:

1) I jumped in from elsewhere, directly to post 225 and started implementing the HOW-TO. It did not work, since I did not have the Option "RandRRotation" set under Device in /etc/X11/xorg.conf. Perhaps add that as a note to the start of the HOW-TO?

2) Bigger problem is that I also no longer have or need any touch-related entries in xorg.conf, and thus xsetwacom commands do not work. Is there any way to rotate the touch without adding lines I do not otherwise need into xorg.conf? Hmm, I guess I should read the full thread first before asking this question, but what the hey.

3) I need to re-install the hp-wmi stuff on every kernel update, right?

Thanks again, looks promising.

---

### Post by Favux on 2009-08-08
Hi joutsen,

You're welcome.  Thanks for trying it.

> It did not work, since I did not have the Option "RandRRotation" set under Device in /etc/X11/xorg.conf.
OK, I didn't want to repeat a lot of stuff.  I can refer folks to Appendix 1 on the first HOW TO.
> I also no longer have or need any touch-related entries in xorg.conf, and thus xsetwacom commands do not work. Is there any way to rotate the touch without adding lines I do not otherwise need into xorg.conf?
Depends on how you're getting touch to work.
> I need to re-install the hp-wmi stuff on every kernel update, right?
Yes.  Until Ubuntu includes the HP-WMI module in "linux-image".

---

### Post by joutsen on 2009-08-08
Touch works on Jaunty without xorg.conf entries using gali98's fdi file from [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11).

Ok, I googled the answer to number 2, not using stylus/touch/etc. entries in xorg.conf. Use "xinput list" to find the name of wacom tablet hardware, in my case "Wacom ISDv4 93", then use that in the xsetwacom command:

```

xsetwacom set "Wacom ISDv4 93" rotate NONE

```

Only one command was sufficient in the script to cover both touch and pen, did not try the eraser.

Now the rotate works beautifully. Thanks again for all the hard work.

---

### Post by Favux on 2009-08-08
Hi joutsen,

Glad you got it working but I feel compelled to point out that something is wrong with your .fdi install.  If it was installed and working correctly "xsetwacom list" should be returning stylus, eraser, and touch.  Which would mean wacomcpl and the rotation xsetwacom commands should work.  You wouldn't need to rename stylus "Wacom ISDv4 93" or any wacom entries in xorg.conf.  You are basically using method 3) in Jaunty Users in the HOW TO on the first page, first post of the thread gali98's HOW TO is on, which only serial tablet pc's need.

---

### Post by jerridan on 2009-08-09
Hi, so I am having a problem where when I have my screen rotated, I cannot see any of the actions I perform on the screen. For example, if I click to open a folder when the screen is down, I will see nothing, but as soon as I put the screen back up, the folder is open. Any ideas? I'm a new user, thanks to all you guys who have worked so hard on making all this stuff possible!

---

### Post by Favux on 2009-08-09
Hi jerridan,

Welcome to Ubuntu Forums!

I need a little more information.  Which tablet pc do you have?  Are you saying you can see the cursor move to the folder and when you click on it nothing happens until you rotate back to landscape (laptop) mode?  Have you installed the auto-magic rotation stuff?

---

### Post by Red_Lion on 2009-08-09
This'is first test "magick rotation" helper programm. It's for patched and native hp_wmi.

It's depend on pyinotify and pygtk for now.

This "release" is just for test - test it and say what wrong. Next uptade in few days (try to add quickstart, make some better look, icons, code clean...).

Install - just unpack ( example to ~/bin/ ), chmod +x, and run. It will auto add to you autostart (if it placed in ~/.config/autostart)

P.S. yes, it's writen not good :)

---

### Post by Favux on 2009-08-09
Hi Red_Lion,

Seems to work fine.  The notification pops up, CellWriter shows itself in tablet, and it added itself to ~/.config/autostart.

Nice job.

---

### Post by MisteR2 on 2009-08-09
Hey Jerridan:

You may still be running with Compiz on. A quick way to disable it is to right click on your desktop and go to change background. Last tab on the right (visual effects) and you should be able to change it to normal or minimal.

Right now Compiz doesn't like to work in portrait mode. Hopefully that will be fixed later.

DT

---

### Post by Favux on 2009-08-09
Hi Red_Lion,

Panel applet looks good too.  Icon may be a problem because it looks like the restart icon.  After an update requiring a restart, if I'm remembering correctly.  Although it actually is the refresh icon.  I've used the redo icon "/usr/share/icons/Human/48x48/actions/redo.png".

Also with Stylus, eraser, touch names (if null, not use), maybe (if null, not used) or (if blank, not used).

---

### Post by Red_Lion on 2009-08-10
(if blank, not used) will be more correct. :) Ehh... i know what in programm can see anover error in english - it's not well at me :)

What icon you choise for normal and disabled?

---

### Post by Favux on 2009-08-10
Hi MisteR2, Red_Lion, Ayuthia, joutsen, and everyone

Please take a look at the launchpad bug where MisteR2 reported our hinge switch problem:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344141)  MisteR2 updated it on 7-19-09 with Matthew Garrett's patch to hp-wmi.c to separate tablet out from dock.  And on 7-31-09 Leann Ogasawara responded.  It I understand correctly the patched HP-WMI is going to be included in Kharmic!
> Marking this Fix Released for Karmic. Thanks.
Wow!  Attaway to go MisteR2!


Hi Red_Lion,

> What icon you choise for normal and disabled? 
Which ones do you want to use?

---

### Post by Red_Lion on 2009-08-10
I not know :) Icons in programm is just test - need choise better look

---

### Post by Ayuthia on 2009-08-10
> **Favux said:**
> Hi MisteR2, Red_Lion, Ayuthia, joutsen, and everyone

Please take a look at the launchpad bug where MisteR2 reported our hinge switch problem:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344141)  MisteR2 updated it on 7-19-09 with Matthew Garrett's patch to hp-wmi.c to separate tablet out from dock.  And on 7-31-09 Leann Ogasawara responded.  It I understand correctly the patched HP-WMI is going to be included in Kharmic!

I just compiled 2.6.31-rc5 for Gentoo and found that the hp-wmi code was updated.  The nice thing with Karmic is that for N-Trig users, the touch should work there, but it will be only missing one patch which can be included as a hid-ntrig.ko update instead of having to download the kernel debs.

---

### Post by Favux on 2009-08-10
Hi Ayuthia,

Great, Kharmic should be good.  And hopefully Ubuntu is going to include the HP-WMI.  So far there doesn't seem to be much of a wacom.fdi update.  That will be interesting to watch.  Or if there is a n-trig.fdi.  So far the linuxwacom is 0.8.3-2.


Hi Red_Lion,

I found a prettier 32x32 redo icon, "edit-redo.png", at "/usr/share/icons/gnome/32x32/actions".  For disabled I just colored it red.  What do you think?

Green = go or active or normal

Red = stop or stopped or disabled

And redo always made sense to me.  I want to "redo" orientation.

---

### Post by jerridan on 2009-08-10
> **Favux said:**
> Hi jerridan,

Welcome to Ubuntu Forums!

I need a little more information.  Which tablet pc do you have?  Are you saying you can see the cursor move to the folder and when you click on it nothing happens until you rotate back to landscape (laptop) mode?  Have you installed the auto-magic rotation stuff?

I have an HP TX2500 tablet. So far everything else for the tx2000 has worked with this computer. I am using Jaunty. I do not have compiz installed at the moment - though I do plan on it, looks cool!  I have installed the auto-magic rotation stuff. I changed the code as per Red_Lion's advice in order to flip the screen a full 180degrees, so I am not ever entering portrait mode. If you need any other info, just say the word.
Yes, that is correct, I can see the cursor just fine, and it moves properly. But when I go to click on a folder, or do anything with the cursor for that matter, I will not see the effects until I flip the screen back. When I click on something multiple times, nothing happens, but when I flip back I'll see the folder opened several times! Strange huh?

---

### Post by Favux on 2009-08-10
Hi jerridan,

Definitely strange.

OK, with a TX2500 you have ATI video.  The reason we asked about Compiz is the proprietary ATI driver "fglrx" doesn't yet work right with Compiz when rotated.  So either you'd have to use Metacity all the time or the Compiz_off_Rotation script or integrate it with your auto-magic rotation script.

I'm assuming you installed the ATI proprietary drivers through Hardware Drivers.  Did you do the aticonfig command?  See Appendix 1 in the Rotation HOW TO on the first page.

---

### Post by Favux on 2009-08-11
Hi Red_Lion,

Cosmetic bug.  The gui doesn't resize consistently.  If I expand the Advanced selection the gui enlarges.  When I collapse it the gui does not shrink to it's original sized.  If I close and reopen it:  it may open in the small size or the large size.

Changing touch to blank works.  If either stylus or eraser is blank, both still work.  Have to make both blank to disable both.  Not sure how important this is.

Feature Request:  Both for those who want to use Compiz in landscape and Cairo Dock a command line entry before rotation is needed to either replace Compiz with Metacity or killall Cairo Dock.

---

### Post by Red_Lion on 2009-08-11
Test this version.

I fixed expander (advanced settings), add pre state change commands. Also make about and fix "if null".

It will remove settins from 0.1 version.

P.S. bezel buttons parsing via PNP0C09 method _Q16.

---

### Post by Favux on 2009-08-11
Hi Red_Lion,

Nice work!  Using the following:
```
After tablet:  cellwriter --show-window; cairo-dock -o &
Before tablet:  killall cairo-dock

After normal:  cellwriter --hide-window;cairo-dock -o &
Before normal:  killall cairo-dock
```
everything works the way I want it to.

Still the same issue with stylus and eraser.  I don't think it's important.  They both share the same usb by-path unlike touch.

By the way the TX2z does not have an eraser.  And the stylus and touch do share the same usb by-path.

I guess you didn't like the icons on post #249?

PS:  Sorry to hear about the bezel buttons.  But not too surprised.  So to get them going, if possible, will take some work.  And we need another coder, especially one hardware oriented.  MisteR2 could you maybe help?

---

### Post by Red_Lion on 2009-08-11
Good what all work :) Just now need code in programm, make normal config file.

About icons i think need just add 2 setup fields - enabled and disabled icons names. In code i try to use icon system in gtk what depend of theme, not system location. In 0.3 version i will add both methods. And yes, icons in #249 looks better :)

Stulys and eraser use same point data - if you calibrate, rotate one of then it will be apply to both. I know it. I think to delete one from setting - so just will need enter name of stulys or eraser. Now 3 names in programm just for test. It's for tx2xxx with wacom. What in tx2z i not know. I will good surpised if this code work with this series :)

P.S. about bezel - last try in dsdt - need know what is ECON variable and what doing GBBV method. I not good in asl code.

P.P.S. It realy in tx2 only 1 button of 4 in bezel work, did you know?

---

### Post by Favux on 2009-08-11
Hi Red_Lion,

Sounds good.

The script at least works for the TX2z.  That's what Ayuthia has.

Yes I knew only one bezel button works with the TX2z.  Not good.

Edit:  67GTA seems to know about DSDT's and is on the kernel mailing list.  Maybe you could ask him?  His thread is here:  [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Edit:  Here are some links.

[http://www.acpi.info/](http://www.acpi.info/)

[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

[http://acpi.sourceforge.net/dsdt/](http://acpi.sourceforge.net/dsdt/)

---

### Post by Ayuthia on 2009-08-11
> **Red_Lion said:**
> 

P.S. about bezel - last try in dsdt - need know what is ECON variable and what doing GBBV method. I not good in asl code.

P.P.S. It realy in tx2 only 1 button of 4 in bezel work, did you know?
Are the bezel buttons the buttons on the lid by the screen?  If so, I only have three buttons--a settings button, a curvy M button (for the HP touchscreen apps in Windows), and a rotate button.  Only the curvy M button registers as an unknown key.  The other two do not register anything.

---

### Post by Red_Lion on 2009-08-12
Hmrr... You have 2 dead buttons and one need to write "by hand". This like on tx2xxx.

---

### Post by Ayuthia on 2009-08-12
> **Red_Lion said:**
> Test this version.

I fixed expander (advanced settings), add pre state change commands. Also make about and fix "if null".

It will remove settins from 0.1 version.

P.S. bezel buttons parsing via PNP0C09 method _Q16.

I just tested out this version and it needs a couple of changes to make the patched hp-wmi work.  The tablet state needs to be 1 instead 4 and the state_hp_wmi_patched check needs to be done before the state_hp_wmi.  This is because the patched version has both a dock and tablet file.  After those changes, it seems to work.

By the way, I am testing this in Gentoo using KDE so the system tray icon is a blank icon instead of the reload icon.  Not a big deal though.

Attached is the diff between my changes and the original code.

---

### Post by Red_Lion on 2009-08-12
Thanks - now test for patched version willbe before normal. Icon is blank becouse it can be from gnome - it's just think.

---

### Post by Favux on 2009-08-15
Hi Red_Lion, MisteR2, Ayuthia, gali98, and everyone,

**Aren't these at least some of our Bezel Buttons?**  Starting at line 79 in the unpatched hp-wmi.c:
```
static struct key_entry hp_wmi_keymap[] = {
	{KE_SW, 0x01, SW_DOCK},
	{KE_KEY, 0x02, KEY_BRIGHTNESSUP},
	{KE_KEY, 0x03, KEY_BRIGHTNESSDOWN},
	{KE_KEY, 0x20e6, KEY_PROG1},
	{KE_KEY, 0x2142, KEY_MEDIA},
	{KE_KEY, 0x231b, KEY_HELP},
	{KE_END, 0}
```
Clearly this is the swivel hinge:
```
	{KE_SW, 0x01, SW_DOCK},
```
Which with the patch adds 'tablet' to the switch (SW).

Are these the Brightness buttons on the keyboard?:
```
	{KE_KEY, 0x02, KEY_BRIGHTNESSUP},
	{KE_KEY, 0x03, KEY_BRIGHTNESSDOWN},
```
Edit:  Doesn't seem likely since the keyboard Brightness keys function without the hp-wmi module installed.  So what are they?

So is this the non-functioning Rotate button?:
```
	{KE_KEY, 0x20e6, KEY_PROG1},
```

This seems to be the "Q" (Media) button:
```
	{KE_KEY, 0x2142, KEY_MEDIA},
```
Although The keycode for the "Q" button is 201 in xev in Intrepid.  Or I suppose it could be the DVD button.

This may be the Mobility Center button:
```
	{KE_KEY, 0x231b, KEY_HELP},
```
Which is the other non-functioning button.

Any thoughts?  There isn't an exact one to one correspondence.  But it seems quite a coincidence that there is the swivel hinge accompanied by 4 buttons in the hp-wmi keymap.

---

### Post by Ayuthia on 2009-08-16
> **Favux said:**
> Hi Red_Lion, MisteR2, Ayuthia, gali98, and everyone,

**Aren't these at least some of our Bezel Buttons?**  Starting at line 79 in the unpatched hp-wmi.c:
```
static struct key_entry hp_wmi_keymap[] = {
	{KE_SW, 0x01, SW_DOCK},
	{KE_KEY, 0x02, KEY_BRIGHTNESSUP},
	{KE_KEY, 0x03, KEY_BRIGHTNESSDOWN},
	{KE_KEY, 0x20e6, KEY_PROG1},
	{KE_KEY, 0x2142, KEY_MEDIA},
	{KE_KEY, 0x231b, KEY_HELP},
	{KE_END, 0}
```
Clearly this is the swivel hinge:
```
	{KE_SW, 0x01, SW_DOCK},
```
Which with the patch adds 'tablet' to the switch (SW).

Are these the Brightness buttons on the keyboard?:
```
	{KE_KEY, 0x02, KEY_BRIGHTNESSUP},
	{KE_KEY, 0x03, KEY_BRIGHTNESSDOWN},
```
Edit:  Doesn't seem likely since the keyboard Brightness keys function without the hp-wmi module installed.  So what are they?

So is this the non-functioning Rotate button?:
```
	{KE_KEY, 0x20e6, KEY_PROG1},
```

This seems to be the "Q" (Media) button:
```
	{KE_KEY, 0x2142, KEY_MEDIA},
```
Although The keycode for the "Q" button is 201 in xev in Intrepid.  Or I suppose it could be the DVD button.

This may be the Mobility Center button:
```
	{KE_KEY, 0x231b, KEY_HELP},
```
Which is the other non-functioning button.

Any thoughts?  There isn't an exact one to one correspondence.  But it seems quite a coincidence that there is the swivel hinge accompanied by 4 buttons in the hp-wmi keymap.

I don't have an exact answer for you, but the codes there do correspond to buttons.  However, they are not responding at this time (they should have appeared in the same events as the swivel /dev/input/eventX).  So something is preventing it from appearing or else we do not have the correct code to register the button.

For my media button (the funky m-shaped button), it is being picked up by the keyboard instead of hp-wmi.  My guess is that the Q-button is responding in the same manner.  So my current thought is that the other buttons are most likely needing to be mapped to the keyboard source (drivers/input/keyboard/atkbd.c) somehow.  I am not for sure if we are going to be able to find it in hp-wmi or not.

---

### Post by Favux on 2009-08-16
Hi Ayuthia,

Thanks.  Good thoughts.

By the way to get the changes to work in tx2_rotation I had to use:
```
# detect what version of hp_wmi used and return file desk.
def prepage_stfile():
	global tablet_state, normal_state
	if os.path.exists(state_hp_wmi_patched):
		stfile=open(state_hp_wmi_patched, "r")
		print "Use patched hp_wmi event file"
		tablet_state="1\n"
		normal_state="0\n"
	elif os.path.exists(state_hp_wmi):
		stfile=open(state_hp_wmi, "r")
		print "Use native hp_wmi event file"
		tablet_state="4\n"
		normal_state="0\n"
	else:
		stfile=False
		print "hp_wmi event file not found..."
	return stfile
```
Does that break it for you?  I confess I jumped the gun and made a version 0.2-2 with the above and spelling and About changes.

---

### Post by Ayuthia on 2009-08-16
> **Favux said:**
> Hi Ayuthia,

Thanks.  Good thoughts.

By the way to get the changes to work in tx2_rotation I had to use:
```
# detect what version of hp_wmi used and return file desk.
def prepage_stfile():
	global tablet_state, normal_state
	if os.path.exists(state_hp_wmi_patched):
		stfile=open(state_hp_wmi_patched, "r")
		print "Use patched hp_wmi event file"
		tablet_state="1\n"
		normal_state="0\n"
	elif os.path.exists(state_hp_wmi):
		stfile=open(state_hp_wmi, "r")
		print "Use native hp_wmi event file"
		tablet_state="4\n"
		normal_state="0\n"
	else:
		stfile=False
		print "hp_wmi event file not found..."
	return stfile
```
Does that break it for you?  I confess I jumped the gun and made a version 0.2-2 with the above and spelling and About changes.

Sorry for getting back so late.  I was working on building a playground set.  For some reason, the code is no longer working in Gentoo (the original source either) and I am currently in Kubuntu and it is not working consistently.  Occasionally it will hang badly enough that I have to restart the desktop manager.

So to answer your question, the changes that you made still work.  However, there is something else in the code that is not responding as well.  The only change that I have made is to change my boot parameters to have acpi_osi="Linux".  The event code is still there and is responding.

---

### Post by Favux on 2009-08-16
Hi Red_Lion, Ayuthia, and everyone,

Hope the playground set goes over big.  Don't like the sound of the code not working well anymore.  Hard to believe it's the kernel line.  No python updates?  I'll attach what I have, not that it will do any good.  But at least it now works theoretically for the patched and unpatched hp-wmi.

Red_Lion,
I hope you don't mind.  I took the liberty of "making" a version 0.2-2 with the changes we talked about.  I think the redo/undo icon pair is the best we (I) can do with what we have.

Edit:  Added a few more corrections.

---

### Post by Ayuthia on 2009-08-16
> **Favux said:**
> Hi Red_Lion, Ayuthia, and everyone,

Hope the playground set goes over big.  Don't like the sound of the code not working well anymore.  Hard to believe it's the kernel line.  No python updates?  I'll attach what I have, not that it will do any good.  But at least it now works theoretically for the patched and unpatched hp-wmi.

Red_Lion,
I hope you don't mind.  I took the liberty of "making" a version 0.2-2 with the changes we talked about.  I think the redo/undo icon pair is the best we (I) can do with what we have.

I just tested it without the kernel parameters and the rotation is now responding.  However, I flipped the screen a few times in a row and then kdm froze.  I had to restart the desktop.

The other thing that I notice is that if you place the mouse on the system tray icon, it always shows Loading...

---

### Post by Favux on 2009-08-16
Hi Ayuthia,

OK, so maybe a problem using the gtk tray setup for qt/KDE?  I wonder if something like the GTK-Qt Theme Engine (here:  [http://code.google.com/p/gtk-qt-engine/](http://code.google.com/p/gtk-qt-engine/) ) would help any?  Probably too complicated?

Edit:  Well it's in Synaptic.  I should have looked there first.

---

### Post by Ayuthia on 2009-08-17
> **Favux said:**
> Hi Ayuthia,

OK, so maybe a problem using the gtk tray setup for qt/KDE?  I wonder if something like the GTK-Qt Theme Engine (here:  [http://code.google.com/p/gtk-qt-engine/](http://code.google.com/p/gtk-qt-engine/) ) would help any?  Probably too complicated?

Edit:  Well it's in Synaptic.  I should have looked there first.

I just tested with Ubuntu also and it is doing the same thing.  I am not for sure about what is happening,

---

### Post by Favux on 2009-08-17
Can't duplicate it.  Working great for me.  I'll look at the tar and see if I corrupted something.  In Advanced is the "eraser" line blank for you?  I have entries in all 4 of the Run & Exec before and after lines.

---

### Post by Ayuthia on 2009-08-17
> **Favux said:**
> Can't duplicate it.  Working great for me.  I'll look at the tar and see if I corrupted something.  In Advanced is the "eraser" line blank for you?  I have entries in all 4 of the Run & Exec before and after lines.

It is not blank.  It is still showing eraser.

Oddly enough, the application seems to be running happily in Gentoo today.  Maybe I had some code running yesterday that was conflicting with it.  I have another version of a rotation script that is running with a daemon that checks for changes in the events.  The down side to it is that it requires two programs to run--one to check the event and report it (since reading /dev events require sudo privileges, I placed it in /etc/init.d) and the other one to read the reported event.  At some point, I am going to add a GUI to it so that I can watch the events being reported and be able to catch and deal with any new events that are not rotation related.

The short answer is that my code might have been fighting with your rotation script or else I was not waiting long enough for the system to adjust to the screen changes before changing it again.

---

### Post by Favux on 2009-08-17
Hi Ayuthia,

I suppose it could be either of those two.  I was able to run it concurrently with the script version and Tom Jaeger's wacomrotate without any problems.  Of course that was because I hadn't disabled them yet to concentrate on testing.

The idea with the eraser line in Advanced is that, since the TX2z doesn't have one, you should remove it.  Make the entry box blank in other words.  Then the xsetwacom line for eraser won't (shouldn't) be applied.  I've seen that generate a warning for other TX2z's.

The set of rotation/monitoring programs sounds interesting.

---

### Post by Favux on 2009-08-18
Hi everyone,

Basically some more cosmetic changes.  Before is now before After in the Advanced Settings in Setup.  Hopefully that will prevent confusion when you are adding your commands.

The "pretty" icons are now included.  Since the current theme is no longer used you have to ensure the icons are in the same directory as the rotation script.  The old icon commands are still there so you can uncomment what you want and comment out the new icons.

And I may have gotten almost all of the spelling now.

Hopefully Red_Lion, you will approve.

---

### Post by Favux on 2009-08-20
Hi everyone,

**More Bezel Button Adventures**

In case you haven't been following along, in addition to automatic rotation, Red_Lion has been investigating the missing bezel buttons.  I told him my guess was the signals were going to hp-wmi like the swivel hinge.

Then he said in post #253 "bezel buttons parsing via PNP0C09 method _Q16."  Then in post #255 he added "about bezel - last try in dsdt - need know what is ECON variable and what doing GBBV method. I not good in asl code."  By the way my guess is the ECON variable refers to the embedded controller.  You can see it at "/proc/acpi/embedded_controller/ECO".

If you are losing track the ACPI-WMI (Windows Management Instrumentation) mapper device is PNP0C14.  According to Microsoft's pnp device info. PNP0C09 is the Microsoft acpi-compatible embedded controller.  What Red_Lion was saying is that from his DSDT it looked like my guess was wrong, the bezel button signals were suppose to go to PNP0C09 (ECO), not PNP0C14 (wmi/hp-wmi).

So I suggested he ask 67GTA for help.  67GTA has a great "HOW TO Fix a Buggy DSDT File" tutorial at:  [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)  Red_Lion gave it a try and posted his DSDT on post #243 of that thread and asked:
> "Now need to search 2 buttons and remoute (after starn vista, hibernate it and back it's dead. Not know where search - in i8042 or acpi).

Please see line 4338 - when ECON is == One?
Also - _Q16 on line 4586 and GBBV on 7929 - if i not mistake all events listed in _Q16 missed in GBBV and first can run only if ECON not true (if true GBBV save it to internal and blank)?

Also see please line 8681 QBTN device - how it work?

P.S. it's for tx2* tablets - we missing some buttons and think what they work via acpi - in i8042 in debug empty."
67GTA very nicely recompiled Red_Lions DSDT and said:
> Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 18 Optimizations

I fixed a warning that kept the kernel from reading your CPU temps. It should run quieter/cooler.
Well OK, cooler and quieter is good.

So I asked in post #261:  "Starting at line 79 in the unpatched hp-wmi.c aren't these at least some of our Bezel Buttons? ...There isn't an exact one to one correspondence.   But it seems quite a coincidence that there is the swivel hinge accompanied by 4 buttons in the hp-wmi keymap."  In other words are you sure PNP0C14 doesn't play a role?

Ayuthia answers in post #262:
> ...but the codes there do correspond to buttons. However, they are not responding at this time (they should have appeared in the same events as the swivel /dev/input/eventX). So something is preventing it from appearing or else we do not have the correct code to register the button.

For my media button (the funky m-shaped button), it is being picked up by the keyboard instead of hp-wmi. My guess is that the Q-button is responding in the same manner. So my current thought is that the other buttons are most likely needing to be mapped to the keyboard source (drivers/input/keyboard/atkbd.c) somehow. I am not for sure if we are going to be able to find it in hp-wmi or not.

Continued with my DSDT adventures.

---

### Post by Favux on 2009-08-20
Hi everyone,

**Bezel Buttons/DSDT Adentures Continued**

A while ago I took a look at my DSDT.  This was in response to a TX2500 user who said after he decompiled his DSDT and optimized it and recompiled it, it fixed his fan noise.  Just like 67GTA told Red_Lion.  I think that was on the TX2500 thread.  So I decompiled my DSDT and recompiled it and got two warnings.
> /home/username/dsdt.dsl  2902:                         And (CTRL, 0x1E)
Warning  1104 - Result is not used, operator has no effect ^ 

/home/username/dsdt.dsl  4260:                 Method (_Q16, 0, NotSerialized)
Warning  1086 -  Not all control paths return a value ^  (_Q16)

ASL Input:  /home/username/dsdt.dsl - 8501 lines, 294472 bytes, 4487 keywords
AML Output: dsdt.aml - 33822 bytes 856 named objects 3631 executable opcodes

Compilation complete. 0 Errors, 2 Warnings, 0 Remarks, 1248 Optimizations
For the line # 4260 warning the fix was easy to locate.  Several of the links 67GTA has to DSDT common errors and fixes sites show you how.

You just need to add to the end:
```
Return (0x00)
```
Making it look like:
```
                Method (_Q16, 0, NotSerialized)
                {
                    Store (QBBB, Local0)
                    If (LEqual (Local0, 0x03))
                    {
                        Notify (\_SB.MUBN, 0x02)
                        Return (0x00)
                    }

                    If (LEqual (Local0, 0x06))
                    {
                        Notify (\_SB.PIBN, 0x02)
                        Return (0x00)
                    }

                    If (LEqual (Local0, 0x12))
                    {
                        Notify (\_SB.LVBN, 0x02)
                        Return (0x00)
                    }

                    Store (0x04, \_SB.WMID.Z01C)
                    Store (0x00, \_SB.WMID.Z01D)
                    Notify (\_SB.WMID, 0x80)
                    Return (0x00)                <--- added that line
                }
```
The line #2902 was more obscure.  I found the fix on a Chinese site.  So I'm not totally confident of it but it seemed to work.  You just change 'And (CTRL, 0x1E)' to 'And (CTRL, 0x1E, CTRL)'.  Now when I recompiled it I got:
> ASL Input:  /home/username/dsdt.dsl - 8502 lines, 294512 bytes, 4488 keywords
AML Output: dsdt.aml - 33827 bytes 856 named objects 3632 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1249 Optimizations
Which seemed pretty sweet.  But since things seemed OK I didn't actually take the next step and install the "optimized" DSDT.  I couldn't see that it related to my thermals.  And a little nervous about "bricking" my tablet I guess.

Remembering that Red_Lion said "bezel buttons parsing via PNP0C09 method _Q16" I took another look at my DSDT.  Sure enough there it was, "_Q16", and lo and behold it was under PNP0C09, the Microsoft acpi-compatible embedded controller section.  One of the very sections whose warning I had fixed.

Could this be the problem causing the disappearance of the two bezel buttons?  I checked Red_Lion's DSDT and sure enough his TX2500 DSDT had the same error my TX2000 had, missing a line saying "Return (0x00)".  And I'll bet the TX2z DSDT has the same error.  Wow I thought, a possible eureka moment.

So I sucked it up and completed 67GTA's HOW TO and actually installed it and....

Nothing!  The two bezel buttons still don't work.  Can't detect anything.  I guess I got carried away otherwise the TX2500 user would have mentioned the bezel buttons appearing.  And I'm sure others have optimized their DSDT's also.

But maybe there is now a signal somewhere we could use?  I could easily be looking at the wrong place or doing it wrong.  So suggestions appreciated.  As an aside "var/log/messages" says:
> input:  HP WMI hotkeys as /devices/virtual/input/input10

---

### Post by MistaED on 2009-08-23
I've recently bought a touchsmart TX2z and have just set up the rotation script, it works very well! Haven't tried the little pygtk tool yet, the bash script seems to be working fine for me.

Another cool little tweak to add to the script if you use inverted/half rotation is to add this on the end so that the font rendering doesn't look like **** on the LCD:

```
gconftool-2 --type string --set /desktop/gnome/font_rendering/rgba_order bgr
```

and for when it goes back:

```
gconftool-2 --type string --set /desktop/gnome/font_rendering/rgba_order rgb
```

so my script is like this:

```
                  if [[ $new == "0" ]]; then
				echo "Rotate to landscape, hide cellwriter."
				xrandr -o normal 
				xsetwacom set stylus rotate none
				xsetwacom set eraser rotate none
				xsetwacom set touch rotate none
				cellwriter --hide-window
				gconftool-2 --type string --set /desktop/gnome/font_rendering/rgba_order rgb
			elif [[ $new == "4" ]]; then
				echo "Rotate to portrait, show cellwriter."
				xrandr -o inverted
				xsetwacom set stylus rotate half
				xsetwacom set eraser rotate half
				xsetwacom set touch rotate half 
				cellwriter --show-window
				gconftool-2 --type string --set /desktop/gnome/font_rendering/rgba_order bgr
			fi 
```

Thanks again for the script! I'm running the 2.6.30 kernel in jaunty but I still haven't found the right wacom drivers or patches yet for the touch and stylus to work :) *keeps rummaging the forums*

Actually for portrait it might work well if you set the rgba_order to vrgb or vbgr, depending on if you're left or right handed, haven't tried but it might work well!

---

### Post by Favux on 2009-08-23
Hi MistaED,

Thanks for sharing the font rendering tips.

If you look at Appendix 2 at the bottom of the Rotation HOW TO on the first page it has the xorg.conf and links to Ayuthia's kernel deb.s or kernel compiling HOW TO that will get you set up.

---

### Post by MistaED on 2009-08-23
I feel like such an idiot Favux! What I've been doing is hacking that kludge of a file xorg.conf when in fact I should have just been hacking the fdi file so hal manages it all! I'm getting far better results by hacking that file instead!

I had this weird bug where the stylus and touch settings never really did anything and there was no pressure sense for gimp or inkscape but xournal and zbrush under wine would have pressure sense...

Are there detailed forum posts on the best fdi hacks or should I just get in there and start putting in the xorg conf settings but in xml-style? If I could get touch to either work or not stuff up the stylus, then I'll be over the moon! :)

Thanks Favux!

---

### Post by Favux on 2009-08-23
Hi MistaED,

Your welcome.  Ayuthia and I spent a fair amount of time trying to get the .fdi to give us touch in addition to the stylus.  It starts at post #164 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=17](http://ubuntuforums.org/showthread.php?t=1038898&page=17)  and goes on for a few pages.  As a matter of fact a couple of pages before that Keeper of the Keys and I also tried.  There are a bunch of sample .fdi's scattered in there.  Maybe you can figure it out.

So far as I know the only way to get touch is to use the "TX2z & XT xorg.conf" attached to the bottom of the Rotation HOW TO on the first page of this thread.  And Appendix 2 has the link's to Ayuthia's stuff.

---

### Post by Favux on 2009-08-23
Hi everyone,

Here's Magick Rotation 0.2-4.

Basically some more cosmetic improvements.  I did rename a few things.  So if you have a previous version save your line commands in Advanced Settings in a text file so you can copy and paste them into this version.

Download the attachment onto your desktop.  Extract it.  Open the Magick Rotation 0.2-4 folder.  Drag and drop the applet and two icons onto 'yourusername' in the left column of Places (/home/yourusername).  To install right click on 'magick-rotation-0.2-4' and select Properties.  Then click on the Permissions tab.  Check "Allow executing file as a program" and close.  Now double click on 'magick-rotation-0.2-4' and choose Run.  The applet is installed.


If you have installed a previous version:

If you check your /home/username/ directory you'll see that tx2_rotation-0.x has been renamed magick-rotation-0.2-4.  Notice that the program is now grouped with the two icons.

To prevent the old version from reloading when you restart go to System > Preferences > Sessions or Startup Applications.  You'll see two entries that say Magick Rotation etc..  Click on one and then click on edit.  The one that has /home/username/tx2_rotation-x in the Command box is the old version.  Close Edit and click on Remove.  You may want to remove the old version.

The .conf file has also been renamed to magick-rotation.conf.  The old .conf file is called .tx2xxx.conf (/home/username/.tx2xxx.conf).  You can leave it in place if you like.  That way if you decide to go back to your old version your configuration is still there.  To see either click "Show Hidden Files" in View in Places.

---

### Post by R3fr4cti0n on 2009-09-07
thanks favux!

---

### Post by Docaltmed on 2009-09-15
Man, you guys are super-cool. I've got automagick rotation working, and I just installed fglrx again. That seems to be working as well.

I would like to do 3D in portrait. I understand that I need to incorporate some of the lines from the compiz_off script into the .automagic_rotation script. I'm just not entirely sure of which ones and where to put them, as I really on dabble in this stuff. I'm also still a bit shell-shocked from when I dove into Ubuntu head-first on this machine a week after 8.10 came out. So I like to make sure before making any moves. Suggestions?

---

### Post by Favux on 2009-09-15
Hi Docaltmed,

Good to hear from you again.  Could you tell me whether you're using the applet or the script?  And either way what commands you may already have in either (Advanced Settings in the applet) and where?

---

### Post by Docaltmed on 2009-09-15
Hi Favux!

I'm using the .automagic_rotation script from your How-to on the first page. I'm using it stock, with no changes. I haven't used the Compiz_off script at all, since I just worked up the courage to install fglrx today.

---

### Post by Favux on 2009-09-15
Hi Docaltmed,

This should work but because I have nvidia I didn't test it.  Good Luck!

---

### Post by Docaltmed on 2009-09-15
Thank you Favux! It worked like a charm.

I looked at the file, and I see I was trying to make things more difficult than they needed to be.

---

### Post by Favux on 2009-09-15
Hi Docaltmed,

Wow, great!  Auto-magic rotation with ATI's "fglrx" and Compiz!

---

### Post by tekknokrat on 2009-09-20
Hi, i wonder if I can rotate screen with a tx2 and an up-to-date jaunty with fglrx.

fglrx: 2:8.600-0ubuntu2
xserver: 1:7.4~5ubuntu18

I applied the ATI settings from 1st page and also tried with RandR option but it shows me a black screen and I can only see the mouspointer moving. On restoring to normal everything is visible again. Result is the same with metacity/compiz. Used command is "xrandr -o inverted". Any hints?

---

### Post by Favux on 2009-09-20
Hi tekknokrat,

You should be able to rotate with that if you've run the aticonfig command.  You don't need the "RandRRotation" option in xorg.conf, that's for nVidia.

The thing to keep in mind is that you can't rotate with "fglrx" with Compiz active.  Compiz is OK in landscape but things mess up when you rotate into portrait.  So either don't use Compiz or use the Compiz off script to shut Compiz off before you rotate.  When you rotate back to landscape you can turn Compiz back on.

Now with Inverted I'm not sure how "fglrx" and Compiz get along.  You'd think they'd be OK.  But from what you're saying, maybe not.

---

### Post by Nphyx on 2009-09-25
Hey, thanks for the guide. I used method 1, rearranged so that it rotates clockwise.

Also wrote up a quick .desktop so I could put it into panel with an icon. You'd want to use the counterclockwise icon. Obviously, replace /path/to/script.

```
[Desktop Entry]
Categories=Application;
Comment[en_US]=Rotate the Screen
Comment=Rotate the Screen
Exec=/path/to/script/rotate
GenericName[en_US]=
GenericName=
Icon=/usr/share/icons/default.kde4/48x48/actions/object-rotate-right.png
MimeType=
Name[en_US]=Rotate
Name=Rotate
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

---

### Post by Favux on 2009-09-25
Hi Nphyx,

You're welcome.

Thanks for that .desktop!  KDE has rotation icons?  I'm envious.

Glad you're getting your TX2z set up.  Neat that touch is working so well in Karmic.

---

### Post by Favux on 2009-09-26
Hi everyone,

Here's **Magick Rotation 0.2-5**.

This version includes Ayuthia's fix for the CellWriter hang that affects some folks and some more cosmetic improvements.  In addition we've verified that the HP 2700 series  tablet pc's (2710p and most likely 2730p) are supported, thanks to zoomy942.

Note:  The fix for CellWriter means you no longer should or need to use '&' after a program.  For example adding '&' to Cairo Dock as in "cairo-dock -o &" is no longer needed, "cairo-dock -o" is fine because the '&' will now be automatically added.  In fact adding the '&' will cause Magick Rotation to hang.

First make sure the infrastructure is in place.  Enter "lsmod" (without the quotes) in a terminal.  In Intrepid you should see 'wmi' & 'hp-wmi'.  In Jaunty and Karmic you should see 'hp-wmi'.  If 'hp-wmi' is not present you'll need to add to the 'modules' file in "/etc/modules".  See the "Auto-magic Rotation HOW TO" in post #225 for details.

If you haven't already, install CellWriter through Synaptic Package Manager.

If an earlier Magick Rotation is running shut it down by right clicking on it's green rotating arrow icon and clicking on Quit.   Download the attachment onto your desktop. Extract it. Open the Magick Rotation 0.2-5 folder. Drag and drop the applet and two icons onto 'yourusername' in the left column of Places (/home/yourusername). To install right click on 'magick-rotation-0.2-5' and select Properties. Then click on the Permissions tab. Check "Allow executing file as a program" and close. Now double click on 'magick-rotation-0.2-5' and choose Run. The applet is installed.

Before rotating right click on the Magick Rotation icon (green arrow) located on the right side of the top panel.  Go into advance settings and if you do not have an eraser delete it.  Or if you do not have touch delete that.  Make any other changes you want and then click on Save.  You are ready to rotate.

If you check your /home/username/ directory you'll see that magick-rotation-0.2-5 is grouped with the two icons.  In System > Preferences > Sessions or Startup Applications you'll see an entry called  Magick Rotation etc..  The .conf file is named magick-rotation.conf.  To see it click "Show Hidden Files" in View in Places (Nautilus).

Ayuthia has come up with some debug code to help **if you have problems** with Magick Rotation.  Download **Magick Rotation 0.2-5.2 (the debug version)** tar and follow the same instructions as for 0.2-5 to extract it and move it to "/home/yourusername/". 

To run the debug version quit Magick (if running) and open a terminal.  To see the debug output in the terminal use:
```
./magick-rotation-0.2-5.2 debug
```
This option let's you quickly eyeball the problem.  Remember you have a limited amount of time to swivel into tablet mode and back before the terminal will overflow and you'll lose the beginning of the debug output.

To print the output to the text file "magick-log" in "/home/yourusername/" for more detailed study use:
```
./magick-rotation-0.2-5.2 log
```
To stop either command make sure the terminal is in focus and use ctrl + C.  You'll see a python traceback after stopping.

You could also use these commands:
```
python magick-rotation-0.2-5.2 debug

python magick-rotation-0.2-5.2 log
```
To stop make sure the terminal is in focus and use ctrl + Z.

Looking at the output should help pin the problem down for you.  And you have the option of posting it as an attachement if you need help.

---

### Post by R3fr4cti0n on 2009-09-27
hey favux, screen rotation work great, however the mouse wont always follow suit, it stays "normal" after i fold my screen to tablet mode and my screen inverts, so basicly when rotation turns on and my picture inverts my mouse pointer/cusor dosen't for sometimes a minuet or longer. Has this happen to u or anyone else and is there a fix?

---

### Post by Favux on 2009-09-27
Hi R3fr4cti0n,

No first I've heard of that.

You rotate to inverted?  And you mean the stylus cursor?

In Advanced Settings did you delete eraser?

---

### Post by R3fr4cti0n on 2009-09-27
ya did all that and yes i rotate to inverted

---

### Post by Favux on 2009-09-27
Hi R3fr4cti0n,

OK, it lags but then kicks in, correct?

See if it goes away after you've done a few reboots.

Are you using Compiz?  Are you using the ATI proprietary driver "fglrx"?  If so did you do the aticonfig command in Appendix 1 in the Rotation HOW TO?

---

### Post by R3fr4cti0n on 2009-09-27
well its acting a bit weird, when it flips the mouse cursor stays as if the screen never fliped/inverted \ as i said, but now after a reboot the screen will freeze when inverted (clock stops) and the cursor may or my not flip to match the inverted screen, but also i cannot "click" on anything the cusor will move it just wont select anything.. if i  twist my screen right side up, sometims it gos back to nomal and and i can use everything again and sometimes its stays inverted and frozen and wont allow me to "click" or select anything useing either mouse pad, touch or stylus.... ok did the ati conf comand from the first page. now what is this about compiz?

---

### Post by Favux on 2009-09-27
Hi R3fr4cti0n,

So I take it you are using the ATI proprietary driver "fglrx"

Compiz is the window manager Ubuntu uses to give fancy 3-D effects.  The "fglrx" driver doesn't work right with Compiz when the screen is rotated.  So if you are using it you have to replace it with the default window manager for Gnome metacity.

To see if Compiz is running check System > Preferences > Appearance > the Visual Effects tab.  If none of the three effects are checked (the little circles in front blank) you are running Compiz.

---

### Post by ioasw on 2009-09-30
I'm using the Auto Magic rotate with the .name.sh file and the launcher, this is what I have in the .name.sh:

```
#These lines are for use with 8.04 (Hardy Heron) and 8.10 (Intrepid Ibex):
#  For TX2000 uncomment next line (and comment out the following one)-
rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"
#  For TX2500 using Xorg's “radeon” driver uncomment next line (and comment out the previous one)-
#rotation="$(xrandr -q --verbose | sed -n '16 {p;q}' | cut -d' ' -f5)"

case "$rotation" in 
    normal) 
        xrandr -o right 
        xsetwacom set "stylus" Rotate CW 
        xsetwacom set "touch" Rotate CW 
        xsetwacom set "eraser" Rotate CW 
        ;; 
    right) 
        xrandr -o normal 
        xsetwacom set "stylus" Rotate NONE 
        xsetwacom set "touch" Rotate NONE 
        xsetwacom set "eraser" Rotate NONE 
        ;; 
esac
```When I click on the launcher on my desktop that is attached to the .name.sh in my home folder, the screen does rotate but it rotates wrong, it stays in landscape mode, and is vertical with a large gap at the bottom so that half the desktop is off the screen.  I'll provide pics if you need it but I was hoping that is something in my .name.sh file that can be fixed.  I tried quoting and unquoting the different commands but then it does nothing.  I'm on a tx2510us 9.04 (Jaunty) running the xorg driver, and ciaro dock.  I do have cellwriter installed but I don't know if I need it.  Thanks for any help!

---

### Post by Favux on 2009-09-30
Hi ioasw,

Welcome to Ubuntu Forums!

The TX2500 has ATI video.  If you've installed the ATI proprietary video driver "fglrx" through Hardware Drivers make sure you've run the aticonfig command in Appendix 1 in the HOW TO.

If you are using the ATI proprietary driver you probably have Compiz running.  The ATI driver doesn't work right with Compiz when rotated so you have to turn Compiz off when rotated.  See the Compiz off script attached to the bottom of the HOW TO.

You're using a method 2 rotation script, not either of the "Magic" methods in Method 4.  So you don't need CellWriter but it's good to have anyway.

Hope this helps.

---

### Post by Favux on 2009-09-30
**[SIZE="2"]Warning:  Do Not Use.  Test Code.[/SIZE]**

---

### Post by ioasw on 2009-10-01
Thanks favux!  It worked, but I figured out quickly that you have to use the rotate with cairo on openGL only.  Unfortunately for me cairo with openGL is super glitchy, any advice on this?  I can't seem to disable the autohide with openGl cairo either.  Is there a better dock that is more compatible, i really like cairo without openGL, but I would rather have screen rotate.  Thanks again!

---

### Post by Favux on 2009-10-01
Hi ioasw,

Good, glad it's working for you.

I think the ATI proprietary drivers in Karmic are suppose to finally support OpenGL, FYI.

Have you tried using:

cairo-dock -c     (the cairo starting command)

rather than?:

cairo-dock -o     (the openGL command)

---

### Post by ioasw on 2009-10-01
Thanks for getting back to me so quickly.  Ok so jaunty doesn't support openGL, ok got it.  I do have the -c on ciaro, and the dock does appear at the bottom of screen when i rotate, but i get two ciaro docks one in the middle of the screen that seems to be stuck in the regular normal mode and then a good one that works at the bottom.  I have to manually close out of the middle one to get it off.  I believe this has been addressed before but I can't seem to find it; so if you know where its at maybe you could point me in the right direction, or just tell me what you think.  Thanks again!

---

### Post by Favux on 2009-10-01
Hi ioasw,

If you are using the Cairo Dock from Synaptic Package Manager you have an old version.

Try:  [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en)

---

### Post by beastrace91 on 2009-10-01
Hey There,

So I am trying to get this working with my HP tx1000 I have the following in the .sh file: ```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set stylus rotate  CW 
    xsetwacom set touch rotate CW 
    xsetwacom set eraser rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set stylus rotate NONE 
    xsetwacom set touch rotate NONE 
    xsetwacom set eraser rotate NONE 
    ;; 
esac
```

And when I run the file in terminal I get the following error(s):

```
jeff@lintouch:~$ ./.flipscreen.sh
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
./.flipscreen.sh: 24: xsetwacom: not found
./.flipscreen.sh: 24: xsetwacom: not found
./.flipscreen.sh: 24: xsetwacom: not found
```

Any ideas/suggestions?

Thanks,
~Jeff

---

### Post by Favux on 2009-10-01
Hi beastrace91,

My fault, I forgot to tell you to remove the xsetwacom lines in the script since you don't have a wacom tablet.

The TX1000 has nVidia I'm pretty sure so like it says in Appendix 1 you need to add:
```
	Option		"RandRRotation"  "on"
```
To your video "Device" section so that it looks something like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"RandRRotation"  "on"
EndSection
```
The TX2z thread you were on:  [http://ubuntuforums.org/showthread.php?p=7863677#post7863677](http://ubuntuforums.org/showthread.php?p=7863677#post7863677)  At step 3 shows you how to back up and edit xorg.conf.  I have some more links I'll post on your other thread in a bit.

---

### Post by beastrace91 on 2009-10-01
Thank you much! Screen is now rotating :)

~Jeff

---

### Post by Favux on 2009-10-01
Hi Jeff,

Outstanding!  Nice work.

You're welcome.

---

### Post by jpeter55 on 2009-10-03
I've installed the magick-rotation 2.5.2 script on a TX2500z running Karmic.  The rotation works well; however, the stylus does not follow when rotated (the directions are all off.)  All other rotation scripts have the same problem.  Any ideas what could be causing this?  I thought perhaps the problem was with the xorg.conf file, but it seems that Karmic doesn't have one anymore.  I've tried with both the default graphics driver as well as the flgrx.  Thanks in advance for any ideas.

---

### Post by Favux on 2009-10-03
Hi jpeter55,

This sounds like the same problem in Jaunty.  The 10-wacom.fdi is not parsing the wacom device names correctly.

The wacom devices won't rotate unless in a terminal:
```
xsetwacom list
```
returns their names:  stylus, eraser, and touch.

To see what HAL/dBus is calling them enter:
```
xinput --list
```

Is touch working for you?

---

### Post by jpeter55 on 2009-10-03
> **Favux said:**
> Hi jpeter55,

This sounds like the same problem in Jaunty.  The 10-wacom.fdi is not parsing the wacom device names correctly.

The wacom devices won't rotate unless in a terminal:
```
xsetwacom list
```
returns their names:  stylus, eraser, and touch.

To see what HAL/dBus is calling them enter:
```
xinput --list
```

Is touch working for you?

Thank you so very much for your help with this.  Touch is not working for me, and there is no output from "xsetwacom list".  I can't seem to deduce from the "xinput --list" command what I should enter for stylus, eraser, and touch.  I've posted the output from both these commands to this email.  Could you perhaps take a look and give me a little guidance?  It would be great to get this working.

---

### Post by Favux on 2009-10-03
Hi jpeter55,

Yes, it looks like the .fdi problem.  What HAL is calling your devices is:

stylus = "Wacom ISDv4 93"
eraser = "Wacom ISDv4 93 eraser"

You also have entries for cursor and pad which you don't have, and none for touch which you do have.  Your entries are also duplicated which I don't understand.  Did you try a custom_wacom.fdi or the wacom control panel on launchpad?  If so remove them and reboot.  Back up your current wacom.fdi.  If you need help with that let me know.  I'd appreciate it if you attached the default 10-wacom.fdi like you did your output.

My suggestion would be to try the 10-wacom.fdi we came up with.  Read "Jaunty Users" near the top here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)  And then follow the link in 1) to gali98's "Jaunty HOW TO" in post #104 to here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

Given the default linuxwacom drivers in Karmic, which I think are 0.8.3-2, you can and should skip Section 1).  Just do "Section 2: Creating the Fdi File" for now and reboot.  See what happens to touch and the "xsetwacom list" command.

---

### Post by jpeter55 on 2009-10-03
That worked!  All I needed to do was replace the fdi file.  Not sure why... I didn't alter it upon installation.  Thanks again.

---

### Post by Favux on 2009-10-03
Hi jpeter55,

Great!  Nice job.  You're welcome.

Could you attach your backup of the default Karmic 10-wacom.fdi?

Now with xsetwacom returning the correct names you need to set up wacomcpl.  See "Section 3: Calibrating your Tablet PC.: here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

---

### Post by Favux on 2009-10-04
Hi everyone,

**[SIZE="3"]Here's Magick Rotation 0.3-3[/SIZE]**

Download the attachment onto your desktop. Extract it. Open the Magick Rotation 0.3-3 folder.  Instructions are in the Magick-README.txt included in the folder.


Edit0: This version, 0.3, incorporates Ayuthia's debugging tool which can now be run from the command line and from the gui.  It also has more cosmetic improvements.  I think it looks pretty good now.  Since there is "significant" change to the code, all in all, I think bringing it out as version 0.3 is justified. 

Edit1:  Since there have been only 5 downloads of 0.3 I substituted 0.3-1 for it rather than do a new post.  There are no functional changes, just cosmetic.  Magick 0.3-1 now has borders for the Setup and About windows.  With the border for the About window the OK button doesn't look quite so hideous so I finally moved it there, where it "belongs".

Edit2:  While there have been 10 downloads of 0.3-1 I decided to substitute 0.3-2 for it.  There have been no functional changes.  Magick 0.3-2 has stock gtk buttons and the About button moved back to the setup window.  This should be the "final" look.

Edit3:  Magick 0.3-3 now has a GPL, gali98's check for '~/.config/autostart/' and if not mkdir code (e.g. the directory can be absent in clean install), and a minor cosmetic improvement.  I decided to put it side by side with 0.3-2 so you can use .3-2 as a fall back if there is a problem.

Edit4:  This is a first pass to get Magick Rotation working in Lucid.  Magick Rotation 0.4-beta1 installs just like previously, so read the READ ME file from the previous version as the beta is unaccompanied by the rest of the package.  Remember to right click on your current version and tell it to quit before installing the beta.

To get your devices to rotate enter 'xinput --list' in a terminal.  Find the device names that correspond to stylus, eraser (if you have one), and touch.  In Advanced Setup enter them in the corresponding input box at the 'The stylus, eraser, and touch entries' section without the quotes.  Note there may be a bug using the Lucid default wacom.ko (from linuxwacom version 0.8.4-4(?)).  Stylus and touch may be called the same, namely "Wacom ISDv4 93", for TX2500 & TX2000's.  So for at least touch use the ID number.  It should be bigger than the stylus ID number.  If you've compiled and installed the linuxwacom 0.8.5-12 or 0.8.6-1 wacom.ko this should have been fixed.

The new line of code adding/allowing the quotes to the Device Name entered in the input box courtesy of Ayuthia.

---

### Post by jpeter55 on 2009-10-04
I'm so sorry... after I got the new fdi file working I deleted the original.  Thanks for the tip about wacomcpl... I'll try to get that going right now.

---

### Post by tekknokrat on 2009-10-09
Magick rotation works great on a tx2 with karmic, also with fglrx and compiz running :)
Thanks favux and all the others for the efforts put in!

I attach recent released karmic packages (0.8.4.1) with the n-trig patch included.

---

### Post by Favux on 2009-10-09
Hi tekknokrat,

I'm glad Magick Rotation 0.3-1 is working for you!  And thank you for the kind words.

I linked your patched 0.8.4-1 linuxwacom deb.s to the HOW TO.  Thank you for posting them.

---

### Post by manu7irl on 2009-10-18
hi favux, I haven't been there for a while!
I'm now getting to work on my new karmic 32 bits install... I have the microphones working (ootb), loud and clear sound (ootb), webcam (ootb), all the tablet stuff working including touch and eraser calibrated, with the "how to" for karmic, got compiz to work and the ATI driver is installed, and finally got rotation from the new magick rotation python script!!! that's really wonderfull thanks a lot for your time and your investment! Like in every good story there's always a "BUT", when I rotated the screen to each one of the orientations I can choose from the magick rotation's setup, I can't get my stilus to write something clear in Xournal!! It's like my grand pa was trying to write something! If you know what I mean. Is there anything to help me?
Just for the record, I've got the "xinput --list" command and the "xsetwacom list" command showing me the same output stilus eraser and touch in every single place they had to appear...

---

### Post by Favux on 2009-10-18
Hi manu7irl,

Great to hear from you again!  Sounds like you're about there.  Thank you for your kind words about Magick, it's been fun.

It sounds like you did the aticonfig command in Appendix 1 in the Rotation HOW TO.  Are you trying to rotate with Compiz on?  ATI still can't handle Compiz when rotating.  You need to turn it off first.

---

### Post by manu7irl on 2009-10-19
sunddenly I feel so stupid! thanks it works! But there's another thing now the cursor refuses to get the wright orientation!?? it's like the stylus or the touch aren't calibrated well... what can I do? and another thing is there  a way to get a dock to work without compiz? like AWN maybe? or something else?

---

### Post by Favux on 2009-10-19
Hi manu7irl,

What you can do with Compiz is in Advanced Setup enter in the following command boxes.

Run before switch to tablet:  metacity --replace

Exec. after switch to normal:  compiz --replace


It would depend on the dock and whether it allows things like fake compositing etc.

I'm more worried about the stylus and touch cursor not tracking now.  Do you know what happened?  In a terminal does:
```
xsetwacom list
```
return stylus, eraser, and touch?

---

### Post by jmcnaught on 2009-10-20
Thanks for the Magick Rotation Script.  It works great on my 2710p.

Is there a license?  I couldn't find one.

My computer also has an accelerometer.  Do other HP tablets also have those?  It would be cool to have an option so while in tablet mode the screen would rotate with the physical device.

This guy has a .py script that rotates only the screen (not the stylus, eraser etc as far as I can tell) based on accelerometer input.  There's no license for his script either, but I asked about it in the comments.
[http://pieleric.blogspot.com/2008/11/automatic-rotation-on-its-way.html](http://pieleric.blogspot.com/2008/11/automatic-rotation-on-its-way.html)

cheers,
Jeremy

---

### Post by Favux on 2009-10-20
Hi jmcnaught,

I'm glad the Magick Rotation applet (python gtk script) is working for you and that your 2710p is set up now.

Thanks for the link to the accelerometer daemon.  It looks like he planned to hook up flipping the stylus and what not but hasn't gotten around to it.  Let's see if he has an updated version.  We also have a daemon version of Magick Rotation.

Do you know if all 2700's (2710p and 2730p and ?) have accelerometers?  With Magick you choose the rotation orientation you want when you go to tablet mode.  With the accelerometer the orientation would change depending on how you are holding it.  So really it would almost be two seperate applets in conception.

---

### Post by jmcnaught on 2009-10-21
Hi Favux,

I was thinking maybe accelerometer based rotation could be an optional mode for when the computer is in tablet mode.

I was considering trying to add that feature into Magick, but because there's no license for your code I wouldn't be able to share it.  So I might not.  Is Magick meant to be GPL, or not really?  It's fine either way, I'd just like to know.

As for the 2730p, it probably has an accelerometer too but I don't know for sure because I couldn't afford that one ;).  The accelerometer is there in mine for the "HP 3D Driveguard" feature that can stop the hard drive if it detects the computer is falling.  So any HP that has that feature probably has an accelerometer.  I found mine by grep'ing through the output of lshal.

---

### Post by Favux on 2009-10-21
Hi jmcnaught,

None of the TX's has an accelerometer.

I'd have to check with Red_Lion to be absolutely sure.  He "gave" me the code but is still around occasionally.  I'm hoping to hear more from him shortly.  I think you can treat it as an implied GPL.  More formally say something like:
> This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public license as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.
I feel certain he'd go for that as long as you share any code you come up with back with us.

I know I'm interested in seeing what you're thinking about.  Maybe incorporate it in Magick?

---

### Post by marranzano on 2009-11-04
tnx for the automagic_rotation script, works wondefully!!!

is there a way to rotate the touchpad orientation so i can keep the laptop open as a book with a vertical orientation and successfully use the touchpad?

tnx

ps. attacched is the script i use to rotate the screen in subsequent positions (a one time "echo normal > .screen-orientation" command is necessary)

---

### Post by Favux on 2009-11-04
Hi marranzano,

Good, I'm glad!  

I don't think so.  I think you'd have to rotate the pad itself.  I don't think something like:
```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```
in the 11-x11-synaptics.fdi would work.  You could look at the .fdi, it's in "/usr/share/hal/fdi/policy/20thirdparty/".

---

### Post by Docaltmed on 2009-11-28
Well, I upgraded to Karmic successfully...almost!

I did a clean install, and have followed the instructions for getting wacom driver installed. Stylus, touch, all works good.

However, I'm having some troubles with rotation. I downloaded the automagick rotation file and installed it. I think it would work properly if the ATI driver would cooperate. When I rotate the screen to portrait mode, I get a bunch of hash. 

I tried running:

```
sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"

```

But the response is:

```
docaltmed@laptop:~$ sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.
docaltmed@laptop:~$ sudo aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections

```

My xorg.conf looks like:
```


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

Which makes sense, I guess, as using xorg.conf is being supplanted by something else these days, insofar as I understand it.

I'm a bit reluctant to mess about with xorg.conf without having a clue (having been down that path before!). Any suggestions?

EDIT: I'm using the latest version of Catalyst, installed from the ATI website.

---

### Post by Docaltmed on 2009-11-28
Never mind!_:p I turned off fglrx and rotation is working fine. I'll just use cairo-dock for eye candy. Compiz was kind of a pain in the neck anyway.

---

### Post by cgul1 on 2009-12-11
Hello Favux et al,

Great resource here, thanks for the all the work!!!

I have an HP Tx2000 running Karmic.
I have read through this posts here and perhaps have missed a step or am confuse on driver/script needed
I am able to use the stylus with cell writer and xournal just fine in landscape mode.
I was able to install the magick rotation and it recognises the hinge switch and announces tablet state just fine and launches cell writer, but desktop stays in landscape orientation.

lsmod returns both hp-wmi and wacom, however wacomcpl opens with no devices and xsetwacom list does nothing??
Like I say, I think I missed a foundation step along the way
Thanks again

---

### Post by Favux on 2009-12-11
Hi cgul1,

Thank you.  From the sound of it you are using the Karmic default 10-linuxwacom.fdi which is why "xsetwacom list" is empty and wacomcpl and the xsetwacom rotation commands don't work.  You could either use the new-generic rc1 .fdi attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") (instructions in Section 2 b) or the .fdi in gali98's HOW TO linked near the top in "Jaunty (9.04) & Karmic (9.10) Users".  The direct link to gali98's HOW TO is [here]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").

Either should work for you.

---

### Post by cgul1 on 2009-12-12
> **Favux said:**
> Hi cgul1,

Thank you.  From the sound of it you are using the Karmic default 10-linuxwacom.fdi which is why "xsetwacom list" is empty and wacomcpl and the xsetwacom rotation commands don't work.  You could either use the new-generic rc1 .fdi attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") (instructions in Section 2 b) or the .fdi in gali98's HOW TO linked near the top in "Jaunty (9.04) & Karmic (9.10) Users".  The direct link to gali98's HOW TO is [here]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").

Either should work for you.

Favux, 
thanks so much, 'xsetwacom list' and 'wacomcpl' both return expected results!!, but I still do not get rotation.
I tried both of the how to methods above. I still have tablet functionality with xournal and cell edit. Desktop visual effects set to 'none'.
Thanks for you help and patience.

---

### Post by Favux on 2009-12-12
Hi cgul1,

Are you using the default Karmic linuxwacom version 0.8.4-1?  Which video drivers are you using for your Nvidia card?

---

### Post by cgul1 on 2009-12-12
> **Favux said:**
> Hi cgul1,

Are you using the default Karmic linuxwacom version 0.8.4-1?  Which video drivers are you using for your Nvidia card?

Favux,
I went through the how to in this thread to install the linuxwacomm update 0.8.4-4, according to EnvyNG video driver is 185.18.36-0ubuntu9. Looks like a newer version is available on teh Nvidia site, but not sure that would help.

How can I verify the linuxwacom version installed??

thanks again for all the help and patience

---

### Post by Favux on 2009-12-12
Hi cgul1,

Not a problem.  I agree, I'd hold off on updating nVidia.  I'd just use the version with Karmic.

I am able to get rotation with linuxwacom 0.8.4-4 and nVidia in Intrepid.

No way to determine the linuxwacom version except by looking at the downloaded linuxwacom file name.

Are you sure you didn't use 0.8.5-x?  Starting with linuxwacom 0.8.5-4 and up rotation has been broken.

Or it's possible you have a version conflict if you didn't manage to completely remove the default 0.8.4-1 before installing 0.8.4-4.  Why did you update 0.8.4-1?  I thought that offered complete support to the TX2000 in Karmic.

---

### Post by cgul1 on 2009-12-12
> **Favux said:**
> Hi cgul1,

Not a problem.  I agree, I'd hold off on updating nVidia.  I'd just use the version with Karmic.

I am able to get rotation with linuxwacom 0.8.4-4 and nVidia in Intrepid.

No way to determine the linuxwacom version except by looking at the downloaded linuxwacom file name.

Are you sure you didn't use 0.8.5-x?  Starting with linuxwacom 0.8.5-4 and up rotation has been broken.

Or it's possible you have a version conflict if you didn't manage to completely remove the default 0.8.4-1 before installing 0.8.4-4.  Why did you update 0.8.4-1?  I thought that offered complete support to the TX2000 in Karmic.
Favux,
Rechecked all, redid some, then realized I skipped updating my xorg.conf file.
DOH! Works great now! and hey it was fun and educational trying to troubleshoot.

Thanks so much for all the help:D

---

### Post by Favux on 2009-12-12
Hi cgul1,

Great!  You're welcome.

Right now I think nVidia proprietary is only video driver that needs the xorg.conf in Karmic.  Good catch.

---

### Post by Docaltmed on 2009-12-13
I must be cursed.

I lost my automagick rotation. It is starting up. The icon for it is in the systray. But when I rotate the screen, nothing happens.

I tried changing the configuration, e.g., having it rotate the other way -- still no response.

I enabled logging, but it has not created a logfile.

Any suggestions?

EDIT: Using RandR by itself, screen rotates ok (without corresponding cursor orientation, of course)

---

### Post by Favux on 2009-12-13
Hi Docaltmed,

Well, there was a kernel update along with other stuff Friday.  Maybe that knocked something out.

Have you checked to see if hp-wmi is loading?:
```
lsmod | grep hp-wmi
```
Hopefully it didn't knock out Python!

---

### Post by Docaltmed on 2009-12-13
Hi Favux,

No hp-wmi :(

This is what I get:

```
docaltmed@arran:~$ lsmod | grep hp-wmi
docaltmed@arran:~$ 

```

---

### Post by Favux on 2009-12-13
Hi Hi Docaltmed,

Something in the update could have broken the modules dependencies so you could try:
```
sudo depmod -a
```
and reboot.

Otherwise add it to modules like the HOW TO in [post #225]("http://ubuntuforums.org/showpost.php?p=7738673&postcount=225") shows you.

---

### Post by Docaltmed on 2009-12-13
I did just a plain "lsmod" and did find that something called "hp_wmi" is running, but no "hp-wmi". 

I'll try sudo depmod -a and let you know what happens.

---

### Post by Docaltmed on 2009-12-13
The "sudo depmod -a" command worked!

Thank you once again, Favux.

You are a prince among men. :D

---

### Post by Favux on 2009-12-13
Hi Docaltmed,

Good!

Happy rotation!

---

### Post by marranzano on 2009-12-14
same thing here:
hp_wmi has been loaded instead of hp-wmi.

but this doesn't prevent automagic_rotation.sh to work because with hp_wmi
/sys/devices/platform/hp-wmi/tablet shows the correct values when open or close...

---

### Post by Favux on 2009-12-14
Hi marranzano,

I think '_' and '-' are equivalent in modules.  I think I read it in the man page or somewhere a while ago.  It was something messed up in the module dependencies by the update I guess.

---

### Post by toobaz on 2010-01-08
I use a slightly modified version (and combination) of some scripts appearing in this thread - someone may be interested:

[http://www.pietrobattiston.it/wiki/doku.php?id=karmic_on_hp_pavilion_tx2500#rotation_and_buttons](http://www.pietrobattiston.it/wiki/doku.php?id=karmic_on_hp_pavilion_tx2500#rotation_and_buttons)

cheers

Pietro

---

### Post by dranorter on 2010-01-08
Hi, I'm using Ubuntu 8.10 and the latest fglrx driver from the ATI website on a tx2z, yet rotating the screen for me does nothing really but garble it.

I set up my system according to the tutorial on page 8 here: [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)

I also tried to use the automagic_rotation script (of Red_Lion) to do nothing but turn off the touch when the screen is folded down; it didn't detect the screen having rotated.

---

### Post by Favux on 2010-01-09
Hi Pietro,

Thank you for linking to your take on automagic rotation and updated wiki for the TX2500 on Karmic (and embedded link to the one for Jaunty).  I'll link to it on the HOW TO.


Hi dranorter,

Did you run the ati config command in Appendix 1 on the HOW TO?

Since you are using Intrepid did you compile hp-wmi.ko like the Auto-magic Rotation HOW TO shows?  Did you check that it and wmi are loading with lsmod?

---

### Post by dranorter on 2010-01-09
Yes, I did run the aticonfig configuration command "sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"".

And, I'd forgotten to do the "sudo make install" somehow; so the automagic script works now, except of course I have the lines which actually do the rotation commented out.

Favux, thank you for your tireless efforts helping everyone out!

---

### Post by Favux on 2010-01-09
Hi dranorter,

Thank you for the thank you!

OK, are you using Compiz?  The current Catalyst almost works with rotation and Compiz but not quite.  If so you can use the Compiz off script (attached to the bottom of the HOW TO) or since you're using the automagic rotation script there's one with Compiz off built into it linked in the Auto-magic Rotation HOW TO.

---

### Post by dranorter on 2010-01-10
I am not using Compiz; visual effects are set to 'none' and I ran metacity --replace just to make sure. "xrandr -o inverted" still garbled the screen.

---

### Post by Favux on 2010-01-10
Hi dranorter,

Have you tried removing the ATI driver and going with the Xorg radeon driver?

---

### Post by dranorter on 2010-01-10
No, I haven't tried it. I'm not sure I want to do that; would I risk losing touch? 

I don't want to reinstall again just to have rotation at this point. I'm pretty satisfied just with disabling touch in tablet mode.

---

### Post by Favux on 2010-01-10
Hi dranorter,

I wouldn't think so.  But I understand not wanting to mess with it.

What I don't understand is why the latest Catalyst/fglrx is messing up on rotation.  Is it so new that support for Xserver 1.5 in Intrepid is being lost?  That doesn't make sense.  So most likely there's a bug affecting rotation.

What's your xorg.conf look like?  You could attach it to your next post.

---

### Post by dranorter on 2010-01-10
My laptop is a tx2-1270us, and on the ATI website I downloaded the driver under Linux x86_64 > Radeon > ATI Radeon HD 3xxx Series (ATI Catalyst 9.12, says it's good for xorg 6.7 thru 7.4, x86 or x86_64).

xorg attached.

---

### Post by Favux on 2010-01-10
Hi dranorter,

OK, it's a hot mess.  The TX2z mess that we can probably optimize a little and you have duplicate ATI sections which is probably the problem.  This will take me a while.  Meanwhile back up your xorg.conf and be prepared to restore the back up from the command line if X breaks.  I don't know if I'll be able to figure out which video sections belong to the new Catalyst.

Edit:  Alright, let's see if this helps any.

---

### Post by dranorter on 2010-01-10
Rotation is unaffected (still gets random garble), but touch now moves the mouse without clicking (except in emacs, where I get "<mouse-10> is undefined"). This was fixed by putting the line

Option "Button10" "1"

back.

Stylus right button works now. :)

---

### Post by Favux on 2010-01-10
Hi dranorter,

Progress.

Thank you!  So that's what 'Option "Button10" "1"' is for, an EMACS error!  I'll add that back in with a comment.

Don't know what's wrong.  Only other thing I can think of is to try and comment out the line:
```
	Load	"dri"
```
Because the duplicate section (from the new Catalyst?) didn't have it.

Edit:  Say do you have one or two buttons on the stylus?

---

### Post by dranorter on 2010-01-10
Nope, that line didn't do the trick.

Also, I seem to be having a lot of trouble with clicking when I restart, curiously. I restart, and find that clicking and dragging works (to select items on the desktop) but not clicking or double clicking. The touchpad tap, touchscreen tap, stylus, and mouse button all fail to function. The first time this happened, I dragged to select a desktop icon, and opened it with 'enter', after which I could click. That worked again the second time, but not the third time- I'm simply unable to click now!

(This is after putting "Load "dri"" back.)

I'm going to ask about my wireless now, too, but I'll do so in the appropriate thread (the tx2 8.10 thread, [http://ubuntuforums.org/showthread.php?t=1038898](http://ubuntuforums.org/showthread.php?t=1038898))

---

### Post by Favux on 2010-01-10
OK, try adding:
```
Option "Button1" "1"
```
back to the touch section.

Too bad with dri.  I'm back to a bug with rotation in the Catalyst you installed.  So you're left with downgrading to a previous Catalyst or using radeon it would seem.  Maybe you should try repeating the ati config command and rebooting now that the xorg.conf is straightened out?

---

### Post by dranorter on 2010-01-10
:) Ok, I guess I should have realized that.

Edit: Oh, actually that didn't work! It's still ignoring clicks of all sorts.

Edit: Huh, it's ignoring clicks now regardless of which xorg I use!! ed: oops, nevermind. Making sure the button1 thing actually got tried, apparently I've been cping wrong.

edit: Yep. The button1 thing didn't help.

---

### Post by Favux on 2010-01-10
Alright, try rebooting a few times.  If that doesn't work comment out (#) the:
```
Option "USB" "on"
```
in the touch section and see if that helps.  That goes against everything I know about xorg.conf and Wacom but it's N-trig after all.

---

### Post by dranorter on 2010-01-10
OK, I'd switched back to my old xorg; I switched to yours again and rebooted and it fixed clicking. Will it last? No idea. But I'll try the aticonfig again.

---

### Post by dranorter on 2010-01-10
Re-doing aticonfig had no effect. Restarting more times made clicking stop working again.

I guess I'll be sticking with my old xorg; though I couldn't find a way to make right clicking work in it.

What instructions should I try for the radeon driver? I tried just de-activating fglrx and it made touch stop working.

---

### Post by Favux on 2010-01-10
Hi dranorter,

Well, it doesn't sound like either xorg.conf is all that stable.  Changing video driver shouldn't affect touch.

You could look at Xorg.0.log in /var/log/ with either xorg.conf when things are working and when they aren't and see if you get an error message telling you what's going on.  Also looking at your lshal (lshal>lshal.txt) would be a good idea.

The other thing in "my" xorg.conf is to see if removing or commenting out  "SendCoreEvents" after touch and/or stylus in "ServerLayout" helps.

Radeon should be installed (check Synaptic Package Manager) and automatically take over on a reboot.

ATI wiki:  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
Radeon info. & links:  [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by dranorter on 2010-01-10
OK, this has gone beyond my curiosity level. I got everything back how it was (replacing "your" xorg.conf with mine restored touch). I'm fine without rotate, I'll play around with things if I have any other problems.

However I am less-than-fine with suspend taking out wireless. Has anybody else had this happen?

---

### Post by Favux on 2010-01-10
Hi dranorter,

I'm not sure.  Something happened with suspend/hibernate with TX2z's in Karmic.  But I think that was due to Ayuthia's new hid-ntrig.ko for Win7 firmware.

You could try adding 'i8042.reset' to the kernel boot options:  [http://ubuntuforums.org/showpost.php?p=6189450&postcount=374](http://ubuntuforums.org/showpost.php?p=6189450&postcount=374)  Post also linked from here:  [http://ubuntuforums.org/showthread.php?t=1217745](http://ubuntuforums.org/showthread.php?t=1217745)

Don't know if it will work but I don't think it would hurt to try.

---

### Post by dranorter on 2010-01-10
Well it didn't work, but it turns out hibernate works, so I guess I've at last got everything I need. :D

So satisfying after a semester of Vista.

---

### Post by Favux on 2010-01-10
Hi dranorter,

Cool!  :)

---

### Post by dranorter on 2010-01-11
My garbled screen must by the fglrx driver. Other people are having the same experience here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1304273&page=9](http://www.uluga.ubuntuforums.org/showthread.php?t=1304273&page=9) Post #90 states the last working version was 9.10.

---

### Post by Docaltmed on 2010-01-13
Has anyone else tried to make this work? I enabled the accessibility features on startup so that I have a keyboard on the screen at usplash. So far, so good. 

But when I try to boot up my TX2500 in rotation, it gets upset. The usplash screen will start in landscape mode. At some point, the rotation kicks in, and the usplash screen appears in the desired portrait mode. Then it disappears for a second and reverts back to landscape mode, where it gets stuck on the login and user input merely makes it recycle.

Any suggestions?

---

### Post by cak3 on 2010-02-02
Just an update with what I have found to work well.

I have a tx2500z, and I am using Xubuntu 9.10 with compiz and the proprietary fglrx driver. I am also using Tom Jaeger's wacomrotate daemon. I also have hp-wmi enabled in /etc/modules (no need to compile as I am on karmic)

To get automagic rotation, all I have to do is run a little bash daemon I wrote (based on the automagic-rotation script from this thread and the rotation command that goes with the wacomrotate daemon):

```

#!/bin/bash
# Daemon to automatically rotate the screen
#
# Traps:
# signal QUIT (3) delete temp files
# signal TERM (15) delete temp files

tempfile=/tmp/ROTATION_$$
touch $tempfile

# set traps
trap 'rm -f $tempfile; exit' 0
trap 'rm -f $tempfile; exit' 3
trap 'rm -f $tempfile; exit' 15

# begin rotation loop

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/tablet ]]; then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
		if [[ $new != $old ]]; then
            if [[ $new == "0" ]]; then
                xrandr -o normal
            elif [[ $new == "1" ]]; then
                xrandr -o right
            fi
        fi
		old=$new
		sleep 1s
	fi
done



```

This is somewhat simpler than some of the other solutions, though required the hp-wmi as well as the wacomrotate daemon. The most interesting bit is that I am using fglrx (from the karmic repos) and compiz, and I have no issues rotating with compiz on. This was true with other rotation scripts as well, not just this one. Not sure if I am a special case, or if the fglrx/compiz version is the repos has been changed to allow rotation.

Edit: updated the script, now it uses the same method of detecting orientation as the original automagic rotation script (by detecting whether it is in tablet mode or not). Essentially, the only real differences are that it relies on the wacomrotate daemon to rotate the input, and that is stores its PID in a fine in /tmp, so that you can get that if you need to kill it, and will clean up that file when it is killed. I will probably add a small configuration file, to allow changing the sleep time and maybe a couple other things, and will update accordingly then.

---

### Post by Favux on 2010-02-02
Hi cak3,

Good to hear from you again.  That's clever, thanks for sharing.  I'll add a link to it in the automagic rotation HOW TO.

That would be good if fglrx finally works with Compiz and rotation!  I don't know if Xubuntu has anything to do with it.  For others can you tell us what versions of Xserver, Compiz, Catalyst, and fglrx you have?

---

### Post by cak3 on 2010-02-02
yea, sorry should have done that above. 

In Xubuntu 9.10, I am using fglrx and have rotation working with compiz. 

From "X -version":
X.Org X Server 1.6.4
xorg-server 2:1.6.4-2ubuntu4.1

(the first is xserver version, second the package version)

the fglrx and catalyst version is 8.660 
(package version of flgrx-kernel-source is 2:8.660-0ubuntu4)
This is just the current package for this in the karmic repositories, installed through the hardware drivers menu item (jockey-gtk)

Compiz is version 0.8.4.

As I stated before, rotation works without disabling compiz or any effects. There is some screen corruption immediately after rotation, but it quickly disappears and after that everything functions normally.


Hope that helps, maybe flgrx, compiz, and rotation do play nice after all. I am also including my xorg.conf, for reference, though it is mostly just what is autogenerated by aticonfig --initial, plus the changed made when enabling rotation (via sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE").

---

### Post by KEMATSE2 on 2010-02-07
When I add hp-wmi to my /etc/modules in Karmic for automagic rotation and reboot, hp-wmi appears as expected in lsmod but my mouse becomes completely unresponsive. Touch still works and when I remove hp-wmi my mouse functionality returns. Does anybody have any thoughts?

---

### Post by Favux on 2010-02-07
Hi KEMATSE2,

Welcome to Ubuntu forums!

That's a new one on me.  Try:
```
sudo depmod -a
```
before rebooting.

---

### Post by KEMATSE2 on 2010-02-08
Thank you Favux for your quick reply! Unfortunately my mouse still doesn't work when hp-wmi is enabled in modules after reboot. I'm confused as to why my mouse goes out but the keyboard and touch functions remain operational. ... :(

---

### Post by Favux on 2010-02-08
Hi KEMATSE2,

I don't understand it either.  What mouse do you have?  Which tablet pc do you have?  What does the output of:
```
xinput --list
```
look like in a terminal without and with hp-wmi?

---

### Post by KEMATSE2 on 2010-02-08
Hmmm... with hp-wmi there is no entry for the touchpad but without it, its there. 

"SynPS/2 Synaptics TouchPad"    id=19    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1

---

### Post by Favux on 2010-02-08
I need to know which tablet pc you have.

Is the Synaptic touchpad the mouse you are talking about?

Sometimes the Syanptic driver can grab the touchscreen, thinking it is a touchpad.  That's why I need to know more.  Seeing the entire outputs for xinput would help too.

We may have to look at lshal and Xorg.0.log in /var/log to see what's happening.

---

### Post by KEMATSE2 on 2010-02-09
Oops sorry! Its a tx2000z. From looking over the Xorg.0.log it looks like it doesn't like all of my input devices and rejects the touchpad. Any thoughts? Its nice to know what's happening though maybe I'll be able to find a solution on the internets. :)

---

### Post by Favux on 2010-02-09
Ok, that was weird.  I have a TX2000 also and I haven't ever seen anything like that.

The Xorg.0.log with hp-wmi says:
```
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(EE) Too many input devices. Ignoring SynPS/2 Synaptics TouchPad
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed (11)
```

I think you must have multiple wacom.fdi's.  Either that or your .fdi is garbled.  You don't have Wacom stuff in xorg.conf, do you?

You should only have one wacom.fdi called 10-linuxwacom.fdi located in /usr/share/hal/fdi/policy/20thirdparty/.  Either use gali98's wacom.fdi linked in Jaunty and Karmic Users near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"), or the new-generic described in 2b).  And you should delete the three lines mentioned.

Another thing is since you're in Karimic you do not need to compile hp-wmi.  It should already be there.  You added it to modules in /etc because it wasn't auto-loading, right?

---

### Post by farmercyst on 2010-04-08
this is for anyone that is testing lucid lynx 10.04. i have a tx2500 with hd3200 and wacom. getting the screen to rotate wasnt any problem with the original instruction although the fglrx driver now supports rotation for the hd3200!!! getting the wacom to rotate was a bit harder. the usual "xsetwacom set stylus rotate CCW" didnt work. i had to replace "stylus" with the device id from "xinput --list" this command. mine showed up as "Wacom ISDv4 93   id-12" so my final command to rotate the wacom was "xsetwacom set 12 rotate  CW" and i didnt have to tell it to rotate "ERASER", "STYLUS" and "TOUCH". just the on command does all. here is my rotation script. 

```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the left 
    xrandr -o left 
    xsetwacom set 12 rotate CCW 
    ;; 
    left) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set 12 rotate HALF 
    ;; 
    inverted) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set 12 rotate  CW 
;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set 12 rotate NONE 
    ;; 
esac
```

---

### Post by Favux on 2010-04-13
Hi farmercyst,

Now that's interesting.  Peter Hutterer rewrote the xsetwacom commands for xf86-input-wacom but I hadn't thought using the xinput id would work.  I thought each device name would have to be used.  They really want you to use the name the kernel returns although it seems a little long and clumsy to me.

Good news on fglrx now supporting rotation.  Which version of Catalyst?

Definitely have to update the HOW TO with some confirmation.

---

### Post by cgul1 on 2010-04-16
Hey Favux et al,
It has been a while since I used my HP tx2000 tablet in portrait mode.
It still rotates fine with magik rotation .3-3 but now the calibration is way off and when I bring up wacomcpl, it shows two stylus and two erasers.
How do I get ride of the extras?
thanks

---

### Post by Favux on 2010-04-16
Hi cgul1,

At a guess you either have two wacom .fdi's or a .fdi and xorg.conf entries.  Any chance of it?

What release of Ubuntu are you in?  Could I see the output of:
```
xinput --list
```
and
```
xsetwacom list
```

---

### Post by cgul1 on 2010-04-16
> **Favux said:**
> Hi cgul1,

At a guess you either have two wacom .fdi's or a .fdi and xorg.conf entries.  Any chance of it?

What release of Ubuntu are you in?  Could I see the output of:
```
xinput --list
```
and
```
xsetwacom list
```

hmm could be
thanks for quick response
here is xsetwacom output:
stylus           stylus    
eraser           eraser    
touch            touch     
stylus           stylus    
pad              pad       
eraser           eraser 
xinput -- list attached:

---

### Post by Favux on 2010-04-16
Duplicates and non-existent devices.  Xsetwacom should show:
> stylus stylus
eraser eraser
stylus stylus
Looks like something wrong with your .fdi at least, if not duplicates.  See Section 2b) in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by cgul1 on 2010-04-16
> **Favux said:**
> Duplicates and non-existent devices.  Xsetwacom should show:

Looks like something wrong with your .fdi at least, if not duplicates.  See Section 2b) in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

OK,
I replaced the 10-linuxwacom.fdi with the contents of new-generic release candidate 10-(linux)wacom.fdi
rebooted and it appears that I still have duplicates.
I also have a 10-wacom.fdi, is this causing the problem?

thanks for the help

---

### Post by Favux on 2010-04-16
If you are in Karmic you should not have a 10-wacom.fdi (name in Jaunty).  That is likely the problem.  Remove it.  You should only have a 10-linuxwacom.fdi located at:  /usr/share/hal/fdi/policy/20thirdparty/

---

### Post by cgul1 on 2010-04-16
> **Favux said:**
> If you are in Karmic you should not have a 10-wacom.fdi (name in Jaunty).  That is likely the problem.  Remove it.  You should only have a 10-linuxwacom.fdi located at:  /usr/share/hal/fdi/policy/20thirdparty/

That is weird, OK deleted, but still showing double stylus and eraser. stylus does not rotate with screen, works fine in normal landscape, but not portrait left or right or inverted landscape.
Not sure what I changed since it worked in the past.

thanks for the help

cgul1

---

### Post by Favux on 2010-04-16
Hi cgul1,

Good the stylus is working.  'xsetwacom list' should look like this:
stylus  stylus
eraser  eraser
touch  touch

Is that what you mean, or are you still seeing the duplicates in 'xinput --list'?

If so, make sure there isn't another wacom .fdi in "/etc/hal/fdi/policy/".  Also make sure there are no wacom sections in xorg.conf (at /etc/X11/) or in the "ServerLayout".

---

### Post by cgul1 on 2010-04-17
> **Favux said:**
> Hi cgul1,

Good the stylus is working.  'xsetwacom list' should look like this:
stylus  stylus
eraser  eraser
touch  touch

Is that what you mean, or are you still seeing the duplicates in 'xinput --list'?

If so, make sure there isn't another wacom .fdi in "/etc/hal/fdi/policy/".  Also make sure there are no wacom sections in xorg.conf (at /etc/X11/) or in the "ServerLayout".

Yeah, still duplicates, I do not have wacom sections, but entries, see attached...
thanks for the help

cgul1

---

### Post by Favux on 2010-04-17
All right, I think we have it.  You have what I call Wacom sections in your xorg.conf as well as lines/entries in "ServerLayout".  You should only use the .fdi or the xorg.conf not both.  I recommend the .fdi.  So comment out (#) or remove the wacom stuff as in the attached xorg.conf.

---

### Post by cgul1 on 2010-04-18
> **Favux said:**
> All right, I think we have it.  You have what I call Wacom sections in your xorg.conf as well as lines/entries in "ServerLayout".  You should only use the .fdi or the xorg.conf not both.  I recommend the .fdi.  So comment out (#) or remove the wacom stuff as in the attached xorg.conf.
I thought maybe so. Yep, that did it, works spot on -left right inverted, no calibration needed.

Not sure how these files get corrupted,some update or upgrade perhaps, but I know where to look next time

Thanks so much Favux

cgul1

---

### Post by Favux on 2010-04-18
Outstanding!  You're welcome.

Yep, next time it won't be a mystery and you'll be able to solve it quickly.

---

### Post by lps1 on 2010-04-19
> **Favux said:**
> Hi everyone,

**[SIZE=3]Here's Magick Rotation 0.3-3[/SIZE]**

Download the attachment onto your desktop. Extract it. Open the Magick Rotation 0.3-3 folder.  Instructions are in the Magick-README.txt included in the folder.


Edit0: This version, 0.3, incorporates Ayuthia's debugging tool which can now be run from the command line and from the gui.  It also has more cosmetic improvements.  I think it looks pretty good now.  Since there is "significant" change to the code, all in all, I think bringing it out as version 0.3 is justified. 

Edit1:  Since there have been only 5 downloads of 0.3 I substituted 0.3-1 for it rather than do a new post.  There are no functional changes, just cosmetic.  Magick 0.3-1 now has borders for the Setup and About windows.  With the border for the About window the OK button doesn't look quite so hideous so I finally moved it there, where it "belongs".

Edit2:  While there have been 10 downloads of 0.3-1 I decided to substitute 0.3-2 for it.  There have been no functional changes.  Magick 0.3-2 has stock gtk buttons and the About button moved back to the setup window.  This should be the "final" look.

Edit3:  Magick 0.3-3 now has a GPL, gali98's check for '~/.config/autostart/' and if not mkdir code (e.g. the directory can be absent in clean install), and a minor cosmetic improvement.  I decided to put it side by side with 0.3-2 so you can use .3-2 as a fall back if there is a problem.

I've installed your applet 0.3, which looks and good and rotates the screen nicely with lucid beta 2, however both my touch and pen (which are working well in normal mode) are registering in opposite parts of the screen. So if click bottom left, the mouse is shown top right and so on. Is there a setting I need to change?

---

### Post by Favux on 2010-04-19
Hi lps1,

Magick currently will only work if 'xinput --list' and 'xsetwacom list' in a terminal returns stylus, eraser, and touch.

There have been changes in the linuxwacom naming conventions and now you are 'suppose' to use the device name.

We'll have to figure out how to parse the device names and add that code to Magick for it to work in Lucid.  Unless you can use an xorg.conf to generate stylus, eraser, and touch.

---

### Post by lps1 on 2010-04-19
You are right, xinput --list shows n-trig pen and n-trig touchscreen whilst xsetwacom list doesn't return anything.

As for xorg,conf, this doesn't seem to mention either driver - it says HAL is used and auto detects the drivers.

---

### Post by Favux on 2010-04-19
That's a little strange.  HAL isn't installed in a default Lucid install AFAIK.

I wonder what would happen if we added the standard Wacom sections to xorg.conf.  They specify the wacom driver and identify the devices as stylus, eraser, and touch.  I know you can have an xorg.conf in Lucid.

Are you interested in experimenting?.  But be warned I think we'd have a relatively high risk of breaking X.  I won't be adding Lucid for at least a few weeks if you want to wait

You can try adding method 3, wacomrotate, by Tom Jaeger because the new version should handle Lucid by parsing the device names.

---

### Post by lps1 on 2010-04-20
Hello.

I just tried wacomrotate but that doesn't work either.  The magicrotate seems better in that it rotates the screen and the mouse pointer correctly but it displays the mouse pointer in the opposite part of the screen. It's also my understanding that HAL is being removed here is my xorg,conf which seems to imply it's being used, but it may just be my lack of understanding!
I don't mind trying some experiments, so longs as I can undo things when they go wrong! I've only being using ubuntu for a month so am a bit short on experience but am learning quick.

```
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice" 
#    Identifier        "stylus" 
#    Driver            "wacom" 
#    Option        "Device"    "/dev/input/event8"
#    Option            "Type"        "stylus"
#    Option            "USB"         "on" 
#    Option            "Button2"     "3"  # make side-switch a right button 
#    Option        "TopX"        "0"
#    Option        "TopY"        "0"
#    Option        "BottomX"    "9600"
#    Option        "BottomY"    "7200"
#EndSection 
#Section "InputDevice" 
#      Identifier        "eraser" 
#      Driver            "wacom" 
#    Option        "Device"    "/dev/input/wacom"
#      Option            "Type"           "eraser"
#      Option            "USB"            "on" 
#EndSection 
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice" 
#    Identifier        "touch" 
#    Driver            "wacom" 
#    Option        "Device"    "/dev/input/n-trig-touch"
#    Option          "Type"           "touch"
#    Option          "USB"            "on" 
#    Option        "TopX"        "0"
#    Option        "TopY"        "0"
#    Option        "BottomX"    "9600"
#    Option        "BottomY"    "7200"
#EndSection

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    # commented out by update-manager, HAL is now used and auto-detects devices
    # Keyboard settings are now read from /etc/default/console-setup
    #    InputDevice    "stylus"    "SendCoreEvents"
    #   Remove the comment below if you have an eraser.
    #    InputDevice    "eraser"    "SendCoreEvents"
    # commented out by update-manager, HAL is now used and auto-detects devices
    # Keyboard settings are now read from /etc/default/console-setup
    #    InputDevice    "touch"        "SendCoreEvents"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
Option "ForceLowPowerMode" "true"
    #    Driver    "fglrx"
EndSection
```

---

### Post by Alejandro Nova on 2010-04-23
I can report that this is working with my TX1000 tablet, but a lot of changes are needed. Also, I'm testing this in Fedora 12, so, your mileage may vary.

The key here is to make the touchscreen work with evdev. I think Lucid should have it working. The results with the latest blob are disastrous (it works, but it totally screws up the powertop wake up count), so, for the sake of Free software, we should make it. If you've found a way of making an eGalax touchscreen to work with evdev under Karmic, please, let me know. Under Fedora 12, the key file is this (please, Ubuntu developers, watch this for Lucid!)

```
[faeris@faeris ~]$ cat /etc/hal/fdi/policy/11-egalax.fdi 

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="eGalax">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.Calibration" type="string">45 4013 125 3975</merge>
      </match>
    </match>    
  </device>
</deviceinfo>

```

This is a HAL fdi file, coming from here: [https://bugzilla.redhat.com/show_bug.cgi?id=473144](https://bugzilla.redhat.com/show_bug.cgi?id=473144) . If you can convert this into an UDEV rule, we can have this working under Lucid. Fedora 13 (also dropping HAL) is making my touchscreen finally work (although uncalibrated) out of the box.

The procedure for automagic rotation is the same, but details vary. This is my autorotate.sh.

```
#!/bin/sh
OLDMODE=$(cat /sys/devices/platform/hp-wmi/tablet)
while true; do
    MODE=$(cat /sys/devices/platform/hp-wmi/tablet)
    if [ "$MODE" != "$OLDMODE" ]
    then
        #echo "$MODE - $OLDMODE"
        case "$MODE" in
            "0")
                # Do something
                echo "Normal mode"
                xrandr -o normal 
                xinput set-prop 10 "Evdev Axis Inversion" 0 0
                xinput set-prop 10 "Evdev Axes Swap" 0
                ;;
            "1")
                # Do something else
                echo "Tablet mode"
                xrandr -o left
                xinput set-prop 10 "Evdev Axis Inversion" 1 0
                xinput set-prop 10 "Evdev Axes Swap" 1
                ;;
        esac
        OLDMODE=$MODE
    fi
    sleep 2s
done

```

This rotates the screen, with the hp_wmi module running, when I fold the screen into tablet mode. Yes, HP WMI also works with the tx1000.

---

### Post by Alejandro Nova on 2010-04-24
About the missing buttons.

Nobody paid attention to this: [http://quickstart.sourceforge.net/](http://quickstart.sourceforge.net/) . This link, found in my year old thread, "[Helpful Hints for a tx1000 (mark II)]("http://ubuntuforums.org/showthread.php?t=1040872")", points to a page of someone who wrote a driver for all these buttons. Moreover, this driver exposes a sysfs interface to query the status of every button, making the delivery of real Vista Quick Start functionalities possible under Linux (you press the DVD button **with the computer turned off**, the computer starts and quickly launches a DVD player, the driver provides samples of how to do this).

This works with the tx1000, but, as you can see, a lot of these theories works across this family. Can you lend me a hand with this?

Edit: This is only useful to manage DVD and the Q button, so, it can be useless for this case. But look into the code, nevertheless. Also, unlocking another part of our laptop's functionalities isn't bad either.

Edit 2: Tested, it works. Here is my script, running at the start of my KDE session. It's modeled after the automagic-rotation script. I don't know how to shorten the process and make Linux forget about loading a desktop, loading the DVD player or media center directly.

```
#!/bin/sh
START=$(cat /sys/devices/platform/quickstart/pressed_button)
case "$START" in
        "none")
                # Do nothing
                ;;
        "QBTN")
                # This is the Q button. Let's launch Moovida!
                moovida
                echo "none" > /sys/devices/platform/quickstart/pressed_button
                ;;
        "DBTN")
                # DVD button. Launch SMPlayer (we'll play a DVD!)
                smplayer dvd://
                echo "none" > /sys/devices/platform/quickstart/pressed_button
esac

```

---

### Post by sacredpotato on 2010-04-25
ok I have tried both the script and applet methods for autorotation wen swiveling on my touchsmart tx2 running 10.04 and they work ... sorta


both have this problem but right now i'm using the applet and when I rotate the screen and lay it flat into tablet mode the display flips 180 as it should. but the problem is that the mouse/touch/pen input doesn't rotate :-(

if anyone can assist me with the to get t working i would be forever grateful. you can reply here or pm me in the forums.

---

### Post by Ayuthia on 2010-04-25
> **sacredpotato said:**
> ok I have tried both the script and applet methods for autorotation wen swiveling on my touchsmart tx2 running 10.04 and they work ... sorta


both have this problem but right now i'm using the applet and when I rotate the screen and lay it flat into tablet mode the display flips 180 as it should. but the problem is that the mouse/touch/pen input doesn't rotate :-(

if anyone can assist me with the to get t working i would be forever grateful. you can reply here or pm me in the forums.

It could be because of the naming convention.  Can you provide the results of:
```
xinput --list
```

---

### Post by sacredpotato on 2010-04-25
ok first off WOW thank you for such a fast response ^_^

2nd here is that output

[http://paste.ubuntu.com/422292/](http://paste.ubuntu.com/422292/)

---

### Post by sacredpotato on 2010-04-25
also if I were to purchase support from ubuntu which level of support do you guys think I need to purcahse for stuff like this? the beginner or middle teir support?

---

### Post by Ayuthia on 2010-04-25
I was able to see two N-Trig Pen and N-Trig Touchscreen entries there.  The reason why the scripts aren't working is because they are using "stylus" instead of "N-Trig Pen" and "touch" instead of "N-Trig Touchscreen".

Before we can test it with the following:
```
xsetwacom set "N-Trig Pen" rotate CCW
```
we need to most likely clear out one of the duplicate entries because it could cause some problems.

Can you post the information in /var/log/Xorg.0.log?  It will help us see what is happening and help fix the entries.

---

### Post by Ayuthia on 2010-04-25
> **sacredpotato said:**
> also if I were to purchase support from ubuntu which level of support do you guys think I need to purcahse for stuff like this? the beginner or middle teir support?

I am not for sure about how they would handle things like this.  The changes here are not all supplied by Ubuntu's repositories so I am not for sure if they would handle it or not.

---

### Post by sacredpotato on 2010-04-25
[http://paste.ubuntu.com/422525/](http://paste.ubuntu.com/422525/)

that should be that file you asked for

like I said right now I'm using the applet method for magic rotate but if it's easier to troubleshoot/fix I can go back to the script it's not big deal.

thank you again for all the help.

---

### Post by Favux on 2010-04-25
Hi sacredpotato,

Your Xorg.0.log shows evdev, not linuxwacom has your tablet.

If linuxwacom had your tablet you could modify the script using:

styus = "N-Trig Pen"

touch = "N-Trig Touchscreen"

probably with the quotes.  And since you do not have an eraser you can remove those two lines.

Figuring out how to parse the new device names in the applet is another matter.  Until I load Lucid I'm not even going to try.  Notice it says it only works up to and with Karmic.  Sorry.

---

### Post by Ayuthia on 2010-04-26
I am currently reinstalling a fresh version of Lucid on my laptop so that I can see what is happening.  Once I get that updated, I will let you know what we need to do to get the stylus and/or touch over to Wacom.

Favux, just to let you know, I am looking at the code a little bit.  I think I have an idea about how to get the information that we need.  xsetwacom --list provides the names that we need and we can collect the information from there.  The question that I have is if we want to split out the stylus and touchscreen because it looks like there are going to be people who will be using evdev and Wacom drivers.

---

### Post by Favux on 2010-04-26
Hi Ayuthia,

> The question that I have is if we want to split out the stylus and touchscreen because it looks like there are going to be people who will be using evdev and Wacom drivers.
Exactly.  And has the naming convention stabilized?
> I think I have an idea about how to get the information that we need.
As usual, I'm looking for all the help I can get!  I have been thinking about it, and it may not be as straightforward as I originally thought.  Depends on the "design" decisions we go with.

Since I didn't originally setup to install multiple releases I have to go through some tedious back up and disk partitioning stuff, if I can persuaded Vista to go along and part with some of the extensive disk space it's occupying, to install Lucid.  And of course am very concerned about losing data.  But this is boring to others.

---

### Post by sacredpotato on 2010-04-26
btw while I have been watch you two make great progress for some time now I was unable to follow your guide successfully so this is the walk through I followed to get touch working in lucid and is probably why evdev has control of tablet input

wget [http://linuxfans.keryxproject.org/packages/ntrig/installer.tar.bz2](http://linuxfans.keryxproject.org/packages/ntrig/installer.tar.bz2)
tar -xvjf installer.tar.bz2
cd installer
./installer.py all

perhaps I should wait till full release and I reinstall linux completely and just try to walk through your steps again ... but I think I always fail at the patching and compiling sections.

---

### Post by Ayuthia on 2010-04-26
Actually, Lucid is currently defaulting to evdev for the pen.  I am currently in it right now and I am going to see if I can cat an xorg.conf.d file for the wacom devices.

---

### Post by Ayuthia on 2010-04-26
At this time, I have only been able to get it to work through xorg.conf.  If you don't have /etc/X11/xorg.conf, create the file with:
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        InputDevice    "stylus"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "stylus"
        Option "Type" "stylus"
        Option "Device" "/dev/input/n-trig"
        Option "Button2" "3"
EndSection

```
That should get the stylus back to normal and using wacom.  If you want the touch there too:
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        InputDevice    "stylus"
        InputDevice    "touch"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "stylus"
        Option "Type" "stylus"
        Option "Device" "/dev/input/n-trig"
        Option "Button2" "3"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "touch"
        Option "Type" "touch"
        Option "Device" "/dev/input/n-trig-touch"
EndSection

```
If you don't have the udev rules created to create the /dev/input/n-trig-touch and n-trig, substitute it with /dev/input/event7 for your pen and /dev/input/event8 for your touch.

By the way, if you use both the touch and pen with wacom, you should be able to use the applet again.  I have not tested that out yet though.

---

### Post by Favux on 2010-04-26
Interesting.

> if you use both the touch and pen with wacom, you should be able to use the applet again.
Right, with the Identifier specifying stylus or touch.  I was wondering.

By the way Ping just submitted a big patch for 2 finger gestures and Chris was impressed.  They're waiting on Peter's review.  This may address some of Rafi's issues with linuxwacom gestures.  I don't know how much it brings it in line with the evdev version of multi-touch.

---

### Post by sacredpotato on 2010-04-26
I can't wait for the day when I can get multi touch up and working easily on this machine ^_^

I'll edit my xorg.conf as soon as I go to lunch and report back if it works

---

### Post by Ayuthia on 2010-04-26
> **Favux said:**
> Interesting.


Right, with the Identifier specifying stylus or touch.  I was wondering.

By the way Ping just submitted a big patch for 2 finger gestures and Chris was impressed.  They're waiting on Peter's review.  This may address some of Rafi's issues with linuxwacom gestures.  I don't know how much it brings it in line with the evdev version of multi-touch.

The main difference with evdev and wacom is that wacom is using gestures and evdev is using multiple pointers.

I will have to try out the patch and see it I can get it running with N-trig.  It still looks like it might be difficult because of their channel usage.  It would have been nice if they could have converted their kernel modules to use ABS_MT* values instead.  I think that it was rejected earlier.  I will either dig it up or talk to Chris about it.

---

### Post by pepar on 2010-04-26
Hello all,


**!!!!** Please check my updated post/script in [**HOW TO: Set up the HP TX2z and Dell XT & XT2 (N-trig digitizer) in Ubuntu**]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9180420&postcount=953") thread. **!!!!**



First of all, thanks to all of you for your efforts & good documentation (although it seems to be getting 'a little' complex).
Special thanks to Favux, rafiyr & Ayuthia.


I have a HP tx2z 1020 w. Vista firmware.

Getting everything:
- touch with grab
- stylus with button
- rotation with hinge (hp-wmi)
- rotation with bezel button (??)
- on-screen keyboard
....

to work (correctly) is quite a challenge. Unfortunately, this would be a deal breaker for most any newbie/MS Win convert.


Here are some of my findings, and a little script I use (I have converted a couple of tx2z to linux).

On one, I have lucid installed (since alpha1).
- I am using the patched hid_ntrig & input-wacom modules.
- My xorg.conf only contains the 'fglrx' section for the ATI video card.
- I modified '10-wacom.conf' to get the stylus button to work.
- Have not tried to get multitouch to work (would like to, but seems to be in a state of flux at the moment).

The stylus ends up being controlled by wacom & touch by evdev.
Both xinput & xsetwacom list devices twice, I have no idea why.

I use the script, attached to a button added to the panel, for a clockwise rotation with each click:
```

/usr/local/bin/rotator.sh  rturn   wacom stylus   evdev touch

```

Usage: rotator.sh   direction|position    method  device    [...]

where:
[INDENT]direction = (lturn|l|rturn|r|right|left|normal|inverted)
method = (wacom|evdev)
device = (stylus|touch)
[/INDENT]

The script could be improved, ie. adding support for multi-touch device, more error checking / feedback, ...

Hope it helps someone (getting closer to a better "Out Of the Box" experience, and maybe "Just Works" some day).


PEP


```

#!/bin/sh
#
# enhanced rotate script, based on rafiyr's http://ubuntuforums.org/showpost.php?p=9133869&postcount=918
# and others (gathered on forums).
# Added rturn & lturn, to rotate screen left/right a quarter turn at a time (mainly
# because default hp-wmi module was not returning an 'event' for the 'Rotate' button on the bezel of my tx2z).
#
# This script can be 'attached' to a 'rotate' applet on the panel (w. 90° rotation).
# 	with (for example) command: ...../rotator.sh rturn evdev touch wacom stylus
#
# Usage: rotator.sh   direction|position    method  device    [...]
#
# where:	direction = (lturn|l|rturn|r|right|left|normal|inverted)
#		method = (wacom|evdev)
#		device = (stylus|touch)
#

syntax_error=0

orientation=$1
shift

#
# Parse & get current orientation, and do integer conversion (in order to be
# able to (in/de)crement for each 90° rotation, also needed later for 'easier' comparison)
#
current_orientation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"
case $current_orientation in
	normal)
		current_orientation=0
	;;
	left)
		current_orientation=1
	;;
	inverted)
		current_orientation=2
	;;
	right)
		current_orientation=3
	;;
esac

#
# Parse the orientation parameter & in case of 'rturn' and 'lturn', check the current
# orientation and make sure that the next value is within bound.
#
case $orientation in
	rturn | r)
		orientation=$((current_orientation-1))
		if [ $orientation -le "-1" ]; then
			orientation=3
		fi
	;;
	lturn | l)
		orientation=$((current_orientation+1))
		if [ $orientation -ge "4" ]; then
			orientation=0
		fi
	;;
	normal | 0)
		orientation=0
	;;
	left | 1)
		orientation=1
	;;
	inverted | 2)
		orientation=2
	;;
	right | 3)
		orientation=3
	;;
	* )
		syntax_error=1
	;;
esac

#
# Check if new orientation is different from current one.
#
if [ $orientation -eq $current_orientation ]; then
	echo "Nothing to do."
	exit
fi

#
# repeat the device rotation/calibration for all devices passed as parameters
#
while [ $# -gt 0 ]
do
	# get and (crudely) parse method for errors
	method=$1; shift
	case $method in
		wacom ) ;;
		evdev ) ;;
		* )	syntax_error=1 ;;
	esac

	#
	# get and (crudely) parse device for errors
	# and convert device name to number
	#
	device=$1; shift
	case $device in
		stylus )
			device=`xinput --list --short "N-Trig Pen" | cut -c 45-46`
		;;
		touch )
			device=`xinput --list --short "N-Trig Touchscreen" | cut -c 45-46`
		;;
		* )	syntax_error=1 ;;
	esac

	if [ $syntax_error -ne 0 ]; then
		echo "Usage: `basename $0` Direction|Orientation   Method Device  [...]"
		echo "\tdirection = (lturn|l)|(rturn|r)|(right|3)|(left|1)|(normal|0|(inverted|2)"
		echo "\tMethod: (wacom|evdev)"
		echo "\tDevice: (stylus|touch)"
		exit 1
	fi

	#
	# Set rotation plane/geometry parameters, and if using "wacom"
	# method, also perform device/calibration rotation
	#
	swap=0
	invert_x=0
	invert_y=0

	real_topx=0
	real_topy=0
	real_bottomx=9600
	real_bottomy=7200

	case $orientation in
		0)
			if [ $method = "wacom" ]; then
				xsetwacom set $device rotate NONE
			else
				swap=0
				invert_x=0
				invert_y=0
				topx=$real_topx
				topy=$real_topy
				bottomx=$real_bottomx
				bottomy=$real_bottomy
			fi
		;;
		1)
			if [ $method = "wacom" ]; then
				xsetwacom set $device rotate CCW
			else
				swap=1
				invert_x=1
				invert_y=0
				topx=$real_topx
				topy=$real_topy
				bottomx=$real_bottomy
				bottomy=$real_bottomx
			fi
		;;
		2 )
			if [ $method = "wacom" ]; then
				xsetwacom set $device rotate HALF
			else
				swap=0
				invert_x=1
				invert_y=1
				topx=$real_topx
				topy=$real_topy
				bottomx=$real_bottomx
				bottomy=$real_bottomy
			fi
		;;
		3 )
			if [ $method = "wacom" ]; then
				xsetwacom set $device rotate CW
			else
				swap=1
				invert_x=0
				invert_y=1
				topx=$real_topx
				topy=$real_topy
				bottomx=$real_bottomy
				bottomy=$real_bottomx
			fi
		;;
	esac

	#
	# If using "evdev" method, adjust the device (touch/calibration) accordingly
	#
	if [ $method = "evdev" ]; then
		xinput set-prop "$device" "Evdev Axes Swap" $swap
		xinput set-prop "$device" "Evdev Axes Swap" $swap
		xinput set-prop "$device" "Evdev Axis Inversion" $invert_x $invert_y
		xinput set-prop "$device" "Evdev Axis Calibration" $topx $bottomx $topy $bottomy
	fi
done

#
# Perform actual rotation of the X display/screen
#
xrandr -o $orientation


```


**!!!!** Please check my updated post/script in [**HOW TO: Set up the HP TX2z and Dell XT & XT2 (N-trig digitizer) in Ubuntu**]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9180420&postcount=953") thread. **!!!!**

---

### Post by Favux on 2010-04-26
Hi pepar,

Welcome to Ubuntu Forums!

And thank you for your report and the rotation script!

You're correct, it has gotten complicated.  But that's partly due to things being so different for each release, the changing hid-ntrig.c, and also not finding an "optimal" solution yet (esp. for multi-touch).

I'm going to encourge you to violate forum convention and double post.  I think your post would be valuable on the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492") thread for rafyir and others to see.

---

### Post by Ayuthia on 2010-04-26
> **pepar said:**
> Hello all,

First of all, thanks to all of you for your efforts & good documentation (although it seems to be getting 'a little' complex).
Special thanks to Favux, rafiyr & Ayuthia.


I have a HP tx2z 1020 w. Vista firmware.

Getting everything:
- touch with grab
- stylus with button
- rotation with hinge (hp-wmi)
- rotation with bezel button (??)
- on-screen keyboard
....

to work (correctly) is quite a challenge. Unfortunately, this would be a deal breaker for most any newbie/MS Win convert.


Here are some of my findings, and a little script I use (I have converted a couple of tx2z to linux).

On one, I have lucid installed (since alpha1).
- I am using the patched hid_ntrig & input-wacom modules.
- My xorg.conf only contains the 'fglrx' section for the ATI video card.
- I modified '10-wacom.conf' to get the stylus button to work.
- Have not tried to get multitouch to work (would like to, but seems to be in a state of flux at the moment).

The stylus ends up being controlled by wacom & touch by evdev.
Both xinput & xsetwacom list devices twice, I have no idea why.

PEP




You might try installing input-utils and run:
```
sudo lsinput
```
I am thinking that you are getting two of the same devices because of how the Vista firmware is created.  It has an if0 and if1 section and I am thinking that you might have two different events with the same name.

It might be possible to remove one by adding some more information to your 10-wacom.conf to only point to a particular event or the /dev/input/by-path event.

Please feel free to post your 10-wacom.conf and results of your lsinput information.  It could be helpful. 

As for the amount of work needed for Lucid, I have found that a reinstall of Lucid (I reinstalled it with the rc version today) and the only thing that I ended up doing was run an update then configured my wacom.conf file to use the wacom driver for my stylus.  There is no need to patch the kernel module anymore and you don't even have to patch the wacom source.  So it has gotten better but it was working a little more nicely prior to the rc release from that I have heard because it was defaulting the stylus automatically to the Wacom driver.

---

### Post by pepar on 2010-04-27
> **Ayuthia said:**
> You might try installing input-utils and run:
```
sudo lsinput
```
I am thinking that you are getting two of the same devices because of how the Vista firmware is created.  It has an if0 and if1 section and I am thinking that you might have two different events with the same name.

It might be possible to remove one by adding some more information to your 10-wacom.conf to only point to a particular event or the /dev/input/by-path event.

Please feel free to post your 10-wacom.conf and results of your lsinput information.  It could be helpful. 

My 10-wacom.conf:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
#       Identifier "Wacom N-Trig class"
#       MatchProduct "HID 1b96:0001"
        Identifier "N-Trig-Pen"
        MatchIsTablet "on"
        Driver "wacom"
        MatchDevicePath "/dev/input/event*"
        Option "Type" "stylus"
        Option "Button2" "3"
EndSection

```

The output of 'lsinput':
```
root:/# lsinput 
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event3
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event4
   bustype : BUS_ADB
   vendor  : 0x1
   product : 0x1
   version : 256
   name    : "Macintosh mouse button emulation"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event5
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event6
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event7
   bustype : BUS_USB
   vendor  : 0x64e
   product : 0xa104
   version : 800
   name    : "HP Webcam"
   phys    : "usb-0000:00:13.2-2/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event8
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Pen"
   phys    : "usb-0000:00:14.5-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event9
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Touchscreen"
   phys    : "usb-0000:00:14.5-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Pen"
   phys    : "usb-0000:00:14.5-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event11
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Touchscreen"
   phys    : "usb-0000:00:14.5-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event12
   bustype : BUS_PCI
   vendor  : 0x10ec
   product : 0x268
   version : 1
   name    : "HDA Digital PCBeep"
   phys    : "card0/codec#0/beep0"
   bits ev : EV_SYN EV_SND

/dev/input/event13
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS


```

> 
As for the amount of work needed for Lucid, I have found that a reinstall of Lucid (I reinstalled it with the rc version today) and the only thing that I ended up doing was run an update then configured my wacom.conf file to use the wacom driver for my stylus.  There is no need to patch the kernel module anymore and you don't even have to patch the wacom source.  So it has gotten better but it was working a little more nicely prior to the rc release from that I have heard because it was defaulting the stylus automatically to the Wacom driver.

Sounds good.
Have not tried the RC, but before, 'things' also worked :) ... but just not 'correctly' enough. :confused:
Touch worked but could not click or grab, so somewhat useless.
Stylus worked but had no right click/button.

We'll get there (hopefully before final).
Thanks.


PEP

---

### Post by Ayuthia on 2010-04-27
> **pepar said:**
> My 10-wacom.conf:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
#       Identifier "Wacom N-Trig class"
#       MatchProduct "HID 1b96:0001"
        Identifier "N-Trig-Pen"
        MatchIsTablet "on"
        Driver "wacom"
        MatchDevicePath "/dev/input/event*"
        Option "Type" "stylus"
        Option "Button2" "3"
EndSection

```

The output of 'lsinput':
```
root:/# lsinput 
/dev/input/event8
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Pen"
   phys    : "usb-0000:00:14.5-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event9
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Touchscreen"
   phys    : "usb-0000:00:14.5-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Pen"
   phys    : "usb-0000:00:14.5-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

/dev/input/event11
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "N-Trig Touchscreen"
   phys    : "usb-0000:00:14.5-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

```


From the information above, it does show that there are two input devices that have the same name for the Pen and Touchscreen.  I am thinking that we have the /dev/input/by-path information, we can add an additional entry to help ignore the device but I could be wrong.  I aqm going to pass this on to rafiyr to review and see if there is a way to prevent this at the kernel level.

My thought is that we can add an entry like:
```

Section "InputClass"
        Identifier "Wacom N-Trig ignore"
        MatchProduct "N-Trig Pen"
        MatchDevicePath "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-mouse"
        Option "Ignore" "on"
EndSection

```
Of course, the path listed in my example might not be the correct one.  You will need to check your list of /dev/input/by-path listing:
```

ls -l /dev/input/by-path

```

---

### Post by martinjochimsen on 2010-05-06
Hi 

I'm using the script for Magic Rotation from post #315.
It works really great and I have only changed one thing. I prefer to have the screen rotate 180 degrees so I changed this part

```
.
.
## these can be set by config ##
# pause before pooling
waittime=0.25
# rotate
rotate_mode=['right', 'CW']
.
.
```

to 

```
.
.
## these can be set by config ##
# pause before pooling
waittime=0.25
# rotate
rotate_mode=['inverted', 'HALF']
.
.
```

How can I make Onboard startup with the Magic_Rotation script instead of CellWriter?
I have tried to just change "cellwriter" to "onboard" the two places where it says "cellwriter", 

before
```
# run in tablet
run_tablet="cellwriter --show-window"
# run before go to tablet
run_tablet_before=""
# run in normal
run_normal="cellwriter --hide-window"
```

after

```
# run in tablet
run_tablet="onboard --show-window"
# run before go to tablet
run_tablet_before=""
# run in normal
run_normal="onboard --hide-window"
```

but that didn't do anything - except Cellwriter didn't startup either!
I can't see any other places where to make the change.

Martin :-)

---

### Post by Ayuthia on 2010-05-07
> **martinjochimsen said:**
> Hi 

I'm using the script for Magic Rotation from post #315.
It works really great and I have only changed one thing. I prefer to have the screen rotate 180 degrees so I changed this part

```
.
.
## these can be set by config ##
# pause before pooling
waittime=0.25
# rotate
rotate_mode=['right', 'CW']
.
.
```

to 

```
.
.
## these can be set by config ##
# pause before pooling
waittime=0.25
# rotate
rotate_mode=['inverted', 'HALF']
.
.
```

How can I make Onboard startup with the Magic_Rotation script instead of CellWriter?
I have tried to just change "cellwriter" to "onboard" the two places where it says "cellwriter", 

before
```
# run in tablet
run_tablet="cellwriter --show-window"
# run before go to tablet
run_tablet_before=""
# run in normal
run_normal="cellwriter --hide-window"
```

after

```
# run in tablet
run_tablet="onboard --show-window"
# run before go to tablet
run_tablet_before=""
# run in normal
run_normal="onboard --hide-window"
```

but that didn't do anything - except Cellwriter didn't startup either!
I can't see any other places where to make the change.

Martin :-)

onboard does not have the --show-window/--hide-window option so the application will not start up.  I am not able to find any option that will allow it to go to minimize mode via the command line.  If you remove the --show-window portion, it will start it up.  An option to make it go away (instead of --hide-window) is to try something like "killall onboard".

---

### Post by martinjochimsen on 2010-05-07
> **Ayuthia said:**
> onboard does not have the --show-window/--hide-window option so the application will not start up.  I am not able to find any option that will allow it to go to minimize mode via the command line.  If you remove the --show-window portion, it will start it up.  An option to make it go away (instead of --hide-window) is to try something like "killall onboard".

OK. I have put Onboard in my taskbar, so I'll settle with that.
Can I just comment out the to lines with cellwriter --show/hide window without breaking anything?
I'd rather just use Onboard.

---

### Post by Ayuthia on 2010-05-07
> **martinjochimsen said:**
> OK. I have put Onboard in my taskbar, so I'll settle with that.
Can I just comment out the to lines with cellwriter --show/hide window without breaking anything?
I'd rather just use Onboard.

You should be able to configure that in the setup screen instead of changing the code.  There should be an green arrow icon in the taskbar that you can right-click and select setup.  You can then click on the Advanced Setup arrow and you should see the boxes that contain the cellwriter information.  You can then clear out those lines and all should be fine after that.

However, if you want to remove it from the code, instead of commenting it out, change it so that it only has the quotes:
```

# run in tablet
run_tablet=""
# run before go to tablet
run_tablet_before=""
# run in normal
run_normal=""

```
This is where the run_normal variable is defined so you might run into problems if you comment it out.

---

### Post by martinjochimsen on 2010-05-08
> **Ayuthia said:**
> You should be able to configure that in the setup screen instead of changing the code.  There should be an green arrow icon in the taskbar that you can right-click and select setup.  You can then click on the Advanced Setup arrow and you should see the boxes that contain the cellwriter information.  You can then clear out those lines and all should be fine after that.

When I first installed the magic_rotation script I just copied the script to my home directory. Made it executable and made sure it would start up after boot.
I can se in the setup (right-click on the green arrow) that I can choose to rotate 180 degrees....but that did'nt work. I just changed it in the script (as I mentioned in an earlier post.)

> **Ayuthia said:**
> However, if you want to remove it from the code, instead of commenting it out, change it so that it only has the quotes:
```

# run in tablet
run_tablet=""
# run before go to tablet
run_tablet_before=""
# run in normal
run_normal=""

```
This is where the run_normal variable is defined so you might run into problems if you comment it out.

I'll give that a try. 
I'm not using Cellwriter (right now) so it would be nice it not to open up everytime I'm in tablet-mode

Martin :-)

---

### Post by Favux on 2010-05-08
Hi Martin,

In Magick when you right click on the green rotating arrow you chose Setup.  Then in Setup you chose the bolded Advanced Setup.  That's where you delete CellWriter.  Then Save.

You're the first person to say that setting Rotation state in Setup doesn't work for them.  So I don't know what's going on.

Remember we haven't updated Magick for Lucid's new wacom device names yet.  You might be able to use it in combination with wacomrotate.

---

### Post by martinjochimsen on 2010-05-08
> **Favux said:**
> Hi Martin,

In Magick when you right click on the green rotating arrow you chose Setup.  Then in Setup you chose the bolded Advanced Setup.  That's where you delete CellWriter.  Then Save.

You're the first person to say that setting Rotation state in Setup doesn't work for them.  So I don't know what's going on.

Well that's just typical me. I can mess up everything.
I just tried all over. Deleted everything with automagick in upstart-sessions and the script as well, and then installed it again  - the right way as the README says!
The green arrow came to the taskbar, but after the first reboot it didn't show up again. I had also "told" the automagick-script that I wanted the screen to rotate 180 degrees (inverted), and that worked after the second reboot AND CellWriter doesn't start up anymore either.

I don't have the green arrow, Cellwriter doesn't start up, the screen rotates perfect, touch works partly. So I'm happy for now!!! :-D

---

### Post by tarjxvf on 2010-05-09
The position of the cursor is way away from the true touch point after rotating to the portrait mode. Plus, it seems that the cursor moves in the direction perpendicular to the true direction: if I flip my finger up and down, the cursor moves left and right, etc. 

I've tried the Magick Rotation 0.3-3, Fauvx's No_Compiz_Rotation script, the script in Method 1. All the same. 

I installs Lucid (10.04) 64bit in my HP tx2z-1000CTO tablet, and upgraded the kernel to 2.6.32 in the repository. I installed ATI fglrx driver. Other than these, I've made no change to the default system.

By the way, the cursor is accurate in the default landscape mode.

---

### Post by Favux on 2010-05-09
Hi tarjxvf,

Magick doesn't work in Lucid yet.  The wacom device names were changed which is why it doesn't work.  A combination of Magick plus wacomrotate (method 3) might work.  Also using a n-trig xorg.conf with the old identifiers should let Magick work.

To see the new device names enter in a terminal:
```
xinput --list
```
Then you substitute the new device names with quotes or the ID number into the appropriate lines in the script of your choice.

---

### Post by marranzano on 2010-05-10
for anyone who wishes to rotate the touchpad as well, there is a patched xserver-xorg-input-synaptics which allows to do this:

ubuntu thread:
[http://swiss.ubuntuforums.org/showthread.php?t=943297](http://swiss.ubuntuforums.org/showthread.php?t=943297)

website:
[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

ppa repository (karmic and lucid):
[https://launchpad.net/~aapo-rantalainen/+archive/ppa-aaporantalainen](https://launchpad.net/~aapo-rantalainen/+archive/ppa-aaporantalainen)

tested and works... :)
marranzano

---

### Post by sacredpotato on 2010-05-11
Wow favux you just answered my question that I have been struggleing with for days but you went a little over my head. I have good news though I found a local Linux tech that is comming over on sat to walk me through both your thread on getting touch working and this thread. ^_^

---

### Post by Favux on 2010-05-11
Hi sacredpotato,

If you still have Magick Rotation installed just right click on it and tell it to quit.  Then download and install Magick Rotation 0.4-beta1.  We're hoping this version works in Lucid.  It's at the same location as 0.3-3 and installs the same way.  You already have the green and red arrows in place.

Once it is installed go to Advanced Setup (right click on green arrow and chose Setup).  Then there some boxes labeled stylus, eraser, and touch with probably stylus, eraser, and touch entered in them.  Now replace the entries with:

stylus = N-Trig Pen

touch = N-Trig Touchscreen

The TX2z doesn't have an eraser so you can delete the eraser entry.  Save and close Setup and hopefully now rotation will work for you.  I think those are the correct names from your 'xinput --list' you posted earlier.

Good luck!

---

### Post by sacredpotato on 2010-05-11
Wow thanks I will try that within the next 30 min and get back to you.

---

### Post by sacredpotato on 2010-05-11
Btw favux I found a script on touchswipe.com that automates the whole process o getting touch working at least for lucid. Let me know if you want to check it out I can post it in your thread.

---

### Post by Favux on 2010-05-11
Sure I'd like to see it.  You know I have Ayuthia's script on the N-trig HOW TO that automates the install too, right?  I don't know which of Rafi's new patches for hid-ntrig.c it installs.  In other words I'm not sure how updated it is.  But it is pretty recent.

---

### Post by sacredpotato on 2010-05-11
ok the rotation didn't work (screen rotates touch input still doesn't) I setup the applet to use the N-Trig Pen and N-Trig Touchscreen but when I check the x-input --list both of those entries show up twice with 2 different IDs is there a way I can figure out which Id is the correct one and then call it by ID?

---

### Post by Favux on 2010-05-11
Hi sacredpotato,

I think it's the Vista firmware that does that, so you might want to consider updating the firmware.

You can use xxd to find out which events have data coming in on them, but the easiest thing is to just try the different ID numbers and find which ones work.

---

### Post by sacredpotato on 2010-05-11
so what syntax do I fill into the applet to use the IDs?

also just before I wiped 10.04 beta 2 and intalled the full release I intalled win 7 and the most up to date firmware.

---

### Post by Favux on 2010-05-11
Haven't had it tried yet, but I imagine just the id number.

OK, if it isn't the firmware it might be the hid-ntrig.ko.  Are you using the default Lucid one?  Although it might still be the firmware, like I said I'm not for sure.

---

### Post by cgul1 on 2010-05-11
Hello Favux et al,

Could not resist upgrading to lucid as it has worked fine since beta on my other machine.

Magick rotation works great under Karmic.
Getting ready to test magick-rotation-0.4-beta1, xinput list results:

```
jerry@jerry-tablet:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 eraser                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=14	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=18	[slave  keyboard (3)]
jerry@jerry-tablet:~$ 

```
looks like I have an eraser, but now stylus?
did I miss a step?

rotation works fine with beta, but stylus is not tracking
stylus works unrotated
Thanks for the help.
gcul1

******
SOLVED: was able to get stylus to work simply by putting "13" without the quotes in the Stylus box of Magick advanced setup dialog.

So, all I had to do to get this working on an TX2000 running Lucid (upgraded from Karmic) was to install the new beta of Magick and input the id# for my stylus. WOOT!
Touch seems to work fine, not sure about eraser...

---

### Post by sacredpotato on 2010-05-11
open terminal:

To download and extract:
CODE: SELECT ALL
cd
wget [http://linuxfans.keryxproject.org/packages/ntrig/installer.tar.bz2](http://linuxfans.keryxproject.org/packages/ntrig/installer.tar.bz2)
tar -xvjf installer.tar.bz2

To install the N-trig kernel module and Wacom driver:
CODE: SELECT ALL
cd installer
./installer.py all





ok that is the walkthrough I used to setup the touch... now the other thread mentions that touch should just work in 10.04 no setup needed so maybe I have the wrong firmware and that's why all this stuff is going wrong ... is there a way I can check which firmware I'm using from withing ubuntu? and can you link me the other script I think I might reinstall and try that script instead



after looking at Authia's script this is the same instructions ^_^ so at least I know I have that correct

guess I have to throw win7 back on and try to redo the firmware

---

### Post by Favux on 2010-05-11
Hi cgul1,

Excellent!  Our first succesful beta tester.  :)

So you used (Wacom ISDv4 93) for touch?


Hi sacredpotato,

I suspected the script you found was Ayuthia's.  Out of curiosity was Ayuthia credited?

The only way we currently have to determine firmware version is through the Windows Control Panel.  Windows is also the only way to install the firmware, and practically, the bios as well.  So there's good reason to have a Windows partition and dual boot.  The Windows partition doesn't have to be any larger than needed.

---

### Post by cgul1 on 2010-05-11
> **Favux said:**
> Hi cgul1,

Excellent!  Our first succesful beta tester.  :)

So you used (Wacom ISDv4 93) for touch?


I left 'touch' in the touch field. not sure I get all the functionality, but I can point with finger.(perhaps I do not fully get the touch function to begin with :)

also I just noticed that the stylus button works right click duty that I did not notice working before.

Great work!!!

---

### Post by marranzano on 2010-05-11
thnx
confirming that magick-rotation-0.4-beta1 works well in lucid, it automatically detected the right id's of stylus, eraser and touch: 12 11 13..

of course there's still the bug mentioned a few pages back of touch not maintaining the pointer in the right place after lifting up the finger.. :( ... hoping in a bugfix in the next release!?!

marranzano

---

### Post by Favux on 2010-05-11
Hi cgul1,

You should have single finger touch.  Select, drag, and click.  Thanks for the info., touch, ok.


Hi marranzano,

Outstanding!  Second beta tester confirmation.  Thanks.

The jump with touch when rotated was fixed in linuxwacom 0.8.6-1.  I don't know if it has made it's way to xf86-input-wacom yet, but I think so.  You could try cloning the git repository.  I don't think you were describing quite the same bug though.  Because the one I filed the bug report on had the pointer move right back to the finger when it retouched the screen.  The calibration was just a little off though.

---

### Post by marranzano on 2010-05-11
> **Favux said:**
> ...
The jump with touch when rotated was fixed in linuxwacom 0.8.6-1.  I don't know if it has made it's way to xf86-input-wacom yet, but I think so.  You could try cloning the git repository.  I don't think you were describing quite the same bug though.  Because the one I filed the bug report on had the pointer move right back to the finger when it retouched the screen.  The calibration was just a little off though.
favux... you're the man...
updated from git and touch now works great when rotated... the pointer will remain in place once the finger is lifted!!
therefore i can confirm that that patch didn't make it in xf86-input-wacom 1:0.10.5-0ubuntu4 but it's in git...
thanx =D> 
marranzano

---

### Post by Favux on 2010-05-11
Hi marranzano,

Great!  And once again you've provided more useful info.  Thanks.

---

### Post by cgul1 on 2010-05-11
Hello,
Yes, now I can confirm touch and stylus work great.
should eraser (back of pen) work in Xjournal as it does in the Windoz equivalent? Else where should eraser behavior be observed?

My settings are now:
Stylus: 13
Eraser: 12
Touch:  14

This is wonderful!!

---

### Post by sacredpotato on 2010-05-11
Ok I think I found my problem. I ran authia's script but haven't done anything else. Is there stuff I have to do in xorg or udev or something?

---

### Post by Favux on 2010-05-11
Hi cgul1,

Good!  Yes eraser should work in Xournal, Gimp, and Inkscape and any other program built for it.  You have to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").


Hi sacredpotato,

Yes you have to configure.  In Lucid you are "suppose" to use the .conf files.  You could try:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

 Section "InputClass"
 	Identifier "Wacom N-Trig Pen class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
 EndSection

 Section "InputClass" 
 	Identifier "Wacom N-Trig Touch class"
	MatchProduct "HID 1b96:0001|N-Trig Touchscreen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
 EndSection
# Created By eNoVa, Inspired by Favux ;P
```
in the 10-wacom.conf at /usr/lib/X11/xorg.conf.d/.  Or you could try the new udev rules and multi-touch xorg.conf on the How TO.

---

### Post by sacredpotato on 2010-05-12
Lol I feel dumb now. I kind of new since last week that I was missing that but I just didn't know what to do about it. I suppose I will try the multi touch.

---

### Post by cgul1 on 2010-05-12
> **Favux said:**
> Hi cgul1,

Good!  Yes eraser should work in Xournal, Gimp, and Inkscape and any other program built for it.  You have to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").


AHHH,(doh) great, yep xjournal and gimp configure and work properly, Inkscape a bit sketchy.

Thanks so much!

---

### Post by sacredpotato on 2010-05-13
ok favux I edited 10-wacom.conf at /usr/lib/X11/xorg.conf.d/ as you said and rebooted and it caused the touch to stop working so I reverted it back. is it possible that I need to do the udev thing instead?

---

### Post by Favux on 2010-05-13
Ha!  eNoVa had to add the touch snippet to get touch to work.  Oh well.
> is it possible that I need to do the udev thing instead? 
Sure.  Anyway I can't see how it would hurt.  Just make sure Lucid has the same directory.

---

### Post by sacredpotato on 2010-05-13
I think I give up I got a guy comming over on sat to help me set this up and get everything working (which I guess technically everything already works except the rotation) so I'll have him mess with that and try to get the rotation to work

---

### Post by nyxtom on 2010-05-14
This is weird, I've been trying to get my wacom drivers setup to actually list in xinput and xsetwacom but nothing is coming up. 

I know that the drivers are there because I can run each of the following commands and get results. I've been running Lucid Lynx and trying to get my Bamboo Wacom Pen and Touch to work.

```

lsusb | grep '[w|W]acom'
Bus 003 Device 005: ID 056a:00d1 Wacom Co., Ltd 

lshal | grep '[w|W]acom'
  info.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)

```

I know I have xorg-xserver-input-wacom yet:

```

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]


xsetwacom --list
~

```

What am I doing wrong?

---

### Post by Favux on 2010-05-14
Hi nyxtom,

Welcome to Ubuntu forums!

Did you compile a newer wacom.ko (the usb kernel driver) to replace the default one in Lucid?

Hope this helps.

---

### Post by nyxtom on 2010-05-14
I don't think I have actually...

---

### Post by nyxtom on 2010-05-14
> **Favux said:**
> Hi nyxtom,

Welcome to Ubuntu forums!

Did you compile a newer wacom.ko (the usb kernel driver) to replace the default one in Lucid?

Hope this helps.

Following the order of:
[http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html)
That works :D

Thanks!

---

### Post by Favux on 2010-05-14
Hi nyxtom,

Great!  :)

Since you used linuxwacom 0.8.6-2 you shouldn't have needed to 'cd src/2.6.30/'.  It should have compiled wacom.ko without that  directory change.  The problem was suppose to be fixed with 0.8.6-2.  Did you find that to be true?

---

### Post by nyxtom on 2010-05-14
Performing a make install was available. I think the only step I was missing was performing the modprobe. After reading up what exactly that does, it has all become apparently clear to me.

Thanks again!

Now, I just need to configure my wacom buttons in the .conf.

---

### Post by Favux on 2010-05-14
Sample:
```
Option "Button2" "3"
```
See Section 2 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by martinjochimsen on 2010-05-14
> **marranzano said:**
> favux... you're the man...
updated from git and touch now works great when rotated... the pointer will remain in place once the finger is lifted!!
therefore i can confirm that that patch didn't make it in xf86-input-wacom 1:0.10.5-0ubuntu4 but it's in git...
thanx =D> 
marranzano


Hi Marranzano

It's great to hear that touch works when rotated after you have "updated from git"...but what is git and how did you do it?
I may have missed something in a previous post, but I would be happy to at least get a hint!!! :-)
By the way I have installed magick-rotation-0.4-beta1 and that works fine, but I don't see (feel) any difference from Magick_Rotation_0.3-3. Stylus and touch works except for the thing with the pointer that jumps when I lift my finger.

Martin

---

### Post by Favux on 2010-05-14
Hi Martin,

He cloned the git repository.  Instructions in Appendix 5 in the [linuxwacom How TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Read Lucid near the top first.

---

### Post by martinjochimsen on 2010-05-14
> **Favux said:**
> Hi Martin,

He cloned the git repository.  Instructions in Appendix 5 in the [linuxwacom How TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Read Lucid near the top first.

Hi Favux

Thanks for the link.
When I run the last command I get some errors
```

martin@martin-laptop:~/Skrivebord/xf86-input-wacom$ make && make install
make  all-recursive
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
Making all in conf
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
Making all in src
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
Making all in man
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
Making all in include
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
Making all in tools
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
Making install in conf
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
/usr/bin/install: kan ikke oprette almindelig fil '/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi': Permission denied
make[2]: *** [install-dist_fdiDATA] Fejl 1
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[1]: *** [install-am] Fejl 2
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make: *** [install-recursive] Fejl 1
martin@martin-laptop:~/Skrivebord/xf86-input-wacom$ sudo make && make install
make  all-recursive
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
Making all in conf
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
Making all in src
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
Making all in man
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
Making all in include
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
Making all in tools
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
Making install in conf
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
/usr/bin/install: kan ikke oprette almindelig fil '/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi': Permission denied
make[2]: *** [install-dist_fdiDATA] Fejl 1
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[1]: *** [install-am] Fejl 2
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make: *** [install-recursive] Fejl 1
```

I get "Permission denied" but it doesn't help to sudo the command.
I must be doing something wrong...but what?
Some of it is in danish but I hope you get the meaning! :-)

Martin

EDIT: I ran the commands one at a time
First make and then make install and I didn't get any errors this time

```
martin@martin-laptop:~/Skrivebord/xf86-input-wacom$ make
make  all-recursive
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
Making all in conf
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
Making all in src
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
Making all in man
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
Making all in include
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
Making all in tools
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
```

and

```
martin@martin-laptop:~/Skrivebord/xf86-input-wacom$ sudo make install
Making install in conf
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
test -z "" || /bin/mkdir -p ""
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/conf'
Making install in src
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wacom_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
libtool: install: /usr/bin/install -c .libs/wacom_drv.lai /usr/lib/xorg/modules/input/wacom_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/lib/xorg/modules/input
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/xorg/modules/input

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/src'
Making install in man
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 wacom.4 '/usr/share/man/man4'
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/man'
Making install in include
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/include/xorg" || /bin/mkdir -p "/usr/include/xorg"
 /usr/bin/install -c -m 644 Xwacom.h wacom-properties.h '/usr/include/xorg'
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/include'
Making install in tools
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c xsetwacom '/usr/bin'
libtool: install: /usr/bin/install -c xsetwacom /usr/bin/xsetwacom
make[2]: Ingenting at gøre for 'install-data-am'.
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom/tools'
make[1]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[2]: Går til katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[2]: Ingenting at gøre for 'install-exec-am'.
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 xorg-wacom.pc '/usr/lib/pkgconfig'
make[2]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
make[1]: Forlader katalog '/home/martin/Skrivebord/xf86-input-wacom'
martin@martin-laptop:~/Skrivebord/xf86-input-wacom$ 
```

---

### Post by Favux on 2010-05-14
OK, Fejl is error?  Anyway I'm not sure.  You are in Lucid right?  It seems to be having problems with installing the wacom .fdi which doesn't makes sense.

---

### Post by martinjochimsen on 2010-05-14
> **Favux said:**
> OK, Fejl is error?  Anyway I'm not sure.  You are in Lucid right?  It seems to be having problems with installing the wacom .fdi which doesn't makes sense.

Yes. Fejl is error. Your danish is pretty good!!! :-D
I'm in Lucid.
I just read the guide again and it said "DO NOT DO THE SUDO MAKE INSTALL".
Can I somehow reverse that?

---

### Post by martinjochimsen on 2010-05-14
YES!!!
I rebooted and the pointer is where it is supposed to be after touch!!!
I HAVE A TABLET.
Thanks for your help Favux.

Martin :-D

---

### Post by Favux on 2010-05-14
Well great!  :)  Glad you got it working.

---

### Post by martinjochimsen on 2010-05-14
hmmm...small set back.
My eraser is now acting as stylus and my stylus (the pointy end) is not working (probably as eraser now).
I'm a bit confused about where to make that change???

EDIT:
I can move the pointer around on the screen with the "stylus", but there is no action.

---

### Post by Favux on 2010-05-14
Hi Martin,

Did you check the 10-wacom.conf and/or xorg.conf to see if they were overwriten.  If so reinstall your settings.

---

### Post by martinjochimsen on 2010-05-15
hmmm...I don't see any changes in xorg.conf, its still the same

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

```

and 10-wacom.conf also looks the same

```
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "Button 3"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection
```

In an earlier post I changed a mouse gesture, so when I kept the stylus point to the screen (and keept it down and still) the "right-click-menu" should pop up.
Now, when I keep the left button down on the touchpad the "right-click-menu" also pops up?!?!?!?

You suggested to reinstall my settings?
What settings would that be exactly?
Sorry to ask that but I'm a bit confused now, and I think I'm mixing the everything together now!!! :-)

Martin

---

### Post by martinjochimsen on 2010-05-15
I think I'm getting CRAZY or at least my laptop is!!! :-D
When I use touch and keep my finger on the screen for 2 seconds the "right-click-menu" pops up - and that also happens when the screen is rotated!!!!!
Thats what I always wanted and thats great, but I think stylus, touch and eraser (the other end of the stylus) somehow now have changed function. With the stylus I can only move the pointer around, but I can't click or anything. The eraser now works as stylus and thats not so comfortable.
Where can I change things back as they were? Or repair?
It doesn't look like that my xorg.conf and 10-wacom.conf have changed after I cloned the git repository???

---

### Post by marranzano on 2010-05-15
@ martinjochimsen

I'm on Lucid with a tx2510us.
i guess every situation is different, but all i did is:

1) installed xf86-input-wacom from git as described in the link provided by favux (including make install)

2) i have hp-wmi module loaded

3) didn't change any xorg or fdi file... i still have the original ones from fresh install

4) have my old calibration options in a .xinitrc file in my home dir

5) have two scripts for rotation as just described [here]("http://ubuntuforums.org/showpost.php?p=9305222&postcount=30") (one automatically activated on screen rotation, one linked to the refresh multimedia-key on the right of the screen, under the dvd one)

hope this helps...
marranzano

---

### Post by sacredpotato on 2010-05-15
toph@toph-laptop:~$ xsetwacom get 13 rotate
Property for 'Rotate' not available.
toph@toph-laptop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=17	[slave  keyboard (3)]







ok that is my xinput --list


what I pop open a term and try to do xsetwacom set "N-Trig Touchscreen" rotate HALF

it tells me it can't do that because there are too many with that name and to try calling it by device ID


when I try xsetwacom set 12 rotate HALF it tells me

Property for 'Rotate' not available.



so I think this is my underlying problem rotate is broken in my xsetwacom

@Favux any idea how I can get around this?


maybe there is something wrong with the rotate command or maybe I can figure out which "N-Trig Touchscreen" is the one that is actually in use and kill the other one (I have no idea how to do that)



also I can't do a xidump -l or xsetwacom list

---

### Post by lps1 on 2010-05-22
Thanks for 0.4 version for use with lucid. I can get it to rotate the stylus but not touch. I've tried using both of the ids listed below, but neither work.
```

paul@home:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=13    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=14    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=16    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=17    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=20    [slave  keyboard (3)]
```

---

### Post by Favux on 2010-05-22
Hi lps1,

Good work on getting the stylus to rotate!

That's likely due to your firmware version and not using the latest hid-ntrig.ko from Rafi.  Ayuthia shows sacredpotato and another guy what to do, and explains why, in the last few pages of the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492").

---

### Post by Favux on 2010-06-01
Hi everyone,

**[SIZE="3"]Here's Magick Rotation 0.4[/SIZE]**

Download the attachment onto your desktop. Extract it. Open the Magick Rotation 0.4 folder.  Instructions are in the Magick-README.txt included in the folder.

Additional instructions added to the README.txt:  To get your devices to rotate enter 'xinput --list' in a terminal.  Find the device names that correspond to stylus, eraser (if you have one), and touch.  In Advanced Setup enter them in the corresponding input box at the 'The stylus, eraser, and touch entries' section without the quotes.  Note there is a bug using the Lucid default wacom.ko (from linuxwacom version 0.8.4-4(?)).  Stylus and touch are called the same, namely "Wacom ISDv4 93", for TX2500 & TX2000's.  So for at least touch use the ID number.  If you've compiled and installed linuxwacom 0.8.5-12 or 0.8.6-2 (or up) wacom.ko this bug was fixed.

---

### Post by cocoa117 on 2010-06-22
Hi, I am frustrated with screen rotation. I am using following, HP TouchSmart TX2, 64-bit Ubuntu Lucid with all the latest package. I am also using fglrx ATI proprietary driver, which I believe is driver version 8.723, which is equal to catalyst 10.4. Base on the tutorial, I should be able to rotate the screen by using
xrandr -q --verbose or ATI rotation without enabling Compiz. After few days of twisting, I still cannot get screen rotation work. In more precise word, it rotates but the pen input still draw the "normal" way, not "Inverted" way.

I got following question:
1. is System -> Appearance Preferences -> Visual Effects -> Normal the Compiz enabled?
2. I am using the Magick_rotation_0.4, but still cannot solve the problem above, anyone know how to solve this?

---

### Post by Favux on 2010-06-22
Hi cocoa117,

I gather you're in Lucid.  Need a little more information.  What is 'xinput --list' showing you?  Are you using the "Device names" or ID #'s in the script or Magick?

---

### Post by cocoa117 on 2010-06-22
> **Favux said:**
> Hi cocoa117,

I gather you're in Lucid.  Need a little more information.  What is 'xinput --list' showing you?  Are you using the "Device names" or ID #'s in the script or Magick?

Hi, thanks for the reply.

the xinput --list showing following
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 413c:3010                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; CNF8038                                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=17	[slave  keyboard (3)]

I am using Device ID with Magick_Rotation. E.g. all I need at the moment is Pen input for notes taking. So I putin 14 for Stylus. 

I personally got feeling the bug is somewhere in the ATI driver for rotation or something. It should not be the USB/kernel driver itself, as I can get touch and pen input when the screen is in normal status. The issue comes in when you rotate the screen. Everything get rotated, but when you touch the screen with hand or pen, the mouse cursor is always horizentally or vertically mirrored opposite position. This is fine when you use mouse to point and click on the icons in the Inverted position.

So the xinput didn't get the notification of rotation?

---

### Post by Favux on 2010-06-22
> So the xinput didn't get the notification of rotation? 
Right.  You may not be using the correct format.  Try substituting in the scripts the device name rather than the ID number:

stylus = "N-Trig Pen"

touch = "N-Trig Touchscreen" or "N-Trig MultiTouch" (depending on which is activated)

In Magick you enter the same device names in Advanced Setup without the quotes.  Maybe the ID number is changing between boots?

---

### Post by cocoa117 on 2010-06-22
> **Favux said:**
> Right.  You may not be using the correct format.  Try substituting in the scripts the device name rather than the ID number:

stylus = "N-Trig Pen"

touch = "N-Trig Touchscreen" or "N-Trig MultiTouch" (depending on which is activated)

In Magick you enter the same device names in Advanced Setup without the quotes.  Maybe the ID number is changing between boots?

I did that, and the result are the same. There wasn't any error message, I started from CLI. What should I do?

---

### Post by Favux on 2010-06-22
OK, you did:
```
sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
```
correct.  From Appendix 1.

Have you done a 'lsmod' and checked for hp-wmi?

---

### Post by cocoa117 on 2010-06-22
> **Favux said:**
> OK, you did:
```
sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
```
correct.  From Appendix 1.

Have you done a 'lsmod' and checked for hp-wmi?

Hi, yes. I did "sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE" part, and the hp-wmi kernel model is loaded, even I didn't put it the /etc/modules file, I can always load it in CLI with
sudo modprobe hp_wmi

---

### Post by Favux on 2010-06-22
Hmmm.  Sounds like you covered most of the bases.

Remember Magick, etc. will only work on the devices you are using the wacom drivers for.  The N-trig HOW TO has scripts when you are using evdev for touch.

Maybe the install of xsetwacom got corrupted?  Try reinstalling xserver-xorg-input-wacom and rebooting.  If that doesn't work try updating xf86-input-wacom to 0.10.7.  See Appenix 5 in the linuxwacom HOW TO.  Besides that will get you 2FG gestures's for multi-touch.

---

### Post by tarjxvf on 2010-07-04
I use Magick_Rotation_0.4. It seems that pen works fine after rotation, but the finger touch is not. When I run "./magick-rotation-0.4", there is an error message "Property for 'Rotate' has no or wrong value - this is a bug." in the terminal. I use the code number from "xinput --list" in the Magick_Rotation_0.4 configuration.

What could be the possible reason that finger touch cannot be rotated? Thank you.

---

### Post by Favux on 2010-07-04
Hi tarjxvf,

Could I see your 'xinput --list"?  Also do the ID numbers stay the same after reboot etc.?  In other words are you plugging usb things in?

---

### Post by tarjxvf on 2010-07-04
> **Favux said:**
> Hi tarjxvf,

Could I see your 'xinput --list"?  Also do the ID numbers stay the same after reboot etc.?  In other words are you plugging usb things in?

This is my "xinput --list":

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Sony OPM-U30                            	id=10	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=14	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=18	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=19	[slave  keyboard (3)]

I'll reboot now, and see if they change.

---

### Post by tarjxvf on 2010-07-04
It seems that the output of "xinput --list" is the same after I reboot.

---

### Post by Favux on 2010-07-04
OK, let's look at:
```
xsetwacom list
```
And try both 14 and 15.  It depends on which touch is active.

---

### Post by tarjxvf on 2010-07-04
This is the output of my "xsetwacom list":
N-Trig Pen eraser ERASER    
N-Trig Pen       STYLUS    
There is no touchscreen there, weird.

I've tried both code 14 and 15 in the Magick_Rotation_0.4 configuration, and none of them works.

---

### Post by Favux on 2010-07-04
My guess is then that the evdev driver has touch, not linuxwacom.  You can use Rafi's latest hybrid linuxwacom/evdev rotation script.  See 4 b) on the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by tarjxvf on 2010-07-04
Thank you Favux for directing me to Rafi's script, now both touch and pen works after rotation. 

However, there is still a problem. When my palm doesn't rest on the screen, the pen works just fine in Xournal; while if my palm does rest on the screen, then the wring in Xournal is messed up. See the screenshot. 

Can this problem be solved? Thank you!

---

### Post by Favux on 2010-07-04
Good!

That's been a long standing problem with Xournal which is why the touch toggle scripts are at 5 a) and then the evdev commands are at 5 b) at the N-trig HOW TO.

---

### Post by tarjxvf on 2010-07-04
> **Favux said:**
> Good!

That's been a long standing problem with Xournal which is why the touch toggle scripts are at 5 a) and then the evdev commands are at 5 b) at the N-trig HOW TO.

Now everything works great! I should really have read your tutorial more carefully. 

Thank you for being so knowledgeable and warm-hearted!

---

### Post by daulpavis on 2010-07-06
Hi, I'm running tx2000 in 10.04

Just tried rotation scripts and auto-rotate using ID numbers to identify touch, pen and eraser.

In both cases the pen works fine. The touch on the other hand appears in the correct position while I make contact with the screen, but on release the cursor jumps to the opposite side of the screen to the position if the rotation had not occurred. 

Any suggestions

cheers.

---

### Post by Favux on 2010-07-06
Alright, in Lucid do you have the default wacom drivers.  In other words you have what came installed and didn't compile anything?

---

### Post by daulpavis on 2010-07-07
Yea. Its all working out of the box. The only changes I have made is the script to calibrate the touch and pen separately.

---

### Post by Favux on 2010-07-07
That should mean you have the default Lucid 0.8.4-4 wacom.ko and 0.10.5 xf86-input-wacom.

I didn't realize the pointer jump bug was present with touch on rotation.  I filed a bug report on linuxwacom 0.8.5-9 on it and it was fixed by about linuxwacom 0.8.6 or 0.8.6-2.

If it's the same thing it is basically cosmetic.  The arrow returns to your finger as soon as it's back on the screen correct?

If so I'm not sure it's worth your time to compile linuxwacom 0.8.6-2 or 0.8.8-4 for the wacom.ko and end up with a non-stock system.  Up to you.

---

### Post by daulpavis on 2010-07-07
The touch does not function properly when in rotation, its not just cosmetic.

As far as I can tell the equivalent of pressing the mouse button in occurs in the correct position. The event of releasing the button appears to occur on the opposite side of the screen. 

I am able to drag windows around the screen, but often they jump to a new position when the finger is released. Clicking of buttons is not a performable operation, either in the correct position, or by lining up the finger in the position on the other side of the screen

---

### Post by Favux on 2010-07-07
OK.  Then you probably need to compile newer wacom drivers.  See I. and II. in the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by daulpavis on 2010-07-07
I ran through those steps. 

NO change, although I'm not sure if it worked correctly, I did it wile watching the World Cup game so wasn't paying much attention. Is there a way to check the wacom driver version?

---

### Post by Favux on 2010-07-07
> Is there a way to check the wacom driver version? 
I don't think so.  Unless they just added it to xf86-input-wacom.  I believe they might have added a way to check xsetwacom version.  Check 'man xsetwacom'.  But I don't think it's a valid proxy.

---

### Post by daulpavis on 2010-07-07
OK

Re-ran the instillation. There must have been a problem before. The new drivers solved the touch problem in rotation mode. 

Cheers.

---

### Post by Favux on 2010-07-07
Good!  :)

---

### Post by daulpavis on 2010-07-08
Ok. I have discovered another problem. The laptop hangs and locks up with a black screen (back-light on) on suspend (either by closing lid or choosing from the menu) after a rotation using the auto rotate is performed. 

I'm using Magick Rotation 0.4 with the newly installed wacom drivers.

It does not hang after a normal rotate. 

If you disable or exit the auto-rotate application it still hangs.

---

### Post by deddokatana on 2010-08-22
thankyou for the wonderful script on how to rotate the display :)

slight problem though,

the mouse cursor doesnt invert when the display does! amusing, but makes life harder.

this is probably due to  the differences in the laptop hardware revision, as show in lsinput. or just because im running 10.04

heres the lsinput readout:

```
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event3
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event4
   bustype : BUS_ADB
   vendor  : 0x1
   product : 0x1
   version : 256
   name    : "Macintosh mouse button emulation"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event5
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event6
   bustype : BUS_USB
   vendor  : 0x56a
   product : 0x93
   version : 1027
   name    : "Wacom ISDv4 93"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event7
   bustype : BUS_USB
   vendor  : 0x56a
   product : 0x93
   version : 1027
   name    : "Wacom ISDv4 93"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event8
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event9
   bustype : BUS_USB
   vendor  : 0x64e
   product : 0xa104
   version : 256
   name    : "HP Webcam"
   phys    : "usb-0000:00:13.2-2/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event10
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event11
   bustype : BUS_PCI
   vendor  : 0x10ec
   product : 0x268
   version : 1
   name    : "HDA Digital PCBeep"
   phys    : "card0/codec#0/beep0"
   bits ev : EV_SYN EV_SND

```

im especially interested in code changes to the script as i might use it in a tablet pc control panel/preferences applet,as im a python beginner looking to contribute.

lovin ubuntu. peace.

---

### Post by Favux on 2010-08-22
Hi deddokatana,

From your product ID you seem to have a HP TX2000.  Is this correct?

It looks like you have the default Lucid 0.8.4-4 wacom.ko because stylus and touch have the same name "Wacom ISDv4 93".  This was a bug that was fixed.  So probably the evdev driver is picking up touch which is why it isn't rotating with the stylus.  To verify look at Xorg.0.log in /var/log.  Copy it into gedit and search 'wacom'.

Let's see what:
```
xinput --list
```
shows us.

I have a TX2000/TX2500 xsetwacom script attached to the second post of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") thread, which let's you fine tune things.

The control panel thing sounds interesting.  Love to see what you come up with.

---

### Post by AndreasB123 on 2010-09-03
I have an HP 2710p Tablet PC, Wacom works out of the box (Ubuntu 10.04)


But rotation didn't work, I found this thread, downloaded Magick_Rotation_0.4.tar.gz, inserted hp-wmi to /etc/modules (and rebooted the system).

But it's still not working, I found out what's the problem, but not the reason:

/etc/devices/plattform/hp-wmi/tablet is always 1 (but it should be 0, because I'm not in tablet mode...)

After reboot it worked one time, but now its still 1... The Tablet don't rotate back...

Maybe somebody has an Idea why...

@Favux
Thank you for the good work!


Andreas

---

### Post by Favux on 2010-09-03
Hi AndreasB123,

That's a puzzler.

What happens to /etc/devices/plattform/hp-wmi/tablet when rotated?  Is it still one?

When you rebooted was it 0 before rotation?

Does auto-rotation work in Windows?

Do you see hp-wmi in lsmod?:
```
lsmod
```

---

### Post by AndreasB123 on 2010-09-04
> **Favux said:**
> 
Does auto-rotation work in Windows?


Yes it did... (And yes, the hp-wmi is loaded, I added it to /etc/modules)

> **Favux said:**
> 
When you rebooted was it 0 before rotation?


/etc/devices/plattform/hp-wmi/tablet is 0, I booted system before 10 minutes... (as I wrote in the first post, the problem is the driver, not your script...)

Now I rotate the screen... And...
/etc/devices/plattform/hp-wmi/tablet is 1, and your script worked as expected...


No I rotate the screen back, but the /etc/devices/plattform/hp-wmi/tablet is still 1....

But now, while I'm writing, it rotated back... 30s?

So I tested again, it's now 1 since 3 minutes, but the display is in normal mode, since 3 minutes...

Maybe I should install Windows again and test if it works there always, I tested it only 2 or 3 times, and then installed Ubuntu;-)

Now, again, it rotated back... But it needs 5 minutes this time, that's to long for me, I have an Fujitsu Siements T4010 Tablet, there it takes 1 to 2 seconds to rotate...


Thank you for your replay, but the driver problem is still there...


Andreas

---

### Post by Favux on 2010-09-04
Hi Andreas,

If you look in Magick's Advanced Setup you'll see the "Information update interval" (the polling rate) is 500 milliseconds.  So rotation should seem almost instantaneous, faster than your Fujitsu.
> Maybe I should install Windows again and test if it works there always
I would, because you may be looking at a hardware problem.  You at least want to eliminate that.  Maybe a corroded contact or weak spring.  I don't actually have a physical concept of how the swivel hinge switch works.

Once a hardware problem has been eliminated you could look into whether there is a problem with your bios/wmi or hp-wmi or the script/python libraries.

---

### Post by Pericius on 2010-09-04
(hp 2730p)
Got the auto magic rotation working and stylus and pressure and everything, but I cannot seem to get the rotate button to work. Anyone has this or 2710p or 2750p (i reckon they're similar)?

---

### Post by Favux on 2010-09-04
Hi Pericius,

For the TX2000 only 2 of our 4 bezel keys show up in xev.  The TX2500 is about the same, 1 of 3?  Anyway we bind rotation to one of the working keys, we've nicknamed it the Q key.

Apparently the wmi or hp-wmi needs to be coded for the missing keys.  Red_Lion was on the track for that and looked like he was getting close to figuring it out.

---

### Post by AndreasB123 on 2010-09-05
After hours of installing windows 7 I can now say it works with Windows...

So I can say it's not a hardware problem...

I will now install again Ubuntu 10.04 (but this time the amd64 Version, last time I choose the x86 version)

But it still do not work, if I rotate back it stay a long time to 1 and so it don't rotate back...

I hope somebody has an idea what it can be...

Does nobody have the same problem?


Andreas

---

### Post by Favux on 2010-09-05
Hi Andreas,

When you had Windows installed (I hope you still do and are dual booting) did you check to see if you have the latest bios from HP?

You're the first one to report this problem.  The few other 2710p's didn't mention a problem.  In fact the tester thanked in Magick had a 2710p.

---

### Post by AndreasB123 on 2010-09-06
> **Favux said:**
> 
When you had Windows installed (I hope you still do and are dual booting) did you check to see if you have the latest bios from HP?


Yes, I have now dual boot, for testing;-)

I have the latest BIOS, because I had a BIOS from 2008 and I installed yesterday the latest version;-)

OK, That's not the problem... I will look in de driver code, I'm a developer... I hope I will find the problem...

Thank you for your support! (And if you or somebody else have an Idea write it, I will test it)

Andreas

---

### Post by AndreasB123 on 2010-09-06
I found out what's the problem, but no real solution yet...

I looked into the driver code, I didn't understand all the code, but I saw its waiting for an IRQ, then it reads the state again.

But I don't get an IRQ, but if I turn the display, and then press the Power Button, then it gets the IRQ and also rereads the Tablet status, so I know a workaround for the moment...

But I'm wondering that only I have this problem;-)


Andreas

---

### Post by Favux on 2010-09-06
Assuming you don't have pynotify on your system why would the state function parser be hanging?  When you place your cursor over the Magick rotating green arrowing icon in the upper right notification area while in landscape do you see "Normal mode"?  We did have some systems hanging early on.

---

### Post by AndreasB123 on 2010-09-06
Your Python script works correctly! Sorry if I didn't write clear enough...
I get the notification Bubble, but only if I press the power Button...

The problem is the driver, it don't read the state, you read the file /sys/devices/platform/hp-wmi/tablet, which is create by the driver, and the problem is that the driver did not update the file. (Because he may didn't get the IRQ, I don't know)

If I press the Power Button the driver updates all states, incl. the tablet state, and changes /sys/devices/platform/hp-wmi/tablet, which is read by your script, and then it works...
(If somebody has the same Problem, press the Power Button;-))



Andreas

---

### Post by Favux on 2010-09-25
Hi everyone,

**[SIZE="3"]Here's Magick Rotation 0.5[/SIZE]**

Download the attachment onto your desktop. Extract it.  Open the Magick Rotation 0.5 folder.  Instructions are in the Magick-README.txt included in the folder.

This version uses Ayuthia's new xrotate.py python rotation script.  This enables evdev rotation for TX2z's with touch on the evdev driver in Lucid and Maverick.  It also eliminates the need for manually entering your "Device names" in Advanced Setup.

Enjoy.

Edit:  Removed extra tab/indent on two lines.  Prevented rotation for at least one user.  So far 23 downloads.

---

### Post by albandy on 2010-10-19
> **Favux said:**
> Hi everyone,

**[SIZE="3"]Here's Magick Rotation 0.5[/SIZE]**

Download the attachment onto your desktop. Extract it.  Open the Magick Rotation 0.5 folder.  Instructions are in the Magick-README.txt included in the folder.

This version uses Ayuthia's new xrotate.py python rotation script.  This enables evdev rotation for TX2z's with touch on the evdev driver in Lucid and Maverick.  It also eliminates the need for manually entering your "Device names" in Advanced Setup.

Enjoy.

Edit:  Removed extra tab/indent on two lines.  Prevented rotation for at least one user.  So far 23 downloads.

Thanks a lot, your scripts works, but I've got a problem. I own an hp compaq 2710p and the script works in it when I rotate the screen, but when I turn it to it's original position it remains rotated. 

Do you know how can I solve this problem? Thanks in advance.

---

### Post by Favux on 2010-10-19
Hi albandy,

Did you add some commands to Advanced Setup?  If something is hanging it would prevent it from rotating back.

---

### Post by albandy on 2010-10-20
> **Favux said:**
> Hi albandy,

Did you add some commands to Advanced Setup?  If something is hanging it would prevent it from rotating back.

I didn't. But I found that if I push some buttons or I plug or unplug the network cable, then the screen rotates again.

---

### Post by Favux on 2010-10-20
OK, that's sounding like there is a hang.  Did you install CellWriter?  If you didn't that might be it.

If you did maybe you could try Magick 1.0.  You might have better luck with it.  It's now hosted on Launchpad:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by albandy on 2010-10-21
> **Favux said:**
> OK, that's sounding like there is a hang.  Did you install CellWriter?  If you didn't that might be it.

If you did maybe you could try Magick 1.0.  You might have better luck with it.  It's now hosted on Launchpad:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

I'll try it. Thanks a lot.

---

### Post by martinjochimsen on 2010-10-31
Hi there

I've got Magic Rotation working as well as keybinding for a rotation-script for the "Q"-key on the screen.
I would like to have the possibility to rotate the screen into portrait-mode while in tablet-mode. I have setup Magic Rotation to show the screen inverted (180 degrees).
Can I make the "Q"-key "overwrite" the Magic Rotation script while in tablet mode or should I just put an icon on the desktop that activates the other rotation script?

Martin :-)
tx2590eo


EDIT: Well for now I have just put an icon on the desktop that rotates the screen as I want. But I would still like to know if it is possible to make one of the screen-key work while in tablet-mode?!?

---

### Post by Favux on 2010-11-01
Hi Martin,

You should be able to do that.  On earlier versions of Magick when I was in Intrepid I still had a rotation script on the "Q" key.  And it worked.  Magick isn't like wacomrotate, it requires a signal from the hinge switch to rotate.  So while you're in tablet there is no signal and Magick won't do anything to interfere with another rotation script.

I noticed when I updated from Intrepid to Karmic I lost the keybinding to the "Q" key.  It's back to making the music player pop up.  I didn't bother to change it back to the rotation script because by then I was comfortable with Magick.  The discouraging thing is I lost the DVD key.  It no longer makes a event in xev.  So I'm down to 1/4 tablet keys.  Another reason I didn't change the key binding.

I guess the DSDT for the TX2000 regressed.  Since you can no longer manually modify it (they removed the kernel support for that) I guess I'm stuck.  Ticks me off because they said they were removing the manual support because they were so good at taking in submitted DSDT's and adding them into the hardware support.  And I submitted the TX2000 DSDT to the DSDT site.  Only upshot is they broke another tablet key.  Super!

---

### Post by martinjochimsen on 2010-11-01
> **Favux said:**
> Hi Martin,

You should be able to do that.  On earlier versions of Magick when I was in Intrepid I still had a rotation script on the "Q" key.  And it worked.

Also in tabletmode?


> Magick isn't like wacomrotate, it requires a signal from the hinge switch to rotate.  So while you're in tablet there is no signal and Magick won't do anything to interfere with another rotation script.

I thought it was like when the screen is in normal position the hinge switch is off, but when the computer is in tabletmode (the screen ontop of the keyboard) the switch is on, and therefore the "Q" key is disabled?!?

My "Q" key doesn't work when the laptop is in tabletmode and xev doesn't show anything.
 
> The discouraging thing is I lost the DVD key.  It no longer makes a event in xev.  So I'm down to 1/4 tablet keys.  Another reason I didn't change the key binding.

I don't think my DVD key never worked, but the Q key always started Rhythmbox - it doesn't anymore! :-)

> I guess the DSDT for the TX2000 regressed.

Sorry to ask, but what does DSDT mean?

Well it's not a big catastrophe that I can't make the Q key rotate the desktop while in tabletmode - the possibility  would be nice though. After all I have a rotate-script assigned to an icon in the taskbar, so it's not that I can't rotate the screen at all i tabletmode.

Martin :-)

---

### Post by Favux on 2010-11-01
> Also in tabletmode?
Yes.
> but when the computer is in tabletmode (the screen ontop of the keyboard) the switch is on, and therefore the "Q" key is disabled?!?
No, that is a bug not Magick.  We found the fix for that a long time ago but I've forgotten it.  Not even sure I could track it down.
> I don't think my DVD key never worked
You often had to use gali98's key code fix in the key code addendom at the bottom of the HOW TO.  I haven't tried it in Karmic.  Worried about breaking something.
> what does DSDT mean?
Differentiated System Description Table, see:  [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)  It's basically a component of the BIOS ACPI chain.

---

### Post by martinjochimsen on 2010-11-01
> **Favux said:**
> Yes.

No, that is a bug not Magick.  We found the fix for that a long time ago but I've forgotten it.  Not even sure I could track it down.

You often had to use gali98's key code fix in the key code addendom at the bottom of the HOW TO.  I haven't tried it in Karmic.  Worried about breaking something.

```
martin@martin-laptop:~$ sudo update-rc.d -f hotkey-setup remove
[sudo] password for martin: 
 Removing any system startup links for /etc/init.d/hotkey-setup ...
martin@martin-laptop:~$ sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .
update-rc.d: /etc/init.d/hotkey-setup: file does not exist
```

I don't think I got the "file does not exist" message in Ubuntu 9.10, but it worked anyway.

---

### Post by Favux on 2010-11-01
Really?!!  You got the DVD key working again in Maverick?  Awesome!

---

### Post by martinjochimsen on 2010-11-01
> **martinjochimsen said:**
> ```
martin@martin-laptop:~$ sudo update-rc.d -f hotkey-setup remove
[sudo] password for martin: 
 Removing any system startup links for /etc/init.d/hotkey-setup ...
martin@martin-laptop:~$ sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .
update-rc.d: /etc/init.d/hotkey-setup: file does not exist
```

I don't think I got the "file does not exist" message in Ubuntu 9.10, but it worked anyway.

No. I mean even though I got that message I got the keybinding for the "Q" key working.
Sorry :-)

---

### Post by Favux on 2010-11-01
Well getting the "Q" key working is what you wanted.  So, oh well on the DVD key.

---

### Post by martinjochimsen on 2010-11-01
> **Favux said:**
> Well getting the "Q" key working is what you wanted.

Yes and it would be nice to have it working in tabletmode as well, so I can switch between landscape and portrait mode.
But I think I'll leave it for now.
My tablet is acting like a tablet now. It's so great!!!

:-)

---

### Post by Favux on 2010-11-01
Good, I'm glad.  :)

Just found what the tablet/bezel button fix was.  It's on this thread.  GrooveTherapy was having the same problem and I suggested he update the BIOS.  When he did it fixed it:  [http://ubuntuforums.org/showpost.php?p=6726069&postcount=57](http://ubuntuforums.org/showpost.php?p=6726069&postcount=57)

He had a TX2000.  I don't know if HP would still have the BIOS for the TX2500 posted.  Do you remember if you have the latest one?

There may have been something about this on the TX2500 thread too.  Hmmm.

---

### Post by martinjochimsen on 2010-11-02
> **Favux said:**
> Good, I'm glad.  :)

Just found what the tablet/bezel button fix was.  It's on this thread.  GrooveTherapy was having the same problem and I suggested he update the BIOS.  When he did it fixed it:  [http://ubuntuforums.org/showpost.php?p=6726069&postcount=57](http://ubuntuforums.org/showpost.php?p=6726069&postcount=57)

He had a TX2000.  I don't know if HP would still have the BIOS for the TX2500 posted.  Do you remember if you have the latest one?

There may have been something about this on the TX2500 thread too.  Hmmm.

Thanks for the link.
I think I've got the latest BIOS. I got a new motherboard this summer, and I presume that the tech-guy also updated the BIOS. But I'll check anyway. :-)

---

### Post by sukigenseki on 2010-11-17
Auto rotation works for my tx2510, but has anyone noticed that when trying to draw in GIMP while the tablet is rotated that the performance is terrible? There is a one to two second delay on drawing on GIMP, and it is with any x rotation script I have tried or written. Normal screen orientation there is no lag when drawing anything in GIMP however.

---

### Post by Favux on 2010-11-17
Hi sukigenseki,

It's possible you need to turn decorations off.  Are you using Compiz?

Also there's a known gtk/Gimp bug.  The CPU gets overwhelmed by all the (excessive) events being sent by the stylus/eraser in Gimp.  The way to determine if that is affecting you is to do a xsetwacom command before starting Gimp:
```
xsetwacom set "Device name" RawSample "20"
```
The default is 4.  If 20 helps decrease the lag, that's by definition the bug.  "Device name" is the what you get for stylus from 'xinput --list' (in quotes).

You could also explore the issue by using TOP.  Enter 'top' in a terminal and see what's consuming the CPU cycles before and after rotation.

---

### Post by sukigenseki on 2010-11-17
Changing the raw sample value makes an improvement for me; do you happen to know if there is a bug filed on launchpad for this? Thanks a lot by the way; it helps a lot to know where the problem is coming from. Top didn't show anything out of the ordinary for me, and trying Gimp using just Metacity doesn't make a difference.

---

### Post by Favux on 2010-11-17
I don't know where the bug is posted.  I think it may be on launchpad and other places.  Alexia Death (a Gimp developer) is the one who told me about it.  So it's well known.  The Gimp folks have made partial fixes in Gimp, I don't know how many are in the current version.  I gather they've had trouble getting the gtk folks to work on it on their end.  Or at least that's the impression I got.

---

### Post by newtonthenewt on 2010-12-19
Hello, I'm just going through the first post and have reached the key binding step. When I type

```
gksudo gedit /etc/X11/xorg.conf
```gedit opens xorg.conf, but it's blank. I'm using Ubuntu 10.10.

I'm somewhat new to this, so thanks for any help.

---

### Post by Favux on 2010-12-19
Hi newtonthenewt,

Welcome to Ubuntu forums!

In Maverick the xorg.conf can be empty unless you are using a video chipset driver that needs it.  For example the Nvidia proprietary driver would have installed one.  You don't need to worry about that step since you have Maverick not Intrepid.

Configuration now occurs in xxxx.conf files in xorg.conf.d.  Since you are in Maverick the wacom.conf would be at /usr/share/X11/xorg.conf.d/50-wacom.conf, and if you needed to edit it you would use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
You can think of the .conf files in xorg.conf.d as sections of the xorg.conf.

What brand and model tablet pc do you have?

---

### Post by benazhack on 2011-01-09
Hi, i've a minor issue using magick-rotation with ubuntu 10.10 (but i remember i had the same problem also using older version) regarding the tray icons.
If you let magick-rotation add him to the startup list, you will note that the next time magick-rotation will be started during the login,  there won't be the nice green/red icon but only messages.
I've checked that the issue comes from the fact that when magick-rotation start from the startup list, the icons files magick-rotation-disabled.png and the other aren't in the PATH variable (in the path where the system run the code).
In fact in the code of the magick-rotation you can note that the references to the icons files are given in terms of relative path.
Example:
```

tray.set_from_file(install_folder+"magick-rotation-enabled.png")

```

You can replicate my issue, simply opening a terminal and running magick from a different folder of the latter.
Example, for me the folder is /home/emiliano/.magickrotate 
so i run bash/terminal and run
```

emiliano@Skully:~$ ./.magickrotation/magick-rotation-0.5

```
Now if u cd in your magick-rotation folder and run magick-rotation you will see that the icon appear.

The method, i used to solve this issue it's to define a new variable install_folder in the script and append this string whenever the icons files names appear.

I decided to post a simple method to solve it.

1. Open a file, name it patch2magick and save this text

```
--- magick-rotation-0.5	2010-10-01 20:32:06.000000000 +0200
+++ magick-rotation-0.5	2011-01-10 03:08:48.180999001 +0100
@@ -98,7 +98,7 @@
 # tablet/normal state files from hp_wmi
 state_hp_wmi="/sys/devices/platform/hp-wmi/dock"
 state_hp_wmi_patched="/sys/devices/platform/hp-wmi/tablet"
-
+install_folder="/home/emiliano/.magickrotation/"
 ## these can be set by config ##
 # pause before pooling
 waittime=0.25
@@ -359,12 +359,12 @@
 	global pooling
 	if pooling:
 		pooling=False
-		tray.set_from_file("magick-rotation-disabled.png")
+		tray.set_from_file(install_folder+"magick-rotation-disabled.png")
 #		tray.set_from_icon_name("undo")
 		menu_disable.child.set_text("Enable")
 	else:
 		pooling=True
-		tray.set_from_file("magick-rotation-enabled.png")
+		tray.set_from_file(install_folder+"magick-rotation-enabled.png")
 #		tray.set_from_icon_name("redo")
 		menu_disable.child.set_text("Disable")
 	print "Now I'm enabled?", pooling
@@ -656,7 +656,7 @@
 menu.append(menu_disable)
 menu.append(menu_setup)
 menu.append(menu_exit)
-tray.set_from_file("magick-rotation-enabled.png")
+tray.set_from_file(install_folder+"magick-rotation-enabled.png")
 #tray.set_from_icon_name("redo")
 tray.set_tooltip("Loading...")
 tray.connect('popup-menu', popup_menu, menu)

```

2. Now edit **install_folder="/home/emiliano/.magickrotation/"** with your magick install directory. WARNING: Remember the slash / after the name of the folder, or it won't work.

3. Save patch2magick in the folder where you have installed magickrotation

4. Open a terminal and cd in the folder of magick and run this command 
```
patch < patch2magick
```

5. Try to logout/login and check if you see the green arrow of magick.

My patch work only for 0.5 version, if you need to adapt for older version read the explain of the the trick at the start of the post.
I wish my contribute help someone like me.
 Emiliano

PS: In winzoz OS the problem disappear, because you can setup the running folder when creating a startup link. Could be nice if the gdm/startup list everytime, before run the app append to the PATH variable the path of the app that will be executed.

PSPS:Sorry for the bad english :popcorn:

---

### Post by Favux on 2011-01-09
Hi benazhack,

Welcome to Ubunutu forums!

Thank you for your contribution to Magick Rotation.  I'm sure it will be helpful to others.


As you probably know we moved Magick to Launchpad and are now up to version 1.2, see:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  You might want to try it.  If you think of other code you would like to add to it please let us know.  We would love to have contributors.

---

### Post by benazhack on 2011-01-09
I don't know that you was so next.
Anyway as you know, and as i see now magick was completh restructured.
Nice the polling of dock/tablet mode with a c file instead of a normal pool.
The problem i have solved was already solved as i see in the GUI_gtk.pt
file.
Thanks for have updated me with the status of magick project
Tomorrow I'll try the new version.
Good night,
Emiliano

---

### Post by dgray_from_dc on 2011-02-25
Hello,

I have a HP Compaq tc4200 dual booting XP Tablet and Kubuntu Lucid.  Out of the box, the primary stylus works, no side button, no eraser.  When I rotate the screen normally, the input goes out of wack.  I've been reading through this thread, and ***_[brenner's thread]("http://ubuntuforums.org/showthread.php?t=1100119")_*** and ***_[pitbullthe1st's thread]("http://ubuntuforums.org/showthread.php?t=1018595")_***.

Out of all of them, I can't seem to divine anything comprehensive for my model tablet PC.  I see settings, xorg.conf files, and bits of code that I can't figure out where to place.

I've used method 3 which resulted in good up-down input, but an incorrect screen width setting (it behaved as if it were still in landscape, as I moved the stylus farther to the right, the cursor got farther away from the stylus).

I then tried method 4, wanting the automatic switch hoping for a better result.  I didn't work at all.  The steps and advanced settings in method 4 aren't explained so I don't know what to do / what to tweak.  This method refers to other posts, but I can't figure out their context.  I don't know whether or not these are commands, or if they are code for a config file.  If this is the case what config file?

I apologize for coming off whiny, but I have completely abandoned all things Microsoft for a few years now, and at the moment, XP is all that allows this machine to be more than a standard laptop.  I appreciate that the OP is kept up-to-date, but I guess that its generic nature throws me off.  I can't seem to figure out what parts of it apply to my model.

As far as I can tell, the tc4400 settings should work, but I can't tell what those settings are.  Because the **benner** thread is so old, I don't trust that it's up-to-date.  Additionally, the **pitbullthe1st** thread doesn't have a comprehensive solution posted.  Seems easy, but I'm confused. :confused:  What combination of methods, scripts and configuration settings can get a Compaq tc4200 to the latest greatest set of capabilities?


Again, sorry to whine, and thanks for any help you can offer...

---

### Post by Favux on 2011-02-26
Hi dgray_from_dc,

Let's tackle one issue at a time.  With the TC4200 & 4400 Magick will work if you right click on the rotating green arrow icon and chose Setup.  Then check the box in front of *BIOS hinge switch values reversed?* and Save that setting.  That's early in the Magick-README.txt in the magick-rotation folder, but I see I forgot to add it to the FAQs.  Oops.

Then we'll work on the stylus button.  Do you have one or two?  And the eraser.

---

### Post by dgray_from_dc on 2011-02-27
> **Favux said:**
> Hi dgray_from_dc,

Let's tackle one issue at a time.  With the TC4200 & 4400 Magick will work if you right click on the rotating green arrow icon and chose Setup.  Then check the box in front of *BIOS hinge switch values reversed?* and Save that setting.  That's early in the Magick-README.txt in the magick-rotation folder, but I see I forgot to add it to the FAQs.  Oops.

Then we'll work on the stylus button.  Do you have one or two?  And the eraser.

I followed the Magick instructions including the BIOS hinge switch in the README.  When I completed the install and rebooted, I had to start the script manually.  The task bar notification icon came up, I rotated the screen, no effect, I clicked the notification bar icon, I saw a red T appear on top of the icon.  I assume that was an indicator to show that it was in tablet mode, but the orientation still hadn't changed.

Since method 4 seemed to have the most promise and native hardware support, I've left it installed, but I now have it disabled.  I've completely removed the package from method 3 and I think I have the one button stylus (e.g. left-click, right-click and eraser).

---

### Post by dgray_from_dc on 2011-03-04
Ok,

So I've started back up with method 4.  I've turned it back on and made sure I went through all the steps in Magick-README.txt and still, absolutely no response.

---

### Post by fire_qc on 2011-03-16
I'm noob and I've Kubuntu 10.04 LTS in a HP Pavilion TX2000 tablet pc.  After I installed MagickRotation and follow carefully the instructions, when I flip the screen nothing happen...!!!

Please help me...........

---

### Post by Favux on 2011-03-16
Hi fire_qc,

Welcome to Ubuntu forums!

Check the magick-rotation folder and see if checkmagic64 or checkmagic32 was compiled.  Did you get any errors when the Installer ran?  Did you reboot?  Do you see the green rotating arrow Magick icon in your tray?

---

### Post by fire_qc on 2011-03-16
If I run the magick_rotation file, I see the Green arrow in the task bar.  But when I just pass the mouse on it, it tells Loading...

I found something in another forum, if I use command xrandr -o inverted the screen flip...
I did ./checkmagic64 but nothing happen, so I click Quit on the green arrow and after (in my terminal) it says Finish...

And by the way, how can I make the small remote works???

Thanks..........

---

### Post by Favux on 2011-03-16
If you did a right click on the green arrow and chose quit you've shut Magick Rotation down.  Go into the magick-rotation folder and double click on the magick-rotation file and chose run.  See if it works then.  The tool tip shouldn't say "loading" it should say for e.g. "Normal mode" when in laptop, but that usually doesn't affect anything.

To test in a terminal change directory into the magick-rotation folder and:
```
./magick-rotation
```
That should tell you about errors.  Because checkmagick64 is a C file ./checkmagic64 won't tell you anything.

Geez, I haven't used the remote in ages.  Forgot all about it.  I'll have to think and remember if we figured out how to get it working and what we did if we did.

---

### Post by fire_qc on 2011-03-17
> **Favux said:**
> 
```
./magick-rotation
```That should tell you about errors.  Because checkmagick64 is a C file ./checkmagic64 won't tell you anything.

Geez, I haven't used the remote in ages.  Forgot all about it.  I'll have to think and remember if we figured out how to get it working and what we did if we did.

I loose my cursor, I've to write ```
./magick-rotation &
```After that, a green arrow appear and nothing more....  If you want we can check together with TeamViewer and you'll see what happen....

And for the remote, please help to remember....  Lirc doesn't seems to work....

---

### Post by Favux on 2011-03-17
Is the tray icon present when you reboot or restart?

---

### Post by fire_qc on 2011-03-17
> **Favux said:**
> Is the tray icon present when you reboot or restart?

Yes...

---

### Post by Favux on 2011-03-17
OK, you have checkmagick64 and Magick is auto-starting.  Running magick-rotation as a script in a terminal isn't giving any errors and it starts because the tray icon appears.  Did you Quit Magick Rotation first before running it as a script in the terminal?  Is hp-wmi autoloading?  Check:
```
lsmod
```
and see if you see hp-wmi or hp_wmi in the output.

---

### Post by fire_qc on 2011-03-17
> **Favux said:**
> and see if you see hp-wmi or hp_wmi in the output.

I can't see that....  How I'll install this package???

---

### Post by Favux on 2011-03-17
Add "hp-wmi" (without the quotes) to the 'modules' file in "/etc/modules" on a separate line at the bottom of the list and reboot.
```
gksudo gedit /etc/modules
```

---

### Post by fire_qc on 2011-03-17
Oh my god....  It works!!!  You're a killer!!!!  :twisted::guitar:

If you want to kill one more, look what you can done for my remote, here the number of it : RC2002002/01

FIRE..........

---

### Post by Favux on 2011-03-17
Good!

I just found some old notes on the remote control and it worked for most folks out of the Box.  So check that the battery is good in it.  Then in a terminal enter *xev* and press a remote key.  The key code should pop up in the xev output.  If the keycode isn't mapped to anything you can use Compiz config to make a key binding.  But it seems most of the buttons were the same as the bezel buttons.  We could only get 2 out of the 4 Bezel buttons working and now we're down to 1.  Super.

---

### Post by fire_qc on 2011-03-18
> **Favux said:**
> terminal enter *xev* and press a remote key.   The key code should pop up in the xev output.  If the keycode isn't  mapped to anything you can use Compiz config to make a key binding.  But  it seems most of the buttons were the same as the bezel buttons.  We  could only get 2 out of the 4 Bezel buttons working and now we're down  to 1.  Super.

I've tried xev, nothing happen, and the battery is good.  Before I  was Microshit Vist-**** and to make the remote work was need a driver  for that.  And I've tried to install LIRC but doesn't work too.....

I'll check with compiz (somewhere) but how can I configure keymap if xev do nothing when I press a key on the remote???

---

### Post by Favux on 2011-03-18
You're right, you don't need to worry about Compiz until xev picks something up.

In Synaptic Package Manager or the Software Center did you try installing *irda-utils*?  Also *anyremote* may be useful.

---

### Post by fire_qc on 2011-03-21
> **Favux said:**
> did you try installing *irda-utils*?  Also *anyremote* may be useful.

I did both of them, and nothing happen.   The command is irdadump but it tells nothing.:confused:

---

### Post by Favux on 2011-03-21
Bummer.

That's the extent of my IR remote knowledge.  You'll have to do some research/googling to come up with something.  If you find a solution please let us know.

You probably need to look at udev to see if your remote is showing up and is being matched somewhere.  If not an attributes walk to come up with keywords for the match.  See the manuals *udev man* and *man udevadm*.

To print a list of current udev matches you could load into gedit and do a find search on:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```
To try and detect it instead of xev you could try:
```
sudo udevadm monitor --property
```
Run it and then press remote buttons.

---

### Post by fire_qc on 2011-03-23
The strange thing I know is someone on internet tells that after he installed ubuntu 8.04 on the same machine (HP Pavilion TX2000), the remote was working fine!!!

---

### Post by Favux on 2011-03-23
Well sure.  We're going back two years or so but that's what I remember.  When I installed Hardy (my first Ubuntu) the remote worked out of the box.  It still worked in Intrepid if I remember correctly.  But like I say I haven't used it in a long time.  So I don't know about Jaunty or later.

---

### Post by Favux on 2011-10-10
[SIZE="4"]**Magick Rotation 1.5 has been released!**[/SIZE]:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by cgul1 on 2011-10-24
Hello all
Been a while since I had Magick Rotation working in an older version of Ubunutu on my HP TX200 Now upgraded to 11.10 and installed ver 1.5.
starting to troubleshoot.

When run from terminal, I get a:

Gtk WARNING ** Unable to locate theme engine in module_path: "pixmap" 
 
four times, then

type cb7c code 4ea5 value d6df
and several lines of similar as I rotate screen.

I am sure I missed something core critical, but where?
thanks

---

### Post by Favux on 2011-10-24
Hi cgul1,

So is 1.5 actually rotating the screen and input tools for you?

I don't think that is from Magick per se.  What do you have running from Magick?  CellWriter?  Anything else?

I noticed you upgraded.  Did you have say Emerald installed as your window decorator?

---

### Post by cgul1 on 2011-10-24
> **Favux said:**
> Hi cgul1,

So is 1.5 actually rotating the screen and input tools for you?

I don't think that is from Magick per se.  What do you have running from Magick?  CellWriter?  Anything else?

I noticed you upgraded.  Did you have say Emerald installed as your window decorator?

No, no rotation. Yes CellWriter is checked to start but does not.
No window decorations. this is a fresh install of 11.10

---

### Post by Favux on 2011-10-24
Alright.  You're running Unity 3D?  CellWriter is installed?

What happens if you remove CellWriter from Advanced Setup?

---

### Post by cgul1 on 2011-10-24
> **Favux said:**
> Alright.  You're running Unity 3D?  CellWriter is installed?

What happens if you remove CellWriter from Advanced Setup?

Yes Unity 3d, CellWriter installed and works fine.
I removed cell writer from setup, still no rotation.

---

### Post by Favux on 2011-10-24
With a HP TX2000 you have Nvidia video.  Nouveau or Nvidia proprietary drivers?

Did you install it or are you running it from the folder?

I assume the Magick Rotation systray icon is appearing.  Go to Advance Setup and check *Debugging tool logging on?* and Save.  Post the log file that appears in /home/yourusername.  Let's see if we can see where it is getting stuck.

---

### Post by cgul1 on 2011-10-24
> **Favux said:**
> With a HP TX2000 you have Nvidia video.  Nouveau or Nvidia proprietary drivers?

Did you install it or are you running it from the folder?

I assume the Magick Rotation systray icon is appearing.  Go to Advance Setup and check *Debugging tool logging on?* and Save.  Post the log file that appears in /home/yourusername.  Let's see if we can see where it is getting stuck.

Nvidia driver, I tried switching to another release beyond the recommended one.
It is installed with the arrow
Debugging just shows:
2011-10-24 21:54:34: checking for rotation
2011-10-24 21:54:34: /usr/bin/checkmagick32
2011-10-24 22:11:54: checking for rotation
2011-10-24 22:11:54: /usr/bin/checkmagick32
Perhaps the hardware switch is broken.....
Just booted into MS Vista, no rotation there except in mobility center, the rotation button no longer works either so perhaps this is hardware?
is there a soft command to rotate?
thanks for the help

---

### Post by Favux on 2011-10-25
That's a shame.  The swivel hinge switch just failed on a HP 2710p I was helping too.  I suspect that it probably is some debris if it is a spring loaded mechanism or maybe the spring.  Perhaps some oxidation of the contacts?  Whatever it probably wouldn't be hard to repair if we knew where it actually was.  I don't know if it is located in the swivel hinge or elsewhere.  Maybe HP has a PDF showing it?

Sure, you can use xrotate.py as a stand alone rotation script.  The README tells you the details.  In addition the HOW TO has two methods that don't require the switch sensing the tablet state.

The problem is traditionally you'd set the rotation script up in a Launcher and then drag the Launcher into a panel if you just wanted to single click it.  That's how a method 1 script is used anyway.  But Oneiric has made setting up a Launcher a bit of a pain much less the panel part.

---

### Post by cgul1 on 2011-10-26
> **Favux said:**
> That's a shame.  The swivel hinge switch just failed on a HP 2710p I was helping too.  I suspect that it probably is some debris if it is a spring loaded mechanism or maybe the spring.  Perhaps some oxidation of the contacts?  Whatever it probably wouldn't be hard to repair if we knew where it actually was.  I don't know if it is located in the swivel hinge or elsewhere.  Maybe HP has a PDF showing it?

Sure, you can use xrotate.py as a stand alone rotation script.  The README tells you the details.  In addition the HOW TO has two methods that don't require the switch sensing the tablet state.

The problem is traditionally you'd set the rotation script up in a Launcher and then drag the Launcher into a panel if you just wanted to single click it.  That's how a method 1 script is used anyway.  But Oneiric has made setting up a Launcher a bit of a pain much less the panel part.
Thanx Favux.
Not ready to prob into the hinge, altho I do see two screws on there...... maybe later.
I will play with the Xrotate.py for a bit.
Thanks for all you help:)

---

### Post by tpinkfloyd on 2012-01-21
So I tried to do this and now my pen is kinda inverted in movement when I go up it goes left, down= right, right=up, and left=down

I have no idea how it happened

---

### Post by Favux on 2012-01-21
Ah yes.  There is a bug in Natty (0.10.11) and Oneiric's (0.11.0) default xf86-input-wacoms for the Portrait orientations that was fixed in 0.11.1.

I recommend updating xf86-input-wacom.  See part II. in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Or just swap cw and ccw in the script.

However what you are reporting sounds like you've rotated the screen's orientation 90 degrees but not the wacom input tools i.e. stylus.

---

### Post by tpinkfloyd on 2012-01-21
[QUOTE=]However what you are reporting sounds like you've rotated the screen's orientation 90 degrees but not the wacom input tools i.e. stylus.[/QUOTE]

Yes but the screen didn't change at all it is still in standard format. I thought maybe if I turned the screen to tablet mode it would rotate and fix the pen.... It did neither.

---

### Post by Favux on 2012-01-21
OK, I think I'm tracking you.  Wacom stuff rotating but not screen, correct?

Post your xorg.conf file.  It is in /etc/X11.  Often not present anymore but will be since you are using Nvidia proprietary driver.  You probably need to add the option:
```
Option  "RandRRotation"  "on"
```
as described in appendix 1.

---

### Post by tpinkfloyd on 2012-01-21
```

Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by Favux on 2012-01-21
Alright add the option like so:
```
Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Option  "RandRRotation"  "on"
EndSection
```
using:
```
gksudo gedit /etc/X11/xorg.conf
```
Save and reboot and you should be able to rotate.

---

### Post by tpinkfloyd on 2012-01-21
Still no rotate but I think that might also have something to do with the buttons for the tablet itself there is a button for rotating but all it does is open Software Center or Dash Home

---

### Post by Favux on 2012-01-21
Does
```
xrandr -o right

```
in a terminal now rotate you to right Portrait orientation?
```
xrandr -o normal

```
To get back to normal laptop.

---

### Post by tpinkfloyd on 2012-01-21
It says failed to change the screen configuration.

But it does work inverted

[Edit]

It messes with the pen again though left moves right up moves down

---

### Post by Favux on 2012-01-21
Alright, I think that is a driver bug then.

I have a vague memory of the Nvidia driver not being able to do portrait orientation.  Because it is vague I'm thinking that was during a Natty beta.  They fixed it by the time of the Natty release.  It sounds like they have the same or similar problem in your driver and they didn't fix it in time for the Oneiric release.  So with that proprietary driver you may be limited to inverted.  But you now have some keywords to google with.

The stylus is now 180 degrees out of phase, indicating you haven't rotated that.  Did you use the stylus "device name" for stylus in the script?

---

### Post by tpinkfloyd on 2012-01-21
I tried that earlier and it does the weird invert of the stylus up is left left is down thing

---

### Post by Favux on 2012-01-21
Could you post the output of:
```
xinput list
```
in a terminal?

---

### Post by tpinkfloyd on 2012-01-22
The input list only had a Wacom Tablet Stylus and Wacom Tablet Eraser, Just standard named inputs. When I tried the rotate ccw is when it changed the directions to the left was down right was up up was left down was right

---

### Post by Favux on 2012-01-22
I need to see the output from *xinput list* so I know what the "device name" is.  I have a script for you to try but I need that first.

---

### Post by tpinkfloyd on 2012-01-23
I will tell the guy that I fixed the computer for to post it I am sure he would like to know how to fix it.

---

### Post by tipp98 on 2012-02-15
In reply to [post #273]("http://ubuntuforums.org/showpost.php?p=7819309&postcount=273") - regarding bezel buttons.

I've spent some time debugging these buttons and have been able to read them by calling the hotkey query. I can say, as a matter of fact, the following:
1. PNP0C09, the EC, contains the the QBBB register(memory location) that stores the code of the most recent button press. But, When PNP0C14, hp-wmi, runs it's query, QBBB is checked for the button pressed and writes an appropriate scancode to the memory location that is read by the query.
2. The QBBB codes for them are 0x7 & 0x8. The scancodes are defined in Method GBBV (the hp-wmi hotkey query) after DBTN & QBTN (0x4 & 0x5).
3. DBTN & QBTN do not currently use Method GBBV, hp-wmi. Although they also come through hp-wmi when hp-wmi runs it's hotkey query.
4. The BIOS never notifies hp-wmi that a key has been pressed like it does for the tablet switch, thus hp-wmi never queries the BIOS for the codes.

So, an interesting point about that is the issue of the two buttons that come through the keyboard event. Since they also come through the hp-wmi event, there should be no need to reset the keyboard in tablet mode if we can get them working correctly. Although, if we manage to succeed in getting the buttons working, it should lead to a double button press when not in tablet mode.

Now for some speculation on my part. I read somewhere that the _Q?? methods correspond to GPIO pins on the embedded controller. Thus, there should be a _Q method to notify hp-wmi when a button has been pressed. We have this in method _Q16. Looking at a motherboard schematic I have, GPIO16 simply reads T50, with no other reference to T50. So, the question is, is the dsdt wrong, or is the EC not calling method _Q16. I believe it to be the latter, and that the EC needs to be programmed to enable the calling of method _Q16. I am currently looking into how to do that, but wanted to share what I have found so far in case anyone else is still working on this.

---

### Post by alecuba16 on 2012-03-19
Hello,

I'm currently trying to edit the dsdt for have a bezel buttons working and the rotate function.

I'm looking for amd cpu Voltage and frecuency tuning to lower the voltage when it's on idle without k8-powernow (like inten speedstep) using the bios _pss method that is load based selector of OS.

Someone can put more information about that?

---

### Post by Favux on 2012-03-19
Hi alecuba16,

Welcome to Ubuntu forums!

I PM'd tipp98 for you.  To alert him to your post.  I hope you two will be able to collaborate.  I asked him if he has any information on AMD cpu Voltage and frequency tuning.

Don't know if this is any help:  [http://doc.opensuse.org/documentation/html/openSUSE/opensuse-tuning/cha.tuning.power.html](http://doc.opensuse.org/documentation/html/openSUSE/opensuse-tuning/cha.tuning.power.html)

---

### Post by tipp98 on 2012-03-21
> **alecuba16 said:**
> Hello,

I'm currently trying to edit the dsdt for have a bezel buttons working and the rotate function.


My latest findings can be found on the linux-acpi mailing list: [http://www.spinics.net/lists/linux-acpi/msg34647.html](http://www.spinics.net/lists/linux-acpi/msg34647.html)

Feel free to PM me. These buttons have taken a back seat to some other projects, but I would still like to get them working.

---

### Post by yury_v on 2012-04-20
Hi! Thanks for great manual! I have one question: how should I modify the automagic_rotation script, so that the orientation of my screen navigation buttons also switches when the screen is rotated? I have ThinkPad X61 and Ubuntu 12.04, 64bit. Thank you in advance!

---

### Post by Favux on 2012-04-20
Hi yury_v,

Welcome to Ubuntu forums!

Thanks for the thank you.
> how should I modify the automagic_rotation script, so that the orientation of my screen navigation buttons also switches when the screen is rotated?
Are you talking about physical buttons on the X61t's screen bezel or frame?  If so I don't know how to change the key maps without restarting X.

If you are talking about virtual buttons on the screen/LCD itself I'd have to know how they're created and located.  There should be some coordinates somewhere placing them in their locations on the screen that can be changed after a rotation.  Similar to an onscreen keyboard.

---

### Post by yury_v on 2012-04-20
> **Favux said:**
> Hi yury_v,

Welcome to Ubuntu forums!

Thanks for the thank you.

Are you talking about physical buttons on the X61t's screen bezel or frame?  If so I don't know how to change the key maps without restarting X.

If you are talking about virtual buttons on the screen/LCD itself I'd have to know how they're created and located.  There should be some coordinates somewhere placing them in their locations on the screen that can be changed after a rotation.  Similar to an onscreen keyboard.
Yes, I meant physical buttons on the screen frame. Anyway, thank you!

---

### Post by Stealthp90 on 2012-04-20
I think if you are using a slandered version of Ubuntu such as 12.04 you should just be able to use the desktop recorder app in the Ubuntu software center. If you are using any kind of custome tablet os distro then sorry but thats all that i got.

---

### Post by fire_qc on 2012-05-27
Please someone help!!!  My HP Pavilion have kubuntu 12.04 fresh install but after many try to install magick-rotation nothing works...  No green arrow and no behaviour when turning screen..  I'm out please help...

---

### Post by Favux on 2012-05-28
Hi fire_qc,

No Magick (green rotating arrow) icon in the systray?

Did the Installer seem to run OK?  Could you attach the install_log to your next post?

---

### Post by fire_qc on 2012-05-28
Where's is that file???  I'll copy-paste it's content..

---

### Post by Favux on 2012-05-28
It's in the magick-rotation folder that you downloaded and installed from.  The Installer creates it when installing.

---

### Post by fire_qc on 2012-05-28
I can't see that file, but I don't understand why after rebooting tons of times, it finally works!!!  OMG!!!

Thanks to all...

---

### Post by dj188us on 2012-12-08
Hi,

Thanks for putting up this page. I just got the Magick Rotation working and everything is working like a charm on a hp 2710p running ubuntu 12.04. However there is still an interesting issue with some software outside of Magick Rotation.

When I rotate from normal view to the side, I find a 'good thing' that most software realizes the changed parameters of the screen orientation, i.e. that the width and height of the screen has change. A good example is chrome, which fits the screen upon rotation precisely.  However, other software, such as Ubuntu task bar, the document-folder-default program, and libre office do not recognize the changed parameters causing the program to open to a full extent that is half off the screen.

Am I missing a step, or is there a known workaround?

Thanks,
dj188us

---

### Post by Favux on 2012-12-09
Hi dj188us,

Welcome to Ubuntu forums!


In Precise (12.04) are you using Unity 2D or 3D?

With 3D the task bar resizes on rotation for me, and as I recall also in 2D.  I gather from:
> document-folder-default program
you mean Nautilus?  Nautilus opens properly sized for me in either laptop or tablet.  If already opened in one or the other and then rotated it can be partially off screen and I just drag it to place.  Sometimes a window can dissapear if you have it right on the rotating edge.  So you need to use the Desktop switcher and go to it on the next Desktop and slide it over enough that you can grab it when you go back to the original Desktop.  If you want it there that is.

Maybe it is your video chipset/driver.  Intel MB video?
```
lspci | grep VGA
```

---

### Post by dj188us on 2012-12-12
> **Favux said:**
> Hi dj188us,

Welcome to Ubuntu forums!


In Precise (12.04) are you using Unity 2D or 3D?

With 3D the task bar resizes on rotation for me, and as I recall also in 2D.  I gather from:

you mean Nautilus?  Nautilus opens properly sized for me in either laptop or tablet.  If already opened in one or the other and then rotated it can be partially off screen and I just drag it to place.  Sometimes a window can dissapear if you have it right on the rotating edge.  So you need to use the Desktop switcher and go to it on the next Desktop and slide it over enough that you can grab it when you go back to the original Desktop.  If you want it there that is.

Maybe it is your video chipset/driver.  Intel MB video?
```
lspci | grep VGA
```

Ok, so sorry I'm new to ubuntu and just figuring things out. 

So, the window switcher helps for libre office and other like apps, Thanks much.

My original question the should not have been for the task bar, but (I think) the "dash home". It is the top most app/button on the task bar for a newly installed 12.04 os, which allows you to open other apps.

It still opens up too large for the rotated tablet screen and the window switcher does not solve the issue.

Thanks, and sorry for not replying sooner. I have exams and projects due this week.

-dj188us

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
~$ 
```

---

### Post by Favux on 2012-12-15
Sure I understand.  Have to prioritize.
> My original question the should not have been for the task bar, but (I think) the "dash home". It is the top most app/button on the task bar for a newly installed 12.04 os, which allows you to open other apps.

It still opens up too large for the rotated tablet screen and the window switcher does not solve the issue.
Since both MyUnity and Ubuntu Tweak have a setting to control Dash size you'd think it is suppose to be resizable.  The settings are Automatic, Desktop, and Netbook.

But testing that with MyUnity only shows Netbook makes it open fullscreen.  But on Automatic or the other two settings it opens too large in portrait for me.  Didn't install Ubuntu Tweak on the tablet PC to test.  I don't know if that means there is a bug for Dash and rotation or the feature hasn't been implemented.  If it is there we'd have to figure out the setting the two configuration gui's are using that and test manually.

Don't see anything in CompizConfig Settings Manager (CCSM) dealing with it.


Looks like things are OK with the Intel MB video chipset and video driver because it is rotating correctly and other things are working.

---

### Post by gco on 2013-01-21
Hi, Favux. First of all, I'd like to thank you for all the help on trying to improve tablet support on Ubuntu. I must say I would probably be still stuck with Windows if it wasn't for you and a few other fellows only, who (heroically) posted a bunch of priceless tips. I'm a tablet PC fan and had not yet had a good experience with Linux on my HP tc4400. I tried twice before, but always ended up coming back to Windows. Not now!

I've spent the last three days reading all about issues on making Linux (Ubuntu, particularly) work on my Tablet PC TC4400. Now, I got Ubuntu 12.04 (PP) and almost everything working, including:
- automatic rotation (w/ Magick Rotation);
- jog dial on the side;
- pen/eraser ajustments when on dual screen mode;
- fingerprint reader (w/ fingerprint-gui);
- decent handwriting recognition software (MyScript Stylus).

The last remaining unresolved issues are:
1) 3 bezel buttons (text input tool, rotation and Q Menu); [SOLVED, see post #628]
2) auto suspend session after closing the screen;
3) sd card reader; [SOLVED]
4) pcmcia.

Items 2, 3 and 4 are not crucial. Item 1 however is very important to me (and all tc4400 users, I think). With no success I tried everything I found so far. I followed the Apendix 2 of this tutorial - nothing on xev, no kernel key codes returned. The 3 buttons seem just dead! I get no signal. They used to work just fine on Windows.

Since it's been a while since we have no updates on this post and no one else reports effective worthy tips, I ask you if you could help on this, please.

For now, I (monkey) patched Magick-Rotation to include a "Rotate" MenuItem to the context menu that opens when we right click the system tray green arrow icon. (Please, check the attachments if interested: magick-rotation.txt:138 and gui_gtk.py.txt:401)

Once again, thank you, thank you very much.

---

### Post by Favux on 2013-01-21
Hi gco,

Welcome to Ubuntu forums!


Thanks, I'll take a look at the Magick code.

Wonder if the the TC1100 fix applies?  Apparently you touch the non-working bezel buttons with the stylus?  Anyway wcmISDV4.c hasn't changed all that much so maybe.  See Erich's patch for the HP TC1100:  [http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTinaQuFPLB6R20xfnYGNPmJ0c6ZWrQ%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTinaQuFPLB6R20xfnYGNPmJ0c6ZWrQ%40mail.gmail.com&forum_name=linuxwacom-devel)

Far less likely I'd think is tipp98's bezel button fix for the TX2***'s.  Heck, maybe it works for the later TCs also.  See post #2 on the new [Tablet PC Rotation HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395").
> Since it's been a while since we have no updates on this post and no one else reports effective worthy tips, I ask you if you could help on this, please.
Ubuntu forums changed policy at the end of June 2012.  Posts after then can only be edited for 7 days.  That locked all tutorial and HOW TO authors out of their tutorials and HOW TOs.  Which is why no updates on the HOW TO itself.

---

### Post by gco on 2013-01-21
> **Favux said:**
> Wonder if the the TC1100 fix applies?  Apparently you touch the non-working bezel buttons with the stylus?  Anyway wcmISDV4.c hasn't changed all that much so maybe.  See Erich's patch for the HP TC1100:  [http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTinaQuFPLB6R20xfnYGNPmJ0c6ZWrQ%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTinaQuFPLB6R20xfnYGNPmJ0c6ZWrQ%40mail.gmail.com&forum_name=linuxwacom-devel)

Thanks Favux. I've already tried Erich's fix. It didn't work. I dug as deeper as I could in order to understand the code and update whatever needed, such as changing 'WCM_MAX_MOUSE_BUTTONS' to 'WCM_MAX_BUTTONS'. Every change I made resulted in system crash. I was able to compile and replace the driver but Unity stopped loading properly - screen turns all black after Ubuntu's logo first appearance and stucks.


> **Favux said:**
> Far less likely I'd think is tipp98's bezel button fix for the TX2***'s.  Heck, maybe it works for the later TCs also.  See post #2 on the new [Tablet PC Rotation HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395").

I was not aware of this solution. I'll give it a try and report back. It seems very promising.


> **Favux said:**
> Ubuntu forums changed policy at the end of June 2012.  Posts after then can only be edited for 7 days.  That locked all tutorial and HOW TO authors out of their tutorials and HOW TOs.  Which is why no updates on the HOW TO itself.

I didn't know this either. Anyway, after all you did, you are totaly dismissed of any guilt :). Of course my note was not a complaint, but a completly innocent observation. Now I get it. Thanks.

---

### Post by gco on 2013-01-22
Favux, I tried Kyle's solution. It seems nothing changed at all. Still no signal.

Do you have notice of anyone trying to make these bezel buttons work on tc4400? On the other hand, with proper orientation, I could try different moves here, test and report back, since I own a tc4400.

Thanks.

---

### Post by Favux on 2013-01-22
There have been a couple of folks looking at the TCs.  Don't think anyone has been active recently but I'll look around at my notes and bookmarks and see if something jogs my memory.

My best guess is it would be something along the line of Erich's fix.  But if you were updating the code 'WCM_MAX_MOUSE_BUTTONS' to 'WCM_MAX_BUTTONS' etc. and still getting nowhere...  But system crash?

I'm going to look that thread over a bit, maybe.  Really haven't paid much attention to it before.

---

### Post by gco on 2013-01-22
> **Favux said:**
> My best guess is it would be something along the line of Erich's fix.  But if you were updating the code 'WCM_MAX_MOUSE_BUTTONS' to 'WCM_MAX_BUTTONS' etc. and still getting nowhere...  But system crash?

Well... I'm not a Linux expert. "System crash" might sound exagerated, I agree. In fact, I got some critical failure after applying the patch, but actually I'm not able to identify it properly. There was no error reported on screen. During boot, screen turned black right after first appearance of Ubuntu's logo and got stuck. (The expected behaviour would be a blink, a second appearance of Ubuntu's logo and then the login screen.)

These symptoms were observed after every try I made on modifying wcmISDV4.c. I was still able to boot the system in terminal mode (no Unity) and recover the backup file of the driver.

I'm guessing a crash of Unity because once I tried restarting the GUI only, instead of rebooting the whole system. The same bug occurred.

---

### Post by Favux on 2013-01-22
If you are using Ubuntu Precise 12.04 did you apply the frankenserver patch to xf86-input-wacom after patching wcmISDV4.c with Erich's patch?  Because without the frankenserver patch xf86-input-wacom will freeze the system in Precise if the tablet is attached.  Which it always is with a tablet PC.

---

### Post by gco on 2013-01-22
> **Favux said:**
> If you are using Ubuntu Precise 12.04 did you apply the frankenserver patch to xf86-input-wacom after patching wcmISDV4.c with Erich's patch?  Because without the frankenserver patch xf86-input-wacom will freeze the system in Precise if the tablet is attached.  Which it always is with a tablet PC.

Wow! I'm using PP but I didn't apply frankenserver's patch. Actually, I haven't seen any reference to this. Where can I find this patch?

*UPDATE:* I got something on this post [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408). This is what you're talking about, I assume.

Thanks.

---

### Post by Favux on 2013-01-22
Yes.  Not surprised you weren't aware of it.  Part of the fallout from the issue we discussed earlier.
[http://ubuntuforums.org/showpost.php?p=12455111&postcount=1401](http://ubuntuforums.org/showpost.php?p=12455111&postcount=1401)
[http://ubuntuforums.org/showpost.php?p=12455083&postcount=1118](http://ubuntuforums.org/showpost.php?p=12455083&postcount=1118)
[Wacom Bamboo Pen and Touch tablet HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408")
[Linux Wacom HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110304")

---

### Post by gco on 2013-01-22
> **Favux said:**
> Yes.  Not surprised you weren't aware of it.  Part of the fallout from the issue we discussed earlier.
[http://ubuntuforums.org/showpost.php?p=12455111&postcount=1401](http://ubuntuforums.org/showpost.php?p=12455111&postcount=1401)
[http://ubuntuforums.org/showpost.php?p=12455083&postcount=1118](http://ubuntuforums.org/showpost.php?p=12455083&postcount=1118)
[Wacom Bamboo Pen and Touch tablet HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408")
[Linux Wacom HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110304")

That's perfect Favux. I'll try this out and report back.
Thank you very much.

---

### Post by gco on 2013-01-23
Good news Favux. It worked! Now I have the 3 bezel buttons of my tc4400 working.


Basically I applied the following two patches to xf86-input-wacom driver:
[LIST=1]
[*]frankenserver's - from [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408) (section II), thanks to you =D>
[*]added the lines below to wcmIDSV4.c:801
[/LIST]
```
        /* Soft keys outside tabletPC  TC4400 */
	if ((data[0] & 0xC1)==0xC1) { 
		switch (data[1]) {
			case 0x01: /* Edit */
				/*DBG(8, priv->debugLevel, ErrorF("isdv4Parse special key EDIT\n"));*/
				/*Simulate mouse button 15 press when EDIT */
				xf86PostButtonEvent(pInfo->dev, 1, 15, 1,0,0);
				xf86PostButtonEvent(pInfo->dev, 1, 15, 0,0,0);
				break;
			case 0x02: /* Recicle */
				/*DBG(8, priv->debugLevel, ErrorF("isdv4Parse special key RECICLE\n"));*/
				/*Simulate mouse button 16 press when RECICLE */
				xf86PostButtonEvent(pInfo->dev, 1, 16, 1,0,0);
				xf86PostButtonEvent(pInfo->dev, 1, 16, 0,0,0);
				break;
			case 0x04: /* Quick */
				/*DBG(8, priv->debugLevel, ErrorF("isdv4Parse special key QUICK\n"));*/
				/*Simulate mouse button 17 press when QUICK */				
				xf86PostButtonEvent(pInfo->dev, 1, 17, 1,0,0);
				xf86PostButtonEvent(pInfo->dev, 1, 17, 0,0,0);
				break;
			default: /* Not reconized */
				break;
		}
	}


```

[INDENT](Note that I haven't used Erich's patch here, but a modified version from [_this one_]("http://code.google.com/p/linuxwacom-patch-for-tc4400/downloads/list") of Igor Galarraga's.)[/INDENT]


I downloaded xf86-input-wacom-0.19.0, made these two changes, compiled and installed. After reboot, I started catching bezel button signals with xev. 

Then, all I had to do was using xbindkeys to bind mouse buttons 15, 16 and 17 respectively to Writing tool, Rotate and Q-Menu buttons. So I added the following lines to my .xbindkeysrc config file:

```
# Binds TC4400's bezel buttons

# Writing tool
# "MyScriptStylus" in my case, but "Cellwriter" is a more commom choice
"MyScriptStylus"
   b:15 + Release

# Rotate
# Used a script provided by Brancaleone at http://ubuntuforums.org/showthread.php?t=1483623&page=4
# Magick-Rotation is still responsible for automatic rotation when switching the screen from one mode to another; while this sh script deals with Rotate bezel button. Perhaps I could use only Magick-Rotation features here.
"/usr/bin/rotator"
   b:16 + Release

# Q-Menu
# Still trying to open Unity's launcher panel here (without using xdotool), but you can bind it to whatever you want. In my case, I set Unity's Launcher to hide when not focused, so it would be nice if I could use Q button to open/focus it. I couldn't yet find a way to do that without xdotool though.  
"[do something]"
   b:17 + Release
```


This is it! Thank you very much. Your tip about frankenserver's patch was crucial.

---

### Post by Favux on 2013-01-23
Beautiful gco!  :)  Thank you for posting the tutorial.


Would you mind if I posted your solution on the new [Tablet PC Rotation HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395") too?

---

### Post by gco on 2013-01-23
> **Favux said:**
> Would you mind if I posted your solution on the new [Tablet PC Rotation HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395") too?
Of course I don't mind! Please be my guest.

---

### Post by Favux on 2013-01-25
Hi gco,

Thought you should know I'm leaning towards including your "Rotate" suggestion for Magick.  Seems to fit the tray menu, it's in context and makes sense.

---

### Post by gco on 2013-01-25
> **Favux said:**
> Hi gco,

Thought you should know I'm leaning towards including your "Rotate" suggestion for Magick.  Seems to fit the tray menu, it's in context and makes sense.

Good to know Favux. Please let me know if you need anything.

---

### Post by tipp98 on 2013-04-02
Good news, I sent the patch to enable the bezel buttons to the platform drivers mailing list and it has been accepted into the 3.9 kernel.

Bad news, the Broadcom driver wl.ko broke with kernel 3.8.

So, I would say to keep an eye out for distro updates containing the 3.9 kernel, but I shall preface that with, make sure the wifi drivers have been fixed before updating. It may be a while.

---

### Post by Favux on 2013-04-07
Hi tipp98,

That is good news!  :)

Nice work.

Bummer about the Broadcom wireless driver.  Sure hope it is fixed quickly.  It would be nice if the 3.9 kernel finally supported everything.

---

### Post by tipp98 on 2013-04-13
Can anyone confirm that the bezel button patch works on TC models? The patch is no good for some other HP models so I need to match against something more specific than the GUID. If you have a model that it works on could you post your dmi info:

```
$ sudo dmidecode -t 1

```
```
# dmidecode 2.10
SMBIOS 2.4 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP Pavilion tx2500 Notebook PC
	Version: Rev 1
	Serial Number: CNF8452N78
	UUID: 434E4638-3435-324E-3738-00238B1ACEEC
	Wake-up Type: Power Switch
	SKU Number: KD436AV
	Family: 103C_5335KV

```

---

### Post by bugle on 2013-05-15
Hello!  
    This seems the right forum to inquire...
 I'm having trouble w/ rotation, and getting the screen soft buttons (Q, Rotate, ePen).
I've followed the patching for xf86-wacom-0.20.0 in the tablet rotation howto...
(patched wacom-0.20.0 with frankenserver >0.18  and the add tc4400 bezel uttons patch) they both patched successfully and the new driver compiled clean and  I installed magick rotation, the rotator script, edited  .xbindkeysrc  I rebooted....
    The tablet was docked (in the docking station) in laptop configuration... gdm loaded in landscape, logged in... desktop loaded in portrait!!!
I undocked... and here I'm guessing magick rotation flipped the screen to landscape.
    When undocked... folding the screen with the swivel hinge into tablet mode has no effect on rotation of the screen. However... putting the laptop into the docking station will initiate a screen rotation (cursor not rotated)
the screen buttons do not function in either position.

```
bugle@TC44ux ~ $ sudo dmidecode -t 1 # dmidecode 2.11
SMBIOS 2.4 present.


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP Compaq tc4400 (EN357UT#ABA)
    Version: F.0C
    Serial Number: CND71604XR
    UUID: A8F4FA4E-B5EC-DB11-0498-66990E1EE129
    Wake-up Type: Power Switch
    SKU Number: EN357UT#ABA
    Family: 103C_5336AN

```

---

### Post by Favux on 2013-05-15
Hi bugle,

In Setup did you check the "BIOS hinge switch values reversed?" box and Save it?

---

### Post by bugle on 2013-05-15
Hello Favux,
      Yes, the box is checked.
  (another possible reversed setting I noticed... someone else with a TC44C had different ID's for the stylus and eraser than mine, 12 and 14 , I think they had ... )
mine...
```
bugle@TC44ux ~ $ xsetwacom listSerial Wacom Tablet stylus          id: 11    type: STYLUS    
Serial Wacom Tablet eraser          id: 13    type: ERASER    



```

This machine is a large upgrade from my previous TC1k running a 2.3 kernel in Gentoo.

---

### Post by Favux on 2013-05-15
> This machine is a large upgrade from my previous TC1k running a 2.3 kernel in Gentoo. 
I'll bet.

ID number can change due to hotplug order.  That's why the "device name" from **xinput list** is preferred in a script or what not.  ID # is convenient for diagnostics in current session.

And yes the dock signal and hinge switch signal can be confabulated.  That was the case for the consumer TX2*** models until a user got the kernel maintainer to seperate them out in hp-wmi.c.  That actually is in this thread.

Not sure what is going on.  One possibility I suppose is your BIOS version.  At this point I don't know how much luck we'd have trying to sort out BIOS versions.  Any way to tell if you have a really old one?

In Advanced Setup you could turn the debugging tool on and record a laptop to tablet mode and back session.  See if that tells us something.  I'd leave out docking for now.  Could also look at running Magick from the shell and see what that says.

---

### Post by bugle on 2013-05-15
Favux,
  the ole tc1000s were maxed out at 768M memory (1G if you wern't scared of prybars)
I'll turn on debug... where's the log stored?
Bios is the most current version of the bios  F.0C (I upgraded it with HP's DrDos  boot disk on a usb drive before installing Mint)
I haven't patched the hp-wmi yet... I was unclear if that was still neccessary.
I was originally trying to get the soft buttons (Q, Rotate, ePen) working BEFORE actual automatic rotating. I don't know at this point which is going to be a bigger pain.
   I can fold the screen with the pivot/hinge into tablet position and then rotate the screen thru Gnome display settings from normal to clockwise (portrait)  and back again... curser / stylus seems fairly well calibrated with no intervention at all from me...  although when returning from the keyboard being covered by the screen I've found 20 or more  gnome terminals started ( I'd like to lock the keyboard somehow, when in tablet mode) gotta figure out where those random terminals are coming from...

---

### Post by bugle on 2013-05-15
Hey Favux!
  turning on the log made magick !  it rotated the screen thru flipping the pivot hinge...
```
22:40:44: cur_state: 2 22:40:44: old_state: 0 
22:40:44: calling rotation b: 
22:40:44: right
22:40:45: calling cellwriter --show-window
22:40:45: Change to Tablet mode
22:40:45: checking for rotation
22:40:45: /usr/bin/checkmagick32
22:41:12: cur_state: 0 
22:41:12: old_state: 2 
22:41:13: calling rotation a: 
22:41:13: normal
22:41:13: calling cellwriter --hide-window
22:41:13: Change to normal state
22:41:13: checking for rotation
22:41:13: /usr/bin/checkmagick32



```

how bout that? 
and it still works now without  debugging tool on.   cool!

still no screen buttons

---

### Post by Favux on 2013-05-15
Weird but cool.  Good it is working now.

Yeah, memory is a problem with the TC1000s.

No you don't need to patch hp-wmi.c.  Matthew Garrett did that ages ago.  I just wasn't sure if that applied to the TC4000s or not.  Can't remember.

So down to the bezel buttons.  The patch applied OK to xf86-input-wacom 0.20 as far as you could tell?  Wonder if changes to xf86-input-wacom broke to bezel button patch functionality.  There's that alternative patch too.

I gather you're using the updated how to on the Mint forums.  Are you posting there too?

---

### Post by bugle on 2013-05-16
FavUx,
 Yes the patches completed and xf86-wacom-0.20.0 compiled ok...
  at least I'm getting SOME xev recognition... no Keycodes tho. But this does lead me to believe that the button patch is doing something.
(I wasn't getting any responce from xev before the patch... (note here, that I may not have had the cursor in the box in xev when testing for keycodes before the button patch was applied)  The Frankenserver > 0.18 patch to xf86-wacom-0.20.0  patched simply and with out error
the AddHPTC****but'.patch I had to change to the wacom src directory and apply with -p0, then it applied with out error.

xev pressing screen buttons...
```
KeymapNotify event, serial 32, synthetic NO, window 0x0,    keys:  4294967212 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


LeaveNotify event, serial 32, synthetic NO, window 0x2e00001,
    root 0xac, subw 0x2e00002, time 75854826, (41,33), root:(44,542),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 0


EnterNotify event, serial 32, synthetic NO, window 0x2e00001,
    root 0xac, subw 0x2e00002, time 75854826, (41,33), root:(44,542),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 0



```
All three screen buttons have the same output...  only the time changes.

  I DID post in Mint forums, but not directly to your Howto, rather in the forums hardware section.

---

### Post by Favux on 2013-05-16
I'm  still trying to figure out why using the debugging log got things working.  I think maybe it was the Save.  Magick doesn't create its .xml file until the first Save, before that it uses the defaults.  So the BIOS value switch check box wouldn't have been active before then I guess.

I went through the bezel button stuff for the TCs at the time they were first posted and thought I mostly understood what was going on.  But have long since forgotten the details.  But don't they use xsetwacom?  Not real sure xev is going to show a button press or release event given that.

---

### Post by bugle on 2013-05-17
Favux,
   my noodle is worn down and I need to get my plotter up and running... I'm not going to sweat about the extraneous toys (buttons) right now. The tablet is very usable now... I've got tablet mode working and stable Much quicker than a Gentoo install!   I'm going to use the tablet and get more familiar with its quirks and let the bigger ones rise to the top. I've got a bunch of familiarizing todo with this new for me distribution .
  thank you for your help.

---

### Post by Favux on 2013-05-17
You're welcome.

I haven't used Gentoo but Jayhawk had it.  I gather it taught you a lot but he'd complain about the time it took to compile everything (that's Gentoo rigth?).

I'm fairly confident you'll figure out the bezel buttons at some point.  Glad to hear otherwise it is giving you what you wanted.

---

