---
title: "intermittent onboard video"
date: 2011-03-19
forum: Multimedia Software
---

### Post by A.B. O'Kelley on 2011-03-19
hello all. let me start by saying that i am a returning ubuntu user, but my experience level is always in question...
 
i am building a custom car computer. i have installed 10.10 netbook remix. the motherboard is a gigabyte ga-h55n-usb3. the system is very barebones, meaning necessities only, at the moment. also of note is that this is about my 50th carputer, and the only thing different this time is the OS i am choosing.
 
i have 2 questions:
 
1) the onboard video seems to work fine, exceptionally even. however, after some amount of time, it freaks out, and looks like the "snow" you might have seen on an old tv when you had no picture, except this version has colors in it. i have added a pci card for video, but do not wish to use it permanently, as space is an issue in the case i am using.
 
2) the reason that i chose to use the netbook version for this install is the touch-friendly front end with the large attractive icons and the task bar on the left side of the screen. i thought that setup would be the default for the netbook edition, but it apparently is not. how do i turn this feature on?
 
feel free to call me a newb, a boob, or anything else you fancy, as long as you can contribute to solving my issue(s).
 
thank you for reading

---

### Post by BicyclerBoy on 2011-03-19
Your on-board video will be the GPU in the i3 or i5 processor ?

You can try making sure you are using the i965 video driver..
You could get the latest from Xorg Edgers ppa..

Other info from
[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

look in std output of:
lsmod

Look in /var/log/Xorg.0.log for info about driver that loads

I thought the 10.10 netbook remix uses unity-mutter by default..
Have you installed netbook remix on a fresh/bare/blank system ?

Have you used CAN bus interface in any of your previous car-puters ?

---

