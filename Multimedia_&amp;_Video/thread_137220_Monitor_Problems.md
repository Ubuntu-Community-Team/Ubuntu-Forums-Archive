---
title: "Monitor Problems"
date: 2006-02-27
forum: Multimedia &amp; Video
---

### Post by maggs on 2006-02-27
Hi all, I have a rather unique problem and can't find a solution in these forums. I installed Ubuntu 5.10 on a Sony Vaio PCG-GRT30P notebook with no problems. Shortly after my install the bascklight died on my LCD screen. So I plugged in and external BenQ FP767 LCD monitor. Everything is sweet until the login screen appears. It's obvious there is a sync problem as the display is unreadable. My video card is an nvidia GeoForce Go5600(builtin). I have run the xconf setup many times and tried various settings as described on these forums to no avail.

I am sure it is the sync rates. The monitor manual is vague about the settings. I don't know exactly what settings to use. Below is a paste from the manual.

Native (maximum) resolution 1,280X1,024
Line frequency 31.47 - 83 kHzMulti- frequency monitor
Image frequency 56.25 - 75.0 Hz modes within these parameters

Can anyone tell me what settings to use in the conf for the horiz and vertical rates?

TIA
maggs

---

### Post by firetux on 2006-02-27
So you just get a blank screen? Do you hear the drums? Do you get any error message? Can you login blindly (usename-enter-password-enter) and hear another sound?

If the answers are yes-yes-no-yes then do this: 

When you get the blank screen just do <ctrl><alt>F1

login.

type

```
sudo nano -w /etc/X11/xorg.conf

```


find this section:

```
Section "Device" 
                 Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"  
                 Driver           "fglrx" 
                 BusID           "PCI:1:0:0" 
                 **Option "monitorlayout" "LVDS,TMDS" **
EndSection
```
Sorry, I forgot to make it bold.


just add the section that is bold.

---

### Post by aysiu on 2006-02-27
This may help:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

For extra repositories:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

For the ranges, look for the **Monitor** section of your xorg.conf file and add these two lines: ```
HorizSync 31.47-83.0
VertRefresh 56.25-75.0
```

---

### Post by maggs on 2006-02-27
I added the option "monitorlayout"  and nothing changed. I hope that's what you meant. There was no code in bold.
I can blind login and hear the drums. The screen is just garbled and unreadable. There are no erros on boot. I can watch all the drivers load and all are ok. It's only when Gnome starts that I get garbled scrrens. If I plug the ribbon connector back my Sony LCD I can read it it's just really hard to see without a backlight.

Any other ideas?

maggs

---

### Post by wrtrdood on 2006-02-27
At this point you might also try CTL-ALT Keypad + (or -) to change resolutions and see if you get a usable display.

---

### Post by maggs on 2006-02-27
added the sync rates, no go. Tried the ctrl+alt+ +or- still nothing. I'm really at a loss to understand this. It's just a monitor. I know the video is working because I can see it on the internal LCD. Maybe this combo of video card and LCD monitor is just not going to work:cry: 

I've been working on this for a week on and off and read just about every post on video and monitors and I'm still no closer.

I did read somewhere that this nvidia has a set refresh of 75hz and the LCD is 60hz or maybe the other way around. Could this be possible?

maggs

---

### Post by firetux on 2006-02-28
I corrected my mistake in my previous post.
Did you also add the "LVDS,TMDS"?

---

### Post by maggs on 2006-02-28
Yes the option statement was added correctly. I'm still looking for more ideas but losing confidence. I think it will be easier to replace the backlight in my notebook display. :-|

---

### Post by firetux on 2006-02-28
Replacing the backlight is no option because it is not broken. It will not solve your problem(I think).

Maybe you can try to reinstall using some install-options like "vga=771", do some research on that.

Before that you could try to install the nvidia drivers as Aysiu said.

---

