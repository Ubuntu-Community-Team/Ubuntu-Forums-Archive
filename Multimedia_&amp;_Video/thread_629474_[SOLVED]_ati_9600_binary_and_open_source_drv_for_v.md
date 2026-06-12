---
title: "[SOLVED] ati 9600 binary and open source drv for vga and dvi"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by d3ni5 on 2007-12-02
hi,

My OS is Gutsy.

i spent whole weekend tring to start it working, but without success..

I have asus videocard with ati 9600 chipset. I connected LCD monitor via VGA D-SUB cable and Panasonic plasma panel via DVI - HDMI cable.

I'm using ati open source driver and now can configure screens using xrandr, but plasma panel connected via dvi doesnt show video (black box). How to configure overlay on the plasma dvi?

I tried proprietary driver (fglrx) from distribution and even builede by myself, but this drivers very unstable. My X is teminated from time to time , and if I press ctrl+alt+backspace - X restarted and hanged in the black screen, although num lock is working it is impossible to get even terminal by ctrl+alt +f1 etc....
Right now if I try "fglxinfo" I got segmentation fault error.


I never used to write to this forum, but after this weekend I'm even thinkin to switch back to Win, after 1 year of ubuntu, since each simple task become puzzle ....

---

### Post by acoustibop on 2007-12-02
Sounds like you may not have removed the fglrx driver properly, d3ni5.  fglrxinfo shouldn't work at all if you don't have an fglrx driver installed - you should just get a couple of lines advising you to install the repository driver.

If you do want to install the repository driver, don't use apt-get or Synaptic, use the Restricted Drivers Manager.  It does the job perfectly.  Nothing in Windows works that well!

If you want to install the latest fglrx driver, 7.11, I'd recommend the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") installation method.  I'm running that driver now on a 9800 XT and it seems rock solid to me - Compiz works perfectly.  The method is very easy: it's laid out line by line and all you have to do is copy-and-paste the lines into a terminal and make a few simple decisions - such as whether you've already installed the fglrx driver .

---

### Post by d3ni5 on 2007-12-02
>> Sounds like you may not have removed the fglrx driver properly, d3ni5. fglrxinfo shouldn't work at all if you don't have an fglrx driver installed - you should just get a couple of lines advising you to install the repository driver.  

yes right. segmentation fault was while the fdriver was installed

I tried both methods through restricted manger and installin it from package downloaded from ati (according to instructions) .

both ways driver hangs...

---

### Post by d3ni5 on 2007-12-04
I realized that this is library mess provided by nvidia driver when I replaced my vnvidia videocard by ati videocard

[http://ubuntuforums.org/showthread.php?p=3888885#post3888885](http://ubuntuforums.org/showthread.php?p=3888885#post3888885)

---

