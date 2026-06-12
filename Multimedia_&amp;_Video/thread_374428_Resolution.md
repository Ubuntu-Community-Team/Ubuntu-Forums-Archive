---
title: "Resolution"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by glok_twen on 2007-03-02
bottom line question is, how does an install know whether to allow the option of 1024x800 vs 800x600?

i used the same install of 6.10 on 2 different desktops. one ended up allowing me the option of 1024x800 in the System->Preferences->Screen Resolution dialogue. the other allowed only a max of 800x600.

i tried installing the 915resolution package and it said it was incompatible with the video chip.

i also looked at one of the config files that actually even listed 1024x800 as an option, but it wouldn't show up on the mentioned dialogue.

the only way i got to that resolution was to switch to kde. is there a way to do it from gnome that i missed?

thanks, gt

---

### Post by disturbedite on 2007-03-02
well, i think before xorg 7.2 it would determine that stuff according to which monitor/video card you choose.

since xorg 7.2 (released recently) xorg can work without xorg.conf and it automatically detects your hardware.  :)

---

### Post by poohma on 2007-03-02
I found that I just had to adjust the frequensy part of xorg.conf to get it working like I wanted to.

somehow it even ignores the resolution set in xorg.conf!?! :-/ (but hey...  it works)

Just find your monitors Horizontal and vertical freq. and input it in xorg.conf

This is for my Eizo FlexScan F77S:
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection


Its really easy to find these freq. if you know what monitor you are using :-)

---

