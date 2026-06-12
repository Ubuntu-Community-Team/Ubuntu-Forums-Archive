---
title: "[nvidia] Seiki U39UY4 (4K resolution) and xrandr problems"
date: 2013-08-02
forum: Multimedia Software
---

### Post by renaud2 on 2013-08-02
Hi there!

I just bought a [Seiki SE39UY04 (39" 4K TV)]("http://www.amazon.com/Seiki-Digital-SE39UY04-39-Inch-Ultra/dp/B00DOPGO2G") to use as a monitor and tried to set it up at 4K resolution (3840x2160), but unfortunately, the highest resolution available is 1920x1080... I'm running ubuntu 12.04, on my [GTX 650 Ti]("http://www.nvidia.fr/object/geforce-gtx-650ti-fr.html") (4K ready), using nvidia proprietary drivers.
 
I'm not a newbie regarding Linux (I'm on embedded Linux for years), but I never looked to the video/X subsystem :-&, and I'm somewhat lost (xorg.conf, modelines, xrandr and so are new to me).

I tried to follow the modline recommandations found on an helpfull review on [that page]("http://www.youtube.com/watch?v=Mv5xyqwEKvw"), but I'm getting a weird error trying to add a new modeline:


```

renaud@fractal:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 860mm x 480mm
   1920x1080      59.9*+   50.0     24.0     30.0     30.0     25.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x720       59.9     50.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3  
   720x576        50.0     25.0  
   720x480        59.9     30.0  
   640x480        75.0     72.8     59.9  
DVI-D-1 disconnected (normal left inverted right x axis y axis)
renaud@fractal:~$ xrandr --newmode "3840x2160" 307.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync
renaud@fractal:~$ xrandr --addmode HDMI-0 "3840x2160"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  35
  Current serial number in output stream:  36

```

I tried using nvidia-current (304), nvidia-experimental (310), and even nvidia-319 (319) but no luck.

Here is my [dmesg]("http://pastebin.com/VY1inMBV") and my [lspci]("http://pastebin.com/UYQeNZYN").

I even tried to create a 10-monitor.conf into /usr/share/X11/xorg.conf.d, but no changes (at all) :

```

renaud@fractal:~$ cat /usr/share/X11/xorg.conf.d/10-monitor.conf
Section "Monitor"
  Identifier "Monitor0"
  Modeline "3840x2160" 307.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "HDMI-0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "3840x2160" "1920x1080"
  EndSubSection
EndSection

```

I'm stuck, and this is very frustrating :(

Any hints appreciated ?

---

### Post by houkouonchi2 on 2013-08-02
Sigh stupid ubuntu forums not letting me access my original account...


Anyway What does the device section of your xorg.conf look like? Can maybe paste your Xorg.0.log to pastebin?

As I mentioned on youtube under the device section you will need it to look something like this (along with the other stuff in it)

```

    Driver      "nvidia"
    Option "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck,  AllowNonEdidModes, NoEdidMaxPClkCheck"

```

---

### Post by renaud2 on 2013-08-02
I tried that, and it did the trick!!! :popcorn: You rocks!

For now, I only tried the 19Hz settings, but here's my 10-monitor.conf :

```

renaud@fractal:~$ cat /usr/share/X11/xorg.conf.d/10-monitor.conf 
Section "Monitor"
  Identifier "Monitor0"
  Modeline "3840x2160" 165.00 3840 3888 3920 4000 2160 2163 2168 2222 +hsync +vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "HDMI-0"
  Option "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "3840x2160" "1920x1080"
  EndSubSection
EndSection

```

According to [your post on YouTube]("http://www.youtube.com/watch?v=Mv5xyqwEKvw"), the settings for ~30Hz are:

```

...
[COLOR=#333333][FONT=arial]Modeline "3840x2160" 307.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync
...
[/FONT][/COLOR]
```

[s]But I still haven't tested it[/s] Works too! But should only work on [very latest nvidia drivers]("http://linuxg.net/nvidia-319-23-has-been-released-how-to-install-nvidia-319-23-drivers-on-linux/"), otherwhise you're stuck with 19Hz refresh rate.

BTW, I'm interested in understanding things : where/how do you get those settings? :confused: Can you explain them a bit for us?
Anyway, you're the best, I'll update the thread title as "solved" and I'll play a bit with my new monitor now ;)

I'm sure this thread will help others.

---

### Post by houkouonchi2 on 2013-08-02
If you run X with -logverbose 6 you can get a lot of details about what is going on. I remember the mode was being rejected because the max pixelclock of HDMI is still only being detected as 165 Mhz by the driver (when it should be like 340Mhz). That modeline your running is 307 Mhz well above the 165. The default 3840x2160 modes (24, 25, 30 Hz) are all around 297 Mhz which again is well over 165 Mhz. The mode validation over-ride stuff is in nvidia's documentation but I have been running 4k monitors since 2005 even using custom modelines (like 2560x1920 on a 22 inch CRT) since like 2000-ish so nothing new to me here.You

You can generate modelines with cvt but in the case of the 31Hz mode I just pulled the 30hz one from EDID and calculated how much more bandwidth would be needed to go from 30 Hz -> 31 Hz which is the max refresh rate at 3840x2160. With logverbose 6 it will list the timings from EDID in the xorg.log so you can pull the modes from there.

---

### Post by renaud2 on 2013-08-02
Many thanks for the clarifications. Do you managed to get crisp fonts? Should I disable anti-aliasing or set the default font size? Everything is sooooo small on the desktrop, that looks a little fuzzy :-/

---

### Post by houkouonchi2 on 2013-08-02
Have you turned the sharpness down to 0 in the menu? For whatever reason they do that which literally makes text and other stuff look blurry (kills the crispness of an LCD). I don't know why it would be disabled but even going from 1 to 0 makes a big difference let alone the default value of 50.

If you haven't already turn the sharpness to 0 and see if things look better.

---

### Post by renaud2 on 2013-08-02
> **houkouonchi2 said:**
> Have you turned the sharpness down to 0 in the menu? For whatever reason they do that which literally makes text and other stuff look blurry (kills the crispness of an LCD). I don't know why it would be disabled but even going from 1 to 0 makes a big difference let alone the default value of 50.

If you haven't already turn the sharpness to 0 and see if things look better.


Again, you did it. You're a god send!

Many, many, many thanks for today, you made my day! :D

---

### Post by houkouonchi2 on 2013-08-02
And I meant to say I don't know why that feature would be 'enabled' not 'disabled' heh. Anyway if your not aware if you hit menu  and then hit 0 four times on the remote you can enter the service menu. From there you can turn down the backlight. I put mine at around 80 as the default (100 backlight setting) is way to high and you get deeper blacks this way where contrast/brightness settings don't help that much.

---

### Post by renaud2 on 2013-08-02
Wow! Impressive findings! I was struggling with the contrast/brightness stuff... =) This thread is becoming a gold mine for Seiki 4K owners!

---

### Post by renaud2 on 2013-08-02
Maybe nothing to do with the Seiki, but do you managed to get sounds over HDMI? Both internal and HDA Nivida HDMI are showing in pavucontrol, the vu-meter are moving (meaning that sounds is going through?) but no sounds on Seiki?

---

### Post by renaud2 on 2013-08-02
Maybe nothing to do with the Seiki, but do you managed to get sounds over HDMI? Both internal and HDA Nivida HDMI are showing in pavucontrol, the vu-meter **is** moving (meaning that sounds is going through?) but no sounds on Seiki?

---

### Post by houkouonchi2 on 2013-08-02
I am not a fan of audio over HDMI as I like to use my actual soundcard rather than spdif pass-through or whatever it does over HDMI. Even when I was driving it off my HTPC box I could never get HDMI audio working quite right and I just used the 1/8th in analog mini-jack instead.

Also some good news. After visiting seiki HQ today (as they hadn't answered my email in 2 weeks) I found out the 39 inch model should do 120Hz when they fix the issue with a new firmware so you might wanna add those high refresh rate 1920x1080/1280x720 modes for use for gaming (if you do at all) for when the firmware update comes out.

---

### Post by renaud2 on 2013-09-15
> **houkouonchi2 said:**
> I am not a fan of audio over HDMI as I like to use my actual soundcard rather than spdif pass-through or whatever it does over HDMI. Even when I was driving it off my HTPC box I could never get HDMI audio working quite right and I just used the 1/8th in analog mini-jack instead.

Just some update after a whole month using my Seiki :

- From time to time, I'm experiencing some glitches : the image start to "jump off" by 3 or 4 pixels, and then the resolution switch to 3840x2159 @ 31Hz ! So, the image is blurry, glitchy, and unusable. Powering off then on the screen multiple time will solve the problem most of the time. Any hint on that? I'd like to tweak my modelines, but I'm missing some informations to fill into [that generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")
- [s]The backlight settings from the hidden menu doesn't remember it's value between power cycle :mad: [/s] -> Got a [firmware update]("https://dl.dropboxusercontent.com/u/56081902/For%20SE39UY04%20%20With%20Backlight%20And%20color%20TEMP.%20-20130828.zip") fixing this!
- The HDMI audio is now working under Ubuntu 13.04 (using nvidia-325)

---

### Post by ivo-welch on 2013-09-21
GTX 650 Ti .   nvidia-310.44-0ubuntu2 driver.

this did not work for me (well, I am running the ubuntu-derived cinnamon mint olivia).  not sure why yet.  when I put this into my /usr/share/X11/xorg.conf.d , I am staring at a black screen and I need to pull the plug.  not fun.

is there a way to use xrandr to try this resolution temporarily?  I tried starting on the 

```
# xrandr --newmode "3840x2160_13.80" 144.25 3840 3944 4320 4800 2160 2163 2168 2180 -hsync +vsync
# xrandr --addmode HDMI-0 "3840x2160_13.80"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34

```

any ideas?

/iaw

---

### Post by renaud2 on 2013-09-22
> **ivo-welch said:**
> GTX 650 Ti . nvidia-310.44-0ubuntu2 driver. this did not work for me (well, I am running the ubuntu-derived cinnamon mint olivia). not sure why yet. when I put this into my /usr/share/X11/xorg.conf.d , I am staring at a black screen and I need to pull the plug. not fun.
Mine is a 650 Ti too, but I'm running the latest nvidia drivers from the swat team. Look at my monitor.conf on [my previous post]("http://ubuntuforums.org/showthread.php?t=2164924&p=12743339#post12743339"), and install the latest drivers.

---

### Post by ivo-welch on 2013-09-22
**Good News**:  there seem to be two repositories of newer X drivers for nvidia

# add-apt-repository ppa:ubuntu-x-swat/x-updates
# apt-get update && sudo apt-get install nvidia-current nvidia-settings
and
# add-apt-repository ppa: xorg-edgers
# apt-get install nvidia-319

(remove the space between ppa: and xorg-edgers.)

I tried both.  Cinnamon Mint Olivia runs without trouble on nvidia-325 (version 325.15-0ubntu1~xedgers~raring2).  for some reason 319 does not show up, even after installing.  but, presumably, later versions are better than earlier ones, so 325 should be ok.  one oddity---even though the driver manager reports I am using 325, it says "no proprietary drivers are in use."


**Bad News**: xrandr still refuses.  so, I will need to try the three-finger salute and pray that it won't come back in black.  this would be a lot more fun if one could use xrandr or a control-panel. :-(

After new-ing the mode, xrandr reports

```
# xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 860mm x 480mm
   1920x1080      59.9*+   50.0     24.0     30.0     30.0     25.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x720       59.9     50.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3  
   720x576        50.0     25.0  
   720x480        59.9     30.0  
   640x480        75.0     72.8     59.9  
  3840x2160_13.80 (0x2c5)  144.2MHz
        h: width  3840 start 3944 end 4320 total 4800 skew    0 clock   30.1KHz
        v: height 2160 start 2163 end 2168 total 2180           clock   13.8Hz



```

--addmode still fails. 
 
Good News:  Your xorg configuration file worked.  It is beautiful now.  The mouse cursor feels a bit slower now, but normal desktop OS operation seems pretty similar.  now, I come from a 30" DELL 3008WFP monitor with 2560x1600 resolution.  the big deal---matte display, IPS display, 60Hz.  frankly, only the lack of matte is annoying.  I couldn't tell if the display was TN or IPS.  the resolution of the seiki is higher and the pixels seem sharp.

/iaw

---

### Post by ivo-welch on 2013-09-23
next questions:

* I only use the seiki as a monitor---probably like most of you.  is there a way to get it to power down immediately upon suspend?  right now, when I suspend, unlike my computer monitors, it stays on blue for quite a while.

* is there a way to turn off the blue and red light?  right now, I am using black masking tape.

* what is the current software version

and one note:

+ the hdmi sound audio output worked immediately.  nice.  it shows up in the panel as an option and selecting it did the job.

/iaw

---

### Post by renaud2 on 2013-09-23
> **ivo-welch said:**
> 
* what is the current software version


I got a software update about the "backlight bug" -> see my [previous post]("http://ubuntuforums.org/showthread.php?t=2164924&p=12789234#post12789234"). 

About auto-switching off, I have no need of that since I'm using the "power-save" feature from my UPS :)  Do you looked at the hidden menu? (press "menu", and then press 4 times the "0" key)

---

### Post by fastfourier2 on 2014-02-03
Hey guys.  My Seiki 39" came in on Friday.  I've read through this thread, and it's solid gold.  But I can't get some things working.  Hopefully you super pros can help me find my issue.

First, I'm running 13.10 with NVidia 331.20.  I have a GTX680.

My symptoms : 

"HDMI1 : 3840x2160@30Hz" properly displays on the screen, but the screen is all black.  The machine is live and responsive.  I can SSH in.  I can CTRL+ALT+F1 and drop to a shell.  I can stop and start lightdm.  But when I start lightdm, it just goes to a blank screen.

I've tried no xorg.conf file and just a /usr/share/X11/xorg.conf.d/10-monitors.conf file.  Same results.

I've tried an xorg file generated with X -configure.  (And then modifying it)  Same result.

I've tried an nvidia-xconfig generated xorg.conf file and then modified it.  Same result.

I've looked through Xorg.0.log but there are no errors.  X apparently thinks everything is fine.  :(

Lastly, three of the Mode Validation Overrides were listed in Xorg.0.log as being invalid.  Specifically, it hated "[COLOR=#000000][FONT=Ubuntu Mono]AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]NoDFPNativeResolutionCheck"[/FONT][/COLOR]

Apparently those modes don't exist anymore, as per the warnings in Xorg.0.log.  I used your modelines, and I've also attempted to generate my own modelines using cvt. 

Here is my xorg.conf.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 331.20  (buildmeister@swio-display-x86-rhel47-05)  Wed Oct 30 18:20:53 PDT 2013


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Seiki"
    ModelName      "SEK039-4k"
    Modeline "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync
    Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option "ModeValidation" "NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes "3840x2160" "1920x1080"
    EndSubSection
EndSection

```

Is there any chance that this newer driver is breaking some of those overrides?  Or is there maybe an issue being on 13.10?  Or have I just missed a step?  Thanks guys.

---

### Post by fastfourier2 on 2014-02-03
Also, one more piece of information.  If I remove all xorg.conf and such, everything is just fine, but at 1920x1080.  As soon as I go to the higher resolution via xorg.conf, it fails.

---

### Post by houkouonchi2 on 2014-02-03
> **fastfourier2 said:**
> Hey guys.  My Seiki 39" came in on Friday.  I've read through this thread, and it's solid gold.  But I can't get some things working.  Hopefully you super pros can help me find my issue.

First, I'm running 13.10 with NVidia 331.20.  I have a GTX680.

My symptoms : 

"HDMI1 : 3840x2160@30Hz" properly displays on the screen, but the screen is all black.  The machine is live and responsive.  I can SSH in.  I can CTRL+ALT+F1 and drop to a shell.  I can stop and start lightdm.  But when I start lightdm, it just goes to a blank screen.

I've tried no xorg.conf file and just a /usr/share/X11/xorg.conf.d/10-monitors.conf file.  Same results.

I've tried an xorg file generated with X -configure.  (And then modifying it)  Same result.

I've tried an nvidia-xconfig generated xorg.conf file and then modified it.  Same result.

I've looked through Xorg.0.log but there are no errors.  X apparently thinks everything is fine.  :(

Lastly, three of the Mode Validation Overrides were listed in Xorg.0.log as being invalid.  Specifically, it hated "[COLOR=#000000][FONT=Ubuntu Mono]AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]NoDFPNativeResolutionCheck"[/FONT][/COLOR]

Apparently those modes don't exist anymore, as per the warnings in Xorg.0.log.  I used your modelines, and I've also attempted to generate my own modelines using cvt. 

Here is my xorg.conf.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 331.20  (buildmeister@swio-display-x86-rhel47-05)  Wed Oct 30 18:20:53 PDT 2013


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Seiki"
    ModelName      "SEK039-4k"
    Modeline "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync
    Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option "ModeValidation" "NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes "3840x2160" "1920x1080"
    EndSubSection
EndSection

```

Is there any chance that this newer driver is breaking some of those overrides?  Or is there maybe an issue being on 13.10?  Or have I just missed a step?  Thanks guys.


Not sure if it matters but the mode validation stuff is usually in the device section (not screen). Anyway I am not sure where you got that modeline for 30Hz:

Modeline "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync

That is 2 Mhz under full HDMI 1.4 spec. The actual seiki modeline is only 300 Mhz. Although since the mode has _30.00 and your not using _30.00 when your loading it from the mode option under screen. Here is a the seiki 30Hz mode and 120Hz 1080p:


Modeline "3840x2160" 296.70 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync
Modeline "1920x1080" 297 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync

I think to help anymore I would try running from command line:

X -logverbose 6 :2


And then upload your /var/log/Xorg.2.log

---

### Post by fastfourier2 on 2014-02-03
FYI, I got it up and running with nvidia-319.  I went back and purged 331, then installed 319.

Unfortunately, this bodes poorly for anyone who upgrades.  Something has changed.

---

### Post by fastfourier2 on 2014-02-03
I had copied and pasted your modelines previously, and was experimenting with creating my own via cvt.  i.e.

```

me@fourier:X11 $ cvt 3840 2160 30
# 3840x2160 29.98 Hz (CVT) hsync: 65.96 kHz; pclk: 338.75 MHz
Modeline "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync

```

That's where it was generated from.  I had identical results with both modelines.  Right now, I'm running what I just posted, and with the 319 driver, and no other changes, it seems to be working. I don't know why.

---

### Post by fastfourier2 on 2014-05-29
FYI, the need for an xorg.conf file to set the modelines for the Seiki is gone in nvidia-337 which is currently available from xorg-edgers.

---

### Post by maxbb on 2014-07-08
Can anyone tell me if SE39UY04 is identical to SE50UY04 (the 50 inch variety) as far as interfacing with Linux and Nvidia GPU is concerned?

I haven't found any reports of people getting SE50UY04 to work with Linux and Nvidia at 4K and 30Hz. In fact, I found a blog post by a programming team saying they tried very hard and failed to do it: [http://tiamat.tsotech.com/4k-is-for-programmers-redux](http://tiamat.tsotech.com/4k-is-for-programmers-redux) which leads me to suspect that it must be effectively impossible.

---

### Post by pleasehelpme2 on 2014-10-07
Hi there,

could anyone help me with my NUC, got an LG 4K tv and struggling to get it running in 4K mode! get the following output

nuc@nuc:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1280x1024      60.0  
   1360x768       60.0  
   1152x864       60.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9     59.9  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
nuc@nuc:~$ xrandr --newmode "3840x2160" 307.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync
nuc@nuc:~$ xrandr --addmode HDMI1 3840x2160
nuc@nuc:~$ xrandr --output HDMI1 --mode "3840x2160"
xrandr: Configure crtc 0 failed
nuc@nuc:~$

---

