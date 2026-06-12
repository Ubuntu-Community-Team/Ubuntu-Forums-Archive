---
title: "Relsolution problem"
date: 2011-06-20
forum: Multimedia Software
---

### Post by coolcaseley67 on 2011-06-20
Hello All,


I am running Ubuntu 10.10 with the NVIDIA Driver 96 on my video card is GeForce4 MX 440  . I have brought a new monitor (   View Sonic VA1913w  ) but i can not find the right  resolution which is 1366 times 768. is there a way i could add it ??

---

### Post by BicyclerBoy on 2011-06-20
What is the video h/w model ?
Is there a reason for running a really old nvidia driver ?

How is your newly bought monitor connected ? DVI is preferred.

It is easier to get the monitor correctly identified by EDID than it is to add custom modes or force modes..so you should try that first..

You could post your
/var/log/Xorg.0.log
file as an attachment to help answer some of the above..

---

### Post by coolcaseley67 on 2011-06-20
Hello BicyclerBoy,

sorry missed that part out would of made......  anyway my video card is a GeForce4 MX 440 which is only supported by the Nvidia 96 :( 

I've attached the log , it's not DVI model is  View Sonic VA1913w 

[SIZE=3]_**What is EDID ?????**_[/SIZE]

---

### Post by BicyclerBoy on 2011-06-20
EDID is the data that identifies the display device & exposes its capabilities.

The VGA standard includes I2C interface (DDC) that allows video card to probe the displays eeprom for model & video mode info (even if powered down).

DVI does the same.
HDMI achieves something similar & for audio ELD only when power is on.

You are right about the driver version & MX440..

From your log file:
Monitor is identified & no video mode is requested..auto is selected & driver uses 1024x768..
so all is okay..

This is a TV styled display , any 19" PC display would have at least 1440x900.
It is possible the VGA input will not accept native resolutions.--I have checked the specs, VGA should work.

I would not recommend buying any DFP monitor without DVI/displayport/hdmi.

You are trying to use the nvidia-settings program to set the resolution ?
Do you have the option of 1368x768 ?


The video mode 1366x768 is not a std mode..   1368x768 is std mode.. 1366 is not divisible by eight.
The modeline calculator "cvt" will not calculate a 1366 modeline...

from cvt calculator , add these sections to /etc/X11/xorg.conf file by including the existing..
```

Section   "Modes"
          Identifier       "CustomModes"
          Modeline     "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section    "Monitor"
          Identifier         "Monitor0"
          VendorName       "Viewsonic"
          ModelName        "VA ----"
          UseModes           "CustomModes"
          Option             "DPMS"
EndSection

Section Screen 
          Identifier         "Screen0"
          Device             "Device0"
          Monitor            "Monitor0"   
# add this 
      SubSection        "Display"
                   Depth        24
           Modes          "1368x768_60.00"
      EndSubSection
EndSection

```
from XFree86 modeline calculator
gives 1360 or 1368 .. will not accept 1366

If you need to force a 1366x768 modeline it could be possible, it depends on the driver accepting the numbers.

---

### Post by coolcaseley67 on 2011-06-21
Hello BicyclerBoy[B],

[/B]Thanks for your help so far **!  **It does not come up in the Nividia settings but in the monitor settings if i apply it from the monitor settings and reboot i get an error saying the X sever does not support the mode. 


[SIZE=3]**I will make the changes to the config and report back ! ( Yes i will need to ****force**[/SIZE][SIZE=3]** it **[/SIZE])

---

### Post by coolcaseley67 on 2011-06-21
Hello BicyclerBoy,

The config file was blank so I ran sudo Nvidia-xconfig once i'd rebooted  the gnome Panel had gone so remove nvidia 96 and this fixed this. I removed everything the nvidia-xconfig command put and add what you said but i get the following error : 


> 2011
[    24.131] (==) Using config file: "/etc/X11/xorg.conf"
[    24.131] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.131] Parse error on line 14 of section Monitor in file /etc/X11/xorg.conf
    The Section keyword requires a quoted string to follow it.
[    24.139] (EE) Problem parsing the config file
[    24.139] (EE) Error parsing the config file
[    24.139] 
Fatal server error:
[    24.139] no screens found
[    24.139] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    24.139] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    24.139] 
[    24.139]  ddxSigGiveUp: Closing log



**[SIZE=3]Help!????[/SIZE]**

---

### Post by coolcaseley67 on 2011-06-21
[SIZE=2]hello Just an update ,

I reinstalled the Nvidia driver  and ran sudo Nvidia-xconfig then made the changes you told me to do but i reboot only to be hit with a terminal screen asking me to log in . 


Any ideas ???


[/SIZE]

---

### Post by BicyclerBoy on 2011-06-21
Whoops..

The error reports that there is "an unquoted string" on line 14 of xorg.conf.
The screen section should have started 
Section "Screen"

i.e. "Screen" keyword must be quoted...

You can do a console login ...
enter username & password when prompted..

you could make a backup of xorg.conf & then delete it..
re-run nvidia-xconfig

Or..
sudo nano /etc/X11/xorg.conf

edit line 14...& add the missing ("").


Maybe you could post your xorg.conf file so I can try to add the extra sections..

---

### Post by coolcaseley67 on 2011-06-21
Hello ,

I have tried logging in but it would not let me so am in fail-safe mode below is my Config i could not see the error :


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Wed Oct 27 19:20:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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

Section   "Modes"
          Identifier       "CustomModes"
          Modeline     "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "VA ----"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    UseModes           "CustomModes"
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
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1368x768_60.00"
    EndSubSection
EndSection

``` 

[SIZE=3]**Thank-you for your help !!!**[/SIZE]

---

### Post by BicyclerBoy on 2011-06-21
May be the formatting/whitespace is messing up the parser..
Don't using any <TAB> characters...just spaces & fixed typeface.

The auto-formatting on this forum is like using MS Word..
I'd **swear** this forum runs on windows..

```

Section                  "Device"  
    Identifier           "Device0"
    Driver               "nvidia"     
    VendorName     "NVIDIA Corporation"     
    Screen             0
EndSection

```

I have added the "Screen    0"
You should fix the Viewsonic model string..I didn't know what it was in your existing xorg.conf.

If all fails..
delete your /etc/X11/xorg.conf file
logout/login if running GUI
then run
sudo nvidia-xconfig
to re-generate a new fresh xorg.conf

---

### Post by coolcaseley67 on 2011-06-22
[SIZE=2]Hello 

ok will try that FYI the error has changed now : 

```
[    26.540] (--) NVIDIA(0):     option
[    26.540] (--) Depth 24 pixmap format is 32 bpp
[    26.543] (II) NVIDIA(0): Initialized GART.
[    26.563] (EE) NVIDIA(0): Failed to allocate/map the primary surface!
[    26.565] 
Fatal server error:
[    26.565] AddScreen/ScreenInit failed for driver 0
```


**I will make the changes and report back !**[/SIZE]

---

### Post by BicyclerBoy on 2011-06-22
Not making any progress are we..
My problem is that I have never used a video driver version or card so old.
So we could be missing some subtle differences to the current driver.

That error can mean the virtual desktop is to big for the amount of ram.
My guess is there an error in your xorg.conf file...

Try adding this to the "Device" section
```

Option       "NvAGP" "2"
BusID        "1:0:0"

```
But why this would be necessary now when the driver has been working is a question ...

Found this...
**  NVIDIA Legacy driver 96.43.19 may require nopat option **

 If X-server fails to start or can't set some resolution on legacy cards and you see the following message: 
 NVIDIA(0): Failed to allocate/map the primary surface!        
try adding **nopat** kernel option (in boot options or in grub menu) 

After all that...
Can you post the xorg.conf & the Xorg.0.log file as attachments.
Please post as attachment, don't let the forum mangle the file.

The log file needs to be from the failed boot if you can..

Maybe the problem is the color depth at the higher resolution...
Maybe you could try Depth 16

---

### Post by coolcaseley67 on 2011-06-22
[SIZE=2]Hello ,

No fixed one issue and made a second ! right I've made changes to the Xconfig and the Grub config. I've done some googling : 

[http://forums.nvidia.com/index.php?showtopic=169294](http://forums.nvidia.com/index.php?showtopic=169294)

It raised on that link ! ill reboot and update this post with everything  ! 

Once again Thanks for your help ! [/SIZE]

---

### Post by coolcaseley67 on 2011-06-22
[SIZE=2]Hello , 

The changes i made fixed the back log-in screen  but once i log in its still the wrong size with no Gnome panel from the X.org log : 

```
[    86.553] (WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    86.553] (WW) NVIDIA(0):     will be used as the requested mode.
[    86.553] (WW) NVIDIA(0): 
[    86.553] (II) NVIDIA(0): Validated modes:
[    86.553] (II) NVIDIA(0):     "nvidia-auto-select"
[    86.554] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    86.554] (--) NVIDIA(0): DPI set to (63, 84); computed from "UseEdidDpi" 
```

_**I how i stop the driver from Checking which modes to use ??? ****I've attached the log and the config **_[/SIZE]

---

### Post by BicyclerBoy on 2011-06-22
The driver seems to be ignoring the screen section completely..
The xorg.conf layout is as per the Xorg defining docs X11R6 & is as I have used with nvidia 173 to 260.
Maybe the earlier nvidia driver did not follow the standard or I have not understood.

There is a shortcut syntax for sticking the modeline directly into "Monitor" section.
Maybe that will work...just copy the modeline (one line) into the monitor section.

From re-reading this thread...
You can not use the Gnome Display preferences with the nvidia X server..
You must only use the nvidia-settings programs, the Gnome tools do not correctly recognize the video modes/refresh rates.

---

### Post by coolcaseley67 on 2011-06-23
[SIZE="2"]Hello ,

I re-ran Nvidia-xconfig and added ```
Modeline     "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection
``` in to the Monitor part. Then added 
```
Option       "NvAGP" "2"
BusID        "1:0:0"
```

Back aswell in the xconfig but rebooted and am back to the black log in screen 


any ideas ??[/SIZE]

---

### Post by BicyclerBoy on 2011-06-23
I think the problem is in the monitor EDID reported..

I think we should try to disable the EDID mode validation bit by bit..
You already have the horiz & vert freq entries for the monitor.

You can create a new section:
Section "ServerFlags"
EndSection
```
[FONT=monospace]
[/FONT]      Option "ModeValidation" "NoEdidModes"[FONT=Verdana]
[/FONT]    Option "UseEDIDFreqs" "FALSE"
      Option "UseEDIDDpi" "FALSE"

```[FONT=Verdana]  
You could try adding these above entries **one at a time** starting from the top one

The last king hit is this...
[/FONT]```

    Option "UseEDID" "FALSE"

```

Failing this buy a PC monitor with DVI & VGA.

---

### Post by coolcaseley67 on 2011-06-24
[SIZE=3]Hello 

Sorry to the time to post back ! I had to clean my pc and fix the internet ! 


Right I will try that , I've attach a newer log with more errors ): it say it can not find the screen ! GRRR Thanks for all your help !![/SIZE]

---

### Post by BicyclerBoy on 2011-06-24
The shortcut modeline entry has to go into the "Monitor" section not the Screen section.

The "Monitor" section can have the modeline (all the list pixel count numbers)
ModeLine     "1368x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync

The "Screen" section must have the modeline "Name"
( in SubSection "Display")
Modes      "1368x768_60.00"

---

### Post by coolcaseley67 on 2011-06-25
[SIZE=2]Hello

The driver appears to carry on use EDID  ,i've been through the sever flags options 

from the x org log 

```
[    25.545] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    25.545] (WW) NVIDIA(0): 
[    25.545] (WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    25.545] (WW) NVIDIA(0):     will be used as the requested mode.
[    25.545] (WW) NVIDIA(0): 
[    25.545] (II) NVIDIA(0): Validated modes:
[    25.545] (II) NVIDIA(0):     "nvidia-auto-select"
[    25.545] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    25.545] (--) NVIDIA(0): DPI set to (63, 84); computed from "UseEdidDpi" X config
[    25.545] (--) NVIDIA(0):     option
[    25.546] (--) Depth 24 pixmap format is 32 bpp
[    25.548] (II) NVIDIA(0): Initialized GART.
[    25.764] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    25.907] (II) Loading extension NV-GLX
```[/SIZE]

---

### Post by BicyclerBoy on 2011-06-25
How bizarre..
It is like the file is ignored..

Can you check that the xorg.conf is named exactly.
"/etc/X11/xorg.conf"
Linux is case sensitive & very pedantic.

File ownership & permissions gotten messed up ?

Maybe running nvidia-xconfig as sudo is a problem ?

Don't have a 
/etc/X11/XF86Config
file do you ?

---

### Post by coolcaseley67 on 2011-06-27
[SIZE=3]Hello 

Yep its named as below , i don't have "XF86Config" 

Any Ideas [/SIZE]???

---

### Post by BicyclerBoy on 2011-06-27
Need to find the actual error/warning messages.

If you startup gdm X server with logverbose >=6 then nvidia driver prints out detailed info on the mode validation process.

startx -- -verbose 5 -logverbose 6
You may be able to run this after stopping the gdm, I have never tried doing this.

Otherwise, I guess you have to edit the script that launches X server somehow.
Then switch to console ..
[sudo] service gdm stop
[sudo] service gdm start

The /var/log/Xorg.0.log will probably be significantly longer..
cat /var/log/Xorg.0.log | grep (WW)

Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

---

### Post by coolcaseley67 on 2011-06-29
[SIZE=3]hello 


sorry for slowness in getting back ! Cool i will try it and report back !!!
[/SIZE]

---

### Post by BicyclerBoy on 2011-06-29
As an alternative to the startx verbose ...

Could add this to /etc/X11/xorg.conf
Option "ModeDebug" "TRUE"
to get more info into the /var/log/Xorg.0.log

But I guess it may not work with the old driver & will not work if the file is ignored..

---

### Post by tjones00 on 2011-06-30
> **BicyclerBoy said:**
> How bizarre..
It is like the file is ignored..

Can you check that the xorg.conf is named exactly.
"/etc/X11/xorg.conf"
Linux is case sensitive & very pedantic.

File ownership & permissions gotten messed up ?

Maybe running nvidia-xconfig as sudo is a problem ?

Don't have a 
/etc/X11/XF86Config
file do you ?

That is really odd.

From the user's Xorg.0.log

```
[    25.000] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 20 22:14:12 2011
[    25.001] (==) Using config file: "/etc/X11/xorg.conf"
[    25.001] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
```

Try using the /usr/share/X11/xorg.conf.d/ partial xorg.conf directory as  well with the single section containing the modeline? eg.  /usr/share/X11/xorg.conf.d/modeline.conf

Maybe kms is on? I know when kms is enabled the system typically ignores  /etc/X11/xorg.conf and it will still check /usr/share/X11/xorg.conf.d/  for partial *.confs.  (only /usr/share/X11/xorg.conf.d/ will be declared  in the log)

However, since /etc/X11/xorg.conf is declared in the log it is suggesting everything is setup properly to work with nvidia.ko.

---

### Post by coolcaseley67 on 2011-07-01
[SIZE=2]Hello ,


BicyclerBoy[/SIZE]: I tried running [sudo] service gdm stop but it came up with an error. I will try the other steps and report.


I think its any issue with the NVIDIA driver am going to try find way to speak to NVIDIA !

---

### Post by coolcaseley67 on 2011-07-01
[SIZE=3]Hello [/SIZE],

[SIZE=3]I've made a post on the NVIDIA Linux forums asking help: [http://www.nvnews.net/vbulletin/showthread.php?p=2451369#post2451369](http://www.nvnews.net/vbulletin/showthread.php?p=2451369#post2451369)[/SIZE]


[SIZE=3] Where would i add Option "ModeDebug" "TRUE" in the config file ?[/SIZE]
[SIZE=3]
Thank you ![/SIZE]

---

### Post by BicyclerBoy on 2011-07-01
(Unfortunately) A lot of the xorg.conf options can go into any section..

I would use a "ServerFlags" section..because this seems logical & tidy.

The only criticism of nVidia drivers readme/docs is that they are very vague about sections in xorg.conf.

There has been some suggestion (inc. prev. post) that Xorg is now using a slightly different configuration file or folders.
/etc/X11/xorg.conf.d/*.conf

Haven't found anything that states the xorg.conf file is ignored..

You are still using Xorg 1.09. Don't let that upgrade to 1.10...else you'll have even more problems.
Did you see this thread about Xorg 1.10 breaking the old drivers.
[http://www.nvnews.net/vbulletin/showthread.php?t=162140](http://www.nvnews.net/vbulletin/showthread.php?t=162140)

---

### Post by coolcaseley67 on 2011-07-02
[SIZE=3]Hello ,

I've been doing some diging and a found this : [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html)

I can turn off mode validation using one of these arguments with option mode  validation ?


[/SIZE][SIZE=3][FONT=Arial][/FONT][/SIZE]

---

### Post by coolcaseley67 on 2011-07-02
[SIZE=3]Hello ,

Please find the X.org log with full info !

Thank-you for your help so far !
[/SIZE]

---

### Post by BicyclerBoy on 2011-07-02
Does not really reveal anything new except the memory allocation error.
I do not know what to make of it..

The nvidia driver version you have 96.43.19 was recently updated for Xorg 1.8 1.9..which you are running.

Maybe you have to go back to 10.04 LTS as it uses Xorg 1.7.6...
The std legacy driver in 10.04 LTS is still 96.43.17.
Maybe 10.10 & legacy driver do not work..

Looks like you may not be alone..
[http://ubuntuforums.org/showthread.php?t=1653498](http://ubuntuforums.org/showthread.php?t=1653498)

---

### Post by coolcaseley67 on 2011-07-04
[SIZE=3]Hello ,


OK thanks anyway ! I plan to buy a new laptop this year anyway this PC may go in the bin  its a bit old ! I will try Ubuntu 10.04[/SIZE]

---

### Post by coolcaseley67 on 2011-07-08
[SIZE="3"]Hello ,


I've changed over to ubuntu 10.04 and installed the driver v96.43.17 and made the changes to the x.sever confg file as before.

It works !!!! but the gnome panel does not load once i change the screen size ! any ideas ??? [/SIZE]

---

### Post by BicyclerBoy on 2011-07-08
When you say gnome panel not loading, do you mean the whole desktop does not load or that the desktop does not get populated with menus & widgets ?

Does the screen "pan & scan" with the mouse at the the screen margins ?
i.e. is the virtual screen bigger than physical ?

Do any shortcut keystrokes work ?

---

### Post by coolcaseley67 on 2011-07-09
[SIZE=3]Hello ,


It's working now i have to wait with clicking or type anything for a few secs ! 

[/SIZE]

---

### Post by coolcaseley67 on 2011-07-20
[SIZE=3]Hello ,


I've just tried to turn on Visual Effects on Normal. It go's gray then go's back to none. 

In the NVIDIA X Server Settings Antialiasing is turned off .


Any ideas ? I've attached my Log the Driver appears to be using 2d only 

Thanks ! [/SIZE]

---

