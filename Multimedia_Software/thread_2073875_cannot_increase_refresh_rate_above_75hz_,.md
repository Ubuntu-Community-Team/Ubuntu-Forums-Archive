---
title: "cannot increase refresh rate above 75hz ,"
date: 2012-10-20
forum: Multimedia Software
---

### Post by paichkash on 2012-10-20
hi
i have dell optiplex 755 . it has builtin intel gma 3100 (not x3100) .. i cannot set it refresh rate above 75hz while resolution is set to 1280X1024..

i would like to set the resolutio at 1152 X 960 ( dont konw the exact values but in i want a value above 1024 x 768 and below 1280 X 1024 . and at a refresh rate of 80 hz .. as i have crt and at 75 its flickering a bit.. 

in windows xp i have no issue with this. i can set to 85hz ..

i am using ubuntu 10.04 lts
Thanks

---

### Post by paichkash on 2012-10-25
please any help ?

---

### Post by paichkash on 2012-10-26
ok i solved the issue .. by following this [post]("http://ubuntuforums.org/showthread.php?t=975657") . 

> **blackened said:**
> Reconfiguring xorg under 8.10 doesn't work anymore for almost anything (unless you have a manually configured xorg.conf and want to restore it to a clean one). Your best bet will be using xrandr to add new resolutions/refresh rates. Should be something like this:

Find the modeline for your appropriate resolution/refresh a la:
```
cvt **<hres> <vres> <refresh>**
```

This will spit out a modeline that you need to paste into the following command:
```
xrandr --newmode **<modeline attained from cvt command>**
```

Then add it to the monitors listed modes (example for 1280x1024@75):
```
xrandr --addmode VGA 1280x1024_75.00
```

After doing all that you should see the newly listed resolution in System->Preferences->Screen Resolution.

Sorry if this is confusing. It's not exactly an easy thing to give examples of.


i got a glitch when i typed the third command and then i typed the xrandr to find my default display is not vga but vga1 .. 

follow that post for if ur issue is not solved or ask me ..

---

