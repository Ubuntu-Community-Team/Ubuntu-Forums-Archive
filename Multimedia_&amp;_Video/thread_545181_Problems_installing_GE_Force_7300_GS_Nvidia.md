---
title: "Problems installing GE Force 7300 GS Nvidia"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by acl123 on 2007-09-07
Hi,
I am having endless troubles trying to get my graphics card working.

I have read about 4 or 5 different ways to get it installed but each one ends with a different problem.

I finally found what seems to be the easiest method - using the Restricted Device Manager and simply clicking "enable" for the Nvidia accelerated graphics driver.

However I get this error message after trying to enable it:
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb: subprocess pre-installation script returned error exit status 2

Can someone help me with this?
I am using Ubuntu 7.04.
Thanks in advance

---

### Post by ubunoobie on 2007-09-07
> **acl123 said:**
> Hi,
I am having endless troubles trying to get my graphics card working.

I have read about 4 or 5 different ways to get it installed but each one ends with a different problem.

I finally found what seems to be the easiest method - using the Restricted Device Manager and simply clicking "enable" for the Nvidia accelerated graphics driver.

However I get this error message after trying to enable it:
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb: subprocess pre-installation script returned error exit status 2

Can someone help me with this?
I am using Ubuntu 7.04.
Thanks in advance

Hi, I'm not sure if this will help you or not... but have you tried Envy?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I hope this works because I planning on using a GeForce 8400GS soon in a new rig I'm building... let me know.

---

### Post by acl123 on 2007-09-09
Great thanks for that.
Yes it all seemed to work with Envy! It had trouble installing the packages but it gave me a list of the ones I needed in the log so I could manually install them.

The problem is now that my resolution is wrong and I can't fix it.

On the recommended resolution for my monitor (1400x1050), the display is too big for my monitor (about 2 cms are cut off at the top and bottom). Using my monitor's built-in controls I can adjust the horizontal size but it doesn't have an option for controlling the vertical size.

Secondly I appear to have slightly fuzzy lines running horizontally across my screen, as though the resolution is not set correctly.

Thirdly, my monitor pops up a message telling me I am not using the recommended resolution although I have set the resolution correctly under Preferences->Screen Resolution.

This is a difficult problem to describe - please let me know what other information I can provide.

---

### Post by acl123 on 2007-09-09
I managed to fix the above problem by playing with the refresh rate a bit under Preferences->Screen Resolution

---

### Post by ubunoobie on 2007-09-11
Great! Thanks for the follow up... I am actually going to be installing my vid card tonight. I hope it all works.

---

