---
title: "can't configure a new samsung monitor t260hd"
date: 2009-05-10
forum: Multimedia Software
---

### Post by giampaolo44 on 2009-05-10
hi guys,

i just bought a samsung monitor 26", model t260hd, but ubuntu (rel. 9.04) shows only 1025x768 as the best resolution available, while the monitor has 1920x1200.
it exchanges the monitor for a 25"...

i already looked around in the forum and on mister G, but no luck.

anybody has a spare sec to help?

bear in mind that i'm a pale green user of ubuntu... i don't even know how to open the terminal yet :-/


thanks a lot in advance,
giampaolo

---

### Post by giampaolo44 on 2009-05-11
please please pleeeaasee

: )

---

### Post by giampaolo44 on 2009-05-11
oky, with the help of a friend at least now i know i have an nvidia GeForce 9500 GT.
we kind of figured that i have to modify the xorg.conf manually, and i got there, but am not very sure of what i'm doing....

should i modify the 
    SubSection "Display"
        Virtual    2048 768
    EndSubSection
with the appropriate resolution (1920x1200) or else?

should i do something more as well?

cheers...

---

### Post by giampaolo44 on 2009-05-12
i figure that the virtual is useless...
i tried to set a metamode to 1920x1200 but zero.

any hint ?

---

### Post by giampaolo44 on 2009-05-13
guys i'm ready to do my share, but if this is the help that a green gets in here, billyG will stay around for the next few centuries.....

---

### Post by xc3RnbFO8P on 2009-05-13
Did you enable  the restricted drivers in
System> Administration> Hardware drivers

---

### Post by aussieboy on 2009-05-13
I had similatr problems with 8.04 with an older NVIDIA chip set.  I solved the problem by editing the /etc/X11/xorg.conf file and doing the following
1. putting screen horizontal and vertical refresh rates using
    HorizSync 31.5-80  (my monitor values
    VertRefresh 56.3-75.1  (you set yours from your monitor manual)
 after model name and before the modeline commands.
2. ensure the modeline commands cover all your display options 
     eg. 640x480@60 , 800x600@56 , 1024x768@60 etc 
   these modeline commands MUST reflect your monitor capabilities.
3. in the "Screen" section make your Virtual command reflect the maximum screen display you want on your monitor eg. Virtual 1024 268 or Virtual 1280 1024 etc 
  only one command and one size.
4. in same section ensure the Modes command cover all the required display modes that you requirer and that these equal the number of modeline commands in the "Monitor" section
eg.  Modes "1024x768@60"  "800x600@56"  "640x480@60"
These must equal to number of modeline command values.
5. Ensure that you have enabled the device drivers in the propietary drivers area 
System/administration/hardware drivers then
6. REBOOT 
and you should be OK

Hope this helps

---

### Post by giampaolo44 on 2009-05-14
yes, the nvidia drivers (rel 180) are enabled

anyway: thanks a lot.
i'll try the rest and let you know (hope i'll be able to do it all :)

---

