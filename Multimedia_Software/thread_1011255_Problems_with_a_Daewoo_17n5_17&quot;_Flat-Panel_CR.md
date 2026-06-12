---
title: "Problems with a Daewoo 17n5 17&quot; Flat-Panel CRT"
date: 2008-12-14
forum: Multimedia Software
---

### Post by zarcom on 2008-12-14
I fully understand, that in order to "optimize" or "set up" my monitor properly, is that I have to use the xorg.conf file to specify its settings.

Here are the specs of my monitor that I use (according to the site from Daewoo.com):

CRT

    * Type: 17" FST Type
    * Dot Pitch: 0.25 mm
    * Face: Anti-Glare / Anti-Static
      Anti-Reflection Invar Mask 

VIDEO

    * Bandwidth: 110 MHz
    * Frequency (H): 30 - 70 KHz
    * Frequency (V): 50 - 150 Hz
    * Max. Resolution: 1280 x 1024
      640 x 480 @ 150 Hz
      800 x 600 @ 110 Hz
      1024 x 768 @ 90 Hz
      1280 x 1024 @ 65 Hz

How would I be able to configure this in xorg.conf??  I am new to ubuntu, but I do know how to get into the file itsself, save etc...

Thanks in advance.

---

### Post by zarcom on 2008-12-15
[http://ubuntuforums.org/showthread.php?t=965660&highlight=monitor+listed+unknown](http://ubuntuforums.org/showthread.php?t=965660&highlight=monitor+listed+unknown)

well...slightly solved anyway, and here is what I did, this also may help out the rest of everyone here:

1) Go to your terminal and type in:

gksudo nvidia-settings

2) Configure your monitor and set it to your peroper refresh rate.

3) You may want to do this EVERY time you log in, I know its a pain, but unfortunately I have NOT found a necessery command for this yet, im sure there is one out there, but right now, just be happy with what you have, lol mine is at 86hz instead of 85, which is also very good.

I will go into detail much later.

Enjoy :).

---

