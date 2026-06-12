---
title: "Video Card and older IBM A50"
date: 2010-05-29
forum: Multimedia Software
---

### Post by wannabegeek on 2010-05-29
Hi all,

I made a mistake and bought  a $50 IBM A50 to use as a media server...
Installed Karmic on it and figured out that the video card couldn't handle
anything beyond the factory setting of 800:600, something like that...

I have not taken the time to learn about video cards and now I suffer....
I found this "solution" 
**[SIZE=2]EVGA 256-P1-N399-LX GeForce 6200 256MB 64-bit GDDR2 PCI Video Card[/SIZE]**


which has mixed reviews on newegg

I want to use this machines( or another) to playback movies on my flat screen.
I suppose I need to find out more about my TV as well...

could use any advice and help,
thank you,
wbg

---

### Post by jerrrys on 2010-05-29
how much do you want to spend?

---

### Post by wannabegeek on 2010-05-29
Amazon has it for ~$40.00  I'd spend that...
do you think it's worth it?

---

### Post by jerrrys on 2010-05-29
[http://www.geeks.com/products.asp?cat=VCD](http://www.geeks.com/products.asp?cat=VCD)

---

### Post by jerrrys on 2010-05-29
did a little research on the A50 and true, it has crap on board video, but im wondering, have you actually hooked it up and just tried it as is?

---

### Post by wannabegeek on 2010-05-29
yeah I did...no options at all, just the 800:600 tiny as hell..
I saw some more positive reviews about that video card above...
I also saw a cheaper $20 on at geeks.com, but not sure I want to risk the drivers being bad...

wbg

---

### Post by jerrrys on 2010-05-29
how did you try to adjust screen size?

---

### Post by wannabegeek on 2010-05-29
I went to system>pref>display

then used mirror...oops maybe that was bad...
I've had trouble getting my thinkpad to have various options and figured out tonight to not use mirror screen
Maybe I should try that with A50 ...

I'll post back\wbg

---

### Post by wannabegeek on 2010-05-29
no luck

there are no options available in Display...none
My lenovo has decent options can get OK wide screen res...
wbg

---

### Post by jerrrys on 2010-05-29
[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

---

### Post by wannabegeek on 2010-05-29
Those pages are great ....thanks so much for the links....

I have been using Ubuntu for about a year...I need to make to make ubuntugeek and ubuntudocs
my first go to  from now on....novice mistakes 

thanks I'm going on vacation  tomorrow in the desert with no electronics for a week....
I think I do need that PCI card b/c the output to the TV with the one working res out of the box
is pretty ugly.

thanks,
wbg

---

### Post by wannabegeek on 2010-05-29
@ Jerrrys

I did try xrandr on the A50 and see that the max res is higher than what is shown as an option...
I'll post back with actual numbers.

It might be able to fit my TV pretty well, but I'll need the right configuration info to make up the
mode.

I found a useful example:
[http://bbs.archlinux.org/viewtopic.php?id=73738](http://bbs.archlinux.org/viewtopic.php?id=73738)

I didn't realize right away that those numbers are for a specific machine. I tried the commands as listed to
make a 1280x1024_60.00  

didn't work...

I'm at least hopful...A friend gave me an old (1999) ATI PCI card for an Imac. I wonder if it will work.
wbg

Edit:
FOund another example same problem same machine. Never messed with xorg.config before.
[http://ubuntuforums.org/archive/index.php/t-14328.html](http://ubuntuforums.org/archive/index.php/t-14328.html)

if anyone feels like helping, I 'll be so grateful...

---

### Post by wannabegeek on 2010-05-30
GOT IT !!

```

cvt 1024 768 60
xrandr  --newmode  "1024x768_60.00"  <cut and paste cvt output>
xrandr  --addmode 1024x768_60.00  --rate 60

```

worked great ...

---

