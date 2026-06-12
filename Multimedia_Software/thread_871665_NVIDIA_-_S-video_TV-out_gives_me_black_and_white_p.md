---
title: "NVIDIA - S-video TV-out gives me black and white picture"
date: 2008-07-27
forum: Multimedia Software
---

### Post by icouldntfindausername on 2008-07-27
I have nvidia 8800 Ultra and using 179.14.09 drivers. I'm trying to use TV-out with s-video, but it only gives me a black and white picture. In windows vista/xp I get colours, so I know the TV can handle it. As far as I know I need PAL-B, but I'm not sure what it is now. How can I get colours in Linux as well? :confused:

Thanks.

---

### Post by Rhubarb on 2008-07-27
From my previous experience a black and white picture is often from your video card outputting NTSC.  This can be fixed up by telling your card to output PAL.

But I'm unsure as how to do this (probably in the nvidia-settings somewhere, as a guess).
Perhaps some one here can help out with this.

---

### Post by icouldntfindausername on 2008-07-27
Thanks, but I can't find it anywhere in nvidia-settings. I need to change it to PAL-B, so maybe someone knows how to do that? :)

---

### Post by Rhubarb on 2008-07-27
Ok, this should work, but it may not, so first we'll backup the xorg.conf file:
```
cd /etc/X11/
sudo cp xorg.conf xorg.backup
```

So if things go wrong, you can restore to the previous working state by running:
```
cd /etc/X11/
sudo cp xorg.backup xorg.conf
```

It seems nvidia-xconfig should be able to do what you need, for the command line options run:
```
man nvidia-xconfig
```
nvidia-xconfig changes your /etc/X11/xorg.conf file, which allows you to control your video card settings / keyboard layout / mouse settings.
(though nvidia-xconfig is mainly to do with your video card settings).

So, in your case you may wish to try running:
```
sudo nvidia-xconfig --tv-standard=PAL-B --tv-out-format=SVIDEO
```
It is also possible to specify overscanning, twinview etc aswell.

---

### Post by jim_naisium on 2008-07-27
I have had this happen before, check both ends of your patch cable and make sure that none of the pins are bent over, one of my pins was bent over which ended up causing it to only display in black and white.

---

### Post by icouldntfindausername on 2008-07-28
Thanks, Rhubarb, that works :)

What it specifically does is adding two lines to the 'Section "Screen"' of the /etc/X11/xorg.conf file:

```
Section "Screen"
    Option         "TVStandard" "PAL-B"
    Option         "TVOutFormat" "SVIDEO"
```

So it might just be easier to add it to your file manually ;)

---

### Post by onesojourner on 2008-07-29
I will be trying this, this afternoon. I hope it works there are a lot of threads on these forums about this.

---

### Post by gregshldn on 2008-08-17
I fixed the b&w problem by putting an svideo to composite converter on the cable, and going into my TV in composite.

[http://www.maplin.co.uk/Module.aspx?ModuleNo=35935&doy=17m8&C=SO&U=strat15](http://www.maplin.co.uk/Module.aspx?ModuleNo=35935&doy=17m8&C=SO&U=strat15)

Full glorious colour, but somehow dirty.  I think I'll get over it tho!

This after a day of xrandr, tweaking nvidiva-settings and going nowhere.  My card : Asus Nvidia 7000GS

---

