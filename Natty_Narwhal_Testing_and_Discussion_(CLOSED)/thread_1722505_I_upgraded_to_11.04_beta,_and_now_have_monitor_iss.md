---
title: "I upgraded to 11.04 beta, and now have monitor issues."
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mindswap1 on 2011-04-05
So I updated to 11.04 beta, and well I'm confused. Now when I turn on my computer I get a message that says not optimal resolution, And tells me that I should have a resolution of 1360x768. So I went to the monitor program in Ubuntu, and the resolution was fine, but I was only allowed to have 52 hz instead of the needed 60 hz. And it also says monitor not identified. So could i fix this?

---

### Post by 23dornot23d on 2011-04-05
What does it give you if you run this in a termnal ....

xrandr --verbose

---

### Post by wojox on 2011-04-05
Graphics driver?

---

### Post by Iowan on 2011-04-05
Moved to Natty Narwhal Testing and Discussion

---

### Post by Mindswap1 on 2011-04-05
i got the follow after typing that in. 
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 (0x1b6) normal (normal) 0mm x 0mm
    Identifier: 0x1b3
    Timestamp:  32681
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1360x768 (0x1b4)   52.2MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   38.4KHz
        v: height  768 start    0 end    0 total  768           clock   50.0Hz
  1360x768 (0x1b5)   53.3MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   39.2KHz
        v: height  768 start    0 end    0 total  768           clock   51.0Hz
  1360x768 (0x1b6)   54.3MHz *current
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   39.9KHz
        v: height  768 start    0 end    0 total  768           clock   52.0Hz
  1024x768 (0x1b7)   41.7MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   40.7KHz
        v: height  768 start    0 end    0 total  768           clock   53.0Hz
  1024x768 (0x1b8)   42.5MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   41.5KHz
        v: height  768 start    0 end    0 total  768           clock   54.0Hz
  1024x768 (0x1b9)   43.3MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   42.2KHz
        v: height  768 start    0 end    0 total  768           clock   55.0Hz
  832x624 (0x1ba)   29.1MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   34.9KHz
        v: height  624 start    0 end    0 total  624           clock   56.0Hz
  800x600 (0x1bb)   27.4MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   34.2KHz
        v: height  600 start    0 end    0 total  600           clock   57.0Hz
  800x600 (0x1bc)   27.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   34.8KHz
        v: height  600 start    0 end    0 total  600           clock   58.0Hz
  800x600 (0x1bd)   28.3MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   35.4KHz
        v: height  600 start    0 end    0 total  600           clock   59.0Hz
  800x600 (0x1be)   28.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  720x450 (0x1bf)   19.8MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   27.4KHz
        v: height  450 start    0 end    0 total  450           clock   61.0Hz
  680x384 (0x1c0)   16.2MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   23.8KHz
        v: height  384 start    0 end    0 total  384           clock   62.0Hz
  680x384 (0x1c1)   16.5MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   24.2KHz
        v: height  384 start    0 end    0 total  384           clock   63.0Hz
  640x480 (0x1c2)   19.7MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   30.7KHz
        v: height  480 start    0 end    0 total  480           clock   64.0Hz
  640x480 (0x1c3)   20.0MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   31.2KHz
        v: height  480 start    0 end    0 total  480           clock   65.0Hz
  640x480 (0x1c4)   20.3MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   31.7KHz
        v: height  480 start    0 end    0 total  480           clock   66.0Hz
  640x480 (0x1c5)   20.6MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   32.2KHz
        v: height  480 start    0 end    0 total  480           clock   67.0Hz
  640x480 (0x1c6)   20.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   32.6KHz
        v: height  480 start    0 end    0 total  480           clock   68.0Hz
  640x480 (0x1c7)   21.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   33.1KHz
        v: height  480 start    0 end    0 total  480           clock   69.0Hz
  576x432 (0x1c8)   17.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   30.2KHz
        v: height  432 start    0 end    0 total  432           clock   70.0Hz
  512x384 (0x1c9)   14.0MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   27.3KHz
        v: height  384 start    0 end    0 total  384           clock   71.0Hz
  512x384 (0x1ca)   14.2MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   27.6KHz
        v: height  384 start    0 end    0 total  384           clock   72.0Hz
  512x384 (0x1cb)   14.4MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   28.0KHz
        v: height  384 start    0 end    0 total  384           clock   73.0Hz
  416x312 (0x1cc)    9.6MHz
        h: width   416 start    0 end    0 total  416 skew    0 clock   23.1KHz
        v: height  312 start    0 end    0 total  312           clock   74.0Hz
  400x300 (0x1cd)    9.0MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   22.5KHz
        v: height  300 start    0 end    0 total  300           clock   75.0Hz
  400x300 (0x1ce)    9.1MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   22.8KHz
        v: height  300 start    0 end    0 total  300           clock   76.0Hz
  400x300 (0x1cf)    9.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   23.1KHz
        v: height  300 start    0 end    0 total  300           clock   77.0Hz
  400x300 (0x1d0)    9.4MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   23.4KHz
        v: height  300 start    0 end    0 total  300           clock   78.0Hz
  320x240 (0x1d1)    6.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.0KHz
        v: height  240 start    0 end    0 total  240           clock   79.0Hz
  320x240 (0x1d2)    6.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.2KHz
        v: height  240 start    0 end    0 total  240           clock   80.0Hz
  320x240 (0x1d3)    6.2MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.4KHz
        v: height  240 start    0 end    0 total  240           clock   81.0Hz

```

and my graphics driver is NVIDIA GeForce 6150 SE Graphics, and I can  using the Proprietary NVIDIA accelerated graphics driver version  current. 
And thank you iowan for moving the post ^.^

---

### Post by 23dornot23d on 2011-04-06
What monitor is it that you are using .... and what type of connection do you have to it .... ?

Does it run at 60hz at that resolution on another system .... ?

sorry for the questions just want to be clear that it can do this .....

> 
I  did solve the problem, though not in the way I would like.  It seems  that Xorg does not do well detecting and using available resolution  modes over an analog VGA connector.  My video card has DVI out and I was  using a DVI-VGA adapter.  When I switched to a DVI-HDMI connector it  came right up with plenty of options (including the 1360x768@60Hz)
This is a quote from a thread I read ....... just if you wonder why I ask about the type of connection that you have.

[]("http://ubuntuforums.org/xrandr%20resolution%20nvidia%20of%201360x768%2060%20hz")

---

### Post by Mindswap1 on 2011-04-06
Thanks So Much For replying [23dornot23d]("http://ubuntuforums.org/member.php?u=953253"). Well when I was on 10.10 it did work at that resolution with 60 Hz, but now that I updated to Unity it doesn't have that option. And I'm pretty sure I have a vga not hdmi cable, but idk how to check. So I guess i'm stuck with the problem, but I guess at least the computer works ^.^. The only down side is that it takes a little longer to boot up cuz of the optimal resolution message, Thanks a bunch! :)

---

### Post by cariboo on 2011-04-06
I have one system that I need an /etc/X11/xorg.conf file inorder to get acceptable resolution on a monitor with a broken EDID. Have you tried creating a new xorg.conf file by opening a terminal and running:

```
nvidia-xconfig
```

If your monitor is a crt you will have to change the Horizontal and vertical refresh rates to the manufacturers specifications, then reboot to see if the problem is solved.

---

### Post by Mindswap1 on 2011-04-06
Hey Cariboo907 I put the command in and got the following 
```



WARNING: Unable to locate/open X configuration file.


ERROR: Unable to write to directory '/etc/X11'.
```And i dont have a crt monitor.

---

### Post by cariboo on 2011-04-06
I assumed you knew to use sudo to run the command.

---

### Post by 23dornot23d on 2011-04-07
> 
Well when I was on 10.10 it did work at that resolution with 60 Hz


If it ran ok before :- 

Then follow as Cariboo907 says ..... 

**sudo nvidia-xconfig**

This is the right place to get this solved  - as the people here know what all the latest changes are ...... and how they are affecting their own systems .......

---

### Post by Mindswap1 on 2011-04-07
I'm really sorry I can't believe it slipped my mind here is the out put with sudo. 
```

 sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

---

### Post by 23dornot23d on 2011-04-07
You have to reboot to see if it worked ok  ...... and do xrandr --verbose again to see if the screen options have changed.

I hope you have the option now.

---

### Post by Mindswap1 on 2011-04-07
sorry but I still don't seem to have the option for it. Here is what i got. 

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 (0x1b4) normal (normal) 0mm x 0mm
    Identifier: 0x1b3
    Timestamp:  30107
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1360x768 (0x1b4)   52.2MHz *current
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   38.4KHz
        v: height  768 start    0 end    0 total  768           clock   50.0Hz
  1360x768 (0x1b5)   53.3MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   39.2KHz
        v: height  768 start    0 end    0 total  768           clock   51.0Hz
  1360x768 (0x1b6)   54.3MHz
        h: width  1360 start    0 end    0 total 1360 skew    0 clock   39.9KHz
        v: height  768 start    0 end    0 total  768           clock   52.0Hz
  1024x768 (0x1b7)   41.7MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   40.7KHz
        v: height  768 start    0 end    0 total  768           clock   53.0Hz
  1024x768 (0x1b8)   42.5MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   41.5KHz
        v: height  768 start    0 end    0 total  768           clock   54.0Hz
  1024x768 (0x1b9)   43.3MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   42.2KHz
        v: height  768 start    0 end    0 total  768           clock   55.0Hz
  832x624 (0x1ba)   29.1MHz
        h: width   832 start    0 end    0 total  832 skew    0 clock   34.9KHz
        v: height  624 start    0 end    0 total  624           clock   56.0Hz
  800x600 (0x1bb)   27.4MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   34.2KHz
        v: height  600 start    0 end    0 total  600           clock   57.0Hz
  800x600 (0x1bc)   27.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   34.8KHz
        v: height  600 start    0 end    0 total  600           clock   58.0Hz
  800x600 (0x1bd)   28.3MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   35.4KHz
        v: height  600 start    0 end    0 total  600           clock   59.0Hz
  800x600 (0x1be)   28.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  720x450 (0x1bf)   19.8MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   27.4KHz
        v: height  450 start    0 end    0 total  450           clock   61.0Hz
  680x384 (0x1c0)   16.2MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   23.8KHz
        v: height  384 start    0 end    0 total  384           clock   62.0Hz
  680x384 (0x1c1)   16.5MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   24.2KHz
        v: height  384 start    0 end    0 total  384           clock   63.0Hz
  640x480 (0x1c2)   19.7MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   30.7KHz
        v: height  480 start    0 end    0 total  480           clock   64.0Hz
  640x480 (0x1c3)   20.0MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   31.2KHz
        v: height  480 start    0 end    0 total  480           clock   65.0Hz
  640x480 (0x1c4)   20.3MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   31.7KHz
        v: height  480 start    0 end    0 total  480           clock   66.0Hz
  640x480 (0x1c5)   20.6MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   32.2KHz
        v: height  480 start    0 end    0 total  480           clock   67.0Hz
  640x480 (0x1c6)   20.9MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   32.6KHz
        v: height  480 start    0 end    0 total  480           clock   68.0Hz
  640x480 (0x1c7)   21.2MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   33.1KHz
        v: height  480 start    0 end    0 total  480           clock   69.0Hz
  576x432 (0x1c8)   17.4MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   30.2KHz
        v: height  432 start    0 end    0 total  432           clock   70.0Hz
  512x384 (0x1c9)   14.0MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   27.3KHz
        v: height  384 start    0 end    0 total  384           clock   71.0Hz
  512x384 (0x1ca)   14.2MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   27.6KHz
        v: height  384 start    0 end    0 total  384           clock   72.0Hz
  512x384 (0x1cb)   14.4MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   28.0KHz
        v: height  384 start    0 end    0 total  384           clock   73.0Hz
  416x312 (0x1cc)    9.6MHz
        h: width   416 start    0 end    0 total  416 skew    0 clock   23.1KHz
        v: height  312 start    0 end    0 total  312           clock   74.0Hz
  400x300 (0x1cd)    9.0MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   22.5KHz
        v: height  300 start    0 end    0 total  300           clock   75.0Hz
  400x300 (0x1ce)    9.1MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   22.8KHz
        v: height  300 start    0 end    0 total  300           clock   76.0Hz
  400x300 (0x1cf)    9.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   23.1KHz
        v: height  300 start    0 end    0 total  300           clock   77.0Hz
  400x300 (0x1d0)    9.4MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   23.4KHz
        v: height  300 start    0 end    0 total  300           clock   78.0Hz
  320x240 (0x1d1)    6.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.0KHz
        v: height  240 start    0 end    0 total  240           clock   79.0Hz
  320x240 (0x1d2)    6.1MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.2KHz
        v: height  240 start    0 end    0 total  240           clock   80.0Hz
  320x240 (0x1d3)    6.2MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   19.4KHz
        v: height  240 start    0 end    0 total  240           clock   81.0Hz
```

---

### Post by cariboo on 2011-04-07
@Mindswap1, you still haven't told use what make/model/type of monitor you are using.

---

### Post by Mindswap1 on 2011-04-08
I apologize for the lack of information. I have a Samsung Sync Master 933 monitor.

---

### Post by 23dornot23d on 2011-04-08
Monitor [URL="http://www.twenga.co.uk/prices-SyncMaster-933HD-SAMSUNG-LCD-monitor-492948-0"]Specifications Link
[/URL]

You can generate the modeline for use in the xorg.conf with this - enter into a terminal ...
     
     cvt 1360 768 60Hz

---

### Post by Mindswap1 on 2011-04-09
Um I kinda didn't understand what you wanted me to do, but I entered into the terminal what you told me to. 
```


@Ubuntu:~$ cvt 1360 768 60Hz
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```

---

### Post by 23dornot23d on 2011-04-09
You should be able to enter that into your xorg.conf file now and get the resolution you wanted 
1360 x 768 with the 60 hz working ......

Your link to the monitor says that the monitor is ok to use this and all you need to do now is tell the computer its ok to go ahead with it ....... 

So .......

If its entered in the /etc/X11/xorg.conf in the correct place then it should work .......... 

Can you add the existing xorg.conf contents here ...... in between CODE quotes

and someone can check it and edit it for you ....... and post you a new one to replace the existing one .....

makes it so you have a backup here too ....... its always handy ....

---

### Post by Mindswap1 on 2011-04-09
Thank You for your reply ^.^ Here are the contents of the file 


```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.30  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Fri Feb 25 14:55:29 PST 2011


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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    EndSubSection
EndSection


```

---

### Post by 23dornot23d on 2011-04-09
I think thats all that is needed ..... to correct the problem .... but if someone can verify this is ok on the new system 
it would make me more confident that it will fix the issue on NATTY


```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.30  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Fri Feb 25 14:55:29 PST 2011


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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    # 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
    Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
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
    EndSubSection
EndSection

```Which Nvidia Graphics card - NVIDIA GeForce 6150 SE Graphics

as its not been identified in the file

---

### Post by cariboo on 2011-04-09
To me it seems that your monitor is not being detected properly, do you get any EDID errors in dmesg:

```
dmesg | grep EDID
```

Are you connected directly to the monitor, or are you using a KVM?

---

### Post by Mindswap1 on 2011-04-10
After I put 
dmesg  
Into the terminal it gave me the following. And grep EDID did not return anything. 

```
 [    0.181781] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.181825] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.181867] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.181943] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.182014] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.182086] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.182157] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.182228] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.182299] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.182369] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.182443] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.182515] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
[    0.182587] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.182658] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.182730] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
[    0.182803] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[    0.182876] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[    0.182949] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.183021] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.183093] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.183166] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[    0.183237] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0, disabled.
[    0.183368] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.183373] vgaarb: loaded
[    0.183606] SCSI subsystem initialized
[    0.183690] libata version 3.00 loaded.
[    0.183746] usbcore: registered new interface driver usbfs
[    0.183759] usbcore: registered new interface driver hub
[    0.183792] usbcore: registered new device driver usb
[    0.183924] wmi: Mapper loaded
[    0.183926] PCI: Using ACPI for IRQ routing
[    0.183931] PCI: pci_cache_line_size set to 64 bytes
[    0.183988] reserve RAM buffer: 000000000009b800 - 000000000009ffff 
[    0.183991] reserve RAM buffer: 00000000b7ee0000 - 00000000b7ffffff 
[    0.184110] NetLabel: Initializing
[    0.184112] NetLabel:  domain hash size = 128
[    0.184114] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184127] NetLabel:  unlabeled traffic allowed by default
[    0.184163] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.184171] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.184176] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.188115] Switching to clocksource hpet
[    0.191859] Switched to NOHz mode on CPU #0
[    0.191888] Switched to NOHz mode on CPU #1
[    0.196292] AppArmor: AppArmor Filesystem Enabled
[    0.196334] pnp: PnP ACPI init
[    0.196355] ACPI: bus type pnp registered
[    0.196923] pnp 00:00: [bus 00-04]
[    0.196927] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.196930] pnp 00:00: [io  0x0000-0x03af window]
[    0.196932] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.196935] pnp 00:00: [io  0x9000-0xffff window]
[    0.196937] pnp 00:00: [io  0x03b0-0x03df window]
[    0.196940] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.196943] pnp 00:00: [mem 0xc0000000-0xefffffff window]
[    0.196945] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
[    0.196948] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.196951] pnp 00:00: [io  0x4700-0x470b window]
[    0.196953] pnp 00:00: [io  0x1c00-0x1c80 window]
[    0.196955] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
[    0.197039] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.197144] pnp 00:01: [io  0x1000-0x107f]
[    0.197146] pnp 00:01: [io  0x1080-0x10ff]
[    0.197149] pnp 00:01: [io  0x1400-0x147f]
[    0.197151] pnp 00:01: [io  0x1480-0x14ff]
[    0.197153] pnp 00:01: [io  0x1800-0x187f]
[    0.197155] pnp 00:01: [io  0x1880-0x18ff]
[    0.197158] pnp 00:01: [mem 0x00000000-0xffffffff disabled]
[    0.197161] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
[    0.197163] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
[    0.197165] pnp 00:01: [mem 0xb8000000-0xbfffffff]
[    0.197168] pnp 00:01: [io  0x2000-0x207f]
[    0.197170] pnp 00:01: [io  0x2080-0x20ff]
[    0.197238] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.197241] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.197243] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.197246] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.197249] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.197251] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.197254] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.197257] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.197261] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.197264] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
[    0.197267] system 00:01: [mem 0xb8000000-0xbfffffff] has been reserved
[    0.197270] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.197334] pnp 00:02: [io  0x0010-0x001f]
[    0.197336] pnp 00:02: [io  0x0022-0x003f]
[    0.197338] pnp 00:02: [io  0x0044-0x004d]
[    0.197340] pnp 00:02: [io  0x0050-0x005e]
[    0.197343] pnp 00:02: [io  0x0062-0x0063]
[    0.197345] pnp 00:02: [io  0x0065-0x006f]
[    0.197347] pnp 00:02: [io  0x0074-0x007f]
[    0.197349] pnp 00:02: [io  0x0091-0x0093]
[    0.197351] pnp 00:02: [io  0x00a2-0x00bf]
[    0.197353] pnp 00:02: [io  0x00e0-0x00ef]
[    0.197355] pnp 00:02: [io  0x04d0-0x04d1]
[    0.197358] pnp 00:02: [io  0x0800-0x087f]
[    0.197360] pnp 00:02: [io  0x0290-0x0297]
[    0.197416] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.197419] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.197422] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.197425] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.197437] pnp 00:03: [dma 4]
[    0.197442] pnp 00:03: [io  0x0000-0x000f]
[    0.197445] pnp 00:03: [io  0x0080-0x0090]
[    0.197447] pnp 00:03: [io  0x0094-0x009f]
[    0.197449] pnp 00:03: [io  0x00c0-0x00df]
[    0.197481] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.197523] pnp 00:04: [irq 0 disabled]
[    0.197540] pnp 00:04: [irq 8]
[    0.197542] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
[    0.197579] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.197603] pnp 00:05: [io  0x0070-0x0073]
[    0.197636] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.197644] pnp 00:06: [io  0x0061]
[    0.197676] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.197685] pnp 00:07: [io  0x00f0-0x00ff]
[    0.197693] pnp 00:07: [irq 13]
[    0.197730] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.197939] pnp 00:08: [io  0x0060]
[    0.197942] pnp 00:08: [io  0x0064]
[    0.197950] pnp 00:08: [irq 1]
[    0.197984] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.198526] pnp 00:09: [mem 0xf0000000-0xf3ffffff]
[    0.198588] system 00:09: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.198592] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.198668] pnp 00:0a: [mem 0x000f0000-0x000fffff]
[    0.198671] pnp 00:0a: [mem 0xfeff0000-0xfeff00ff]
[    0.198673] pnp 00:0a: [mem 0xb7ee0000-0xb7efffff]
[    0.198675] pnp 00:0a: [mem 0xffff0000-0xffffffff]
[    0.198678] pnp 00:0a: [mem 0x00000000-0x0009ffff]
[    0.198680] pnp 00:0a: [mem 0x00100000-0xb7edffff]
[    0.198682] pnp 00:0a: [mem 0xb7f00000-0xbfefffff]
[    0.198685] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.198687] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    0.198689] pnp 00:0a: [mem 0xfefff000-0xfeffffff]
[    0.198692] pnp 00:0a: [mem 0xfff80000-0xfff80fff]
[    0.198694] pnp 00:0a: [mem 0xfff90000-0xfffbffff]
[    0.198696] pnp 00:0a: [mem 0xfffed000-0xfffeffff]
[    0.198766] system 00:0a: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.198769] system 00:0a: [mem 0xfeff0000-0xfeff00ff] has been reserved
[    0.198772] system 00:0a: [mem 0xb7ee0000-0xb7efffff] could not be reserved
[    0.198775] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
[    0.198778] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.198782] system 00:0a: [mem 0x00100000-0xb7edffff] could not be reserved
[    0.198785] system 00:0a: [mem 0xb7f00000-0xbfefffff] could not be reserved
[    0.198788] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.198791] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.198794] system 00:0a: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.198797] system 00:0a: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.198800] system 00:0a: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.198803] system 00:0a: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.198806] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.198825] pnp: PnP ACPI: found 11 devices
[    0.198827] ACPI: ACPI bus type pnp unregistered
[    0.198830] PnPBIOS: Disabled by ACPI PNP
[    0.235258] pci 0000:00:0d.0: BAR 6: assigned [mem 0xc0000000-0xc001ffff pref]
[    0.235262] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.235266] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.235270] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.235273] pci 0000:00:04.0:   bridge window [mem 0xfd800000-0xfd8fffff pref]
[    0.235278] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.235280] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.235284] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.235287] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.235291] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.235293] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.235297] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.235302] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.235306] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.235308] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.235311] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.235315] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.235324] pci 0000:00:04.0: setting latency timer to 64
[    0.235329] pci 0000:00:09.0: setting latency timer to 64
[    0.235333] pci 0000:00:0b.0: setting latency timer to 64
[    0.235338] pci 0000:00:0c.0: setting latency timer to 64
[    0.235341] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.235344] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.235346] pci_bus 0000:00: resource 6 [io  0x9000-0xffff]
[    0.235349] pci_bus 0000:00: resource 7 [io  0x03b0-0x03df]
[    0.235351] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.235354] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xefffffff]
[    0.235357] pci_bus 0000:00: resource 10 [mem 0xf4000000-0xfe02ffff]
[    0.235359] pci_bus 0000:00: resource 11 [mem 0xfed40000-0xfed44fff]
[    0.235362] pci_bus 0000:00: resource 12 [io  0x4700-0x470b]
[    0.235365] pci_bus 0000:00: resource 13 [io  0x1c00-0x1c80]
[    0.235367] pci_bus 0000:00: resource 14 [mem 0xfec80000-0xfecbffff]
[    0.235370] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.235373] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.235375] pci_bus 0000:01: resource 2 [mem 0xfd800000-0xfd8fffff pref]
[    0.235378] pci_bus 0000:01: resource 4 [io  0x0000-0x03af]
[    0.235381] pci_bus 0000:01: resource 5 [io  0x03e0-0x0cf7]
[    0.235383] pci_bus 0000:01: resource 6 [io  0x9000-0xffff]
[    0.235386] pci_bus 0000:01: resource 7 [io  0x03b0-0x03df]
[    0.235388] pci_bus 0000:01: resource 8 [mem 0x000a0000-0x000bffff]
[    0.235391] pci_bus 0000:01: resource 9 [mem 0xc0000000-0xefffffff]
[    0.235394] pci_bus 0000:01: resource 10 [mem 0xf4000000-0xfe02ffff]
[    0.235397] pci_bus 0000:01: resource 11 [mem 0xfed40000-0xfed44fff]
[    0.235399] pci_bus 0000:01: resource 12 [io  0x4700-0x470b]
[    0.235402] pci_bus 0000:01: resource 13 [io  0x1c00-0x1c80]
[    0.235404] pci_bus 0000:01: resource 14 [mem 0xfec80000-0xfecbffff]
[    0.235407] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.235410] pci_bus 0000:02: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.235413] pci_bus 0000:02: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.235416] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.235418] pci_bus 0000:03: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.235421] pci_bus 0000:03: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.235424] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.235426] pci_bus 0000:04: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.235429] pci_bus 0000:04: resource 2 [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.235470] NET: Registered protocol family 2
[    0.235545] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.235833] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.236643] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.237055] TCP: Hash tables configured (established 131072 bind 65536)
[    0.237058] TCP reno registered
[    0.237062] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.237076] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.237180] NET: Registered protocol family 1
[    0.252078] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252128] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252188] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252245] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252308] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252375] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252445] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.252452] pci 0000:00:0d.0: Boot video device
[    0.252463] PCI: CLS 64 bytes, default 64
[    0.252710] cpufreq-nforce2: No nForce2 chipset.
[    0.252858] audit: initializing netlink socket (disabled)
[    0.252871] type=2000 audit(1302449051.248:1): initialized
[    0.262872] highmem bounce pool size: 64 pages
[    0.262878] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.264594] VFS: Disk quotas dquot_6.5.2
[    0.264655] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.265308] fuse init (API version 7.16)
[    0.265402] msgmni has been set to 1655
[    0.265647] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.265675] io scheduler noop registered
[    0.265678] io scheduler deadline registered
[    0.265694] io scheduler cfq registered (default)
[    0.265815] pcieport 0000:00:09.0: setting latency timer to 64
[    0.265847] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.265886] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.265905] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.265946] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.265964] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.266034] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.266062] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.266236] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.266242] ACPI: Power Button [PWRB]
[    0.266309] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.266312] ACPI: Power Button [PWRF]
[    0.266369] ACPI: Fan [FAN] (on)
[    0.266598] ACPI: acpi_idle registered with cpuidle
[    0.268734] thermal LNXTHERM:00: registered as thermal_zone0
[    0.268737] ACPI: Thermal Zone [THRM] (40 C)
[    0.268797] ERST: Table is not found!
[    0.268898] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.269395] isapnp: Scanning for PnP cards...
[    0.464050] Freeing initrd memory: 12520k freed
[    0.622087] isapnp: No Plug & Play device found
[    0.684461] Linux agpgart interface v0.103
[    0.685929] brd: module loaded
[    0.686540] loop: module loaded
[    0.686660] i2c-core: driver [adp5520] using legacy suspend method
[    0.686662] i2c-core: driver [adp5520] using legacy resume method
[    0.686855] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.687077] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.687097] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.687113] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.687119] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.687531] Fixed MDIO Bus: probed
[    0.687579] PPP generic driver version 2.4.2
[    0.687625] tun: Universal TUN/TAP device driver, 1.6
[    0.687627] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.687723] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.687879] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.687890] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.687905] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.687908] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.687949] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.688045] ehci_hcd 0000:00:02.1: debug port 1
[    0.688053] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.688077] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.700015] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.700181] hub 1-0:1.0: USB hub found
[    0.700186] hub 1-0:1.0: 10 ports detected
[    0.700279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.700487] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.700506] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.700526] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.700529] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.700576] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.700636] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    0.758137] hub 2-0:1.0: USB hub found
[    0.758143] hub 2-0:1.0: 10 ports detected
[    0.758230] uhci_hcd: USB Universal Host Controller Interface driver
[    0.772043] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.772045] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.772200] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.772315] mousedev: PS/2 mouse device common for all mice
[    0.772463] rtc_cmos 00:05: RTC can wake from S4
[    0.788064] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.788103] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.788186] device-mapper: uevent: version 1.0.3
[    0.788272] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.788366] device-mapper: multipath: version 1.2.0 loaded
[    0.788369] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.788449] EISA: Probing bus 0 at eisa.0
[    0.788453] EISA: Cannot allocate resource for mainboard
[    0.788456] Cannot allocate resource for EISA slot 1
[    0.788459] Cannot allocate resource for EISA slot 2
[    0.788475] EISA: Detected 0 cards.
[    0.788548] cpuidle: using governor ladder
[    0.788550] cpuidle: using governor menu
[    0.788865] TCP cubic registered
[    0.789012] NET: Registered protocol family 10
[    0.789234] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.789564] NET: Registered protocol family 17
[    0.789587] Registering the dns_resolver key type
[    0.789616] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4450e (2 cpu cores) (version 2.20.00)
[    0.789659] powernow-k8:    0 : fid 0xf (2300 MHz), vid 0xe
[    0.789661] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xf
[    0.789664] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x11
[    0.789666] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x13
[    0.789669] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x16
[    0.789725] Using IPI No-Shortcut mode
[    0.789820] PM: Hibernation image not present or could not be loaded.
[    0.789834] registered taskstats version 1
[    0.790025]   Magic number: 7:702:436
[    0.790138] rtc_cmos 00:05: setting system clock to 2011-04-10 15:24:11 UTC (1302449051)
[    0.790141] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.790143] EDD information not available.
[    0.790253] Freeing unused kernel memory: 700k freed
[    0.790703] Write protecting the kernel text: 5192k
[    0.790747] Write protecting the kernel read-only data: 2148k
[    0.815442] <30>udev[64]: starting version 167
[    0.891473] pata_amd 0000:00:06.0: version 0.4.1
[    0.891525] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.905292] scsi0 : pata_amd
[    0.908133] scsi1 : pata_amd
[    0.908599] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.908602] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.909905] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.910114] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    0.910134] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    0.910139] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.012020] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.075005] ata2: port disabled. ignoring.
[    1.144676] hub 1-4:1.0: USB hub found
[    1.144728] hub 1-4:1.0: 2 ports detected
[    1.432943] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:97:c4:cd:a5
[    1.432949] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.432982] sata_nv 0000:00:08.0: version 3.5
[    1.433002] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.433064] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.433366] scsi2 : sata_nv
[    1.433641] scsi3 : sata_nv
[    1.433790] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.433793] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    1.656105] usb 1-4.1: new high speed USB device using ehci_hcd and address 3
[    1.900040] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.908125] ata3.00: ATA-7: ST3250310AS, 3.AHC, max UDMA/100
[    1.908130] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.924118] ata3.00: configured for UDMA/100
[    1.924287] scsi 2:0:0:0: Direct-Access     ATA      ST3250310AS      3.AH PQ: 0 ANSI: 5
[    1.924497] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.924519] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.924584] sd 2:0:0:0: [sda] Write Protect is off
[    1.924587] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.924609] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.969248]  sda: sda1 sda2 < sda5 >
[    1.969587] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.392034] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.400115] ata4.00: ATAPI: hp      DVD-RAM GH40L, RB0E, max UDMA/100
[    2.416111] ata4.00: configured for UDMA/100
[    2.421446] scsi 3:0:0:0: CD-ROM            hp       DVD-RAM GH40L    RB0E PQ: 0 ANSI: 5
[    2.425391] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.425395] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.425523] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.425687] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.732638] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.331245] Adding 3011580k swap on /dev/sda5.  Priority:-1 extents:1 across:3011580k 
[    6.189503] <30>udev[296]: starting version 167
[    6.548321] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.765180] lp: driver loaded but no devices found
[    7.795993] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    7.825862] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    7.825975] i2c i2c-1: nForce2 SMBus adapter at 0xf400
[    9.492101] type=1400 audit(1302449060.198:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=490 comm="apparmor_parser"
[    9.492123] type=1400 audit(1302449060.198:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=491 comm="apparmor_parser"
[    9.492471] type=1400 audit(1302449060.198:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 comm="apparmor_parser"
[    9.492507] type=1400 audit(1302449060.198:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
[    9.492707] type=1400 audit(1302449060.198:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm="apparmor_parser"
[    9.492752] type=1400 audit(1302449060.198:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[   11.220194] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x1F04
[   11.220248] usbcore: registered new interface driver usblp
[   11.582641] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   11.582649] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   11.582654] hda_intel: Disable MSI for Nvidia chipset
[   11.582679] HDA Intel 0000:00:05.0: setting latency timer to 64
[   12.533326] nvidia: module license 'NVIDIA' taints kernel.
[   12.533332] Disabling lock debugging due to kernel taint
[   13.736018] hda_codec: ALC888: BIOS auto-probing.
[   13.736024] hda_codec: ALC888: SKU not ready 0x411111f0
[   14.240329] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input3
[   14.240715] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
[   14.240722] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
[   14.240730] nvidia 0000:00:0d.0: setting latency timer to 64
[   14.240736] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.241001] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.30  Fri Feb 25 14:34:41 PST 2011
[   14.954534] type=1400 audit(1302449065.658:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=728 comm="apparmor_parser"
[   14.954930] type=1400 audit(1302449065.658:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=728 comm="apparmor_parser"
[   14.955172] type=1400 audit(1302449065.658:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=728 comm="apparmor_parser"
[   14.976240] type=1400 audit(1302449065.682:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=727 comm="apparmor_parser"
[   15.013380] type=1400 audit(1302449065.718:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=731 comm="apparmor_parser"
[   15.013843] type=1400 audit(1302449065.718:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=731 comm="apparmor_parser"
[   15.055245] type=1400 audit(1302449065.758:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=732 comm="apparmor_parser"
[   15.075666] type=1400 audit(1302449065.778:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=729 comm="apparmor_parser"
[   15.080699] type=1400 audit(1302449065.786:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=729 comm="apparmor_parser"
[   15.083628] type=1400 audit(1302449065.786:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=729 comm="apparmor_parser"
[   17.565118] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   18.162567] ppdev: user-space parallel port driver
[   22.947240] usb 1-4.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   27.688009] eth0: no IPv6 routers present
[   28.474914] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   37.189301] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   63.052272] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.255766] ISO 9660 Extensions: IEEE_1282
[   82.136033] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   83.609549] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4
[   83.609697] generic-usb 0003:045E:00CB.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:02.0-3/input0
[   83.609722] usbcore: registered new interface driver usbhid
[   83.609724] usbhid: USB HID core driver
[  210.514051] show_signal_msg: 6 callbacks suppressed
[  210.514057] empathy[1689]: segfault at 0 ip 067445cc sp bff36a04 error 4 in libglib-2.0.so.0.2800.5[66e0000+d5000] 

```

Should I change my config file as mentioned above?

---

