---
title: "nvidia dual screens at different res"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by tyros8000 on 2007-02-18
Hi,

I am new to ubuntu and linux and so far love it.  i have everything sorted apart from my dual screens.

I have installed the drivers for my old nvidia gforce4 ti 4200 and works fine.

I now want my dual screens to work.  I have one which is 19" LCD at a resolutions of 1280x1024 and the other is a 15" LCD at a resolution of 1024x768.

I have the 19" working as my default fine but I want to hook my 15" screen up as a secondary screen.

I have followed these:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[http://www.ubuntuforums.org/showthread.php?p=1773584](http://www.ubuntuforums.org/showthread.php?p=1773584)

but nothing seems to have happened.

Any help is much appreciated.

Dave.

---

### Post by tseliot on 2007-02-18
Install the latest Nvidia driver via Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

then (after you get back to the desktop environment) type:
```
sudo nvidia-settings
```

and you will have a nice GUI to set dual screens

---

### Post by tyros8000 on 2007-02-18
nice piece of software.

i got it so it was wider but still only on one screen.  it doesn't seem to be picking up the second smaller screen.

any thoughts?

EDIT:

ok, i got the dual screens working well at resolution 2048x768 but i want the one screen to be 1024 high and the other 768 high.  how do i go about doing this?

---

### Post by tyros8000 on 2007-02-19
please, can anyone help?  i am really stuck.

---

### Post by dmcdante on 2007-02-25
ever thought about using the utility nvidia-xconfig? it set up a huge dualscreen-setup for me. different resolutions, too.

[Edit:]

there are multiple ways of setting up dualscreens: twinview, xinerama, separate screens. all have their advantages.
if you have a more detailed questions, email me on [email]danteonline@gmail.com[/email], i can send you my xorg.conf files and such, and help you too.
make sure you integrate the details on graka and screens in it and set a header to make me think it's not spam.
then if we get to solve it, post a guide on how you did it here for the benefit of others!

regards, dante

---

