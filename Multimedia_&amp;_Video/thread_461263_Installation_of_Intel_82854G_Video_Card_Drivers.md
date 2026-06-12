---
title: "Installation of Intel 82854G Video Card Drivers"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by Pinger05 on 2007-06-01
I have been researching how to get the video drivers working for my integrated Intel 82854G Video card.  While the default drivers do a good job rendering th 2-D desktop when I try to play games like Penguin Racer I get about 3 FPS.  This hardware should do better.

Symptoms:
1)  When trying to install BERYL the directions here tell you to type in glxinfo | grep direct.  The directions here [https://wiki.ubuntu.com/BerylOnFeisty](https://wiki.ubuntu.com/BerylOnFeisty) say that you should get a line that says:
Direct Rendering = Yes
-or-
Direct Rendering = No

I get garbage:
dan@dan-desktop:~$ glxinfo | grep direct
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
which makes me think that there is a problem with the dirvers

2) When I go to System => Administration => Restriceted Drivers I get an  message that says "Your hardware does not require any restricted drivers".

3)  Only 3FPS when playing penguin racer.

Here is my XORG.CONF file:
```
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Can anyone help please?  Thanks!

---

### Post by coffeecat on 2007-06-01
Have a look at this bit of your xorg.conf.

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection
```You're using the vesa driver which will work with any (as far as I know) video chipset but which is very limited - as you've discovered. Did the install CD setup xorg.conf for you?

Try changing "vesa" for "i810" which is the driver for most (if not all) Intel chipsets and will give reasonable 3D on the later ones. I suggest you backup xorg.conf first though, because I do not have experience of that particular chipset and if I'm wrong and the xserver crashes, you can at least revert to a (half)working configuration.

One complication - the latest Intel driver is now called 'intel' - at least with some distros. I don't know what the situation is with Ubuntu. You might want to do a forum search for intel xserver drivers first and see what others are saying.

**Edit:** Intel open-sourced their video driver - I believe - which is why you're getting the "Your hardware does not require any restricted drivers" message.

---

### Post by Pinger05 on 2007-06-01
Thanks for the help I will try tomorrow to get it to work.

I have scowered the forums looking for help on this.  I read a lot before I post.


Thanks for the help.  I will update as soon as I know.

---

### Post by coffeecat on 2007-06-01
> **Pinger05 said:**
> I have scowered the forums looking for help on this.  I read a lot before I post.

That's OK. I was just emphasising that I wasn't quite sure where Ubuntu was on this business of renaming/replacing the i810 driver with intel.

**Edit**: I'm using my desktop with an nvidia card at the moment so it's no use my looking in my xorg.conf, but I've just had a look in Synaptic and there are two packages, xserver-xorg-video-i810 and xserver-xorg-video-intel, listed. So I suggest you check and see which of those packages you have installed already, and amend xorg.conf accordingly.

A question though. You say you have the, "Intel 82854G Video card." I was not aware of a 854G which is why I said I had no experience of it. But the package description for both those packages says:

> This package provides the driver for the Intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865, i915, and i945 series chips.

Is 82854 a typo for 82845? I have a desktop with the 845G chipset which is one of the older ones and I have to tell you that 3D performance and rendering of PPRacer varies from hopeless to modest depending on the distro, whereas the 915G chipset using the same driver in my laptop goes quite well. If you do have the 845G chipset you may be disappointed.

---

### Post by Pinger05 on 2007-06-02
> **coffeecat said:**
> Have a look at this bit of your xorg.conf.



Try changing "vesa" for "i810" which is the driver for most (if not all) Intel chipsets and will give reasonable 3D on the later ones.

**Edit:** Intel open-sourced their video driver - I believe - which is why you're getting the "Your hardware does not require any restricted drivers" message.

It worked perfectly - the command glxinfo | grep direct gives me a yes now.

Another issue surfaced though.  The desktop is shifted to the left about an inch.  An inch of the left is cut off and there is an inch of black space to the right.

Any ideas?

---

### Post by coffeecat on 2007-06-02
I run three machines through a KVM switch and going from one graphics card to another or one driver to another always gives me a slight shift horizontally and/or vertically which I deal with by pressing the auto button on the monitor - which is a LCD one.

But an inch seems a lot. Is that a flat screen or CRT monitor? If it's an LCD/TFT screen have you tried the auto (or whatever it's called on your monitor) button? Or you can get it to auto-tune to the signal through the monitor menu somewhere.

It's worth doing that anyway rather than hoping for the best. I've been playing around with a Mac Mini today, hooked up to my flat screen TV with a native 1366x768 screen. The Mac was putting out a 1360x768 image (as would the Linux drivers that can cope with this resolution) and at first the picture was appalling. Then I searched through the menu (it's a TV - no auto button), got it to autotune and the result was stunning. The story would have been the same with a Linux box.

---

### Post by Pinger05 on 2007-06-03
You are my new best friend!  I found the remote and hit the Auto button - problem resolved!

Thank you very much!

---

