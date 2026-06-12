---
title: "TV-out on ATI proprietary driver"
date: 2008-07-27
forum: Multimedia Software
---

### Post by zwaardmeester on 2008-07-27
Hello everyone,

I'm trying to get my TV working on the S-video output of my Radeon 9800pro. I have the proprietary drivers installed and want to follow [this guide]("http://gentoo-wiki.com/HOWTO_TV-Out#ATI-proprietary-drivers"). But for the `aticonfig' command given there, I'm required to know the hsync and vertRefresh of my TV. 

The problem is that I don't know these values, since it only says "50 Hz"  on the back of the TV, what i think is the required frequency for the power. In the manual nothing about sync rate, nor on internet. Is there a way i can figure the values out, or set up the TV without knowing them? In Windows I never needed them...

Thanks in advance,

Leo

edit: solved

---

### Post by markbuntu on 2008-07-27
Wow, that is a really old guide.

You can find the capabilities of your tv in Xorg.0.log which you can find in System/Administration/System logs. It should have been autodetected if it was turned on and connected when you booted up.

You can also type aticonfig --help for a list of commands to query the tv about its capabilities and to configure it.

---

### Post by zwaardmeester on 2008-07-28
Thanks for the reply. I did as you said - boot with the TV turned on. Below this post you can find the relevant lines from the Xorg log file. 
I get now a screen on my TV, which is a clone from the LCD. 
This is something ofcourse, but there are still two things bothering me:
[LIST]
[*]there is a black bar on the bottom of the tv, making me think that the sync values might not be optimal.
[*]the virtual size is 1280x1024, with a viewport of 1024x768, annoying for watching video. 
[/LIST]
With the second thing I have been fighting now for some time, but I was unable to figure it out. In the end I messed up my xorg.conf, after which I reinstalled the driver. 
The first seems even more complicated to me. Since my tv did not provide EDID information (it's an old one), the driver might have guessed slightly wrong values. I have no idea how to fix this. I'm very grateful for any help given on the subject.

Regards,

Leo


====================================
Attachments
====================================


Relevant lines in the [Xorg.0.log file (click)]("http://leo.home.fmf.nl/files/Xorg.0.log.txt"):

```
(II) fglrx(0): Connected Display1: TV on TVDAC [tv]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
```

```
(II) fglrx(0): Total of 12 modes found for secondary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1024x768": 43.0 MHz (scaled from 0.0 MHz), 15.7 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x60.0   42.95  1024 2320 2336 2730  768 483 485 525 interlace (15.7 kHz)
```

Output of aticonfig --tv-info 

```
The TV Format is "PAL-G"
The TV geometry is "50x50+0+0"
The horizontal position limits are [-6, 6]
The vertical position limits are [-6, 6] 
TV overscan mode is disabled

```

---

### Post by markbuntu on 2008-07-28
The driver seems to be guessing at your tv configuration and is playing it safe. 

You can use the Catalyst Control Center to adjust the resolution of the second display, or you can use the aticonfig commands if Catalyst Control does not give you the options you need. The good thing about using CCC is if something goes wrong or you do not accept the changes, it automatically reverts to the old settings in 35 seconds.

Catalyst Control Center usually lives in Applications/Other which may be hidden. You can fix that in System/Preferences/Main Menu. If you are using the 8.3 driver from the repository, you may not have Catalyst Control Center installed. You can get it with Synaptic, search amdcccle.

There is no need to be messing around with xorg.conf for these adjustments.

---

### Post by zwaardmeester on 2008-07-29
Dear Mark, thanks a lot for helping me out!  Installing the Catalyst Control Center did the trick for me. I still cannot run different resolutions on both screens, but for a movie i can temporarily change to 1024x768 to make it work. I didn't know about the existence of CCC at all. Maybe in future it will appear automatically. Anyway, it works now :KS

---

