---
title: "1440x900 resolution on a HP TFT7600 &amp; ATI ES1000"
date: 2010-02-08
forum: Multimedia Software
---

### Post by krige on 2010-02-08
Hello there,

I am trying to get the HP TFT7600 monitor of a rackmount system work on its native resolution of 1440x900. 

I have just installed a fresh copy of Ubuntu 9.10 64bit but it didn't  recognise the monitor and it's now working at 1152x864.

The monitor is attached to the computer through a 4 port KVM switch.

There is no xorg.conf file in the /etc/X11/ directory.

Outputs of the gft and cvt commands follow:

```
root:# gtf 1440 900 60
1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

root:# gtf 1440 900 75
1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync

root:# cvt 1440 900
1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```

Configuration summary:

Graphic card: ATI ES1000
Display: HP TFT 7600
Screen size: 17 inch
Screen type: Active Matrix TFT LCD
Maximum resolution: 1440 x 900 WXGA+
Supported refresh rates: 60, 70, 72 and 75Hz

---

### Post by krige on 2010-02-09
Does anybody know how to set that resolution manually?

---

### Post by efflandt on 2010-02-10
**man xrandr** and see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Try just **xrandr** first to see what your video device is (I imagine VGA-0).  Then assuming there is no existing 1440x900 mode, you could try:

```
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA-0 1440x900_60.00
xrandr --output VGA-0 --mode 1440x900_60.00
```Note, these commands run from terminal are just temporary, so if you are trying similar modes and do not know how to delete a mode with xrandr, just log out of X and log back in.  Also see **man xvidtune**.

---

### Post by krige on 2010-02-10
Thank you efflandt!

When I run xrandr I only get the message:

```
Can't open display
```

---

### Post by krige on 2010-02-10
Ok, I got that because I run that command from a remote terminal.

Running it from a terminal in the graphical interface I got the following:

```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
VGA-0 disconnected (normal left inverted right x axis y axis)
```

---

### Post by krige on 2010-02-10
The first two commands you gave worked fine, but when I run the third one, on VGA-1, it gives me back this message:

```
xrandr: screen cannot be larger than 1360x1360 (desired size 1440x900)
```

---

### Post by frederickjh on 2010-02-11
> **krige said:**
> 

```
Screen 0: minimum 320 x 200, current 1152 x 864, [COLOR="Red"]maximum 1360 x 1360[/COLOR]
VGA-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 
```

The maximum for your setting is set to 1360 x 1360. It is right there in your post. 


Try the command below to increase the maximum allowed size.

xrandr --fbmm 1440x900

I never did get the xrandr setting to change the size to 1440x900.

I ended up changing my xorg.conf file to get 1440x900. I had a different monitor on before and had changed the xorg.conf file before. After you do that it will not update it at the next xorg upgrade. So I manually went in and added the mode with "1440x900" on the Modes line in /etc/X11/xorg.conf  I have attached my xorg.conf as xorg.conf.txt in case it helps you out. I am running Karmic. You can find more info about the xorg.conf file here

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

and here [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")

---

### Post by krige on 2010-02-11
Thank you frederickjh.

> **frederickjh said:**
> The maximum for your setting is set to 1360 x 1360. It is right there in your post.

I did notice that, but I wasn't able to find the xrandr option to set a new maximum size.


> **frederickjh said:**
> Try the command below to increase the maximum allowed size.

xrandr --fbmm 1440x900

That didn't affect the maximum size.


> **frederickjh said:**
> I ended up changing my xorg.conf file to get 1440x900. I had a different monitor on before and had changed the xorg.conf file before. After you do that it will not update it at the next xorg upgrade.

I don't have a xorg.conf file in any of my Ubuntu machines. Will it suffice just to create a file with that name into the /etc/X11/ directory to make it work?


> **frederickjh said:**
> So I manually went in and added the mode with "1440x900" on the Modes line in /etc/X11/xorg.conf  I have attached my xorg.conf as xorg.conf.txt in case it helps you out.

I am sorry, where did you attach it?

---

### Post by krige on 2010-02-11
The command "dexconf" retrieves values from debconf’s database and uses them to build an xorg.conf file.

[http://manpages.ubuntu.com/manpages/karmic/en/man1/dexconf.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/dexconf.1.html)

I tried running it but it didn't produce any xorg.conf in /etc/X11/. I even tried the -o option to write to a specific file instead but didn't work. It doesn't get me any error message either.

---

### Post by krige on 2010-02-11
I think I almost solved it, here is what I have done:

[LIST=1]
[*]sudo Xorg -configure
[*]sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
[*]sudo vim xorg.conf
[*]found the SubSection "Display" with Depth 24 and changed it to:
```
SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1440x900"
                Virtual 1440 900
EndSubSection
```
[/LIST]

After doing that I run startx and the resolution was at 1440x900.

Still there must be something not right because I can see some flickering of the screen and there appear some thin black horizontal lines. I guess it's because I must provide more information about the monitor in the xorg.conf or because the refresh rate is set to 60Hz while the monitor is supposed to work to other rates (70, 72 or 75Hz).

---

### Post by krige on 2010-02-11
I have made some progress: I run gtf several times with different refresh rates, copied and paste the results in the Section "Monitor" as follows:

```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "HP"
        ModelName    "TFT7600"
        Modeline     "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
        Modeline     "1440x900_70.00"  126.98  1440 1536 1688 1936  900 901 904 937  -HSync +Vsync
        Modeline     "1440x900_72.00"  130.75  1440 1536 1688 1936  900 901 904 938  -HSync +Vsync
        Modeline     "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
        Option       "PreferredMode" "1440x900_75.00"
EndSection
```

But still the graphic interface starts @ 60Hz. What's more 60Hz is the only refresh rate available in the System / Preferences / Display configuration panel.

---

### Post by krige on 2010-02-11
I didn't manage to make the monitor go to other refresh rates other than 60Hz. I initially thought that its blurry look was due to the low refresh rate but then I noticed on other monitors the image is sharply clear even at 60Hz so I guess the problem with the TFT7600 is due to its poor quality, or more likely to the in-between 4 port KVM switch.

Another thing I noticed is that the outputs of the cvt and the gtf commands, with the same resolution, are different: I tried both configurations in xorg.conf and found out that with the cvt one  the graphic interface looks slightly better so I left that in the xorg.conf.

I have saved my xorg.conf [here]("http://pastebin.com/f5751331a") in case anyone else might need it: if you have a HP TFT7600 monitor and an ATI ES1000 graphic card and you put it in your /etc/X11/ directory it will make your screen resolution work at 1440x900.

---

