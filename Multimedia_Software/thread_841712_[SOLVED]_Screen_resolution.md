---
title: "[SOLVED] Screen resolution"
date: 2008-06-26
forum: Multimedia Software
---

### Post by anthony2010 on 2008-06-26
Hi all.

I resolved the nvidia sound issues with a clean install of ubuntu 8.04 64 bit.

However I now have a screen full of HUGE letters and icons! Ive gone through System : Preferences : Screen resolution, without any joy at all.

A button on my monitor says for optimum performance I should set it at 
1680 x 1050. That isnt available on the menu.

Does anyone know what I should do to correct this? Its hurting my eyes!!

Thanks in advance.

Anthony.

---

### Post by Pjotr123 on 2008-06-26
Check this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by Dave Otter on 2008-06-26
Try


      alt + F2 >>sudo displayconfig-gtk
click on Model then chose your screan model

---

### Post by aeiah on 2008-06-26
you could also try setting it in nvidia-settings. open a terminal and launch it with sudo if you want the changes you make to be saved. if you havent got nvidia-settings, you should be able to 'sudo apt-get install nvidia-settings'

---

### Post by anthony2010 on 2008-06-26
THANK YOU Both!!!!!!!

I now have a good resource and my ubuntu is now looking and sounding good!

Carmina Burana in Mplayer...

Thanks once again :)

In your debt.

Anthony.

---

### Post by fudoki on 2008-06-26
> **Dave Otter said:**
> Try


      alt + F2 >>sudo displayconfig-gtk
click on Model then chose your screan model

This utility comes up, identifies my MGA Millennium 2-head.  Allows me to enter the monitor type and select the 1024-768 mode I need (the system insists on the unusable 800-600 mode since the "upgrade", regardless the content of the xorg.conf file...), and save it as "Shop" after successfully testing the video mode; BUT when I exit I am back in 800-600 and logoff and re-login or complete Restart do not cause the settings to be retained, even though they were set as "Root".

Any ideas about how one makes the new, correct settings "stick" so the computer can be, once again, used for some useful purpose?

Thanks in advance, these undocumented changes in "Hardy" are really frustrating and have lost me considerable business, so ANY realistic fix to the display problems will be VERY welcome.

---

### Post by Pjotr123 on 2008-06-27
> **fudoki said:**
> This utility comes up, identifies my MGA Millennium 2-head.  Allows me to enter the monitor type and select the 1024-768 mode I need (the system insists on the unusable 800-600 mode since the "upgrade", regardless the content of the xorg.conf file...), and save it as "Shop" after successfully testing the video mode; BUT when I exit I am back in 800-600 and logoff and re-login or complete Restart do not cause the settings to be retained, even though they were set as "Root".

Any ideas about how one makes the new, correct settings "stick" so the computer can be, once again, used for some useful purpose?

Thanks in advance, these undocumented changes in "Hardy" are really frustrating and have lost me considerable business, so ANY realistic fix to the display problems will be VERY welcome.

The solution is probably this: do NOT "save it as Shop". In fact: do not save it *at all*. Saving is only a means of saving a copy, not the real change. You want the real change done to your computer.

---

