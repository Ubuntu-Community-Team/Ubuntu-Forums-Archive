---
title: "Screen size problems when mirroring laptop to a Tv using HDMI"
date: 2016-08-11
forum: Multimedia Software
---

### Post by irvine_himself2 on 2016-08-11
The basic problem is that the virtual Tv screen is bigger than the actual Tv screen resulting in the panel, task-bar and other useful bits not being visible or clickable on the Tv. My distro is Xenial Xerus with dual Intel/Nvdia proprietary drivers. Currently, I am using the Intel driver, but I have unsuccessfully tried to get it working with Nvidia.

For reference, here is the xrandr ouptut

```
memyself@Mine:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080     60.02*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i    60.00*+  50.00    59.94  
   1920x1080     24.00    23.98  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    70.07    60.00  
   1440x480i     59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   2152x1210_60.00  59.95  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

I know its fairly common problem that has been asked before, but the most relevant solution dates back to 2011 and the linked [Nvidia tutorial]("https://ubuntuforums.org/showthread.php?t=1795124") is appears to be dead, (or at least leads to a blank page.) 

Since using a lower resolution on HDMI1 makes the problem worse, I have been trying to set up a higher custom resolution using [this post]("https://askubuntu.com/questions/377937/how-to-set-a-custom-resolution") as a guide. The steps were as follows: 

```
# Get modeline
memyself@Mine:~$ cvt 2151 1210 60
# 2152x1210 59.95 Hz (CVT) hsync: 75.24 kHz; pclk: 218.50 MHz
Modeline "2152x1210_60.00"  218.50  2152 2304 2528 2904  1210 1213 1223 1255 -hsync +vsync
#
memyself@Mine:~$ xrandr --newmode "2152x1210_60.00"  218.50  2152 2304 2528 2904  1210 1213 1223 1255 -hsync +vsync
#
memyself@Mine:~$ xrandr --addmode HDMI1 2152x1210_60.00
```

This seems to be showing promise. At first the refresh rate was way to high, but when cutting it back to 30Hz I was able to see a flickering panel and task-bar, In other-words, the height seems to be very close, but the refresh-rate and width are still way off.

Am I on the right track, and if so, does anybody have any idea for the correct values of width, height and refresh-rate?

Thanks in advance

Irvine

---

### Post by irvine_himself2 on 2016-08-12
I am happy to report that after buckets of blood, sweat and tears, I have finally solved this problem.

Basically, it is not a Ubuntu/Linux problem, but rather a problem with the Tv. It is called [&#8220;overscan&#8221;]("https://www.google.co.uk/search?q=what+is+overscan&safe=off&client=ubuntu&hs=0hb&channel=fs&gbv=2&sei=3O-tV5zKIMSY6ASQl5TwBA"), and, contrary to much of the posted advice you will find with a google search, it has nothing to do with modelines, EDID&#8217;s, xrandr, Nvidia drivers&#8230; etc. Since Tv manufacturers play fast and loose with the various standards and terminology, there is no generic solution, and this adds greatly to the overall level of confusion. But, as a brief overview&#8230;. 

Overscan is partly a legacy from the analogue/teletext days and partly a response to poor broadcast quality around the edges of a TV stream. Essentially, it crops the image to a varying degree. See 

1) [http://www.howtogeek.com/252193/hdtv-overscan-what-it-is-and-why-you-should-probably-turn-it-off/](http://www.howtogeek.com/252193/hdtv-overscan-what-it-is-and-why-you-should-probably-turn-it-off/)

2) [https://www.engadget.com/2010/05/27/hd-101-overscan-and-why-all-tvs-do-it/](https://www.engadget.com/2010/05/27/hd-101-overscan-and-why-all-tvs-do-it/)

For us geeks, the real problem though is fixing it. Telling your average consumer that their expensive high definition digital Tv crops 3 or 4 % of the image is not a strong selling point. So, as stated above, Tv manufacturers prefer to obfuscate the terminology with advertising jargon. As you can see from the post linked below, there is great variation in what the manufacturers call it and how you fix it. (You will also note the number of unhelpful post suggesting it is somehow a problem with linux graphics drivers, display settings&#8230; etc.)

3) [https://askubuntu.com/questions/4358/how-do-i-fix-overscan-on-my-hdmi-hdtv](https://askubuntu.com/questions/4358/how-do-i-fix-overscan-on-my-hdmi-hdtv)

For reference: On my Tv, (a very cheap &#8220;Alba LCDW16HDF&#8221;,) using the remote to bring up the control panel, under &#8220;Picture&#8221; you see a property called &#8220;Picture Zoom&#8221;. It is fixed at 16:9 and there is nothing you can do to change it!!!!

This is probably the biggest single reason for why I was searching for a Ubuntu/Linux based solution. However, after fully digesting what post #3 above was actually telling me, I finally gave up on exotic modelines and other esoteric solutions. Exploring the Tv&#8217;s control panel further, I found under &#8220;Favourites&#8221; an option called &#8220;HDMI PC Full Mode&#8221; switching this on an et-voila, Bobs&#8217; your uncle.

EDIT:
I should add that, (interestingly,) in the control panel under "Picture" there was also a switch for "Game Mode", this did absolutely nothing as far as the overscan problem was concerned.

End Edit

So, for anybody else facing this problem, I strongly recommend you ignore any offered solutions that suggest using/altering xrandr, xconfig, drivers, modelines... and concentrate on exploring the Tv&#8217;s control panel. In essence, look for weird terminology designed to disguises the fact the Tv uses &#8220;overscan&#8221;.

Good luck 

Irvine

---

