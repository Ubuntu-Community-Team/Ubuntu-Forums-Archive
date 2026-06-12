---
title: "Lucid - Nouveau chooses wrong resolution"
date: 2010-07-27
forum: Multimedia Software
---

### Post by rollinns on 2010-07-27
I have kubuntu 10.04 installed using the nouveau drivers for a Geforce 6600 card.  When it boots up, it uses 1600x1200 resolution, which the monitor supports but is too high for what I need, I have to change it to 1024x768 every time it boots.  I've tried the non-free drivers and would use them if they worked but they either: A) cause the system to freeze requiring a hard reboot or B) it just boots to a command line. After 4 complete reinstalls, trying to use the non-free driver (trying all 3 different versions and all kinds of tweaks found here and elsewhere) I'm fine with the nouveau driver as long as I can lock it to 1024x768.

I need to get it to boot up to 1024x768 every time.  After all the bugs are worked out on this machine and my projector is mounted, I'll be using this as a home theater PC feeding the projector. The max resolution the projector can handle is 1024x768.

I've already tried this:
[http://nouveau.freedesktop.org/wiki/KernelModeSetting](http://nouveau.freedesktop.org/wiki/KernelModeSetting)

but it still came up as 1600x1200.

Any help is greatly appreciated.

Thanks,
rollinns

---

### Post by Yellow Pasque on 2010-07-28
There may be a cleaner way to do this, but here;s my hack. First, Generate modeline:
```
cvt 1024 768 60.0Hz
```
Take note of the hsync it returns.

Now, create/edit xorg.conf (I use kate editor in this example, use whatever you want). 
```
kdesudo kate /etc/X11/xorg.conf
```
The important line is in the monitor section. Make the maximum HorizSync (magic number) slightly larger than the hsync returned by cvt output. Larger resolutions should now be rejected because the hsync needed for them is too high.
```

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 28.0 - <magic number>
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```
Save. Quit. Log out. If you get stuck in terminal, just delete the xorg.conf. If it starts X, but doesn't work like you want, then post output of /var/log/Xorg.0.log

---

### Post by rollinns on 2010-08-21
Thanks for the help, I tweaked your file slightly and got this to work great:

```
Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 28.0 - 85
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
	Depth	24
	Modes	"1024x768"
EndSubSection
EndSection
```

It works exactly as I need it to now, I really appreciate the help.

---

