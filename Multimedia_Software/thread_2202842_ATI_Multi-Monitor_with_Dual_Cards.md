---
title: "ATI Multi-Monitor with Dual Cards"
date: 2014-01-31
forum: Multimedia Software
---

### Post by Mulefire on 2014-01-31
Is there any way to extend a desktop across four monitors using 2 video cards? I have an old ATI 5760 and ATI 5660 in my box, one card is outputting via 2 DVI and 1 DisplayPort whilst the other card is using 1 DVI. I could use 2 DVI on both if required. Both cards are driving identical 1680x1050 monitors in a vertical orientation, so 1680x1050 or 1680x4200 total.

At the moment I have it working well with Windows 8 but I would prefer to run Ubuntu if possible. I've had an ungodly amount of xrandr and xorg scripts from Dual Monitor configs since the days of Ubuntu Hardy, but I haven't round anything that will give me an extended desktop with my current setup. Best I could manage was an extended desktop on 2 monitors and a blank X server screen on the other 2. I forget exactly what combination of settings that was but IIRC it was using eyefinity and no Unity acceleration (due to total screen resolution). With windows I am not using any eyefinity configuration, it is just plain extended desktop settings.

Thanks!

---

### Post by jp734 on 2014-01-31
Yes there is. I am using two ATI cards and 3 monitors and works with no problem

1. You can try using **xrandr**. You will need version 1.4 though. This is the newest version I heard that support dual cards.
2. You can **download driver** from their website or use the open source driver. Install the catalyst and use it to configure your setup. (This is a hit or miss though) I've tried using this and it did not save the settings for me.

So the solution I actually used as my xrandr version is only 1.3:
3. Run "sudo aticonfig --initial" and edit the configuration file created. File it will create will be xorg.conf.new I believe (can't remember, it's been a while)

---

### Post by centras on 2014-03-13
[COLOR=#000000][I]That should sort you out also you have to chainlink both card and put crossfire on that can be done using aticonfig



Section "ServerLayout"[/I][/COLOR]
[COLOR=#000000]*Identifier "aticonfig Layout"*[/COLOR]
[COLOR=#000000]*Screen 0 "aticonfig-Screen[0]-0" 0 0*[/COLOR]
[COLOR=#000000]*Screen "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"*[/COLOR]
[COLOR=#000000]*Screen "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-1"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Module"*[/COLOR]
[COLOR=#000000]*Load "glx"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "ServerFlags"*[/COLOR]
[COLOR=#000000]*Option "Xinerama" "0"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Monitor"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Monitor[0]-0"*[/COLOR]
[COLOR=#000000]*Option "VendorName" "ATI Proprietary Driver"*[/COLOR]
[COLOR=#000000]*Option "ModelName" "Generic Autodetecting Monitor"*[/COLOR]
[COLOR=#000000]*Option "DPMS" "true"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Monitor"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Monitor[0]-1"*[/COLOR]
[COLOR=#000000]*Option "VendorName" "ATI Proprietary Driver"*[/COLOR]
[COLOR=#000000]*Option "ModelName" "Generic Autodetecting Monitor"*[/COLOR]
[COLOR=#000000]*Option "DPMS" "true"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Monitor"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Monitor[1]-0"*[/COLOR]
[COLOR=#000000]*Option "VendorName" "ATI Proprietary Driver"*[/COLOR]
[COLOR=#000000]*Option "ModelName" "Generic Autodetecting Monitor"*[/COLOR]
[COLOR=#000000]*Option "DPMS" "true"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]


[COLOR=#000000]*Section "Device"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Device[0]-0"*[/COLOR]
[COLOR=#000000]*Driver "fglrx"*[/COLOR]
[COLOR=#000000]*BusID "PCI:11:0:0"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Device"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Device[0]-1"*[/COLOR]
[COLOR=#000000]*Driver "fglrx"*[/COLOR]
[COLOR=#000000]*BusID "PCI:11:0:0"*[/COLOR]
[COLOR=#000000]*Screen 1*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Device"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Device[1]-0"*[/COLOR]
[COLOR=#000000]*Driver "fglrx"*[/COLOR]
[COLOR=#000000]*BusID "PCI:12:0:0"*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Screen"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Screen[0]-0"*[/COLOR]
[COLOR=#000000]*Device "aticonfig-Device[0]-0"*[/COLOR]
[COLOR=#000000]*Monitor "aticonfig-Monitor[0]-0"*[/COLOR]
[COLOR=#000000]*DefaultDepth 24*[/COLOR]
[COLOR=#000000]*SubSection "Display"*[/COLOR]
[COLOR=#000000]*Depth 24*[/COLOR]
[COLOR=#000000]*EndSubSection*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Screen"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Screen[0]-1"*[/COLOR]
[COLOR=#000000]*Device "aticonfig-Device[0]-1"*[/COLOR]
[COLOR=#000000]*Monitor "aticonfig-Monitor[0]-1"*[/COLOR]
[COLOR=#000000]*DefaultDepth 24*[/COLOR]
[COLOR=#000000]*SubSection "Display"*[/COLOR]
[COLOR=#000000]*Viewport 0 0*[/COLOR]
[COLOR=#000000]*Depth 24*[/COLOR]
[COLOR=#000000]*EndSubSection*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]

[COLOR=#000000]*Section "Screen"*[/COLOR]
[COLOR=#000000]*Identifier "aticonfig-Screen[1]-0"*[/COLOR]
[COLOR=#000000]*Device "aticonfig-Device[1]-0"*[/COLOR]
[COLOR=#000000]*Monitor "aticonfig-Monitor[1]-0"*[/COLOR]
[COLOR=#000000]*DefaultDepth 24*[/COLOR]
[COLOR=#000000]*SubSection "Display"*[/COLOR]
[COLOR=#000000]*Viewport 0 0*[/COLOR]
[COLOR=#000000]*Depth 24*[/COLOR]
[COLOR=#000000]*EndSubSection*[/COLOR]
[COLOR=#000000]*EndSection*[/COLOR]
[RIGHT][/RIGHT]

---

