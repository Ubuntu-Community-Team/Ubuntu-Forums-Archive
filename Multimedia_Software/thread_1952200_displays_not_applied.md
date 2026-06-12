---
title: "displays not applied"
date: 2012-04-03
forum: Multimedia Software
---

### Post by banksiaman on 2012-04-03
I have attached a screenshot of what I get when I try to go out of mirror displays it says
"required virtual size does nor fit availablesize:requested=(2048,768 ) min = (320,200),max= (1024,1024)
my size each monitor is 1024 * 768(4:3)
I think its treating it as if I want 1 Big monitor not 2 monitors.I have put some details below
):P
 
 
I have a HD 4650 card I used to install drivers [http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu](http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu)
 
 
 
glxinfo | grep -i vendor 
server glx vendor string: ATI
client glx vendor string: ATI
OpenGL vendor string: Advanced Micro Devices, Inc
 
egrep -i "connected|card detect| primary dev" /var/log/Xorg.0.log
[ 21.568] (II) fglrx(0): PCIE card detected
[ 24.733] (II) fglrx(0): Connected Display0: CRT1
[ 24.734] (II) fglrx(0): Connected Display1: CRT2
[ 24.831] (II) fglrx(0): Output DFP1 disconnected
[ 24.831] (II) fglrx(0): Output DFP2 disconnected
[ 24.831] (II) fglrx(0): Output CRT1 connected
[ 24.831] (II) fglrx(0): Output CRT2 connected
[ 24.831] (II) fglrx(0): Adapter ATI Radeon HD 4600 Series has 2 configurable heads and 2 displays connected.
 
.

---

### Post by banksiaman on 2012-04-04
I believe I have to add a line under
SubSection "Display"
[COLOR=red]Virtual 2048,768[/COLOR] 
can anyone tell me if I am right thanks
 
 
MY xorg.conf
 
Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection
Section "Module"
Load "glx"
EndSection
Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection
Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection
Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
 
and ran xrandr
xrandrhome1@home1-GS293AA-ABG-m8175a:~$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024 
DFP1 disconnected (normal left inverted right x axis y axis) 
DFP2 disconnected (normal left inverted right x axis y axis) 
CRT1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 54mm x 486mm 1024x768 75.0*+ 70.1 60.0 800x600 72.2 75.0 70.0 60.3 56.2 720x480 60.0 640x480 75.0 72.8 60.0 
CRT2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm 1024x768 60.0*+ 75.0 70.1 800x600 72.2 75.0 70.0 60.3 56.2 720x480 60.0 640x480 75.0 72.8 60.0

---

### Post by banksiaman on 2012-04-04
I solved my problem I was clicking the System Menu selecting displays and getting the problems above.
I went to dash home typed "a" in search up come "AMD catalyst control center (Administrative) the rest is easy in fact anything is easy if you know how.
I am a virtual novice but it does not take much googling to find that even the experienced
find it hard to start in Linux.I can see why many give up
Any how hope my solution may help someone :p

---

