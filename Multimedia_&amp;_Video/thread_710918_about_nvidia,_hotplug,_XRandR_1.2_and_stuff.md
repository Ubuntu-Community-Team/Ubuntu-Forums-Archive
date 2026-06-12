---
title: "about nvidia, hotplug, XRandR 1.2 and stuff"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by morticul on 2008-02-29
Hi all.

I really wish I could unplug my laptop from home-monitor, suspend the session, go to work, unsuspend and plug it to work-monitor (all monitors have different resolutions).

It seemed possible with XRandR 1.2 but I recently learned that the Nvidia restricted driver wasn't supporting XRandR 1.2. I was really disappointed :(. I then tried the nv driver. The XrandR 1.2 stuff was working but there was no more 2d acceleration nor 3d acceleration and suspend wasn't working anymore. There is probably some solutions around those problems but it seems to be hard work...

I was about to give up before I started to play with the nvidia-settings GUI. The "X Server Display Configuration" tab allow you to do exactly what I need. It can detect displays, disable the laptop screen, enable the new screen and set the appropriate resolution. All of this without restarting X.

Wow !!! really cool. Now, how can I script this ? The manpages of nvidia-settings tells that every attribute in the GUI should be available through the command line version. This seems to be true except for the "X Server Display Configuration" tab. None of those are available. They seems to be more kind of XRandR commands. However, trying xrandr doesn't apply the changes. On the other hand, the following commands let me think that the nvidia driver support XRandR 1.2, at least partly....

```

$nvidia-settings --query all
...
  Attribute 'GPUCurrentClockFreqs' (xps:0.0): 275,301.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (xps:0.0): 100.14.19

  Attribute 'NvControlVersion' (xps:0.0): 1.13

  Attribute 'GLXServerVersion' (xps:0.0): 1.4

  Attribute 'GLXClientVersion' (xps:0.0): 1.4

  Attribute 'OpenGLVersion' (xps:0.0): 2.1.1 NVIDIA 100.14.19

  **Attribute 'XRandRVersion' (xps:0.0): 1.2**

  Attribute 'XF86VidModeVersion' (xps:0.0): 2.2

  Attribute 'XvVersion' (xps:0.0): 2.2


```

Can some one shed light on this... How could I make a small script that switch my video settings without restarting x.... Any kind of hint would be really appreciated..

---

### Post by morticul on 2008-03-07
Ain't anybody interested in that fabulous subject...

maybe the smell of popcorn will attract peoples... :popcorn:

---

### Post by NicoA380 on 2008-03-08
I want the same feature too.

I discover xrandr with an eeepc and I want to do the same with my nvidia card.
I have customise my Xorg for my desktop screen, but when I move I use nvidia-settings.

nvidia-settings makes a big virtual desktop, not like xinerama (emulate by : Option "NoTwinViewXineramaInfo" "False", needs X restart) because when I maximize a window, it doesn't fit one screen but the big virtual desktop. It's bad for fullscreen and for all WM (compiz/metacity ...).

---

### Post by morticul on 2008-03-08
> 
nvidia-settings makes a big virtual desktop, not like xinerama (emulate by : Option "NoTwinViewXineramaInfo" "False", needs X restart) because when I maximize a window, it doesn't fit one screen but the big virtual desktop. It's bad for fullscreen and for all WM (compiz/metacity ...).


Yeah... that really sucks. I've also seen other peoples having the same problem. However, If I restart my X, both displays will be on different screens through twin view with maximize working correctly, something I wasn't able to do using nvidia-settings. 

But I can accept to have my laptop screen disabled while working on my big LCD. I Just don't like to work a full day on my small laptop screen.

---

### Post by Kiri on 2008-04-10
Did anyone get this working yet?? I think it should be possible...

---

### Post by morticul on 2008-04-10
I've been able to switch between predefined modes using the xrandr -s <index> command. To predefine modes, I put a list in my xorg.conf "MetaModes" options of my twin view configuration. Unfortunately, only valid modes at the time of my xstart are kept. So when I plug into another monitor that wasn't there at boot time... it doesn't work.

It seems that every elements are in place to achieve this. But they don't work well together yet...

---

### Post by Kiri on 2008-04-10
Really? I couldnt get xrandr working with nvidia. when I try to set the virtual desktop space it makes it really huge and messed up over my smaller laptop display (which was still set to the primary one for some reason)

Can you tell me your xorg settings and how you got it going?
Are you able to switch between laptop display, external, twin view, tv out etc?
thanks!

---

### Post by morticul on 2008-04-10
Here is my Screen section of my xorg.conf


```

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8400M GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "TwinView" "True" # this enable twinview
    Option         "TwinViewOrientation" "RightOf" 
    Option         "UseEdidFreqs" "True" # this asks automatically for frequencies
    Option         "MetaModes" "NULL,1920x1200; NULL,1680x1050; NULL,1366x768; 1440x900,NULL" # put possible resolution in the  order specified by useDisplayDevice
    Option         "UseDisplayDevice" "DFP-0,DFP-1" # determine the order of the screens.
    Option         "DynamicTwinView" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x1440"
    EndSubSection
EndSection

```

There is a couple of things you don't need, like the SubSection "Display". I don't remember exactly why I've put this... but I'm leaving it in case this is helping... Any way TwinView + nvidia always worked fine for me and there is plenty of twinview tutorial outthere. And the two screens work well (i.e. you can maximize on different screens). 

In my case my MetaModes list always have one of the two monitor turned off (NULL) but you can put two resolutions if you want. 

Once your Xorg is set, just restart your X and it will choose the first available MetaMode. 

If there is any problems or if you want to see which modes were rejected, use :
```

grep -i nvidia /var/log/Xorg.0.log # or something like that

```

If you want to see available modes, just do :

```

xrandr

```

If you want to select a mode, just do :

```

xrandr -s <index> 

```
where <index> is the index of the mode you want as returned from xrandr.

However, it doesn't always work for me... After suspend and unsuspend, I never managed to make it work. Also, I've installed the latest nvidia driver 169.12, but I'm not sure it is necessary.

So... tell me how is it going....

---

### Post by Kiri on 2008-04-11
Thanks heaps for posting that morticul. I'm going to try to write mine from referring to yours and see how it goes. 
One question, didn't you need to add the Virtual entry to make it work with xandr?
Every document I've read about xandr says you need that, but when I tried it it messed up, but I notice your config doesnt have it...

---

### Post by morticul on 2008-04-11
As far as I understand it, the Virtual option is related to the "real" xrandr 1.2 features. However, in my case, I think I'm kind of using the nvidia's custom implementation of the dynamic resolution developed before xrandr 1.2 was out so I don't need the virtual option. 

I do have this option set in an older xorg.conf, using the nv driver and the full xrandr 1.2 features. But now, without this option, I'm able to switch between the modes NULL,1920x1200; and  1440x900,NULL, using xrandr -s 0 and xrandr -s 2.

---

### Post by Kiri on 2008-04-11
Awesome, I'll try it when I get home later

---

### Post by Kiri on 2008-04-13
hey morticul, it worked!
well kind of anyway. 
I can now use xandr to switch between twinview laptop and external monitor, and just laptop display and it seems to work quite well.

Unfortunately I haven't been able to get it working with my tv out. I wanted to have another meta mode for using the tv out but it doesn't seem to work at all.. not sure about that part.
The other problem is that I cannot get my primary display (with all the desktop icons, panel etc) to be to the right of the setup. It always defaults to whichever monitor is set to be on the left. 
I would prefer my external monitor to be to the right and the primary display, but can't seem to get that to work. 
But apart from those two problems, it is going ok :)
thanks


PS, my xorg.conf ended up quite different. Here it is if anyone else might go through this process:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1920+400; CRT: null, DFP: nvidia-auto-select +0+0"
EndSection


```

---

### Post by morticul on 2008-04-14
Nice man !!

> 
Unfortunately I haven't been able to get it working with my tv out. I wanted to have another meta mode for using the tv out but it doesn't seem to work at all.. not sure about that part.


I've seen things about xrandr and tv out on this page:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")
but I don't think this will help...

> 
The other problem is that I cannot get my primary display (with all the desktop icons, panel etc) to be to the right of the setup. It always defaults to whichever monitor is set to be on the left.


I'm using KDE and I can specify on which screen my toolbar will be. By the configure toolbar GUI or Display configuration GUI. I can also set different wallpapers on each screen. But I don't remember exactly how, I'm not in dual monitor right now....


And thanks for pimping up this thread man ;)

---

### Post by Kiri on 2008-04-14
Hey thanks for all your help.

It seems like it should definately be possible to do what I want with xandr, but I think I need to have a really well written xorg.conf for it to work. 
I really don't understand the xorg.conf file. Everyones seems to be very different and the syntax changes all the time. There are not any really clear guides that I can find either. :(

I think that maybe other DEs like KDE work better with multi-screen setups, so I'm thinking of switching... 
Just got used to gnome though (><) hehe

---

### Post by Kiri on 2008-04-28
Well I still cannot seem to find a way to switch between the LCD display and TV out. I can use xrandr for switching between my laptop and external LCD, but just cant seem to switch to the tv out display. Very frustrating. 

I also tried KDE, but it had the same problems with not being able to put my secondary display on the left side. 
:(

---

### Post by morticul on 2008-04-28
Well... maybe you can go an buy a new hdtv with hdmi input and use a dvi to hdmi cable...

But this is a quite expensive solution ;)

---

