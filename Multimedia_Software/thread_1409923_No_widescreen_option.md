---
title: "No widescreen option"
date: 2010-02-18
forum: Multimedia Software
---

### Post by Sam3280 on 2010-02-18
Hi,
I have had a few problems so I have done a fresh install and I am now using 9.10 however I now remember that I had problems when I first got my widescreen monitor. I currently can't find how to change the resolution to 16:9 as the only options in display properties are 4:3. I believe I may need nvidia drivers can anyone help. Thanks

---

### Post by Chromagnum on 2010-02-18
If you go to the **System>Administration>Hardware Drivers**, you will find drivers in there. Choose the recommended one and activate. After that, if by any chance *Display Properties* still won't give you the 16:9 aspect ratio, then go to **System>Administration>NVIDIA X Server settings**. You can change the resolution there. But of course you should do the activate *Hardware Drivers* first.

Hope that will help.

Edit to add:
If you still having problem after install recomended Nvidia drivers perhaps this thread will give you a better solution. [http://ubuntuforums.org/showthread.php?t=1307848]("http://ubuntuforums.org/showthread.php?t=1307848")

---

### Post by Sam3280 on 2010-02-21
I have treid going into hardware drivers but none are found. I am using Karmic now

---

### Post by Sam3280 on 2010-02-22
Could anybody suggest anything

---

### Post by Sam3280 on 2010-02-27
Could someone please help. I have tried the link suggested but it seems too complicated for me. Here is the information i get from system testing

Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9

I have tried going into Hardware drivers but no drivers show up. Another problem is that im not sure what model graphics card i have.

Thanks any help would be great

---

### Post by no2498 on 2010-02-27
you need a x window sever
sorry i can not help more than that

---

### Post by Sam3280 on 2010-02-28
Can i install an x window server through terminal or am i not understanding what an x windows server is

---

### Post by efflandt on 2010-02-28
Look in /var/log/Xorg.0.log to see what modes might show up there, but not active.  Then see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution).  Pay attention to what **xrandr** calls your video devices.

From that I figured out how to set a 1360x765 mode that seemed to be an optimum mode for connnecting VGA from my desktop to a display that said it was 1366x768.

Although for a 1080p screen I had to get a mode from a DVI to HDMI connected desktop because the 1920x1080 mode that cvt came up with was pillar boxed and offset from center.

For an old laptop limited to maximum 1360x1360 (it would error if I tried to set a mode bigger than that) I came up with a 1360x768 mode that worked on the 1080p HDTV.

---

### Post by Sam3280 on 2010-03-01
I can see all the resolutions in /var/log/Xorg.0.log . but im unsure how to enable them. do i use the commands from the above link in a terminal?

---

### Post by efflandt on 2010-03-01
Yes you can use xrandr commands in a terminal (xterm), but it is impossible to be specific without knowing the native resolution of your monitor.

---

