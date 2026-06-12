---
title: "Error when after installing nVidia 8500GT on Ubuntu6.06"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by mauii on 2007-11-08
Hi all,

I need your help, error occured when when I run "sudo startx" after successfully installing nVidia driver by envy legacy for Ubuntu6.06.1 on Gateway 5628 with 8500GT.

[What I did] #################################################
 wget [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu11_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu11_all.deb)
 sudo dpkg -i envy_0.9.8-0ubuntu11_all.deb 
 sudo apt-get install build-essential
 sudo apt-get -f install
 sudo envy
 sudo envy -t

[Error] ####################################################
$ startx

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux sqa24-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  8 11:23:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
xauth:  error in locking authority file /home/sqa24/.Xauthority

[/etc/X11/xorg.conf] #########################################
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VA903 SERIES"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Nvidia Corporation 80G"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia Corporation 80G"
    Monitor        "VA903 SERIES"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Thanks for any clue to resolve this issue.

Regards,
Gary

---

### Post by carlinuxlearner on 2007-11-09
You need to have a "BusID" in the "Device" section of your /etc/X11/xorg.conf
EXAMPLE
"
Section "Device"
    Identifier     "Nvidia Geforce4 MX 420"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:11:0"
    Screen          0
EndSection
"
Usually if you just put in any BusID number (such as "PCI:1:11:0") when you try startx, it will give you an error and suggest the correct BusID number, so just go correct it to what it suggest, and it should work!

C@RL

::EDIT 
I just realized that this is probably NOT going to fix it. Sorry.

Envy evidential didn't not install it correctly (some times this happens).
You could try installing it manualy. Here's a "HOW TO" I wrote.


HOW TO: install your Nvidia driver in Ubuntu 7.10

(Please MAKE SURE with ANY commands (or path names) that you capitalized what I capitalize!!!! This is VERY important!)


2.1
Open up a terminal window (Applications>>Accessories>>Terminal) type this in "sudo apt-get install build-essential"


2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here 
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run) 
(if that link is old go to this page to get driver) 
[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) 
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE 

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

end of example)

2.3
IF YOUR GRAPHICS CARD NAME IS NOT ON THAT LIST look and see if it's on this one
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If it was in the "The 1.0-96xx driver supports the following set of GPU" section, then download this driver to your Desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run)
(If that link is old then go here)
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html](http://www.nvidia.com/object/linux_display_x86_96.43.01.html)
(If that link is old go here and select the driver that starts with "96")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

If you graphics card name was in the "The 1.0-71xx driver supports the following set of GPUs" section,
then download this driver to your Desktop.
[http://us.download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run)
(If that link is old go here)
[http://www.nvidia.com/object/linux_display_x86_71.86.01.html](http://www.nvidia.com/object/linux_display_x86_71.86.01.html)
(If that link is old go here and select the driver that starts with "71")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


2.4
Print out this page!

2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name) 
click the TAB button on your key board twice, and it should fill out the rest of the name for you, 
THEN hit enter.

2.7
The installer will ask you some question (don't worry if it says your in "runlevel 1" it doesn't matter) just make sure you answer all the questions so that it will continue the installation process.

2.8
Once the installer is done restart your computer by pressing CTRL+ALT+DELETE, boot up normally. And your Nvidia driver should be installed!

TROUBLE SHOOTING

When you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver       "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY helpfull please write down, or copy any you get)

C@RL

---

