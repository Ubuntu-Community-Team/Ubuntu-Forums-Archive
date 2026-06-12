---
title: "Browser Performances - Ubuntu 12.10 vs Windows 7"
date: 2013-01-06
forum: Multimedia Software
---

### Post by solidfish on 2013-01-06
I've just completed a dual boot installation of Ubuntu 12.10 on my Windows 7 machine. Its an old machine and its currently spec'd as follows:

AMD Phenom X4 965
12GB DD3 RAM
1.5 tb hd 7200 rpm
Radeon HD4870 graphics card (Gallium RV770 driver)

I've ran tests using Microsofts testdrive site:
[http://ie.microsoft.com/testdrive/performance/bubbles/](http://ie.microsoft.com/testdrive/performance/bubbles/)

I've used this bubbles one plus a couple of other ones that shows FPS.

I've ran tests using the following browsers:
Chrome 23.x
Firefox 17.x
Opera 12.x (with hardware acceleration set to 1)

When on Windows 7 (SP1), I get about 40 - 60 FPS for each of the browsers.

However on Ubuntu 12, its totally different. I get something like:
Firefox = 3 - 6 FPS
Opera = 10 - 15 FPS
Chrome = 30 - 35 FPS

Anyone know why these browsers are significantly slower on Ubuntu?

---

### Post by solidfish on 2013-01-06
Sorry my question might be too blunt. 

Would anyone know what I could do to determine why my Ubuntu browser performance is slower than Windows 7?

Perhaps some better tests out there than that Microsoft testdrive site?

---

### Post by offgridguy on 2013-01-06
In actual real world performance, do you find these browsers slower in ubuntu than windows ?

In my own case, i find very little difference in browser speed between windows and
ubuntu 12.04.  It would probably take a stop watch, which i don't have to measure any
actual difference.

---

### Post by solidfish on 2013-01-06
Ya actually it did seem a little slower which was why I ran the testdrive tests. I'm doing some searches and looks like Ubuntu is a little slower in performance overall compared to Windows 7 (??).

---

### Post by epikvision on 2013-01-06
Trying the testdrive on my Lenovo X220, I experienced a framerate of 1-5 on my firefox as well.   Quite peculiar, but performance-wise, Ubuntu didn't fail me in web browsing.  

Or maybe I just don't care about the numbers. :)

---

### Post by brainwash on 2013-01-06
On my machine even the Windows version of Firefox (-> wine) outperforms the native version.

---

### Post by Yellow Pasque on 2013-01-06
Midori (WebKitGTK-based) does pretty well for me. Firefox is abyssmal in that IE bubbles test. I'm trying to figure out what that test is using (WebGL?).

---

### Post by czgirb on 2013-01-07
I used XP SP2 and 12.04 ... both with Chrome.
To me ... Ubuntu + Chrome outperform windows

---

### Post by solidfish on 2013-01-08
I'm looked into it a bit more and I think Ubuntu definitely outperforms Windows XP but comes up short against Windows 7. And looks like IE10 is actually going to be faster than any of the other browsers. 

My ubuntu browsing for general sites is alright, just on some of the heavy animation sites (like browser games) you can see a performance difference.

---

### Post by linthas on 2013-04-08
> **offgridguy said:**
> In actual real world performance, do you find these browsers slower in ubuntu than windows ?

In my own case, i find very little difference in browser speed between windows and
ubuntu 12.04.  It would probably take a stop watch, which i don't have to measure any
actual difference.

I find windows7 to be much faster than ubuntu _12.10_. I can tell that not only does firefox run slower, but so does the file browser. I would get screen freezes about every 15 mins that would last up to 2 mins long. Mouse would move but clicks would get no response during those time periods. Ubuntu 12.10 also takes much more time to boot than win7 on my pc, sometimes with what seems like graphical errors(ie:sometimes I see the ubuntu logo with 4 white dots, sometimes the ubuntu logo is repaced with just text 'ubuntu', sometimes I get black screen with white text first). Note: Booting in Legacy mode.

Referrenced OS's: Win7 64Bit SP1 & Ubuntu 12.10 64Bit
CPU:AMD64 Phenom II x4 BE DENEB 3.2GHZ
RAM:4GB DDR3(1333)
GPU: NVIDIA GEFORCE 9500
HDD:1TB 7200rpm 32mb cache

---

