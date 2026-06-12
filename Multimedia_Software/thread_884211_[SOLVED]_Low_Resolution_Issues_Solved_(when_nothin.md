---
title: "[SOLVED] Low Resolution Issues Solved (when nothing else works. . . .)"
date: 2008-08-08
forum: Multimedia Software
---

### Post by Anlace on 2008-08-08
Greetings,

I went around and around with low resolution issues with my GeForce 6800 GTX video card in Gutsy and then again with Hardy.  I ended up using vesa drivers just to get native 1680x1050 resolution on my ViewSonic VX2025 monitor.  Nothing I did, and I do mean nothing, would make the monitor use any of the Nvidia drivers and display native resolution.

Recently I built a brand new computer with a 9800 GTX video card and had the exact same problem.  I spent (literally) 3 days trying to figure out what was going on and would like to share my experience and the way that I solved my resolution issues.

What I discovered is that my monitor, along with many other older LCD monitors, was passing corrupt EDID info to xorg.  Put very simply EDID info resides within the monitor itself and when the data becomes corrupt the video driver falls back to a mode that is absolutely safe for your monitor although it's usually unusably low.

Take a look at Bug 194760: EDID fail ([https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)).  That bug report will help you to determine if your monitor has corrupt EDID info.

To the best of my understanding Ubuntu/Xorg is using EDID info exclusively to determine the best resolution for the monitor.  Everything I tried to over-ride EDID in xorg.conf was ignored and the Nvidia driver ended up loading its default mode which was very low resolution.  Nothing, absolutely nothing I did to edit xorg.conf would encourage it to behave in any other way.  Talk about frustrating!

Take a look at my post in Questions for xorg-server in ubuntu: How Do I Override EDID Info in Xorg.conf?
[https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299](https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299)

What I did to finally solve my resolution issue was this:

1) I installed the Nvidia driver (from Nvidia's web site).  I used this guide to do so:
BinaryDriverHowtoNvidia
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

2) I shut down my computer, connected my monitor with an analog connection to the video card (because I got perfect resolution when using analog).

3) I opened the Nvidia X Server Settings program and under GPU 0 - (GeForce 9800 GTX) > DFP-0.  I used Acquire EDID... to make a edid.bin file.

4) I saved the edid.bin in /home/gail/Nvidia/edid.bin

5) I edited the xorg.conf file as root and under the Device section added the line
Option  "CustomEDID" "DFP-0:/home/gail/Nvidia/edid.bin"

6) I shut down the computer, connected the monitor using DVI and it booted up with perfect resolution.  No more problems.

Start by finding out if your monitor has corrupt EDID info, then see if it will boot into good resolution using an analog connection.  If it does then this may be the way you can get native resolution working on your monitor.

I sincerely hope this information helps with those of you struggling with resolution issues.  It can be frustrating as heck to know that your monitor works with good resolution (it does in Windows, OS X, etc) but not be able to get it to work with (K)Ubuntu.

Peace,
Gail

---

### Post by kabuchin on 2008-08-09
Awesome, I have the exact same problem. I'll try and let you guys know. Thanks!

---

### Post by kabuchin on 2008-08-09
My monitor (ViewSonic 2035wm on 8800gts) is not being recognized even using analog cable. My get-edid fails and I don-t have the 'get-edid' option in the nvidia x server settings application. More data: my monitor is being recognized as a CRT monitor and using the 1680x1050 resolution. Everything is fine, except for the vertical fuzzy bars all over the screen.

---

### Post by Anlace on 2008-08-10
Check out the thread
Nvidia just won't work! Why, why, why?!
[http://ubuntuforums.org/showthread.php?t=883938](http://ubuntuforums.org/showthread.php?t=883938)

It goes into some depth about how to get an edid.bin file generated from an analog (VGA) connection.

In the meantime I may just get inspired enough to write a bit of a HowTo and outline the steps specifically.  Tomorrow, when I'm not so sleepy.

---

### Post by kabuchin on 2008-08-10
IT WORKED!!!!!!!!!!!!
Oh man, I'm sooooo thankful, thank you very very much. You rule.
The fuzzy bars disappeared and I'm using ubuntu at native resolution on dvi cable, amazing, thanks again!

Btw, my monitor is a viewsonic 2035wm, 8800gts vga. On standard xorg.conf file, adding the following line under "device" section:

```
Option "CustomEDID" "DFP-0:/home/username/edid.bin"
```

With the edid.bin file that Anlace provided me, it worked like a charm
Thanks again.

PS: if anyone wants the *working* edid.bin file for this monitors, here it is: [http://www.sendspace.com/file/951owg](http://www.sendspace.com/file/951owg)

If you can't get it there, ask me, i'll send it to you.

---

### Post by agamonD on 2008-08-20
I just wanted to add that if, like me, you then proceed to try and use nvidia-settings to set up multiple monitors using TwinView, when you save the new settings back to your xorg file (remember to gksu nvidia-settings!), it will sort of mangle your file and cause X to ignore the custom EDID options set up here.  

Easy to fix: just edit your xorg.conf so that the "Device" section being used contains the EDID option (eliminate the new extra section) and make sure the "Monitor" sections still reflect you original file (It may throw in an extra one of those too).  I also like to go through and name my card and monitors somethings more human-friendly.  

From what I understand (shaky ground ahead) you need to save the settings back to xorg.conf, as opposed to just relying on the xrandr extension, in order for nvidia to emulate the Xinerama extension and allow you window manager to behave sensibly (like not maximizing stuff across both screens).

---

### Post by Hessesian on 2008-08-21
Thank you ! That trick with analog conenction worked ! I have Samsung SyncMaster 2032bw, and now I have finally right resolution :)

For anyone out there, here is working edid.bin file for this monitor
[http://hessesian.own.cz/dl/edid.bin](http://hessesian.own.cz/dl/edid.bin)

And here is my xorg.conf file
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
    Option         "CustomEDID" "DFP-0:/home/duri/edid.bin"
EndSection

Section "Screen"

# Removed Option "metamodes" "1680x1050 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0"
EndSection


```

---

### Post by cba.421 on 2008-09-07
Not getting resolution above 640x480

I am very new to Linux. So excuse me if I show my noobness in every sentence :).
I  Installed  ubuntu 8.04 a few days ago.
I use Geforce 7200 GS  Graphics Card, and I installed the NVIDIA driver  173.14.12 manually after downloading it from NVIDIA website and restarted. But I have not been getting a resolution above 640x480. 
I  followed this thread  “[SOLVED] Low Resolution Issues Solved (when nothing else works. . . .)” and worked accordingly. I have attached my final  Xorg.conf file. 
I used  DVI-D cable ONLY to connect the Graphics Card and my Monitor ( LG 194WT), although I prefer using D-SUB. 
I have also attached screenshots of Nvidia X server program. The most important thing for me looks to be , the Frontend resolution which is not equal to the native resolution.
Somebody please help me out :(

---

### Post by BigSilly on 2008-11-18
Just wanted to post up to say -

THANKYOU!THANKYOU!THANKYOU!THANKYOU!THANKYOU!THANKYOU!


Been fighting with this for daaaaays. Had some great help off the forums, but no joy. Then I found your tutorial just after I'd actually given up and plugged in the old CRT. I thought "why not?" and gave your tutorial a go, since my issues were very similar. I've just this minute booted into the correct resolution via DVI-D for the very first time! I cannot tell you how utterly stoked with this I am! 

You've absolutely made my day. Nay, week!

Now, who do we tell about this, and is there a way it can be sorted so it doesn't happen again? Are we going to have to do this each time we install Linux fresh, or is there someone that can incorporate this fix automatically? 

My heartfelt thanks again!

:guitar:

---

### Post by BigSilly on 2008-11-23
Just thought I ought to post up my EDID.bin file for my monitor. It's a pretty oldish Acer AL1521 TFT screen. If you have one of these and are unable for whatever reason to get your edid.bin, just extract the archive attached and use that one. It should be fine. :)

Hope it's of some use to someone anyway. I reckon there are a few people out there with resolution problems who could do with having a look at this little tutorial!

---

### Post by Spectre5 on 2009-05-03
Yes - I do realize that this thread is VERY old...but I just wanted to add my THANKS to the OP!  THANK YOU SO MUCH!  This method worked for me like a charm - after hours and hours and hours of trying to disable EDID and using hundreds of different Modelines!

THANK YOU!!!!

Now to get my audio working through the HDMI :)

---

### Post by falkaholic on 2009-11-12
Thanks, I suddenly had this same problem. I have been banging my head against the wall for weeks. 

Nvidia 9800GT, with a couple ACER AL1916W monitors. One day, one was only 640x480. Windows worked fine but the nVidia drivers in ubuntu 9.X didnt seem to be able to handle it. Turned out to be a bad DVI cable.


EDIT: I take it back, looks like it reverted after a log in. Seems to be one of the monitors i think. Now using single monitor, i just give up.

---

### Post by ChukG on 2010-02-10
> **Anlace said:**
> Greetings,

I went around and around with low resolution issues with my GeForce 6800 GTX video card in Gutsy and then again with Hardy.  I ended up using vesa drivers just to get native 1680x1050 resolution on my ViewSonic VX2025 monitor.  Nothing I did, and I do mean nothing, would make the monitor use any of the Nvidia drivers and display native resolution.
Peace,
Gail

Thanks -- we've had EDID problems with this monitor since maybe six months in, even had it replaced once. I just did a fresh 9.10 install and after updates had no high resolutions, but with your help, I'm up and running.:p

---

### Post by ThePurpleStreak on 2010-03-09
I have a Samsung Syncmaster 2343, a 23" wide screen.  It works fine with Windows, even an old version, but on an up-to-date-as-of-yesterday Ubuntu, the screen is described by System->Preferences->Display as 17".  I have another Samsung monitor, different model, and it works fine, its EDID info is correct, but it is not as capable as the 2343.  I've used read-edid on the 2343, connected in analog mode, and the information seems "generic" and not at all suited to the 2343.  I think I need an edid.bin file for the monitor ... any help would be appreciated.

---

