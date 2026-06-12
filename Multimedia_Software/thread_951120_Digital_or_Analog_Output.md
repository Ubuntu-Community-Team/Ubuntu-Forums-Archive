---
title: "Digital or Analog Output?"
date: 2008-10-17
forum: Multimedia Software
---

### Post by adduds on 2008-10-17
When i boot up into ubuntu after gdm screen my moniter flickers a bit

it seems to get confused whether to use digital and analog.
if dvi cable is only cable won't have video
but analog (serial cable) it will

any ideas?

cheers,
ad.

---

### Post by Tharmas on 2008-10-17
I guess that you are using a resolution in Ubuntu which is not native for your monitor.
In my experience, in digital (DVI cable) mode, you have to stick with the native resolution of the monitor. You can have higher resolutions only in analog mode (with VGA cable).

---

### Post by adduds on 2008-10-18
1680x*1050 is the native resolution of my moniter though?

---

### Post by Tharmas on 2008-10-19
You haven't tell us what is the model of your monitor.
But, assuming it's the one you have in your sig, you can check [the manual of Samsung SyncMaster 193s]("http://www.samsung.com/ca/support/search/supportSearchResultView.do?group=&group_cd=&type=&type_cd=&subtype=&subtype_cd=&model_nm=193S&dType=D&vType=L&mType=&model_cd=&menu=download&prd_ia_cd=&disp_nm=193S"), where it clearly says that your maximum (native) resolution is 1280x1024.
You can only have 1680x1050 resolution (fake, by interpolation) in analogue mode.

---

### Post by adduds on 2008-10-21
moniter is a Samsung SyncMaster 226BW 22" Widescreen sig is outta date lol

found this clip of code to add the the xorg.conf

If i use this would that be good?

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" 
    EndSubSection

can i do anything about my dvi output with this part of the code in the xorg.conf file?

---

### Post by adduds on 2008-10-21
or is it under

Section "Monitor"
    Identifier     "SyncMaster"
    DisplaySize     432    324
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

---

### Post by adduds on 2008-10-22
BUMP! Still need help guys thanks!

cheers,
ad.

---

### Post by adduds on 2008-10-23
Anyone know how to get my DVI working. analog works but i want dvi to work

---

### Post by adduds on 2008-10-25
BUmp

---

