---
title: "nvidia card and TV output"
date: 2009-08-16
forum: Multimedia Software
---

### Post by philippe75 on 2009-08-16
Hi everybody, I am a very new user of Ubuntu (2 days), everything looks to work well, except on the graphics level.
Although it looks like that my questions have been more or less already covered by browsing the forum, it is never clear to me.

So here I go: I use a sony laptop, with a nvidia geforce 6400 graphic card, and the laptop screen is almost broken (meaning that it is impossible to read it, but sometimes I can see some shapes, so I can click on some button if I look at a screen snapshot)  - but that's ok, because my TV is connected via VGA cable and is well recognized.

Here is my problem: in system > administration > drivers, I see that a version of the nvdia card is available (driver NVIDIA version 180), but as soon I install it, the TV doesn't work anymore: the boot starts well, but on the login screen it looks like the TV output is cut. But on the broken screen, everything looks fine, so I guess the driver works fine for the laptop screen - but not for the TV!

To be honest I have trouble to identify my current config, I tried several things, like xrandr, I tried to edit xorg.conf, but it looks empty... it is clear to me that I don't use the graphic card at its maximum, even though it works well (I am writing this message with ubuntu, I could watch some videos this morning etc)

I really have no clue for correcting this. My ultimate goal is to make the TV output the main output, suppress the sony screen, and that's it. With windows (already installed on the PC) I could do that after some efforts (now nothing is displayed on the laptop screen), and I am pretty sure this is possible aso with ubuntu.

Thanks a lot for any help, and sorry if this has been asked over and over

Philippe

---

### Post by hellomoto on 2009-08-17
ok so sounds like to me before you installed the nvidia driver u were running on low graphics mode (which was being displayed by ur TV and not by ur laptop)

when u installed the new nvidia driver ur laptop screen works but ur TV doesn't?

if that is the case you will most likly need to edit ur xorg.conf file to enable video out on ur graphics card whilst using the superior driver. 

please post ur xorg.conf file. go to a terminal and type: 

```
 gedit /etc/X11/xorg.conf 
```

and copy and paste what appears in gedit.

---

### Post by philippe75 on 2009-08-17
OK, I will do that as soon as I get back home.
I did not know where to look for log messages actually... now, this will help I am pretty sure!

Thanks

Phil

---

### Post by hellomoto on 2009-08-17
ok, off to work now but will gladly have a look at ur xorg file when im next free. also if u go to system>admin>hardware drivers 

and post what (if any) nvidia driver you are using-- check that it says enabled too.

---

### Post by philippe75 on 2009-08-17
ok, here is what the xorg file looks like, just after installing the nvidia driver (version 180)

[B]Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection[/B]

after a reboot, the TV screen (by the way, it is an akai hd ready - don't know if this important or not...) has been again cut of, so I restarted again and chose the "fix video problem" in the safe mode start up.

now the xorg.conf now looks like this:

[B]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/B]

did i miss something while installing the driver? maybe a special command or something else?

anyway, I have several things to check now - how this file works (or should work in my case) etc...

thanks a lot, again

philippe

---

### Post by hellomoto on 2009-08-18
when u enter safe graphics mode the xorg file will be diffrent as ubuntu has loaded a different (basic) graphics driver. 

So what are you using to connect your laptop to you TV? eg: a VGA cable, DVI cable or S-video cable. Depending how you connect your laptop to your TV will dictate how you need to change your xorg file?

Also have u tried pressing F5 whilst the laptop is plugged into the TV?

And have you tried going to system>prefs>display and clicking on detect monitors?

Also your Xorg file doesn't currently have  "Boardname" and "BUSID" options in the Device section (this tells xorg what and wear your graphics card is) 

You may find a useful tool a GUI xorg editor available [here.]("http://sourceforge.net/projects/xorg-edit/")

---

### Post by philippe75 on 2009-08-18
hello and thanks for the answer!

I am using a vga cable to connect the laptop to the TV.
I tried the F5 key => this does nothing for me right now.

then, I went to pref > display, here I am warned that I don't use the right driver for the card (I mean I use a proprietary driver). the menu displayed here is pretty much all about nvidia - logo and stuff. some of the options (not so many anyway) does not really look interesting (like 'enable tooltips'), but one looked interesting (well complicated); this is 'include display name in the config file'
so I tried that, played a little bit with firefox to write this message, and then to check few things in the display menu, I came back there: at this point I was asked to run nvidia-xconfig, which i did

here is the output...

[B]Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/B]          

lots of warnings... I am going to try to reboot to see if something has changed

(by the way at this point I have automatically changed of driver, confirmed in the driver menu, the xorg file is like this:

[B]Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection[/B]     

)

---

### Post by philippe75 on 2009-08-18
nope... this hasn't worked for some reason........

okay, I will rollback and play with your little tool to see if it helps!!

---

### Post by philippe75 on 2009-08-18
hum, as I see, there are lots of options here - and I am surprised for example that I never need to specify a screen resolution for the TV...
so I will have to study that... but I should go to work now.

anyway thanks again for the help, this is very appreciated

---

### Post by philippe75 on 2009-08-19
Sorry for being so thick, but I have spent hours trying to solve my little issue, and nothing worked...

Everytime I try to use the proposed linux nvidia driver, or run nvidia-xconfig, or everything else read in the forum, it always ends the same way: when the login screen appears, the TV becomes blue, 'no signal'.
I have no idea what is going on.

Also, my tv seems not to be recognized - functions like detect monitors simply don't work, is this normal?
The tool proposed by hellomoto did not really help on that: the tv is always unknown.

Anyway I am not sure that I will be able to have better results with the linux driver than with the proprietary driver since the actual resolution is the one I get with windows (who does recongnize the TV).

But I have spent so many hours on that particular issue that I'd like to close it... any help much appreciated!

Philippe

---

### Post by philippe75 on 2009-11-02
This thread is pretty old I know.

But recently (!!) a friend of mine stopped at my place and resolved my little issue, so it may interest someone...

This has been done in two very little steps: first, he changed the relevant parts of the xorg.conf file like this

[B]Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
    Option        "TwinView"
EndSection[/B]

So this is very similar to the "default" xorg.conf generated after activating the nvidia driver the usual way, he just added the option TwinView which made the trick: after a reboot, the TV screen was still up.

This was not exactly what I wanted, the laptop screen and the TV were on, and I just wanted the TV screen as principal output, nothing on the laptop.

But it was easily done with the nvidia Gui (in system / preference / display), I could configure everything as I wanted, and now the xorg.conf is far longer and more complex, but everything works well!

For many this resolution must look obvious, but if it can help... who knows...

Thanks again to all the people who helped me!!

[B]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection[/B]

---

