---
title: "nvidia 5950 ultra - tseliot guide"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by ART_Adventures on 2006-09-16
Hello People,

I decided to install ubuntu and to then install the drivers for my geforce 5950 Ultra card. I used this guide here: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_TO_DO_IF_THE_METHOD_YOU_CHOSE_DID_NOT_WORK_OR_WORKED_PARTIALLY](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_TO_DO_IF_THE_METHOD_YOU_CHOSE_DID_NOT_WORK_OR_WORKED_PARTIALLY)

I selected method 1, and the system I am using is: 2.6.15-26-386

I followed each of the steps; at step 3 I selected:

sudo apt-get install nvidia-glx

and at step 6 I selected:

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

At the end, I restarted the computer and a problem occurs. I do not get to see the ubuntu login screen. At this point, the screen is black and the power light on my monitor changes from green to orange.

Can anybody help me,
Thanks.
Alan.

---

### Post by tseliot on 2006-09-16
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine

I'll give you further instructions after you do that

---

### Post by ART_Adventures on 2006-09-16
Thank you for your reply. I'm sorry if this response seems a little lengthy, but I wanted to reply in some detail so that it might help and be useful to others who may also encouter this problem.

I followed the instructions you gave and unfortunately have not yet been able to boot successfully back into the Ubuntu desktop.

I booted in Recovery mode from the grub menu, and entered:

```
dpkg-reconfigure xserver-xorg
```

This took me to a utility where I answered a number of questions, mostly I press enter for defaults. These screens were:

1. Autodetect Graphics Card [Yes/No]. *I select Yes

2. Select Type. *I select NV

3. Graphics Card Identifier. *It automatically enters:
"nvidia geforce 5950 ultra@ and I press OK.

4.Info dialog about bus format. *I press OK.

5. Enter video card bus. Default: PCI:1:0:0. *I press OK. I don't know if this is correct. I saw the word PCI and believe my card is AGP- if this is related, I don't know.

6. Enter amount of mem in KB for card to use. Empty text box. *I just press enter.

7. Use kernel frame buffer [Yes/No]. If I choose No I find that when Ubuntu later starts back in normal mode (login screen) I get the coloured blocks and mess all over the screen. If I choose Yes, then when it reoots in normal mode (login screen) it shows me a dialog about x server not being able to start and asks whether I want an error report. I choose Yes and include that report at the end of this message.
8. Autodetect keyboard. *I choose Yes. It correctly shows "UK".

9. Select XKB rule for keyboard. *I just press enter.

10. Select keyboard model. Default: PC104. *I just press enter.

11. Select Keyboard Variant. *I just press enter.

12. Select Keyboard Options. *I just press enter.

13. Select Mouse. I choose Imp/ps2.

14. Emulate 3 Button Mouse? I choose Yes. I have two button.

15. Then an advanced screen about modules. *I just press enter.

16. Write Default files section to config file? *I choose Yes.

17. Autodetect Monitor. I choose the default: Yes.

18. Enter Monitor ID. It says "Generic Monitor". I just press enter.

19. Select video mode. * I just press enter.

20. Write monitor ranges to config file. I choose defaut: Yes.

21. Color depth. I choose default: 24.

--------------------------------

If I select Yes to 7(use kernel frame buffer). When the system reboots in normal mode to the login screen I get an error message  box about xserver not being able to start. The report is as follows:

x windows system version 7.0.0
release date 21 december 2005
x protocal version 11, revision 0, release 7.0
build operating system: linux 2.6.15.7 i686
current operating system: linux alan-desktop 2.6.15-26-386 \1 PREEMPT

module loader present
markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(ww) warning, (ee) error, (NI) not implemented, (??) unknown,
(==) log gile: "/var/log/xorg.0.log" time: sat september 16 2006
(==) using config file: "/var/x11/xorg.conf"


Thanks. Sorry for the long post :-)

---

### Post by tseliot on 2006-09-16
follow my suggestion again but this time use "vesa" instead of "nv"

---

### Post by ART_Adventures on 2006-09-16
Thanks for the reply :-) I selected Vesa, and now I can log into ubuntu normally again. That seemed to work.

Of course, I don't think the nvidia driver was installed since in System|Screen Resoluton I still cannot select a res above 1024x768 or a refresh rate other than 61hz.

What would you suggest now?

Thanks for helping me with this.

---

### Post by tseliot on 2006-09-16
Ok, let's try to diagnose the error:

Boot with the "vesa" driver in your xorg.conf (as you did)

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "vesa" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by ART_Adventures on 2006-09-16
OK. I'm going to try that now. Before I do so, how exactly do I change the driver to nvidia in my xorg.conf.

Should I actually open the file in the editor and change the following:

Section "Device"
	Identifier	"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Do I change the driver line to read:

Driver      "nvidia"

?

Though, I would like to confirm that since the file says it's read only. Or, do I open a terminal and type:

sudo apt-get install nvidia-glx

?

PS. I also notice that, if I click Log Out and it takes me back to the login screen, if I press "Ctrl + Alt + F1" there, it seems to have no affect.

Thanks.

---

### Post by tseliot on 2006-09-17
> **ART_Adventures said:**
> OK. I'm going to try that now. Before I do so, how exactly do I change the driver to nvidia in my xorg.conf.

Should I actually open the file in the editor and change the following:

Section "Device"
	Identifier	"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Do I change the driver line to read:

Driver      "nvidia"

?
Exactly

> **ART_Adventures said:**
> Though, I would like to confirm that since the file says it's read only.
Type:
```
sudo nano -w /etc/X11/xorg.conf
```
and do what you need to do.

then press CTRL+X to exit (save the file)


> **ART_Adventures said:**
> PS. I also notice that, if I click Log Out and it takes me back to the login screen, if I press "Ctrl + Alt + F1" there, it seems to have no affect.
If CTRL ALT F1 doesn't work try point 13 of the Problems section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by ART_Adventures on 2006-09-17
Thanks for the reply, tseliot.

I must be doing something wrong here. The first thing I tried to resovle was the ctrl+alt+f1 boot issue, since I'll need this menu to follow your instructions. I took a look at point 13, opened a terminal and typed:

```
sudo nano -w /boot/grub/menu.lst
```

This showed me the contents of that file in the terminal and I used my arrow keys to scroll down to where it said:

```
# defoptions=quiet splash
```

and I removed splash so that it read:

```
# defoptions=quiet
```

Then I pressed Ctrl+X and pressed 'Y' to confirm the save.

Then I entered:

```
sudo update-grub
```

And then it showed:

```

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.15-26-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

After this, I restarted the computer. I was expecting the login prompt to look basic and austere, but it seemed to show no difference at all, and I still can't use the ctrl+alt+f1 keyboard combination. I loaded back up the menu.lst file in the terminal and the changes I made to # defoptions appear to be correct- there is no word "splash".

---

### Post by tseliot on 2006-09-17
> **ART_Adventures said:**
> Thanks for the reply, tseliot.

I must be doing something wrong here. The first thing I tried to resovle was the ctrl+alt+f1 boot issue, since I'll need this menu to follow your instructions. I took a look at point 13, opened a terminal and typed:

```
sudo nano -w /boot/grub/menu.lst
```

This showed me the contents of that file in the terminal and I used my arrow keys to scroll down to where it said:

```
# defoptions=quiet splash
```

and I removed splash so that it read:

```
# defoptions=quiet
```

Then I pressed Ctrl+X and pressed 'Y' to confirm the save.

Then I entered:

```
sudo update-grub
```

And then it showed:

```

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.15-26-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

After this, I restarted the computer. I was expecting the login prompt to look basic and austere, but it seemed to show no difference at all, and I still can't use the ctrl+alt+f1 keyboard combination. I loaded back up the menu.lst file in the terminal and the changes I made to # defoptions appear to be correct- there is no word "splash".

This is weird...

You don't press "+" between "ctrl", "alt" and "f1", do you?

---

### Post by ART_Adventures on 2006-09-17
No :-) I press Ctrl, Alt, F1 almost simulatenously. In the same way as I would press Ctrl + Alt + Del.

The contents of my menu.lst are (incase this helps):

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry


# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST


### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda7 ro


## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet


## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,5)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/sda7 ro quiet
initrd          /initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,5)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/sda7 ro single
initrd          /initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by tseliot on 2006-09-17
I wouldn't know how to solve that problem...

Let's try this:

Boot in Recovery Mode (it will boot to the command line)

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano -w /etc/X11/xorg.conf
```
Set the driver back to "vesa" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo reboot
```
and boot as usual


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by ART_Adventures on 2006-09-17
Ok. I'll try this. Before I do that, to set the nvidia driver in recovery mode, do I type the same at the prompt:

```
sudo nano -w /etc/X11/xorg.conf
```

And then presumably, I edit the file much like I edited menu.lst?

---

### Post by tseliot on 2006-09-17
> **ART_Adventures said:**
> Ok. I'll try this. Before I do that, to set the nvidia driver in recovery mode, do I type the same at the prompt:

```
sudo nano -w /etc/X11/xorg.conf
```

And then presumably, I edit the file much like I edited menu.lst?

yes. But in Recovery mode you don't even need to use "sudo"

---

### Post by ART_Adventures on 2006-09-17
Thanks for the reply. I ran into a problem.

I entered recovery mode and typed

```
nano -w /etc/X11/xorg.conf
```

I edited the file so the driver line read: "nvidia"

I pressed Ctrl + O to save and then Ctrl + X to exit.

I then typed

```
start x -- -verbose5 -logverbose 5
```

At this point writing begins to scroll down the screen faster than I can read it, only for about a second, and then the display mode appears to change- or something. The screen goes black and the power light on my monitor turns orange in the same way it does when yesterday I tried booting normally with nvidia drivers set.

I tried pressing Ctrl + Alt + F1 and Ctrl + C and these appear to have no affect, at least so far as the screen remains black and the power light orange.

Thanks.

---

### Post by tseliot on 2006-09-17
I see...

Try point 4 of the Problems Section of my guide

---

### Post by ART_Adventures on 2006-09-17
Thanks for the reply. I tried section 4 of the problems section guide, and I set the xorg.conf to both include and omit the line Option "Accel" "off". It looks as follows.

```

Section "Device"
	Identifier	"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "0"
	Option		"RenderAccel" "off"
	Option		"IgnoreDisplayDevices" "DFP,TV"
	Option		"NoRenderExtension" "off"
	Option		"AllowGLXWithComposite" "off"
	Option		"Accel" "off"
EndSection

```

In all cases, it cause that black screen problem whenever I type in recovery mode:

```

starx -verbose 5 -logverbose 5

```

I get the impression this isn't a good thing. Do you have any suggestions? I know it's a reasonably old card, and though it would be great to achieve its full potential in Linux, my main aim is to get that higher res of 1280x1024 since right now it looks similar to Windows Safe mode.

Thanks :-)

---

### Post by tseliot on 2006-09-17
Try also point 10 of the problems Section.

If that doesn't work you should ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by ART_Adventures on 2006-09-17
Thank you for the reply. Unfortunately, step 10 didn't seem to solve it either. I edited the xorg.conf to look as follows:

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "0"
	Option		"RenderAccel" "off"
	Option		"IgnoreDisplayDevices" "DFP,TV"
	Option		"NoRenderExtension" "off"
	Option		"AllowGLXWithComposite" "off"
	Option		"Accel" "off"
	Option		"UseEDID" "False"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768_61" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768_61" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768_61" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768_61" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768_61" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768_61" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

and the same crash occures when startx is called in recovery mode.

Nevertheless, I would like to thank you for all your help and information. If you think of any more suggestions please let me know. I have started a thread over at the forum you mentioned here: 

[http://www.nvnews.net/vbulletin/showthread.php?p=992134&posted=1#post992134](http://www.nvnews.net/vbulletin/showthread.php?p=992134&posted=1#post992134)

If I finally reach a solution I will let you know so, if you want, you can add that info to your nvidia driver guide.

Thanks.

---

### Post by ART_Adventures on 2006-09-17
I made some progress to this. I booted into recover mode and typed:

```

startx -- -verbose 5 -logverbose 5

```

and the error occured where the monitor power light turned orange. However, by pressing Ctrl + Alt + BackSpace I managed to get back to a command prompt and copied over the log, as suggested.

The log was rather long. But is as follows...

---

### Post by ART_Adventures on 2006-09-17
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux alan-desktop 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 17 13:52:46 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1458,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 8086,2573 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1458,24d2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1458,24d2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1458,24d1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1458,24d2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1458,a002 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0333 card 1043,814e rev a1 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1019 card 1458,1019 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:05:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfa0fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfa100000 - 0xfa1fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV38 [GeForce FX 5950 Ultra] rev 161, Mem @ 0xf8000000/24, 0xe0000000/28
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[1] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[2] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[3] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[4] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[1] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[2] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[3] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[4] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[5] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[6] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[7] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[8] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so

```

Cont...

---

### Post by ART_Adventures on 2006-09-17
```

(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[5] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[6] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[7] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[8] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[5] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[6] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[7] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[8] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[33] 0	0	0xf90003b0 - 0xf90003bb (0xc) IS[B]
	[34] 0	0	0xf90003c0 - 0xf90003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5950 Ultra at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(II) NVIDIA(0): GPU Architecture: 0x30
(II) NVIDIA(0): GPU Implementation: 0x35
(II) NVIDIA(0): GPU Revision: 0xa1
(--) NVIDIA(0): VideoBIOS: 04.35.20.36.00
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce FX 5950 Ultra
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5950 Ultra at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Iiyama (CRT-1)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for CRT-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for CRT-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): Iiyama (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for Iiyama (CRT-1) ---
(--) NVIDIA(0): EDID Version                 : 1.1
(--) NVIDIA(0): Manufacturer                 : IVM
(--) NVIDIA(0): Monitor Name                 : Iiyama
(--) NVIDIA(0): Product ID                   : 17920
(--) NVIDIA(0): 32-bit Serial Number         : 0
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 1999, week 6
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : No
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 360mm x 290mm
(--) NVIDIA(0): Valid HSync Range            : 31 kHz - 79 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 56 Hz - 75 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 135.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 72 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 56 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 72 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 70 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0):   1280 x 1024 @ 75 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   1280 x 1024 @ 72 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for Iiyama (CRT-1) ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for CRT-0:
(II) NVIDIA(0):   HorizSync   : 28.000-49.000 kHz
(II) NVIDIA(0):   VertRefresh : 43.000-72.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
(II) NVIDIA(0): "nvidia-auto-select"   : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x768"             : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768_60"          : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x768"             : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1152x768_55"          : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"             : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_60"          : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600"              :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_72"           :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_60"           :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_56"           :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480"              :  640 x  480 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"           :  640 x  480 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x384"              :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"           :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x384"              :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x384d55"           :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"              :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"           :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"              :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"           :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"           :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"           :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"              :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"           :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for CRT-0: ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1024x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1024, 768]
(II) NVIDIA(0):     CRT-0: "1024x768"
(II) NVIDIA(0):         Size          : 1024 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1024 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1024, 768]
(II) NVIDIA(0): MetaMode "800x600":
(II) NVIDIA(0):     Bounding Box: [0, 0, 800, 600]
(II) NVIDIA(0):     CRT-0: "800x600"
(II) NVIDIA(0):         Size          : 800 x 600
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 800 x 600
(II) NVIDIA(0):         Position      : [0, 0, 800, 600]
(II) NVIDIA(0): MetaMode "640x480":
(II) NVIDIA(0):     Bounding Box: [0, 0, 640, 480]
(II) NVIDIA(0):     CRT-0: "640x480"
(II) NVIDIA(0):         Size          : 640 x 480
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 640 x 480
(II) NVIDIA(0):         Position      : [0, 0, 640, 480]
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[1] 0	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[7] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[8] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[9] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[10] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[11] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[12] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[33] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[35] 0	0	0xf90003b0 - 0xf90003bb (0xc) IS[B]
	[36] 0	0	0xf90003c0 - 0xf90003df (0x20) IS[B]
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): CRT-0 assigned CRTC 0
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/input/mice"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
[/code]

---

### Post by ART_Adventures on 2006-09-17
Actually, I managed to generate the Nvidia error report related to this graphics card problem.

Does anybody know, from this info, why my Nvidia Card might not be working?

Thanks.

---

### Post by ART_Adventures on 2006-09-17
I've been searching around and I noticed on the nvidia website it mentiond that "nv" needed to be disabled in /etc/default/linux-restricted-modules . So I edited the file and changed DISABLED_MODULES="" to DISABLED_MODULES="nv".

I then enable the nvidia driver and now I no longer get the same error where the montior power light goes orange, and also xserver outputs a different log. One of the errors is "(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!".

Can anybody help me. The log follows:

```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux alan-desktop 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 17 18:45:44 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1458,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 8086,2573 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1458,24d2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1458,24d2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1458,24d1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1458,24d2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1458,a002 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0333 card 1043,814e rev a1 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1019 card 1458,1019 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:05:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfa0fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfa100000 - 0xfa1fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV38 [GeForce FX 5950 Ultra] rev 161, Mem @ 0xf8000000/24, 0xe0000000/28
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[1] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[2] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[3] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[4] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[1] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[2] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[3] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[4] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[5] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[6] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[7] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[8] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[5] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[6] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[7] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[8] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa103fff (0x4000) MX[B]
	[5] -1	0	0xfa104000 - 0xfa1047ff (0x800) MX[B]
	[6] -1	0	0xfa000000 - 0xfa01ffff (0x20000) MX[B]
	[7] -1	0	0xfa202000 - 0xfa2020ff (0x100) MX[B]
	[8] -1	0	0xfa201000 - 0xfa2011ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfa200000 - 0xfa2003ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[33] 0	0	0xf90003b0 - 0xf90003bb (0xc) IS[B]
	[34] 0	0	0xf90003c0 - 0xf90003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

---

### Post by tseliot on 2006-09-17
> **ART_Adventures said:**
> I've been searching around and I noticed on the nvidia website it mentiond that "nv" needed to be disabled in /etc/default/linux-restricted-modules . So I edited the file and changed DISABLED_MODULES="" to DISABLED_MODULES="nv"
Putting "nv" in /etc/default/linux-restricted-modules disables the Nvidia module in the restricted modules. But you need that

---

### Post by ART_Adventures on 2006-09-17
Oh, ok. Guess I'd better change it back.

It's just that the person on the nvidia forum gave me this link which refers to ubuntu at the bottom:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

:confused:

Thanks

---

### Post by tseliot on 2006-09-17
> **ART_Adventures said:**
> Oh, ok. Guess I'd better change it back.

It's just that the person on the nvidia forum gave me this link which refers to ubuntu at the bottom:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

:confused:

Thanks

That suggestion works if you use Method 2. But it won't solve your problem.

---

### Post by ART_Adventures on 2006-09-17
Oh I see :( 

Well, thanks for letting me know, otherwise I would have probably been chasing shadows.

I guess I'll need to wait and see if the nvnews forum says anything. Otherwise I'm not sure what else I can do. I really like the idea of Linux and wanted to learn more by using it as my main OS for doing things like browsing the net, writing and so on, and though I can *use* it in 1024x768, it doesn't really feel very comfortable.

Still, you have been very helpful and supportive. Thank you :-)

---

### Post by ART_Adventures on 2006-09-17
If I type

```

uname -r

```

It says: 2.6.15-26-386

Does this have any signifcance for installing the drivers?

I say this because in the logs, I noticed that it says:

Build Operating System:Linux 2.6.15.7 i**686**

...

I don't especially mind if 3D acceleration isn't enabled or whether the card can use all its features. Is there a simple, shortcut way to be able to set my res higher than 1024x768?

Thanks.

---

### Post by tseliot on 2006-09-17
> **ART_Adventures said:**
> I don't especially mind if 3D acceleration isn't enabled or whether the card can use all its features. Is there a simple, shortcut way to be able to set my res higher than 1024x768?

Thanks.
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by ART_Adventures on 2006-09-17
Ok. I finally managed to get 1280x1024. It's in vesa mode because I could find no other mode that would seem to work.

I booted into recovery mode and loaded that program

dpkg-reconfigure xserver-xorg

On following this through I pressed space to select 1280x1024 mode. It worked and I can now select and use that res. I'm sure with the appropriate drivers it'd work faster than it is now, but it doesn't look as though I'll be installing those anytime soon with this card.

Interestingly though, ubuntu draws faster with its vesa driver than Windows XP did before installing the nvidia drivers.

Thanks.

---

### Post by hecato on 2006-09-17
Hi there...
> 
Try to follow this one??? [http://ubuntuforums.org/showpost.php?p=1388643&postcount=14](http://ubuntuforums.org/showpost.php?p=1388643&postcount=14) also downside is another comment [IMG]http://www.ogre3d.org/phpBB2/images/smiles/icon_razz.gif[/IMG]. 
 
 
If you have already the nvidia logo showing when entering graphic mode that is good... if the problem is the black screen, like I see in your log file, there is the resolution of 1280 or some like that, but in your xorg.conf you only have allowed up to 1024... read carefully the comments that I do about valid modes and valid modes validated in xorg.conf [IMG]http://www.ogre3d.org/phpBB2/images/smiles/icon_wink.gif[/IMG].


---

