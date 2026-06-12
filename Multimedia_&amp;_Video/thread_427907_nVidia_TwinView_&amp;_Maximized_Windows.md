---
title: "nVidia TwinView &amp; Maximized Windows"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by JymmyZ on 2007-04-29
I've seen this concern voiced in a few other posts and after a week of hunting I still haven't found a solution to the problem of using TwinView and having windows maximize across both screens.
I'm running an nVidia 7950GT with a Samsung DVI LCD and TV-Out from S-Video. I'm currently using self-installed nVidia 9755 drivers, though I've tried the restricted drivers with "apt-get install nvidia-glx-new" (and nvidia-glx)  I've also used several different variations of my xorg.conf file, I'm currently back to a standard one-screen setup (that isn't Beryl friendly either, but that's another issue I'm guessing)
 I've gotten a few different configurations set-up, including having an unreachable desktop on my TV, weird resolutions but somewhat stable maximization of windows, and of course having correct resolutions but having windows maximize across both screens.  So how on earth can I, and others with the same problem, get a usable display on my main monitor (the lcd) while being able to watch movies on my TV in fullscreen? (Another issue is that mplayer does not properly do full-screen/double/normal, it's always squished at the bottom couple inches or so, though its width is normal)  I will get my xorg to the settings that give this issue and post it if it's needed, but I don't have any weird flags or settings, and I'm using what flags I understand are most current to my card and driver.  
Am I just missing a setting, or is there something else wrong?  I've read a couple people who have solved this problem though they haven't been generous enough to post what they did to fix the issue.  Thanks for your time.

--
I should also mention that I do not get a suitable program when I try nvidia-settings, just a few minor choices, and nothing at all useful.

---

### Post by Henrythewound on 2007-05-04
I'm interested in a similar fix. I just re-dove into ubuntu after a long XP hiatus (don't ask) and I have 2 LCDs this time around. I found info on twinview, installed it, and I can move windoes across my two monitors as if they were one. 2 things I have noticed so far and know others have noticed as well are that maximized windows go across both screens and tooltip (if thats the word) and menus appear on my left monitor even if a window is on the right. Is there an all-encompassing thread for fixing this? I just started looking but it seems a lot of questions are posted and only a few answers.

Thx, no intention to hijack here

---

### Post by mocha on 2007-06-13
I was also wondering about this, or if there is a way to put options in mplayer or vlc to show the video as fullscreen in the secondary device.

---

### Post by gtr225 on 2007-07-30
Add me to the list. I've just got the TV-out on my GeForce 6200 to work today and the only way I can get Mplayer or VLC to play videos fullscreen on my TV is if I put it in Clone mode and have the resolution of my CRT match that of my TV (1024x768 on both screens). The reason I would like videos fullscreen only on my TV is because when watching movies on my PC, both screens are occupied so no one else can use the PC while I'm watching a movie on the TV.

---

### Post by MrHippocampus on 2007-07-30
My suggestion, if you have the problem please post your xorg.conf so everyone can see if theres anything wrong with it :)

---

### Post by gtr225 on 2007-07-30
Well I don't think there's anything wrong persay, I think what I'm looking to do is change the way my PC does TV-out.

---

### Post by MrHippocampus on 2007-07-30
If you want to have your PC and TV on separate screens and X isnt doing it then I would consider that as wrong :)

I had a similar set-up a while back so if you post it I should be able to give you some pointers :)

---

### Post by Holodoc on 2007-07-30
hi there

i had almost the same issue last night, after installing proprietary nvidia drivers.
well, i did this for the first time after having a lot of trouble with restricted driver and
kernel 2.6.20-16.

- driver installation according to this very nice guide using method 2: [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2 ]("http://http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2")

- setting up TwinView using nvidia-settings (open terminal and type: sudo nvidia-settings

after that, i was at the same point: windows maximizing throughout both screens.
i tried this and that, but nothing important, i think. nevertheless, when i turned on my
computer tonight, the issue was fixed. Windows are maximized over one screen only.

you may find your answer in my xorg.conf. 

Used HW:
2x Samsung SyncMaster 204B, 1600x1200@60Hz
GF8600GTS

Regards
Your n00b Holodoc

---

### Post by gtr225 on 2007-07-30
> **MrHippocampus said:**
> If you want to have your PC and TV on separate screens and X isnt doing it then I would consider that as wrong :)

I had a similar set-up a while back so if you post it I should be able to give you some pointers :)

Eureka! Thank you for the offered help, but it looks like I got it running two seperate displays for my TV and CRT now. I followed the directions @ [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) and got TwinView working, however the set of instructions: "A more complicated way - Running 2 X-Screens" didn't seem to work until I read: >  On some systems it is necessary to explicitly set what 'head' that was used with the ConnectedMonitor option. For example 'CRT-0' and 'TV-0'. This is also documented under [WWW] Multiple X Screens with Nvidia cards. On other systems, specifying this option is known to _prevent_ TV-out from working, possibly with a message like "Unable to find available display devices for screen 1" in Xorg's log/output. Try commenting the ConnectedMonitor lines out if it doesn't work for you.

So I commented out ConnectedMonitor and it works! However I got two more questions hopefully someone can help with. Firstly, is there a quick way to enable/disable the TV-out? I only wanna have it on when I need it. Secondly, is there a way to run Mplayer (or any media player for that matter) with a higher CPU priority so when I run Firefox, etc on my CRT it won't slow down playback on my TV? I'd rather have apps on my CRT slowdown then choppy playback on the TV.

---

### Post by MrHippocampus on 2007-07-31
There are probably different ways to give mplayer a higher priority, but one way which is universal for all programs is "nice", ive found a forum post which explains it nicely [link]("http://ubuntuforums.org/showthread.php?p=1919695").


I have dual screens set up so when I play games the second one turns off and just leaves the first one on, the same Idea should work for your TV.

Open up your xorg.conf again and find your "metamodes" line, this is the one from my laptop, laptop screen is first and TV is second.

```
Option "MetaModes" "1280x800,nvidia-auto-select;"
```

If you add a second set of metamodes with the tv resolution as NULL instead of a resolution or nvidia-auto-select you will have a display mode which will only show up on the monitor, e.g:

```
Option "MetaModes" "1280x800,nvidia-auto-select; 1280x800,NULL;"
```

To switch between the two you can do Ctrl+Alt++ (thats the plus key on the numpad) or Ctrl+Alt+- (ive found though that these key combinations dont always work), you can also use the normal gnome resolution changer or xrandr on the command line :)

---

### Post by gtr225 on 2007-08-01
That works, but for only one display because the TV and CRT have their own screen section in my xorg.conf. My xorg.conf looks like this: ```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 140.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:1:11:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:1:11:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0,"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: 720x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```One method I found that works is using nvidia-settings to disable the tv and I've set xorg to restart when i logout so after logging out then in the tv is disabled and I can do that to renable it as well. However changing it with a simple hot key sounds much more useful.

---

### Post by MrHippocampus on 2007-08-01
Ah, I assumed you were using twinview but you clearly arent. Im not sure how to accomplish the same thing with two X screens :(

---

### Post by slowhand73 on 2007-11-07
As suggested here : [https://bugs.launchpad.net/ubuntu/+bug/139313](https://bugs.launchpad.net/ubuntu/+bug/139313)

I did "mkdir ~/.config/xserver-xgl/" and "touch ~/.config/xserver-xgl/disable" and the problem was fixed, or at least was worked-around.

---

