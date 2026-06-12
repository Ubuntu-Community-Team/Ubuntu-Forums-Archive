---
title: "Poor display qualities, new install, 32&quot; TV as monitor"
date: 2011-04-11
forum: Multimedia Software
---

### Post by EriktheAwful on 2011-04-11
I asked this question in the installation forum and got as far as possible with the advice there. I'm using a 32" Insignia TV as my sole monitor. I'm using the HDMI from the integrated video on my ASUS E35M1-M motherboard. I have it running at 1920x1080. When it boots up the monitor says the BIOS is running at 1080p, but as soon as Ubuntu loads the TV switches to 1080i. When I was setting the computer up the other day it was running 1024x768 and the text looked beautiful, now similar size text is blue/black and scraggly/shadowy looking.

I followed some instructions for xrandr, but ran into problems and the person giving me advice admitted he was too unfamiliar with xrandr to get me any further. Here's as far as I get:
```
erik@erik-System-Product-Name-System-Product-Name:~$ cvt -r 1920 1080 60
# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync
erik@erik-System-Product-Name-System-Product-Name:~$ xrandr --newmode "1920x1080R" 138.50 1920 1968 2000 2080 1080 1083 1088 1111 +hsync -vsync
erik@erik-System-Product-Name-System-Product-Name:~$ xrandr --addmode DFP1 1920x1080R
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

```Where am I going wrong?
Edit: Forgot to show current xrandr output (after inputting the above)
```
erik@erik-System-Product-Name-System-Product-Name:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      30.0*+   30.0  
   1776x1000      30.0  
   1680x1050      30.0     30.0  
   1400x1050      30.0     30.0  
   1600x900       30.0  
   1280x1024      30.0     30.0  
   1440x900       30.0  
   1280x960       30.0  
   1280x768       59.9  
   1280x720       60.0     59.9  
   1024x768       75.0     70.1     60.0  
   1152x648       60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   720x480        30.0     60.0     30.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
  1920x1080R (0x8f)  138.5MHz
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   66.6KHz
        v: height 1080 start 1083 end 1088 total 1111           clock   59.9Hz
```

---

### Post by EriktheAwful on 2011-04-13
Tonight I discovered that black text on a gray background is really hard to read. Does anybody have any advice? What am I doing wrong in xrandr?

---

### Post by wolfen69 on 2011-04-13
What is the built in video card? Ati? Nvidia? Intel?

---

### Post by BicyclerBoy on 2011-04-14
Better check if the Zacate IGP is actually supported at all in the ATI driver ..
The zacate/bulldozer/bobcat stuff is very new ??

Try:
xrandr --newmode "1920x1080_59" 138.50 1920 1968 2000 2080 1080 1083 1088 1111 +hsync -vsync
xrandr --addmode DFP1 1920x1080_59
then
xrandr --output DFP1 --mode 1920x1080 --rate 59.93

Xrandr seems to have an inconsistent method of mode naming & then picking refresh rate ..

Did you post the xorg.conf file previous ??
You may be limiting the freq ranges ..

We never looked into the /var/log/Xorg.0.log either...

---

### Post by 1clue on 2011-04-14
<op> the brutal and tenacious.
<op> mercy sakes, goodness gracious!
Subtle as a chainsaw lacking all the social graces.
You could run but you could not hide!

Sorry, nothing to add to the discussion except an appreciation for the finer musical talents of yesteryear.

---

### Post by BicyclerBoy on 2011-04-14
@ no clue
Is your mother's phone engaged/off the hook again !

The title is a list of keywords that are reasonably descriptive.

Please checkout the community cafe forum.

---

### Post by 1clue on 2011-04-14
Erik the Awful is the name of a song by Ray Stevens.

I strongly suspect the OP appreciated acknowledgment.  That said, I will step out again.

---

### Post by EriktheAwful on 2011-04-14
Yes, 1clue, I do appreciate Ray Stevens.

Wolfen69, it's an ASUS motherboard and AMD Zacate processor with integrated ATI video.

BicyclerBoy, I tried tweaking the xrandr commands as you recommended, but when I got to --addmode I got the same result:
```
erik@erik-System-Product-Name-System-Product-Name:~$ xrandr --addmode DFP1 1920x1080_59
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

```Here's the current xorg.conf:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "30"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```The xorg.0.log is pretty long, what am I looking for?

---

### Post by EriktheAwful on 2011-04-14
In xorg.conf, would changing "TargetRefresh" to "60" be beneficial?

---

### Post by EriktheAwful on 2011-04-18
Any ideas?

---

### Post by EriktheAwful on 2011-04-20
Found my monitor specs on Insignia's site.

[http://insigniaproducts.com/products/televisions/NS-32L450A11.html](http://insigniaproducts.com/products/televisions/NS-32L450A11.html)

Vertical Resolution     1080p
Aspect Ratio     16:9
Screen Refresh Rate     60Hz
Maximum Resolution     1920 x 1080

Edit:
I downloaded the manual and just read a bit about connecting to a computer. It only mentions running as a monitor with the VGA input, but I'm using the HDMI input. Would that make a difference?

---

### Post by EriktheAwful on 2011-04-26
Windowed video files play fine, full-screen is jumpy. SuperTuxRacer doesn't load up, the computer just drops it. I'm thinking it's still a driver issue. Does this sound right?

---

### Post by EriktheAwful on 2011-07-15
It's been a few months and I've decided to try tackling this problem again.

When I boot the computer up and the motherboard turns the monitor on, the monitor says it's running at 1080p. Once Ubuntu's gui loads it switches to 1080i. The manual for the monitor says it's capable of 1080p. The monitor is also capable of 60hz, and that's the recommended setting, but xrandr and System/Preferences/Monitors only allow me 30hz.

How can I force Ubuntu to run my monitor in 1080p at 60hz? As stated, I've tried using xrandr to add a mode, but it won't let me. Am I just going to have to live with it?

Edit: SuperTuxKart runs just fine now. DiabloII/Wine runs good. Smoking Guns ran fine. Warmux runs fine. I can stream The Daily Show fine. Youtube runs great.

---

### Post by EriktheAwful on 2011-12-10
Upgraded to 11.10 this morning. Display is now 1080p! I'm guessing it was a video driver issue. Thanks for the attempts to help.

---

