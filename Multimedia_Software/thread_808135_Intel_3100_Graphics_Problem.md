---
title: "Intel 3100 Graphics Problem"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Brian96 on 2008-05-26
[I posted this in the 64 bit users forum, but think it may be more appropriate here.]

I have a Dell Inspiron 530 using the Intel 3100 onboard GMA and I'm running Hardy 64 bit. Compiz works, but my screen has a black bar around the sides and bottom. I've tried running "sudo dpkg-reconfigure xserver-xorg" to be sure the proper driver ("intel" right?) is in use, but the program quit after the keyboard configuration (no error messages, just quit).

My xorg.conf:

> 

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection



It almost looks like the video devices have not been configured at all (or are configured elsewhere?).

I determined through the "Screens and Graphics" tool that I am using the VESA driver, but I still don't know how to change it (changing it there failed).

Any ideas? I am particularly perplexed that dpkg-reconfigure xserver-xorg exits after the keyboard configurations. Why will it not even let me configure the video?

---

### Post by Brian96 on 2008-05-26
bump

I know this is a common system (used, for example, in the default configuration for the Dell Inspiron 530). Is no one else having trouble with this graphics controller?

---

### Post by prshah on 2008-05-29
> **Brian96 said:**
> 
I have a Dell Inspiron 530 using the Intel 3100 onboard GMA and I'm running Hardy 64 bit. Compiz works, but my screen has a black bar around the sides and bottom. 

(or are configured elsewhere?).

I determined through the "Screens and Graphics" tool that I am using the VESA driver, but I still don't know how to change it (changing it there failed).

Any ideas? I am particularly perplexed that dpkg-reconfigure xserver-xorg exits after the keyboard configurations. Why will it not even let me configure the video?

"dpkg-reconfigure..." no longer configures video settings on Hardy. To change the driver, use the GUI: Press Alt+F2, then ```
gksudo displayconfig-gtk
``` and there in the "Graphics Card" tab, you can change over to the "Intel Experimental Modesetting" driver.

[My guess:] As to the black bars; on my fujitsu, the native resolution in 1280x800; If I run it in anything lower, the whole display is "boxed" in at the center of the screen with a thick black border  ("framed" with black) . I can get rid of it by enabling "Display Compensation" in the BIOS (which "zooms" the "framed box" to full screen); your option may be called something else. If you are running it in the native resolution (in your case, I think it's 1680x1050), and it's still boxed in, then this is not your problem; otherwise you might want to look in the BIOS for a similar solution. (Also, Fn+F8 on my laptop enables and disables display compensation on the fly; you may also have such a facility).

If for any reason you cannot change to the Intel driver using displayconfig-gtk, post back for manual change over instructions.

I believe that if you get your display card working fine the "black frame" problem should resolve itself.

---

### Post by Brian96 on 2008-05-30
> **prshah said:**
> "dpkg-reconfigure..." no longer configures video settings on Hardy. To change the driver, use the GUI: Press Alt+F2, then ```
gksudo displayconfig-gtk
``` and there in the "Graphics Card" tab, you can change over to the "Intel Experimental Modesetting" driver.

[My guess:] As to the black bars; on my fujitsu, the native resolution in 1280x800; If I run it in anything lower, the whole display is "boxed" in at the center of the screen with a thick black border  ("framed" with black) . I can get rid of it by enabling "Display Compensation" in the BIOS (which "zooms" the "framed box" to full screen); your option may be called something else. If you are running it in the native resolution (in your case, I think it's 1680x1050), and it's still boxed in, then this is not your problem; otherwise you might want to look in the BIOS for a similar solution. (Also, Fn+F8 on my laptop enables and disables display compensation on the fly; you may also have such a facility).

If for any reason you cannot change to the Intel driver using displayconfig-gtk, post back for manual change over instructions.

I believe that if you get your display card working fine the "black frame" problem should resolve itself.

Thanks for the help. I did not know that about dpkg-reconfigure. At least I know that is not broken!

My machine is actually a desktop. I had set it up while visiting my parents using a 15" CRT they had laying around. When I brought it home and plugged it into my 19" LCD (1440x900) the VESA driver worked fine. When I get back home I may play around with the utility you mentioned (is that the same thing called "Screens and Graphics" in the menu?). So far it is working fine with VESA, so I may just leave it alone.

Thanks again for your help.

---

### Post by nvt on 2008-06-01
Hi All,

I have two desktops with GMA 3100. One is Shuttle SG31G2, which is my home computer and it works fine. Another is Lenovo ThinkCenter, which I've got at work and tried to setup today. In short, it does not work the way I'd like. It fails to recognize monitor (SyncMaster 204B, 1600x1200) when it is connected to DVI, but when it is connected to VGA the default xorg.conf works fine setting the resolution to 1600x1200 at 60 Hz. And yes, I tried to modify xorg.conf in different ways by specifying the driver, e.g.
```

Section "Device"
        Identifier      "Intel Corporation Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

```
and monitor parameters, e.g. 
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Integrated Graphics Controller"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```
or even listing modes in "Monitor" section.
It did not help :(
In /var/log/Xorg.0.log I can see information on resolutions and frequencies when connected to VGA, but not when to DVI. And I really like to have DVI. It works much better. 

Any help or advice are welcome...

Thanks in advance.

---

### Post by Brian96 on 2008-06-01
(deleted)

---

### Post by oddonto on 2008-09-09
I am running a Dell Hybrid Station with Hardy and with same Intel GMA 3100 - no success with DVI only VGA. Any clues - have not touched the xorg.conf - it is the default.

---

