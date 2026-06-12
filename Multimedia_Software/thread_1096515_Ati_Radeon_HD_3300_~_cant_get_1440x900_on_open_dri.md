---
title: "Ati Radeon HD 3300 ~ cant get 1440x900 on open driver"
date: 2009-03-15
forum: Multimedia Software
---

### Post by tehk on 2009-03-15
Oi!

I really hope to get some help on this one as I've contibuted over 5 hours learning about writing a proper xorg.conf customized for my video card and monitor. Too bad, I still am not a master enough to get it to work.

Upon initially installing the open driver, I'm limited to 1280x1024 resolution, but would rather go 1440x900 as that's what I used on the closed driver.

So, here's the best xorg.conf file I could come up with to date:

```
Section "Device"
        Identifier "RadeonHD3300"
        Driver "ati"
        BusID "PCI:1:5:0"
EndSection
Section "Monitor"
	Identifier "HannsG HW191D"
	Option "DPMS"
        HorizSync 28-72
        VertRefresh 43-60
	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection
Section "Screen"
        Identifier "Default Screen"
        Device "RadeonHD3300"
        Monitor "HannsG HW191D"
        DefaultDepth 24
        SubSection "Display"
                Depth      24
                Modes      "1440x900" "1280x1024" "1024x768"
        EndSubSection
EndSection
```

When I save this conf and restart kdm, x server just tries to startup unsuccessfully over and over again. Oh yah, using the closed driver is not an option for me as I am using linux-rt and that kernel does not support it.

halp!

---

### Post by chadjensen on 2009-03-15
I used to have to force my video card resolution by typing 

sudo dpkg-reconfigure xserver-xorg

and unchecking the resolutions i didn't want and checking the ones I did. Try that

---

### Post by tehk on 2009-03-15
that tool never worked for me, it only allows me to configure xserver for my keyboard and never asks for display or graphic settings.

---

### Post by chadjensen on 2009-03-15
Yeah I just found out they did away with major portions of the config options in that command. doh! sorry try this.

sudo displayconfig-gtk

---

### Post by tehk on 2009-03-15
dont have that tool, and cant install it. also, dont have xandr either. :(

---

### Post by tehk on 2009-03-15
i feel like im just missing one line or something small... any ideas?

---

### Post by FormerSlacker on 2009-03-15
I'm not sure if this helps but...

Is the open source driver grabbing the edid of your monitor? I had a similar problem with an Nvidia that I solved by saving the edid with get-edid and then forcing the nvidia driver to load it.

I'm not sure if the ati driver has such a option.

---

### Post by tehk on 2009-03-15
it turns out that the ATI Radeon HD 3300 chip is 'too' new for xserver 6.9 which is in intrepid. supposedly 6.11+ will support it in jaunty, but im not daring enough to upgrade to alpha6 of that just yet, think ill wait. even as such, the new drivers in xserver 6.11 support only 2d and dont provide any 3d support. so, im going back to my old nvidia 7600 GT which runs flawlessy w/o any xorg.conf :)

---

### Post by markbuntu on 2009-03-16
You can use the latest fglrx driver 9.2 from ati with that chipset.

---

### Post by tehk on 2009-03-16
yes, but if u read my first post, i said i wanted to use the open driver not the closed one. the reason for this is that it works under linux-rt whereas the fglrx driver doesn't at all.

---

### Post by markbuntu on 2009-03-16
Then you should try the radeonhd driver instead of ati. No 3D there either but 2D works.

---

