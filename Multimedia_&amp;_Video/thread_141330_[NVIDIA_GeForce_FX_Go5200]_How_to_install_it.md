---
title: "[NVIDIA GeForce FX Go5200] How to install it ?"
date: 2006-03-08
forum: Multimedia &amp; Video
---

### Post by patrick295767 on 2006-03-08
Hi, 

I was using the video card as S3 for a while on this pc, then need to do gaming (not for me) ... 
```
sudo dpkg-reconfigure xserver-xorg #I selected the S3
```

   
So, I installed :
```
apt-get -f -y install xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
```
  
Then, ```
dpkg-reconfigure xserver-xorg          # I select NV like Nvidea
```
  
I select NV for Nvidea, right ... 
  
Then, I do :
```
/etc/init.d/gdm restart
```
  
Ok, the gdm restart wihtout any prob and error message   
   
So into my X session now, I type :
   
Then, check with : 
```
fglrxinfo
```
  
And get : 
OPENgl  
MESA 
  
That's not right ... 
Cos I tried with emupen, and nintendo games are laggy ... 

 I could read, that the drivers nvidea are in the repos ...  
What should I do to install it to be working ??
 
Help !

I found this : 
[http://ubuntuforums.org/showthread.php?t=75074&highlight=5200](http://ubuntuforums.org/showthread.php?t=75074&highlight=5200)
So, I'll try it tonight ... (method 1)

Thank you

Greetings, 

Pat"

---

### Post by Maverick88 on 2006-03-08
I have the same graphics card/chip on my laptop.

Here is how you get it to work:

If you want to use the free nvidia driver, you probably need to do nothing.  Ubuntu should set it up for you dueing installation.  There should be a line Driver "nv" in your /etc/X11/xorg.conf file.

If you want to use the proprietary binary nvidia driver, just follow method one in this Guide [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
The driver line should now read Driver "nvidia".

To get the 1440x900 resolution to work with the proprietary nvidia driver, you will need to comment out the HorizSync and VertRefresh lines and add the following modeline to your xorg.conf:

Modeline    	"1440x900" 97.54  1440 1472 1840 1872 900 919 927 946

FYI - Here is my xorg.conf file:

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
# HorizSync 28-72
# VertRefresh 43-60
Modeline    	"1440x900" 97.54  1440 1472 1840 1872 900 919 927 946
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

-------

I hope this helps.

Rob

---

### Post by patrick295767 on 2006-03-08
[QUOTE=Maverick88]I have the same graphics card/chip on my laptop.

Here is how you get it to work:

If you want to use the free nvidia driver, you probably need to do nothing.  Ubuntu should set it up for you dueing installation.  There should be a line Driver "nv" in your /etc/X11/xorg.conf file.

If you want to use the proprietary binary nvidia driver, just follow method one in this Guide [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
The driver line should now read Driver "nvidia".

To get the 1440x900 resolution to work with the proprietary nvidia driver, you will need to comment out the HorizSync and VertRefresh lines and add the following modeline to your xorg.conf:

Modeline    	"1440x900" 97.54  1440 1472 1840 1872 900 919 927 946

FYI - Here is my xorg.conf file:

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
# HorizSync 28-72
# VertRefresh 43-60
Modeline    	"1440x900" 97.54  1440 1472 1840 1872 900 919 927 946
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900"  "1024x768"  "800x600"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

-------

I hope this helps.

Rob[/QUOTE]
  
Thank you Rob for your nice reply !!
  
I 'll try your post tongiht or tomorrow, cos no pc here ....
  
Concerning the installation, Could you try the :
[http://mupen64.emulation64.com/shots.htm](http://mupen64.emulation64.com/shots.htm)
that u can dowload it there : [http://mupen64.emulation64.com/down.htm](http://mupen64.emulation64.com/down.htm)
  (to make it work, just unpack and do ./mupen64 something in the folder) (very easy)
  
Is it laggy for you too ??
or working ??
I am very curious 
  
Let's help each other with this video card & keep in contact, Rob !

Greetings from Cloudy Belgium,
 
Patrick

---

### Post by Maverick88 on 2006-03-08
Thanks for the link to the game.  I will give it a try.  But as you know the NVIDIA GeForce FX Go5200 is not a great graphics card.

Another way to measure the performance of any graphics card is to run glxgears.  Open up a terminal windows and execute the following command "glxgears -printfps"

I get around 1290 fps on this Toshiba laptop.

Please note that you may not need to add the modeline line to your xorg.conf file.  It depends on the capabilities of your monitor.  I found that the 1440x900 resolution was not being detected automatically so I needed to add the line.  

If you really have questions about the nvidia driver, the best place to post questions is the [www.nvnews.net](www.nvnews.net) forums.  That is where I found about about the modeline that I needed to add.

See [http://www.nvnews.net/vbulletin/showthread.php?t=65828](http://www.nvnews.net/vbulletin/showthread.php?t=65828)

Cheers
Rob - Sunny West Palm Beach, FL

---

### Post by Maverick88 on 2006-03-08
Patrick,

I forget top mention one thing.  If you use the proprietary binary nvidia driver, you will also need to comment out the the following modules in your xorg.cong file:

GLcore
dri

I posted an earlier version of my xorg.conf file by mistake.

My xorg.cong file actually reads:

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
#Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
# HorizSync 28-72
# VertRefresh 43-60
Modeline "1440x900" 97.54 1440 1472 1840 1872 900 919 927 946
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1024x768" "800x600"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

----------------------

If you use the Ubuntu non-proprietary driver, you should keep these two modules.  (i.e.  do not comment them out).

Rob

---

### Post by patrick295767 on 2006-03-09
Thanks a lot maverick88 for your help & information,

I think I'll have time this weekend to try to make these installation...
  
If you'd need ROM's of the N64 emu, let me know... 

 Greetings, 

Pat'

---

### Post by patrick295767 on 2006-03-09
I replied your email ... 

You got it running the mario then with emulator ? 

Greetz

---

