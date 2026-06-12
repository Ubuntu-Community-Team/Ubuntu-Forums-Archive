---
title: "1440x900 resolution"
date: 2009-08-14
forum: Multimedia Software
---

### Post by wintersun on 2009-08-14
Hi everyone!

I'm new here, and I'm also very new to ubuntu and linux overall. So far everything works perfect, and I really really like what I see, but I just can't seem to set my monitors default resolution, which is 1440x900 as mentioned in the title. I tried to follow older relevant topics on the forum, but all I got was a messed up xorg.conf file, so I reinstalled ubuntu. And here I am now :)

I'm running the latest 9.04 version of ubuntu, and my graphics card is nvidia 9500 gt.

Could anyone help me fix this? I'm really new to all this, so it would be great if anyone would have the nerves to go easily step by step.

Thanks in advace!

---

### Post by sharkbite1414 on 2009-08-14
Have you tried installing the nvidia drivers (System > Administration > Hardware Drivers)?

---

### Post by wintersun on 2009-08-16
Hey

I'm so sorry for not replying earlier. I've been too busy last few days, and then I forgot I posted. Anyways, good news is I found a way to set this up!

This is what I added to my xorg.conf file:

Section "Monitor"
  HorizSync    30-81
  Identifier   "Monitor[0]"
  ModelName    "1440X900@60HZ"
  Option       "DPMS"
  VendorName   "--> LCD"
  VertRefresh  56-75
  UseModes     "Modes[0]"
EndSection 

Section "Modes"
  Identifier   "Modes[0]"
  Modeline      "1024x768" 76.16 1024 1080 1192 1360 768 769 772 800
  Modeline      "1024x768" 64.11 1024 1080 1184 1344 768 769 772 795
  Modeline      "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync -vsync
EndSection 

Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1440x900" "1024x768"
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1440x900" "1024x768"
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1440x900" "1024x768"
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1440x900" "1024x768"
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1440x900" "1024x768"
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Works great now!! Sharkbite, thank you so much for replying and willing to help. Hopefully someone with the same problem will run onto this and find it useful.

Thanks!

---

### Post by gogogo111 on 2009-08-16
Thats strange. I haven't had to edit my xorg.conf since 6.06? 

Did you install the drivers? You may have the correct resolution but not any drivers installed for the card.

---

### Post by wintersun on 2009-08-16
> **gogogo111 said:**
> Thats strange. I haven't had to edit my xorg.conf since 6.06? 

Did you install the drivers? You may have the correct resolution but not any drivers installed for the card.

Yes I did! But I didn't use the latest version (there were 2 available), cos I found somewhere that it was possible to achieve with this older version (173).. So I just followed that. Now I can't activate this newer driver version (180), cos I get the error message stating that xorg.conf is invalid. I wonder how will I update drivers in the future if this can't be avoided?

---

### Post by dargles on 2009-08-17
> **wintersun said:**
> Yes I did! But I didn't use the latest version (there were 2 available), cos I found somewhere that it was possible to achieve with this older version (173).. So I just followed that. Now I can't activate this newer driver version (180), cos I get the error message stating that xorg.conf is invalid. I wonder how will I update drivers in the future if this can't be avoided?

Thanks, Wintersun :KS !
I've just upgraded to 9.04 and was trying to work out how to get my external monitor (Iiyama E1902WSV) working properly again.  I cut and pasted your code into my xorg.conf and it works a treat!

BTW, if this causes a problem with future updates, there's a fix mentioned in the xorg.conf itself to get it to revert to auto updates.  Might want a copy of the code fix first though...
Regards, David

---

