---
title: "Dell Latitude D610, play full HD?"
date: 2014-11-02
forum: Multimedia Software
---

### Post by Pelvur on 2014-11-02
Hello.

I have an old laptop (Dell latitude D610, Pentium M 2.13GHz // 2GB RAM) that I'm willing to use as HTPC. I plays 720p videos ok, but it cannot play 1080p, and it is lagging heavily when playing youtube, anything better than 480p.
Is there any trick to play it well? May be a certain player (I currently use Parole), or settings, or something? Will special HTPC OS help (like OpenELEC or similar)?
Or is it simply insufficient processing power and nothing can be done? Kind of weird to see they can play FullHD on Raspberry Pi stuff while 2.13 GHz Intel cannot play it. 
Right now I use Dell Precision M4400 (X9100 @ 3.06GHz × 2 , Quadro FX 770M,8 GB RAM) as HTPC, and it plays everything very well, but it seems a waste of computing power to me. 

Thanks.

---

### Post by sudodus on 2014-11-02
You might be able to boost the video playing ability with a separate graphics card in a desktop computer, but that is not easy in a laptop, and the CPU itself is too old and slow. I'm glad it works for you playing 720p :-) (I'm afraid that the graphics chip is too old or too simple for advanced acceleration, for example VDPAU (for nvidia).)

I see that you have ***Lubuntu*** in one computer. The ***LXDE*** graphics is faster than XFCE of Xubuntu and much faster than Unity of standard Ubuntu. In addition to that you can try ***mplayer2***, run it from a terminal window and tweak the video playing according to the options described in the manual pages

```
man mplayer
```

It might be even lighter (and save some CPU power for playing video) with only a window manager, ***Openbox*** comes with Lubuntu, or some other and even lighter window manager, for example ***Fluxbox*** or ***JWM***. You can build a very light system from the Ubuntu ***mini.iso***.

---

### Post by Pelvur on 2014-11-03
> **sudodus said:**
> 

It might be even lighter (and save some CPU power for playing video) with only a window manager, ***Openbox*** comes with Lubuntu, or some other and even lighter window manager, for example ***Fluxbox*** or ***JWM***. You can build a very light system from the Ubuntu ***mini.iso***.

Does it make sense then to go for HTPC-specified distro like OpenElec or XBMCbuntu? I tried OpenElec from LiveUSB, Youtube at 720p looks better, didn't try local 1080p though. But the problem is I don't have sound at all, not sure why.

---

### Post by sudodus on 2014-11-03
I think you should try many distros and maybe build something yourself by adding program packages to a very light basic distro. But the hardware in that Dell latitude D610 might not play 1080p well anyway.

Some distros need the sound software to be tweaked to recognize the hardware. Pulseaudio and Pavucontrol can help. Install them if they are not already there, and try with all the options in the menus of Pavucontrol.

---

### Post by Rob Sayer on 2014-11-03
I suspect the video card is too weak or not well supported anymore in linux.  AMD cards can be bad for that.

Open the terminal and type

sudo lshw -C video

---

### Post by Pelvur on 2014-11-03
> **Rob Sayer said:**
> 

Open the terminal and type

sudo lshw -C video

Here is the result. 

```
*-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff00000-dff7ffff ioport:ec38(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff
```

I understand, that the video card is weak, the laptop is 9-years old, I just thought may be I'm missing something, may be there is still a way. Well, I guess I will have to stick to 720p max and probably 480p on Youtube if I want to use this laptop for HTPC.

---

### Post by QIII on 2014-11-03
Hello!

I have a D620.  Those were basically business class laptops and not really intended for multimedia.  I got a little bit better performance by swapping out the OEM Core Duo (32 bit, not a Core 2 Duo) processor in mine for a Core 2 Duo (64 bit) T7200, but the resolution with the graphics chip is still limited.  You pretty much get only the 1440x900 native resolution of the screen.

By the way:  fan control on those things was absolutely terrible, so I installed i8kutils (it runs Fedora) and have the module loaded on startup, then added a conf to start the fan on low at 35 degrees and high at 60 degrees.  Otherwise it was not even coming on at low until 60 degrees and high at something like 90.  That's hot enough to burn the thighs!

---

### Post by Rob Sayer on 2014-11-04
Your card may not have 3D acceleration properly suppored in linux.  Seeing whether it is or not seems to be a bit of a black art, but try this in terminal:

 glxinfo | grep direct

and if it says no, you aren't.  But I'm not sure you would have proper 3D accel even if it says yes ...

You should try an mplayer GUI like smplayer (my default video player) or gnome-mplayer (which is the lightest mplayer GUI I know of).  Mplayer is not only very powerful but it's quite fast.  Much faster than vlc, and has better codec support.  Using programs like xbmc (which are large and heavy and made for modern hardware) will just make things worse.  Mplayer is the best for slow hardware.  Some here will recommend using mplayer in CLI mode but I wouldn't go that far unless *absolutely* necessary.

If you don't have good 3D support or it's just slow experiment with mplayer output modules/settings.  You may need to use the x11 video output module.  Do a search on mplayer settings.

---

### Post by Pelvur on 2014-11-05
> **Rob Sayer said:**
> Your card may not have 3D acceleration properly suppored in linux.  Seeing whether it is or not seems to be a bit of a black art, but try this in terminal:

 glxinfo | grep direct

and if it says no, you aren't.  But I'm not sure you would have proper 3D accel even if it says yes ...


It says

```
[COLOR=#ff0000]**direct **[/COLOR]rendering: Yes
```

> 
 You should try an mplayer GUI like smplayer (my default video player) or gnome-mplayer (which is the lightest mplayer GUI I know of).  Mplayer is not only very powerful but it's quite fast.  Much faster than vlc, and has better codec support. 

I use either SMPlayer or Parole (default Xubuntu player, seems to have problems with subtitles though, cannot turn them off).

> 
Using programs like xbmc (which are large and heavy and made for modern hardware) will just make things worse. 

I thought that if XBMCbuntu or OpenElec are made for HTPC, then there will be no other unnecessary crap and they should be light and less resource-hungry compared to full OS even such a light one as Xubuntu.

---

### Post by Pelvur on 2014-11-05
> **QIII said:**
> Hello!

I have a D620.  Those were basically business class laptops and not really intended for multimedia.  I got a little bit better performance by swapping out the OEM Core Duo (32 bit, not a Core 2 Duo) processor in mine for a Core 2 Duo (64 bit) T7200, but the resolution with the graphics chip is still limited. 

By the way:  fan control on those things was absolutely terrible, so I installed i8kutils (it runs Fedora) and have the module loaded on startup, then added a conf to start the fan on low at 35 degrees and high at 60 degrees.  Otherwise it was not even coming on at low until 60 degrees and high at something like 90.  That's hot enough to burn the thighs!

The best processor available for D610 is Intel Pentium M 780. I couldn't find it for an reasonable price, I got M 770 (I used to have M 750). 
No problems with cooling other than original cooler became nosiy after several years. I replaced it with new one, and it doesn't bother me for couple of years now. No overheating problems seen ever with this laptop.

---

### Post by Pelvur on 2014-11-20
In case if someone will be interested at some point.
I have not figured out how to play full HD on my D610. But HD is good enough for me, and I found solution for that. I have installed OpenElec onto the drive, and it works like a charm.Even Youtube videos in 720p play flawlessly. It is faster than liveUSB version, and no problems with sound. Had to employ xrandr to get external screen working, did it through Putty (OpenElec does not have terminal).
I tried to have minimum Lubuntu installation, but it is nowhere as fast, especially for youtube (480p videos were lagging). I tried to install OpenElec along the existing system and did not succeed. So had to give it all my hard drive. 
Wonder if SSD would make it even better (not sure about speed of PATA SSD), but shy to invest into such an old laptop. 
Main outcome - now my powerful M4400 is in my hands, instead of wasting its power for HTPC needs.

---

### Post by sudodus on 2014-11-20
Congratulations :KS

Thanks for sharing your result, that ***OpenElec*** works well for you :-) Finally, please click on Thread Tools at the top of the page and mark this thread as SOLVED

---

