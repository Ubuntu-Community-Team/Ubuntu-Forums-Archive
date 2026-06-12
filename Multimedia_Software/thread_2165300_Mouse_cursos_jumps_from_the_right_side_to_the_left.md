---
title: "Mouse cursos jumps from the right side to the left when I switch GPU through Catalyst"
date: 2013-08-04
forum: Multimedia Software
---

### Post by charles2 on 2013-08-04
Hello, I am new to Ubuntu, I've installed it recently and there is a problem with my hardware. Ubuntu version is 12.04 LTS (64 bit) and computer is acer aspire v3-551g-10466G75Makk laptop.
My laptop has hybrid graphics (AMD Radeon HD 7660G + HD 7670M). When I launched Ubuntu fot the first time laptop was working very loud and its body was hot. I installed proprietary driver from "Additional Drivers", "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" (there is an experimental beta driver, but problem is the same for that one). Noise and heat disappeared and I wanted to find the instrument through which I could switch my graphics cards. In Windows I do this with Catalyst Control Center. But Catalyst Control Center in Ubuntu didn't see my second discrete graphics card, HD 7670M. On the Internet I found solution - to type in Terminal:
sudo aticonfig --initial --adapter=all
That made Catalyst see all graphics cards and I could switch between them. But it brings another problem - when I moved cursor to the right cursor immediately jumped to the left. Cursor didn't jump if I move it to the left. I wanted to disable it because it was very annoying. I thought it was somehow connected with several displays so I went to the Display Manager in Catalyst Control Center. The program asked me whether I wanted to apply changes (I didn't change anything). I applied, rebooted. Cursor was working right (no jumps), but Catalyst stopped to see my second graphics card. After shutting down Ubuntu didn't boot.
Right now I have almost clear system only wih updates from default repositories and proprietary driver for ATI graphics, I didn't change anything yet. I hope someone can write something that could solve the problem.

Some informtation that could be useful:

lspci | grep VGA:

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9900
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]

fglrxinfo:

OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7660G
OpenGL version string: 4.2.11903 Compatibility Profile Context

By the way, brightness of the screen can be changed only after reboot. Honestly, I haven't searched anything about this problem yet because I want to fix previous problem first, and I mentioned it only because it could be connected somehow with previous problem. And another thing: in "Additional Drivers" it's always written that "this driver is activated but not currently in use".

P.S. Sorry if something isn't clear after my explanation. English is not my native language.

---

### Post by charles2 on 2013-08-05
New information. I noticed that cursor jumps from the right side to the left side only when I switch to power-saving GPU (7660G). There's no such problem with high-performance GPU (7670M).

---

### Post by charles2 on 2013-08-06
Well, maybe contents of my xorg.conf file could help to find solution? I discovered that there're two 'screen' and 'monitor' sections, although it's laptop and there's only one monitor. I'm sure it's somehow connected with several displays, although Display Manager in Catalyst doesn't see the second non-existing monitor. I attached two files: after executing command 'aticonfig --initial --adapters=all' and after apllying changes in Display Manager of Catalyst Control Center (As I said, I didn't change anything, so I have no idea what these changes are). Maybe I should rewrite something in xorg.conf? I tried to edit the first file intuitively, replaced
"aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
in
ServerLayout section with
"aticonfig-Screen[1]-0" 0 0
And after reboot, when I move cursor to the right side, it disappeared. So at least editing the file does change something :)
By the way, when I'm on high-performance GPU, fglrxinfo shows only one screen, but when I'm on power-saving GPU (when problem with cursor appears) there're two screens.

xorg.conf after executing command:
```

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:0:1:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection


```

xorg.conf after applying changes in Display Manager:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:0:1:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
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

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by charles2 on 2013-08-08
Anybody?..

---

### Post by Boab1993 on 2013-08-08
Hi charles2, 

As far as my knowledge extends, hybrid graphics is  when the use of both your graphics processors(HD and discrete) are used  in conjunction with each other.

Since your discrete processor is  what is essentially an 'add-on' processor, its highly possible it  simpley cant take the load of being run on its own, hence having drawing  problems with your mouse, i say this because your using a 64bit OS,  hence higher graphics usage.

Advice would be to research the  capabilites of your discrete processor, and research the graphics  requirements for your 64bit OS. If they dont match up in a bad way,  theres your problem.

Other issues can simpley be the drivers in linux dont fully support that processor.

Hope this helps

---

### Post by nickthecook on 2013-10-16
Hi charles2,

I had the same issue with my mouse pointer. If it hit the right edge of the screen it would jump to the left of the screen.

I have a PC with two Radeon HD 7850s. I only have one monitor plugged in, but my Xorg.conf file had two screens, two monitors, and two devices set up, similar to yours. Based on your posts, I decided to try commenting out all references to adapter 1, screen 1, monitor 1, while leaving adapter 0, screen 0, monitor 0 in place. I also commented out the line you mention from ServerLayout instead of just removing the adapter 1 reference as you did.

This worked. My pointer is now still visible when it hits the right edge, and it doesn't jump back to the left.

I'm not sure if my solution would work for you, but it might be worth a shot.

nickthecook

---

