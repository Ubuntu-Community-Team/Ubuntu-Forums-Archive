---
title: "Major graphics problem....."
date: 2009-02-10
forum: Multimedia Software
---

### Post by _Orion_ on 2009-02-10
I am brand new to linux, and am running Ubuntu 8.10 on an old tower cobbled together out of spare parts. It took a while, but I finally got Ubuntu installed and running smoothly. I went to update my drivers to the Nvidia X 173 version so I could have 3d acceleration and upon reboot found that the login screen encounters 1 of 4 kinds of errors every time i reboot: 
1)Flashes regular ubuntu login screen sporadically, unable to interact in any way
2) Extremely distorted and snowy version of #1
3) White background with nothing except the text input bar, unable to interact
4) Black screen

The graphics card is a nVidia geForce FX 5200 (128 mb)

I have been looking for a solution all week for this. Please help me.....

---

### Post by NT4usB on 2009-02-10
Install envyng from the repositories and try that?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Suggest first use the option to completely remove nvidia drivers, then install.

If your screen is too jacked to even use it, Ctrl+Alt+F1 and log in to a terminal.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart x```
 sudo /etc/init.d/gdm restart
```
Or, restart the computer```
 sudo shutdown now -r
```

If that doesn't work run it again but leave out the -phigh. Step through all the defaults until it gets to the video and select the vesa driver. Then you should get a screen back. Try envy.

(Advanced way. If you're comfortable with the command line and vi: 
cd to /etc/X11/ and edit xorg.conf using a non graphical editor like vi.
If the nvidia driver is listed, change to vesa. Otherwise, add the driver line.)

---

### Post by _Orion_ on 2009-02-10
I've already tried something similar to this....Is there any way I can get my computer to work while keeping the graphics drivers?  I know how to uninstall/deactivate them, but I was planning on using this computer for 3d applications....

---

### Post by NT4usB on 2009-02-11
The goal is **not** to uninstall/deactivate them. The goal is to make them work.
envyng does a better job, imo, than the restricted drivers mangler.
Adding info to the anemic default xorg.conf will make it work. The bitch of it is, Ubuntu now has the failsafe X which replaces your xorg if things don't go well.
To start, add refresh info to the monitor section. You have to look up the specs on your monitor. ```
Section "Monitor"
 
    Identifier     "whatever your monitor's called"
    HorizSync       xx.0 - xx.0
    VertRefresh     xx.0 - xx.0
EndSection
```

It's a battle to keep failsafe from replacing xorg.conf.
I work in tty1 (Ctrl+Alt+F1) while constantly switching to the xscreen (...F7) to kill the stupid x is broken popup.
Then stop gdm again.
Then change xorg.conf again.
Then start gdm.
repeat until the stupid popup doesn't popup.

---

### Post by _Orion_ on 2009-02-11
Keeping in mind that I am a linux noob here and don't have too much knowledge about how the system works, how do I do that?  Do I just enter it in the Terminal? Or do I actually have to find a source code file?

---

### Post by NT4usB on 2009-02-12
Did you run dpkg-reconfigure... like I posted above?
Do you have a screen at all?
Can you run nvidia-settings?
Did you find the specs of your monitor. You're looking for the horizontal and vertical refresh rates. Usually described:
fh xx.x-xx.x fv xx.x-xx.x

---

### Post by _Orion_ on 2009-02-12
Yes, I did run dpkg-reconfigure
Yes, I have a working screen (only when running in low graphics mode)
Yes, I can run nVidia X server settings
No, I don't know how to find the monitor specs
Yes, my computer is still screwed up

---

### Post by _Orion_ on 2009-02-13
All I want to know is where you type in above commands to get the monitor info.....anyone help me on this?

---

### Post by NT4usB on 2009-02-14
> **_Orion_ said:**
> All I want to know is where you type in above commands to get the monitor info.....anyone help me on this?

What is the brand and model of the monitor?

---

### Post by _Orion_ on 2009-02-14
its a Dell Ultrasharp Model No. 1800FP
When I use the "set screen resolution" tool it doesn't detect it or the refresh rate.

---

### Post by _Orion_ on 2009-02-15
bump, anyone able to shed some light on the situation?

---

### Post by NT4usB on 2009-02-15
Ok, here's your [monitor]("http://support.dell.com/support/edocs/monitors/1800FP/English/specs.htm").
Couple choices.
The specs are different for early production and late production. How new is yours?
Are you connecting the D-sub or DVI connector?

---

### Post by _Orion_ on 2009-02-15
-As far as I know, this monitor was made in 2003
-I am using the D-Sub connection....


-You would probably know better than I do, but I'm not so sure that this has to do with the monitor....when I start up the computer with ANY of the nVidia drivers for linux (I've tried them all) the login screen will either vanish and just leave the blank white text bar, or it will look normal, except that you cannot enter text or use the "options" button.  However, I can move the mouse onscreen, although the keyboard gets no response.  This just doesn't really seem connected to the monitor type.

---

### Post by NT4usB on 2009-02-16
It has to do with how the video driver communicates with the monitor. 
We have to configure it so it speaks a language the monitor understands.
That would be HorizSync, VertRefresh, and resolution.
Post the output of:```
cat /etc/X11/xorg.conf
```

---

### Post by _Orion_ on 2009-02-17
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"vesa"
EndSection

---

### Post by NT4usB on 2009-02-17
So now it gets complicated if you're not familar with how to use a non graphical editor. 
I use vi and it's not the most intuitive editor. 
Others talk about gedit though I've never tried it. 
iirc, you can edit xorg.conf running nvidia-settings as root. There's an option to save to xorg.conf and there an option to preview. You can add the changes and save it.

Pick your poison, google to learn how to use it, print a cheat sheet for commands (or have a second pc available to read how to run the editor) and lets add some things to xorg.conf.
First off, back up the existing xorg.conf. We're going to do this after every change since the 'failsafe' x will rename yours and replace it if yours doesn't work. 

cd to /etc/X11/
```
sudo cp xorg.conf bkup.xorg.conf
```

Remember to use Tab autocomplete to complete filenames. If you type: cp xor(Tab) it will autocomplete to xorg.conf. Saves a lot of typing (and miss typing)

I see you're still using the vesa driver Section "Device".
First off, lets change that to nvidia and see what happens.
Ctrl+Alt+Backspace will restart the xserver after you make the changes.

ed: looks like you said you already tried this in post #13.
If so, we'll have to wait until I get home tonight to type some more configuration things to try.

---

### Post by _Orion_ on 2009-02-17
Ok, so I tried that (editing the driver) and it still doesnt work....the only reason it said "vesa" there was because at the time of the post I didn't have the driver installed at the time....I added the driver and it switched to "nVidia"....still didn't work.

---

### Post by NT4usB on 2009-02-17
Make these changes to your xorg.conf and restart the xserver.
Also, try the same but use Driver "nv" instead of nvidia.
nv is the free included driver and nvidia is the restricted one.
```

Section "Monitor"
Identifier "Configured Monitor"
[COLOR="DeepSkyBlue"]    HorizSync       31.0 - 80.0
    VertRefresh     55.0 - 85.0[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[COLOR="DeepSkyBlue"]DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection[/COLOR]
EndSection

Section "Module"
Load "dri"
Load "GLcore"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
Driver "[COLOR="DeepSkyBlue"]nvidia[/COLOR]"
EndSection

```

Post the output of:```
cat /var/log/Xorg.0.log
```

When you post these big ol' long pastes, put the word code enclosed in square brackets "["code"]" before and /code enclosed in square brackets "["/code"]" after it. (without all the quotes)
This will put it in a scrollable window and not fill the page with, well... code.

---

### Post by NT4usB on 2009-02-17
> **_Orion_ said:**
> Ok, so I tried that (editing the driver) and it still doesnt work....the only reason it said "vesa" there was because at the time of the post I didn't have the driver installed at the time....I added the driver and it switched to "nVidia"....still didn't work.

All of the (non restricted) drivers are installed by default. Shouldn't have to add or remove any drivers.

Changing the 'Driver' "...." section in xorg.conf calls whichever driver you want. The rest just sit around doing nothing.
I'm a little concerned you don't have the drivers installed that we need. Xorg.0.log should tell us that.

---

### Post by _Orion_ on 2009-02-19
```
 
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device DELL DELL USB Keyboard
(**) DELL DELL USB Keyboard: always reports core events
(**) DELL DELL USB Keyboard: Device: "/dev/input/event1"
(II) DELL DELL USB Keyboard: Found keys
(II) DELL DELL USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) DELL DELL USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) DELL DELL USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) DELL DELL USB Keyboard: xkb_layout: "us"
AUDIT: Wed Feb 18 15:20:09 2009: 5360 X: client 4 rejected from local host ( uid=0 gid=0 pid=5538 )
AUDIT: Wed Feb 18 15:21:47 2009: 5360 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5604 )
AUDIT: Wed Feb 18 15:21:47 2009: 5360 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5605 )
AUDIT: Wed Feb 18 15:21:47 2009: 5360 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5606 )
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) Open ACPI successful (/var/run/acpid.socket)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) DELL DELL USB Keyboard: Device reopened after 10 attempts.
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device DELL DELL USB Keyboard
(II) DELL DELL USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device DELL DELL USB Keyboard
(**) DELL DELL USB Keyboard: always reports core events
(**) DELL DELL USB Keyboard: Device: "/dev/input/event1"
(II) DELL DELL USB Keyboard: Found keys
(II) DELL DELL USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) DELL DELL USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) DELL DELL USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) DELL DELL USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) Open ACPI successful (/var/run/acpid.socket)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Optical USB Mouse"
(EE) config/hal: NewInputDeviceRequest failed
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) DELL DELL USB Keyboard: Device reopened after 10 attempts.
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) DELL DELL USB Keyboard: Device reopened after 10 attempts.
(II) Logitech Optical USB Mouse: Device reopened after 10 attempts.
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(EE) DELL DELL USB Keyboard: Read error: No such device
(II) config/hal: removing device DELL DELL USB Keyboard
(II) DELL DELL USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device DELL DELL USB Keyboard
(**) DELL DELL USB Keyboard: always reports core events
(**) DELL DELL USB Keyboard: Device: "/dev/input/event1"
(II) DELL DELL USB Keyboard: Found keys
(II) DELL DELL USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) DELL DELL USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) DELL DELL USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) DELL DELL USB Keyboard: xkb_layout: "us"
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech Optical USB Mouse: Read error: No such device
(II) config/hal: removing device Logitech Optical USB Mouse
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

Ok, there's the Xorg.0.log file output...or most of it anyways. Looking at this, I realized that there's something wrong with my mouse....I'll have to go get a new one.

---

