---
title: "Dual Monitors with gaming only on a single monitor: is it possible?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by magomago on 2006-08-27
Hi, I'm recieving my second 19 inch monitor soon and I have been looking around the forums without an exact answer...

So here is my situation:

I want the benefit of dual monitors, but if I run games I want to be able to default back to a single monitor.

I tried enabling twinview with an old 17inch CRT I had laying around and if I load up a game through Cedega what happens is the game is streched between BOTH monitors...which I don't want.

Is there a way to have it so the desktop spans between both screens, but a game is fixed on one screen?  I wouldn't care if the other monitor would blank out, although it would be nice if I could still see it (perhaps leave gaim open on that side so although I can't respond to a person since everything is focused on the game window atleast I know who might be messaging me)

So does anyone have an idea, or if what I'm asking is even possible?  Thanks :D

---

### Post by toasted on 2006-08-27
ATI X1600
Dual screens - big desktop mode
I run Enemy Territory and when it runs it is just on the main monitor. No config necessary, it just works.

---

### Post by magomago on 2006-08-28
That is nice to hear, especially considering you have an ATI card.  I'm hoping that would work for nvidia...
but in the past when i tried it with that other CRT it didn't :oops: 
Guess i'll find out this weekend when I get time

---

### Post by magomago on 2006-08-29
bump

I've been searching google and there IS a way to do it...but no one ever details how beyond "Well it works now cause i figured i tout thanks!"

one person even went as far as asking "can you tell us what you did" ;)

Perhaps we can get it resolved clearly here!

---

### Post by magomago on 2006-08-29
Well I figured out how to do it...kinda of :twisted: 

I can get the primary monitor to stay active, but it kills the secondary monitor.

How?

We need to add another line in the META MODES


[q]Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4800 SE]"
    Driver         "nvidia"
    Option "TwinView" "True"  
    Option "TwinViewOrientation" "LeftOf" 
    Option "UseEdidFreqs" "True" 
    Option "MetaModes" "1280x1024,1280x1024; 1280x1024,NULL"
EndSection[/q]

see the second one?  The NULL is very important, and somehow magically Cedega focuses on one screen.


Now the next question: is it still possible to have the second monitor active, or am I dreaming now? ;)

---

### Post by Wim Sjøholm on 2007-01-22
This almost works for me, except that it displays it on the right half of my left monitor and the left half of my right monitor instead of just my left monitor. I have ATi though (ati 9600xt) using the open source drivers. On AIGLX/beryl if thats relevant. Anyone know of a way of moving it to the correct position ?

---

### Post by nixendra on 2007-01-22
it's perhaps not the way you want to achieve it but there is my way of running ut2004 on one screen (i use nvidia, twinview, and the same X setup you posted)



xvidtune -next
ut2004
xvidtune -next



the first "xvidtune -next" swicth to a single desktop, next launch ut2004 and then switch back to twinview

---

### Post by Wim Sjøholm on 2007-01-22
> **nixendra said:**
> it's perhaps not the way you want to achieve it but there is my way of running ut2004 on one screen (i use nvidia, twinview, and the same X setup you posted)



xvidtune -next
ut2004
xvidtune -next



the first "xvidtune -next" swicth to a single desktop, next launch ut2004 and then switch back to twinview

Doesnt seem to switch here. I think there's only one mode set up for my computer, although i did add the meta mode line

---

### Post by nixendra on 2007-01-22
here is my relevant section of xorg.conf if that could help you:


```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA"
    Monitor        "MonitorMain"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "NvAGP" "3"
    Option         "NoLogo" "true"
    Option         "TripleBuffer" "true"
    Option         "RenderAccel" "true"
    Option         "TwinView" "on"
    Option         "MetaModes" "1280x1024, 1280x1024; 1280x1024,NULL"
    Option         "SecondMonitorHorizSync" "50-75"
    Option         "SecondMonitorVertRefresh" "60-80"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

```

---

