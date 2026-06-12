---
title: "Nvidia Geforce 9600 GT: Resolution problems with new LCD screen"
date: 2014-02-26
forum: Multimedia Software
---

### Post by mths2 on 2014-02-26
First off, hi everyone, and thanks in advance for your help. *I know that this is quite a frequent problem, but I have been trying to solve it for more than two hours now, applying "solutions" from different sources, and nothing helped.*


I just got an old LCD screen (HP w2216v) to replace my even older, and very ugly, former screen, thus switching from 4:3 ratio to "wide" ratio (1.6). After a few problems, I managed to get an image, but with a wrong ratio. [FONT=system]xrandr[/FONT] gives me the following information :

```
Screen 0: minimum 8 x 8, current 1152 x 864, maximum 8192 x 8192DVI-I-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0* 
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
```

On this screen, I want to have a 1680x1050 resolution at 60 Hz, so I Google stuff and read about the [FONT=system]xrandr --newmode[/FONT] and [FONT=system]xrandr --addmode[/FONT] options. The first one works perfectly, and these lines are added to the [FONT=system]xrandr[/FONT] output :

```
  1680x1050_60.00 (0x271)  147.1MHz        h: width  1680 start 1784 end 1968 total 2256 skew    0 clock   65.2KHz
        v: height 1050 start 1051 end 1054 total 1087           clock   60.0Hz
```

I got the corresponding ModeLine with [FONT=system]gtf[/FONT], but the one I got by using [FONT=system]cvt[/FONT] does not help me either : when I try to add my new mode to my "DVI-I-0", I get a BadMatch error.

I tried to edit my [FONT=system]/etc/X11/xorg.conf[/FONT] file, but it didn't help either. So I [FONT=system]cp[/FONT]'ed back my backup [FONT=system]xorg.conf[/FONT], and it looks like this :

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection


Section "Module"
        Load    "glx"
EndSection


Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

I was actually expecting a somewhat longer and more detailed configuration file...

My graphics card is a Geforce 9600 GT (the resolution I want to get is way lower than the maximum resolution for this card), and my driver is the Nvidia 331.20.

Do some of you have some specific ideas ? (Please, please, please... ^_^)


PS : sorry for any grammatical error. I'm French. Pardon my English :)

---

### Post by mths2 on 2014-03-01
I'm "upping" the topic, even though it may seem misplaced (?). I still have no clue about how to solve this problem, and my crappy 4:3 resolution is kind of sad, especially on a screen built for hi-res wide images :)

Note to the moderators : If no one can help me, I won't up this topic a second time, I promise :)

Once again, thanks for any kind of help.

---

### Post by oldfred on 2014-03-01
Does the nVidia configure screen show the monitor correctly.

My 9600GT sees my old 4:3 HP1903 LCD and just works.

---

### Post by mths2 on 2014-03-04
No, I think it does not recognize it. It is shown as "unknown" everywhere.

May it be because I have to use a VGA/DVI adaptor to connect the screen and the graphics card ?

---

### Post by PotatoHead007 on 2014-03-05
> **mths2 said:**
> No, I think it does not recognize it. It is shown as "unknown" everywhere.

May it be because I have to use a VGA/DVI adaptor to connect the screen and the graphics card ?

Are you using HDMI? I use VGA, works perfectly(that said, i do not have the GeForce 9600GT, but it should still work flawlessly).

---

### Post by mths2 on 2014-03-05
As I said, I have to use a VGA/HDI adaptor, so this is what I'm using.

But I have found a solution to my problem, finally ! This is what I did :

1) sudo rm ~/.config/monitors.xml
2) edited /etc/X11/xorg.conf in order to change the horizontal and vertical refresh rates (after having Googled their values for my screen) in the "Monitor" section of the file.

Just restarted X (AltGr+Syst+K) and the Setup menu gave me access to a large choice of resolutions, including the one I wanted !

Thanks for your help, anyways :)

---

### Post by PotatoHead007 on 2014-03-05
> **mths2 said:**
> As I said, I have to use a VGA/HDI adaptor, so this is what I'm using.



Ah my bad :( Misread your post, sorry.

---

### Post by mths2 on 2014-03-05
> **PotatoHead007 said:**
> Ah my bad :( Misread your post, sorry.
No problem :)

---

