---
title: "which video driver to use for intel mobile 915 w/ GUTSY"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by silvari on 2008-01-13
I have a Toshiba laptop with an Intel Mobile 915GM/GMS/910GML video adapter. I'm running Gutsy (7.10).

Having the following problems:

1. I have a  Gateway FPD2275 TFT LCD display hooked up via VGA cable. The optimal resolution for this display is 1680x1050. But the best resolution that Gnome with do, is 1440x900 at 60Mhz. Funny thing is, I have xorg.conf set up to use 1680x1050 at 75 , but in Gnome's 'Screen Resolution' app, neither '1680x1050' nor '75' are options.   

2. I have done so much futzing around with this, at this point, I have no idea what driver I should be using. At one point (when I was at Feisty?) xorg.conf was using the 'i810' driver, and I also installed the i915resolution package (but I don't know if I ever got it doing anything useful). Since upgrading to Gutsy, xorg.conf is now using the 'intel' driver. And if I run 

> dpkg-reconfigure xserver-xorg

... the 'i810 driver isn't even an option anymore

3. When I try to play DVD's, downloaded video, etc. things look pretty nasty Colors are all off. Yes, xorg.conf is set to 24-bit . 

SO: My questions are:
1. What driver is the recommended driver, for an Intel Mobile 915GM/GMS/910GML, under Gutsy? And, what's the best way to get / install this?
2. Is the use of '915resolution' needed or recommended, with the recommended driver?
3. Thoughts on why Gnome seems incapable of seeing and using all the resolutions / modes supported by the card, especially the 1680x1050 ? 

Thanks VERY MUCH in advance for any assistance you can give. I have spent a ridiculous amount of time trying to get my (rather awesome) external display to work under Linux. I don't want to have to keep rebooting into Windows just to watch DVD's.

---

### Post by silvari on 2008-01-14
Bump.

Been keeping some updates here:
[http://ubuntuforums.org/showthread.php?p=4132670](http://ubuntuforums.org/showthread.php?p=4132670)

Any ideas would be much appreciated.

---

