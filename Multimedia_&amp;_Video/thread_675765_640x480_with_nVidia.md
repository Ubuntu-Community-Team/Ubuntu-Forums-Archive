---
title: "640x480 with nVidia"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by andrew.co.za on 2008-01-23
I've been playing around with Ubuntu for about a year and a half now. I've done a course on 'Using Linux', i've done a course on 'Linux Administration' but i am still a beginner.

I am quite comfortable with using 'nano to edit the xorg.conf file. i am very familiar with the 'monitor', 'device' and 'screen' sections within the file. All the neccessary resolution modes have been put in under the 'screen' section. i used a command (can't remember it right now) to generate a modeline for '1024x768 75Hz', which i then copied to xorg.conf under the 'monitor' section. The HorizSync and VertRefresh have been commented out (#) and every time i attempt to use those the xserver (graphical user interface) won't start up again. I am also comfortable with using gdm stop, start and restart.

Note: i have installed the latest nvidia drivers as of 19 Jan 2008. The drivers generated the xorg.conf file which had all the neccessary modes but did not have any modelines under 'monitor'. the glxgears work perfectly so it seems the drivers (and my gfx card) are working fine.

Before i installed the nvidia drivers i got 800x600, afterwards i got 640x480 max. In windowsXP i run my destop at 1024x768, 120Hz. My screen is a standard 19" CRT capable of 1600x1200 at 75Hz (Make: AOpen, if that makes a difference). My graphics card is a 7900GTX. I've upgraded Ubuntu fully to 7.10 (gutsy).

To me it seems like a refresh rate problem, are there any standard rages for a 19"? I don't have the user manual anymore. I'll paste my xorg.conf later if it's neccessary.

Just to add, i acctually managed to get my HSDPA modem working with wvdial in Ubuntu (which i told myself at one point never to even attempt) so i have internet access.

---

### Post by andrew.co.za on 2008-01-23
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VM9G"
    VendorName   "AOpen"
    ModelName    "VM9G"
#    Option         "DPMS"
#    HorizSync    31.5 - 48.5
#    VertRefresh  50.0 - 90.0
    Modeline "1024x768"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GTX]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GTX]"
    Monitor        "VM9G"
    DefaultDepth    24
    SubSection     "Display"
#        Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"  "640x480"
    EndSubSection
EndSection

```

---

### Post by DataMatrix on 2008-01-23
Hello. I've just installed ubuntu 7.10 64bit. At the beginning, it was running on 800x600 @24bpp. I've installed the restricted driver for my NVidia and after the restart I've got stuck on 640x480 @24bpp, 50Hz. It's impossible to change the setting. 
sudo nvidia-settings,
Screen Resolutions
 and editing xorg.conf
didn't help at all. I really want to get this fixed.

Edit: OK, I've just disabled the driver for nvidia and the thing started on resolution 800x600 @ 60Hz and is offering only this and the 640x480 setting
I want 1024x768 (17" CRT monitor)

---

### Post by andrew.co.za on 2008-01-24
Could we please get a response! I don't want to write this off as another failed attempt at getting Ubuntu up and running (i have about 4 of those under my belt). I've even resorted to paying someone to come and help me and as one might have guessed he didn't manage to.

This really seems like a straight forward issue; drivers are installed, resolution can't be increased.

---

### Post by andrew.co.za on 2008-01-25
I downloaded Envy,
enabled universe and multiverse repositories in synaptics package manager,
installed a package required by Envy (dkms i think),
i logged out, 
i pressed ctrl+alt+F1, 
logged in then did the following

```

sudo envy -t

```

selected option 6

```

gdm restart

```

log back in in graphical mode (on 800x600),
clicked on: Applications>system settings>Envy,
clicked on 'install nvidia drivers',
it downloaded for a while then installed for a while then set my my xorg.conf file,
i restarted,
GUI she's not want to wek
That's bantu for "the GUI failed to initialise"

any thoughts?

---

### Post by andrew.co.za on 2008-01-25
Okay, for those of you who have had similar problems here is the solution:

- System>Administration>Screens & Graphics
- now select the model (I chose Generic Monitor 1600x1200)
my resolution woes have ended

This problem was as straight forward as they come but for those of us who are unfamiliar with Linux and the way it recognises hardware, it was a fscking mission. So thank you to those at ubuntu forums for a complete lack of service once again.

At least i've learned a good deal of persistence and problem solving skills, always look for the positives ;)
Now i'm off to face an endless wasteland of problems in the alternate world of linux, it's still a step up from windoz though.

---

### Post by bedlam on 2008-01-26
To anyone having problems with screen resolutions.
Try another screen first.
When I upgraded to 7.10 all I could get was 800X600
I followed various threads to resolve the issue but with no success
Finally I swapped my BENQ T905 monitor with a V7 Novatech which I had on my other computer and my resolution problem was solved,:) proving the BENQ was the bug

---

### Post by Mariolo on 2008-01-27
Thank you for this post.  If it was not for this I would have never figured out the problem with my geforce ti4600.:)

---

### Post by Huss on 2008-01-27
I have a similar problem - stuck at 640X480. 

It all started when I tried to get the dual monitor function working. Activating the second monitor changed the laptop screen settings and when I changed them back I couldn't get back into the 'screens and graphics' section. I did manage to change the settings in 'screen resolution' the first time I rebooted, but now it's back to 640x480 and it wont change.

Will try a few things and get back if anything works

---

### Post by Huss on 2008-01-27
Logging in to GNOME let me change the resolution settings but not the 'screens and graphics' settings. ... ...

---

### Post by andrew.co.za on 2008-01-31
log in as user: root, to do that you need to check the box called "allow administrator log in" i think that's under the "login screen" settings

---

### Post by wolfen69 on 2008-01-31
> **andrew.co.za said:**
>  So thank you to those at ubuntu forums for a complete lack of service once again.


do yourself a favor and lose the atitude. if you dont like it, demand your money back. wait....

---

### Post by andrew.co.za on 2008-01-31
lol, okay okay, i'll lose the attitude but it would have been nice to have gotten some help along the way.

---

### Post by kpkeerthi on 2008-01-31
If you already have modelines in xorg.conf, you will not be able to change resolutions from nvidia-settings graphically. You need to restore xorg.conf to the state it was exactly after nvidia driver was installed and enabled, and before you added modelines. Good luck.

---

### Post by andrew.co.za on 2008-02-01
Thanks but i already managed to sort it out. Turns out the Plug and Play monitor driver was the problem.

---

### Post by Waldo2020 on 2008-02-01
c'mon people! don't blame Ubuntu for the shite that is the Nvidia driver? After weeks of fidding, I finally got something other than 640x480 - and the fault was Nvidia throwing out all the resolutions it thought were invalid. Blame Nvidia and go holler at them... BTW telling the  "nvidia" driver to ignore EDID or igore EDID freqs will get you working in some cases. often the settings don't persist and have to be manually reset after bootup. None of these problems with VESA or NV driver, but then no acceleration either. The is what happens when drivers are closed! The stinky hippie (Stallman) was right! All it takes is one idiot to break a driver for millions of people, and no one can fix it because the source is locked up..

---

### Post by andrew.co.za on 2008-02-03
> **Waldo2020 said:**
> c'mon people! don't blame Ubuntu for the shite that is the Nvidia driver?...

No..... I'm quite sure ubuntu wasn't recognising my screen properly. But truthfully my monitor is a bit wierd at times, even in windows. I won't go into details but the nvidia drivers were doing exactly what ubuntu was. They looked at the monitor and said WTF is this thing?

---

### Post by mrtrick on 2008-02-03
> **andrew.co.za said:**
> Okay, for those of you who have had similar problems here is the solution:

- System>Administration>Screens & Graphics
- now select the model (I chose Generic Monitor 1600x1200)
my resolution woes have ended


Thanks for this. I'm fairly proficient, but this one still got me. Life is good once again. :)

---

### Post by DataMatrix on 2008-03-04
I've enabled (updated) the restricted drivers for my nvidia. KDE is still working like a charm, but every logon attempt with gnome results in returning to the login screen. More strangely, failsafe gnome works. The crash happens when gnome tries to change resolution, thus resulting in a crash. KDE and FailSafe Gnome don't try to change resolution at logon, so they don't crash. :confused:
Also, in normal gnome mode, there weren't any resolutions in System>Administration>Screens and Graphics - the complate lists only appears in Failsafe gnome. Any idea what the hell is going on?!
NVidia 6600
Monitor: AOC Spectrum 7GlrA (it gets detected, so i don't think that it's the problem).

---

