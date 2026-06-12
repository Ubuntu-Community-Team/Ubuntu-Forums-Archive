---
title: "ATI Radeon 2100 issues."
date: 2008-07-21
forum: Multimedia Software
---

### Post by ewh1533 on 2008-07-21
Ok. I've spent the last few days working this out, while the situations improved vastly, it isn't completely resolved. 

Heres the output 
```

:~$ lspci -n | grep 0300
01:05.0 0300: 1002:796e

:~$ lspci|grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100

```

I'm using the onboard graphics adaptor for the gigabyte motherboard ga-ma74gm-s2h.

Ati doesn't even list this radeon 2100 at all.. so there are no specific drivers for it. I ran Envy and restarted, that at least let me run in full graphics mode, though a little buggy at that.

I have the range of my resolution, however, it's still very faulty. It locks up after the screen saver comes on if I try to get back to the desktop. Even the screen saver menu locks up if I let it run too long. Games and video flicker badly. I'm hoping this is just something that can bet tweaked, otherwise I'm back to square one with the graphics driver.

---

### Post by ewh1533 on 2008-07-22
Well, aparently the flickering is a result of the desktop visual effects. Turned off, the flickering completely stops. 

However,still having an issue of it freezing in the screen savers..

---

### Post by pritishpratap on 2011-11-03
Well I just checked and ATI does have a listing for Radeon 2100. 

It can be found here [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) if you choose the system type as "Integrated Motherboard Graphics"

---

