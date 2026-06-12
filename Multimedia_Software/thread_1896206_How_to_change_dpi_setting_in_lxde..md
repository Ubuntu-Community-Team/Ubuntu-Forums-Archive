---
title: "How to change dpi setting in lxde."
date: 2011-12-16
forum: Multimedia Software
---

### Post by mystika1 on 2011-12-16
Hi,
I am trying to set my dpi settings in lubuntu. There is no GUI that I know of to change dpi settings. I have found threads indicating that I should edit the xorg.config file and add the following to the monitor section...
> Section "Monitor"
    Identifier "Monitor0"
    Option   "DPI" "96 x 96"
EndSection

However...I don't have a section for monitor in my xorg.config file. Should I just sudo into leafpad and paste the entire section??? I really don't want to screw things up but..I have already tried to enlarge the font in openbox settings manager and currently still have tiny fonts. I also have an NVidia card so I went into those settings and changed resolution. That made my fonts for online viewing much bigger but everything else is still the same. 

Thanks,

Penny

---

### Post by SteveDee on 2011-12-16
> **mystika1 said:**
> ...I don't have a section for monitor in my xorg.config file. Should I just sudo into leafpad and paste the entire section??? I really don't want to screw things up but...

I suggest you make a copy of your xorg.conf (call it xorg.last or something) then go ahead with the edit of xorg.conf.

When you reboot, if things go really bad and you can't edit it back, you can always boot from a LiveCD and navigate to your hard drive and rename your xorg.last to xorg.conf.

---

### Post by mystika1 on 2011-12-16
Well, 
I tried that and nothing changed. I am really stumped on this one...

Penny

---

### Post by SteveDee on 2011-12-16
> **mystika1 said:**
> ..I am really stumped on this one...

It looks like you can check the current DPI like this:-
```

xdpyinfo|grep res

```
...and you can set it like this:-
```

xrandr --dpi 118x118

```
...so you can check the affect of any change.

---

### Post by mystika1 on 2011-12-16
Current resolution is set at

> resolution:    49x50 dots per inch
    ButtonPressMask          ButtonReleaseMask        EnterWindowMask    

and when I run the second command I get this...

> xrandr: Failed to get size of gamma for output default


  :confused: I am clueless.  :D

Penny

---

### Post by mystika1 on 2012-01-31
Ok, I know this post is a bit aged but I thought I would post my solution in case someone else could benefit from it. I have an nvidia card and lubuntu installed it quite easily but I needed to run:

> sudo nvidia-xconfig

in order to generate the file that I was trying to edit.(xorg.conf) Once that is done the solution to add line

> Option "DPI" "96 x 96"

in the monitors section of xorg.conf will work.

Thanks,
Penny

---

### Post by juanfi on 2012-02-05
The nvidia trick worked perfectly, Thanks!!

(on an asus barebone with NVIDIA and Ubuntu 11.10)

---

### Post by mystika1 on 2012-02-05
I am glad it worked. :)

Penny

---

