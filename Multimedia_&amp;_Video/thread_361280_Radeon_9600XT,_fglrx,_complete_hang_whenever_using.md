---
title: "Radeon 9600XT, fglrx, complete hang whenever using 3D"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by marikka on 2007-02-14
Greetings.

I'm running ubuntu 6.10 with a Radeon 9600XT card.
I have fglrx installed, version 8.28.8

Everything runs smoothly, except  when using 3d apps, the
3d-acceleration works, I can do stuff, but after using for a while the whole computer
hangs completely. If I'm using Blender the screen just freezes while SecondLife seems to
shut down the monitor.

Thanks for your help in advance.

---

### Post by Airsix on 2008-04-19
hi, 
up for this problem!

I have got a p4 + gutsi + ati hd2400pro

i'm able to use my computer for normal things: mail, browser, etc, but when i try to use a program using 3D my system completely freezes. No response from keys, mouse, nothing happens when pressing ctrl+alt+bs or ctrl+alt+canc, 
i cannot switch to console, there is nothing to do, i need a brute reboot using the reset  button.

I have read about similar bugs, i tried the shown patches or fixes but the problem is still present.

There is not an exact moment, for example when using Secondlife or simply glxgears it can hang after 2 secs or after a minute or two. I was not able to go over 5 mins.

Any help would be appreciated, thank you in advance

---

### Post by pietjanjaap on 2008-04-19
With 7.04 i fix it this way.

Go to save mode.(with startup)
Then sudo dpkg-reconfigure xserver-xorg  
Choose the screen resolution you want to use, all the others disable.
Choose vesa driver.
save xorg file.

Then install/reinstall xgl server and compiz

Then install video driver(i did with envy), then everything worked.

---

