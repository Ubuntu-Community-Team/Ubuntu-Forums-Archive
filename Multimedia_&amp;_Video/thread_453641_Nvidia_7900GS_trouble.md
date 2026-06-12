---
title: "Nvidia 7900GS trouble"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by KManZ on 2007-05-24
Ok, on my quest to go completely Windowless, I have one remaining problem: getting my GPU to work properly. I have a 7900GS 256MB card. I have ran Envy, and here is what has happened both times:

1) Install Nvidia driver. Then it asks if I want to edit my xorg.conf (recommended), and I do that. Then it asks me to restart. 

2) After the restart, it did not start GNOME. It went to a black screen, and said: "/dev/sda1 mounted 32 times without being checked, force check" and it went on to do some check. This only happened the last time I tried to install the driver via Envy.

3) Next, it attempts to start normally, but then gives me this screen: "Failed to start Xserver (graphical interface). It is likely that it is not set up correctly. Would you like to view the Xserver output to diagnose the problem?". So I hit "Yes"

4) After hitting "Yes", I read this: "API mismatch: this Nvidia driver component has version 100.14.03 but the Nvidia kernal module's version does not match. Please make sure that the kernal module & all Nvidia driver components have the same version." So I exit out, and it kicks me to the command line.

5) I then went in and rm my xorg.conf, and reboot. My machine then boots normally into GNOME and all is well. Plus, under System Tools, there is even "Nvidia Settings". So something went right, but something else went wrong.

Anyone have the answer to this one? Sounds to me like something is not labeled correctly somewhere. Thanks!

Matt

---

### Post by dabl on 2007-05-24
I have the same Nvidia card -- it works great, but installing that driver is "character building"!

I've had my best results, when finding my video all screwed up, by (1) reconfiguring it as a VESA graphics system, (2) un-installing everything that starts with "nvidia-", and finally (3) reinstalling my chosen Nvidia driver.

So, to do (1), and assuming you can get logged in to a console, it is ```
sudo dpkg-reconfigure xserver-xorg
``` and on the first screen choose "no" to autodetect, and on the second screen choose "vesa", and then the defaults are all OK for standard hardware, and when you get to the monitor part of it, choose only the resolution that you want to work with while you're getting through the re-installation process.  When the script is ended and you are tossed back to the command line, enter ```
startx
``` and you should get a functional GUI.

(2) is only applicable if you used the nvidia-glx-new or one of the other nvidia drivers from the repositiories.  In that case, open your synaptic or adept package manager and mark any packages that start with "nvidia" for removal, and then hit the "apply" button.

(3) If you want the proprietary driver, I use Envy (now that he has it working for Feisty).  On my Kubuntu installation (same hardware, different hard drive) I got it by selecting the package nvidia-glx-new -- that's the only one you need.  On Ubuntu 64-bit, I used Envy, and it worked great.

HTH   :D

p.s. the file system check is unrelated to anything about video or your Nvidia card, notwithstanding the coincidental timing

---

### Post by KManZ on 2007-05-24
So after reconfiguring and removing all the Nvidia pkgs from Synaptic, I then use Envy again, or do I go back to Synaptic and choose nvidia-glx-new?

---

### Post by dabl on 2007-05-24
Try Envy first -- if it doesn't work you can go the other way.

EDIT: I'm assuming you have a recent installation of Envy -- he only released it for Feisty a couple of weeks ago, so you need to make sure that you are current on it.

---

### Post by KManZ on 2007-05-24
Rock on man, trying it now!

---

### Post by KManZ on 2007-05-24
It didn't work. I haven't a clue what could have went wrong, but now my wireless card won't even turn on, and my resolution is messed. When I restarted I got a splash screen for the Nvidia Beta driver, but after that got an error about the xorg.conf file or something :( you were right about this being a character building experience. 

How do I get it to turn my wireless card back on? I think it has something to do with the Restricted drivers or something, as I remember seeing my wireless card being listed under there along with the Nvidia card.

---

### Post by dabl on 2007-05-24
Hmmmm -- and you are running Feisty, and you have the current version of Envy, right?

Wireless cards -- I dunno -- don't have one, don't use one -- sorry.  But your theory about it being related to restricted drivers sounds right to me.

Sounds like time for Plan B.  Set up your graphics as a VESA system again (Step 2 above), and this time after you have re-started, open Synaptic and mark ONLY nvidia-glx-new for installation.  Click "apply", then after closing Synaptic, say a prayer to the monkey-god and hit Ctrl-Alt-Backspace to restart the xserver.

I'll cross my fingers.....

P.S. I just got notification of software updates available, and I see there is an update to linux-restricted-modules.  You probably want that.

---

### Post by KManZ on 2007-05-24
Thanks for the help, but I am going to re-install... frustrating. But I am still sticking with Linux versus going back to Windows.

---

### Post by dabl on 2007-05-24
OK, I understand.  I installed Kubuntu about 10 times before I actually felt like I knew what I was doing.  Consider it "practice"......

:D


HOWEVER, you will STILL need to install the Nvidia driver ......

---

### Post by KManZ on 2007-05-24
^^ This is the first place I am going to stop after the clean install brotha :) Thanks for your help!

---

### Post by dabl on 2007-05-24
> **KManZ said:**
> ^^ This is the first place I am going to stop after the clean install brotha :) Thanks for your help!

Hang in there -- you are in the process of escaping Win-World -- it's not easy, but it is sweet when you get there!

:D

---

### Post by KManZ on 2007-05-24
haha its like withdrawl almost... I am tempted to dual boot, but I am resisting! I want to break free completely! I think I am close!

I finished reinstalling (so fast compared to Windows) and have things set up again. I followed your instructions, and discovered how i lost internet: when I went to remove all the Nvidia packages, it took off the restricted drivers modules too... ie. my intel wireless card ceased to function. :o

I was careful not to do that this time! The only thing Nvidia that was installed was the Nvidia Kernal, and if I took that off, I would again lose internet. So I just installed the Nvidia-glx-new, and so far things are ok.. haven't restarted yet. How do I know if I have 3D capabilities after the restart?

Also, my resolution is too low. How do I get back to my native 1920x1200?

Edit: I uninstalled the Nvidia-glx-new and just tried Envy again. My question is: if I can't remove the Nvidia Kernal already present, will this conflict with Envy?

Yep, it does. I get the same error as my original post. It starts me at the command line and then tells me that the X Server failed to start. I am confused again haha what do I do? The Nvidia-GLX-new didn't do anything to my system... ie I didn't have any menu to change any settings etc.

---

### Post by dabl on 2007-05-24
No prob -- weaning one guy off Windows is worth it!

OK, in a console window you type > glxgears to find out if you have glx installed and working.

---

### Post by dabl on 2007-05-24
In case it is helpful, I'm providing my xorg.conf file (this is for Feisty 64-bit):

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:37:58 PST 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:38:28 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 130.0
    VertRefresh     50.0 - 160.0
    ModeLine       "1600x1200" 242.0 1600 1728 2024 2568 1200 1200 1204 1256 +hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1600x1200 +0+0"
    Option         "Coolbits" "1"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by KManZ on 2007-05-24
Ok, Envy isn't working.. so I took it off. I then updated to the newest linux Restricted Modules and at the same time uninstalled the old one. Finally I cleared out everything Nvidia but the Nvidia kernal stuff, and reinstalled Glx-new. 

After all this, the Nvidia driver is not showing up in my Restricted Drivers section. I know that it isn't activated. What am I missing? I am close to figuring this out, I can feel it!

---

### Post by dabl on 2007-05-24
I dunno -- do you have linux-restricted-modules-generic

?

---

### Post by KManZ on 2007-05-24
I am using Linux-restricted-modules-2.6.20-16-generic, linux-restricted-modules-common, and now a few NVidia ones: Nvidia kernal 2.6.20-15, kernel-common, and kernel source.. I have no idea what I need and what I don't need. Plus, now in the System Tools menu I have a "Nvidia settings" section.

How do you update the repositories? Also, I run glxgears and it says: 
"GLX missing on display ":0.0"
"Couldn't get an RGB, Double buffered visual"

---

### Post by ryanVickers on 2007-05-24
As coincidencial as this may seem, the checking the disk and the falure of the X server are not connected.  It automaticly checks it every now and then.  Now about the card, it couldn't start the GNOME because the file xorg.conf was broken by the installer.  I would try using the built in driver manager for 7.04.  Unlike everything that came before, it exists and when it installs it works (for me at least.)  Try it out.

---

### Post by KManZ on 2007-05-24
> **ryanVickers said:**
> As coincidencial as this may seem, the checking the disk and the falure of the X server are not connected.  It automaticly checks it every now and then.  Now about the card, it couldn't start the GNOME because the file xorg.conf was broken by the installer.  I would try using the built in driver manager for 7.04.  Unlike everything that came before, it exists and when it installs it works (for me at least.)  Try it out.

How do I do this?

---

### Post by dabl on 2007-05-25
Sure -- Ryan is referring to the "Restricted Drivers Manager" under System>Administration.  I have not needed to use it, since Envy worked for me, but open it up and see what you can do with it.  Might want to try a search in the forum to see what other folks have done with it.

Here's another possibility.  If Ryan is right and the installer is messing up xorg.conf, then maybe all you need to do is open a console window and type > sudo nvidia-xconfig --add-argb-glx-visuals --composite

and then Ctrl-Alt-Backspace to restart the xserver.  But before you do that, make sure you see the Nvidia splash screen at the end of the boot process, right before it attempts to put up the GUI desktop.  In other words, if the driver is installed, but xorg.conf is messed up, then the command I gave you should get the glx and compositing functions working.

---

### Post by ryanVickers on 2007-05-25
Yes, follow all that and you should be fine

---

