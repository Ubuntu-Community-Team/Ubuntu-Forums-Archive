---
title: "Can i have more than one video card running ?"
date: 2009-12-30
forum: Multimedia Software
---

### Post by zonemikel on 2009-12-30
Hello everyone, 
  I'm running 9.04, is there any way i can use the onboard video card as well as my pci-e video card ? I want to be able to have various x sessions going on seperate monitors with different keyboard/mouse, but thats a little down the road. 

The only thing that shows up in lspci is 
02:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)
which is the pci-e video card (geforce 6800). 

Is this possible ? How do i enable the other video card thats onboard. I think its some sort of geforce something. 

thanks !

---

### Post by Fire_Chief on 2009-12-30
Many motherboards will disable onboard video when a graphics card is detected in a PCI-E slot (kind of like an override). Sometimes you can change the BIOS to prevent this behavior (I think).
To use another video card, you would need to put in another PCI-E or PCI card.
Not sure about running separate X sessions though.

---

### Post by zonemikel on 2009-12-30
zomg that was so easy ! All I did was set my thing in the bios to do "onboard->pci-Pci-e" then when i booted up i tried nvidia-settings and it showed my tv still hooked up to "gpu-1" so that is my pci-e card .. "gpu-0" is my onboard video. 

I've wanted to do this for so long ! :P

I told it to make it a seperate "x" screen and it works fine when i roll my mouse offscreen it just goes to the other one, i mean the other screen on gpu-1 

linux rocks ! I hope i can do this on other pc's (meaning i hope their bios has that feature)

thanks !!

---

### Post by zonemikel on 2009-12-30
Ok i figured out how to get the displays working, now how would i go about assigning input devices to each display. I have usb keyboards and mice i want to assign a mouse/keyb pair to each display instead of using all keyb/mice for all screens. 

I know in xorg.conf there is stuff like 
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
```

and looking in my /dev/input folder 
```
michael@michael-desktop:/dev/input$ ls
by-id    event0  event2  event4  event7  mouse0  mouse2
by-path  event1  event3  event5  mice    mouse1
```

anyone know how i could assign them ? I dont see anything in the nvidia-setting utility that does anything with input devices.

---

