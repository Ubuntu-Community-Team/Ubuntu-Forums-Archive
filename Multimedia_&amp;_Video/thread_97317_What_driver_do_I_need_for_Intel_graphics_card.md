---
title: "What driver do I need for Intel graphics card?"
date: 2005-11-30
forum: Multimedia &amp; Video
---

### Post by nalmeth on 2005-11-30
I have a Gigabyte Motherboard, with built in Intel Graphics card, and Intel pentium 4 processor with hyperthreading. Here are model names:
Motherboard: GA-81915ME-GL
Graphics: Intel 82915G express (915gl series)

NVIDIA and ATI drivers don't work.
this page has possibly working graphics drivers for linux:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1764&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1764&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)
The only installation types available are a tarball and an rpm. I hesitate to try them because there is no uninstallation script. (Can I use alien to install rpm?)

Is there any work around I can use to install drivers that are compatible with my graphics card? Do I need to buy a new graphics card to have 3D acceleration? If you can't answer these questions, do you know any persons or places that can fill me in?

Thanks for any suggestion
nalmeth

---

### Post by taurus on 2005-11-30
You can use alien to convert rpm to deb and install it as a normal deb package which means you can remove it later if you want...

---

### Post by nalmeth on 2005-12-01
thanks for reply taurus
I wasn't sure how that worked, I assumed alien was just an rpm installer or something.
Anyway, I've learned that the driver on the intel website I put on my previous post is only supported on i386 architecture, and I have an AMD64 system. 
I already have a 32-bit chroot setup.
I've also learned that this "driver" is actually an accelerated x-server, not just a driver.
What I'm now wondering is if I can install this x-server on my 32-bit chroot environment, and maybe create some kind of boot menu to change between xservers. Is this a wholly impractical idea? Otherwise I'm screwed into paying for a NVIDIA graphics card.. which would be a bummer. :(
If anybody can respond to this, please do. PLEASE and thank you as always.

P.S.
I'M STILL TAKING SUGGESTIONS TO WORK AROUNDS TO INSTALLING A MAGICAL WONDER DRIVER IN MY AMD64-bit ENVIRONMENT. :D

---

### Post by az on 2005-12-01
Try this:
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

See this related howto:

[http://ubuntuforums.org/showthread.php?t=75393&highlight=savage](http://ubuntuforums.org/showthread.php?t=75393&highlight=savage)

---

### Post by tokyovigilante on 2005-12-01
Hi nalmeth,

Ubuntu includes the 3D accelerated driver you need, it's called i810. Look [here]("http://www.die.net/doc/linux/man/man4/i810.4.html").

In a console, try
```
cat /etc/X11/xorg.conf | grep i810
```

and post the output if it's not blank.

The reason the ATI/Nvidia drivers didn't work is because they don't make your hardware, intel does. I suggest you stay away from the Intel proprietary drivers, as they are old (2004), and the open-source i810 drivers will be regularly updated and support 3D acceleration if configured correctly.

If the above command doesn't return something along the lines of 
```
Driver "i810"
```

Then try
```
sudo dpkg-reconfigure xserver-xorg
```

and after entering your password, Choose the "Automatically detect your video card" option, and make sure it chooses i810. Then accept the defaults for the remaining questions, excluding the part where it asks you about video modules to load. Make sure "dri", "glx" and "GLCore" are enabled, as these provide 3D acceleration. Then continue on through, and once it finishes, hit <Ctrl>-<Alt>-<Backspace> to restart the X server. If it doesn't restart, type ```
startx
```

to force it to reload. Hope this helps, post again if you get any errors.

P.S. What 3D apps are you trying to run? The Intel integrated stuff is OK for desktop work and older OpenGL games, but it will struggle a bit with Doom 3 for example. You may want to pick up a dedicated 3D accelerator. NVIDIA currently has the best Linux support. Also, the integrated graphics take up some of your system RAM, and you'll get this back if you get a dedicated card.

---

### Post by nalmeth on 2005-12-02
thanks guys

This is exactly the type of information I'm looking for.
Right now I'm running dsl because I got myself into xserver trouble. I read somewhere about the dpkg-reconfigure xserver, and went through it all, but after reconfiguring, my monitor goes black and power saving light blinks. I've had this problem a lot before with other computers because a have a pretty crappy monitor... :rolleyes: 
Anyway, obviously it made a difference. Heres what I did.
I reconfigured xserver, and the default selection (out of about 20 others) was indeed i810, but at the time I wasn't convinced it was right.. Anyway, I went through basically with all defaults, and I came out locked out of the xserver. This was before I read this post, and I'm not positive on what was selected for video modules, so I will go back 'under' and see if that might be the problem. I followed the link, and considering it says it also supports i915G it looks very promising. 
I can still log in via terminal cnrt-alt--(f1-f6), but f7, my xserver does not have a display.
When I startx I'm told no properly configured xservers are available, so its something in the config I have to change.

I will repost after I try

thanks again for ideas

---

### Post by nalmeth on 2005-12-02
hey

got xserver going again, didn't even change anything during reconfigure, but x loaded ok.

cat /etc/X11/xorg.conf | grep i810

gets me

Driver "i810"

which it is supposed to. "Dri", "glx" and "GLCore" are enabled in video modules (snapshot of this step attached).

But no 3Dapps of any kind are running. So far I am only playing around with OpenGL 3dapps, like 3ddesktop, billiard-gl, etc. Nothing too extreme. 3ddesktop tells me it cannot find server, and no other app will even open.

Is there anything I am missing here? What is funny is that before I had the ATI driver installed, and it partially made 3D-acceleration work. I don't understand why the proper driver is not working at all. I must just be missing something.

If everything is as it should be, and just isn't working for whatever reason, should I try azz's link? I think it has a driver or image of somesort precisely for my graphics card (model name).

If I can get this driver going, I will be content to live without running huge 3D games like doom3 and others. I have an xbox with doom3 and other games already. I just basically want 3ddesktop and 3d screensavers etc. A 3D layer if you will. But if I can't get it going I'll have to live without until I can buy a new card.

thanks for any help you can offer
nalmeth

---

### Post by tokyovigilante on 2005-12-03
Good stuff, I'm glad you managed to get X running. Try typing in a console:

```
glxinfo | grep OpenGL
```
and posting the results.

also post the results of 

```
cat /etc/X11/xorg.conf
```

(glxinfo tells you about 3D acceleration with OpenGL, and grep selects only those lines containing "OpenGL". The vertical bar "|" tells bash (the console) to send the info of glx to grep rather than straight to the screen. cat outputs the contents of a file (in this case your X server configuration) to the screen.)

I don't think the instructions azz's link leads to will work for you, because they refer to S3 Savage graphics accelerators running on Intel 915 motherboard chipsets, whereas you have an Intel Extreme (i915) graphics accelerator running on an Intel 915 motherboard chipset.

I'm sure we can get 3D acceleration running on your chipset, it's definitely supported, but (like all things in Linux) it needs a bit of fiddling ;).

---

### Post by nalmeth on 2005-12-03
hey vigilante
thanks helping me out

glxinfo | grep OpenGL
Seemed to stall the console. No output to be seen.

cat /etc/X11/xorg.conf

I wasn't sure you needed to just see device section or not so heres the whole thing:

[I]Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Intel Corporation i915 Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation i915 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
[/I]

[B]quote:
I'm sure we can get 3D acceleration running on your chipset, it's definitely supported, but (like all things in Linux) it needs a bit of fiddling .[/B]

Thats cool with me. I enjoy the tinkering process. It leads to greater knowledge in the end. Thanks for passing yours on.

nalmeth

---

### Post by nalmeth on 2005-12-05
any thoughts or ideas?
I am not rushed and not trying to push for help, but this was getting buried so I had to keep active.
thanks all

---

### Post by hansv on 2006-06-02
I have the same problem with my Intel Extreme Graphics 2.0 cadr.
Although I'm a step further, when you push the 'F1' button you can search for intel i810. When you read the first line, you see that the 3D accelaration is not supported when you use 24 bit color mode. 

Maybe that wil enable your 3D accelaration. I'm still trying to enable mine...

---

### Post by nalmeth on 2006-06-05
[quote=hansv]I have the same problem with my Intel Extreme Graphics 2.0 cadr.
Although I'm a step further, when you push the 'F1' button you can search for intel i810. When you read the first line, you see that the 3D accelaration is not supported when you use 24 bit color mode. 

Maybe that wil enable your 3D accelaration. I'm still trying to enable mine...[/quote]
i solved this problem a long time ago, I switched to the 386 kernel and it was setup out of the box. 

i suppose i am guilty of leaving thread's unresolved.

At least you have a clue as to your own problem.

Have you tried this in the terminal?

sudo dpkg-reconfigure xserver-xorg

---

### Post by go_beep_yourself on 2007-12-18
I don't have the i810 driver. My graphics card is this.

00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)

Do I need any of these?

xserver-xorg-video-i810 - X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver
i810switch - Enables/disables video output to CRT/LCD on i810 video hardware

What is the difference between the first two? Are these the open source drivers provided by intel?

---

### Post by tgalati4 on 2007-12-18
How much memory are you sharing with Video?  On my machine (i945 graphics chipset, it's max at 224 MB).  If you don't max out the shared video memory in the BIOS, then you don't have enough video memory to run 3D.  Dropping to 16-bit or dropping resolution will help to get 3D, but you need to max out your video memory first.

---

