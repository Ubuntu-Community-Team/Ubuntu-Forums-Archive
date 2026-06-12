---
title: "Flash video full screen goes to wrong monitor in dual-monitor setup"
date: 2008-08-12
forum: Multimedia Software
---

### Post by hypersoar on 2008-08-12
I have a dual-monitor setup in Hardy setup with NVidea's configuration tool. When I try to go to full screen with a flash video, it goes to the secondary monitor. How can I get it to go to the primary monitor?

---

### Post by MarkusThielmann on 2008-09-17
> **hypersoar said:**
> How can I get it to go to the primary monitor?

You can't, it's a [bug]("https://bugs.adobe.com/jira/browse/FP-562").

---

### Post by Banter on 2009-03-30
Would you like to know my shameful workaround for this? I have another copy of Ubuntu virtualized in virtual box which I make full screen on my big monitor.

It's a sad state of affairs, but I'll be damned if I'm not going to use my bigger monitor.

---

### Post by dal on 2009-06-15
Some people seem to be saying they can't get flash to fullscreen on their primary monitor, some can't seem to get it to fullscreen on their secondary. I'm guessing that it always goes for the leftmost monitor as that monitor contains the 0,0 X coords, but as I'm speed capped right now and don't really feel like waiting 10min for youtube to buffer a small clip for testing purposes (yeah, that's an exaggeration, but not as much of one as you might think), I can't say for sure.

Swapping monitor orientation in xorg.conf or nvidia-settings might not be an elegant solution but it may do the job.

Now, if I can just get the flash fullscreen windows firefox pops up to stay open when I switch focus from it (or for that matter find a standalone flash video player that will work :( )...

---

### Post by Geling on 2009-07-03
The biggest problem for me so far (without even some reasonable workaround)...
Is there any suggestion / fix / other flash version / other browser compatible to avoid it?  :(

---

### Post by markbuntu on 2009-07-25
No, it is a flash issue that was reported almost a year ago and they do not seem interested in resolving it so maybe a bunch of people should pile into this bug report to get their attention.

[http://bugs.adobe.com/jira/browse/FP-562](http://bugs.adobe.com/jira/browse/FP-562)

---

### Post by gcbzzzz on 2009-10-10
my work around:
1. move browser to 2nd window.
2. use compiz to zoom. center on flash with mouse.
3 option 1. use compiz's local zoom and move pointer back to other screen.
3 option 2. lock screen. move mouse to other screen, unlock. :)

---

### Post by jandrioli on 2009-12-02
Please VOTE in adobe bug-tracking system to get this fixed.
as of now there's only 19 votes :(

[http://bugs.adobe.com/jira/browse/FP-562](http://bugs.adobe.com/jira/browse/FP-562)

cheers!

---

### Post by bottomline on 2010-02-23
Try switching the left-right orientation of your monitors. That fixed it for me.

---

### Post by Zoharc on 2010-07-24
I have came across the fact that switching a windows manager (I have tested this on Openbox), and setting new windows to spawn under the mouse, will make the flash screen go where you choose. 

(tested this on ubuntu 8.04 and 10.04)

---

### Post by Julianz on 2010-11-11
I have the same problem. None of the suggestions worked of me. 
It does not seem to me like problem with flash. Any program that goes into full screen mode opens the screen at my PC monitor (and not my second monitor from which the program was launched). 

For example, when opening a open office presentation in my second monitor (TV) and hitting the full screen option it also opens the full screen in my PC monitor.
One of the main reasons I bought a digital TV was to connect it to my PC and watch flash movies. Without the nvidia driver I got it to work but I need the driver to have a proper resolution. So it looks to me that the problem is with the driver

---

### Post by spaceboy909 on 2010-11-27
> **Julianz said:**
> I have the same problem. None of the suggestions worked of me. 
It does not seem to me like problem with flash. Any program that goes into full screen mode opens the screen at my PC monitor (and not my second monitor from which the program was launched). 

For example, when opening a open office presentation in my second monitor (TV) and hitting the full screen option it also opens the full screen in my PC monitor.
One of the main reasons I bought a digital TV was to connect it to my PC and watch flash movies. Without the nvidia driver I got it to work but I need the driver to have a proper resolution. So it looks to me that the problem is with the driver
I seem to have the same variation on the problem as you do, although mine is a bit different.

Mine will show the full screen on both monitors, but the 2nd monitor's graphics are partly distorted and garbled, so even if I wanted it on both, the 2nd one is basically unwatchable, and this also adds noticeable resource drain.  (**ETA**:  *Actually, mine seems to only be a Flash problem.*)

---

### Post by DrDmoney on 2011-01-27
I am having the same problem. Flash video only wants to expand to the left most monitor. Adobe would be wise to fix this issue. It bad when a clear issue has yet to be fixed over many years. I can't wait for html5 to start taking over.

---

### Post by sabme on 2011-02-07
Same general problem as others here.

My simple workaround is just maximize or full-screen my browser.  Then Ctrl++ or Ctrl Mouse-wheel to zoom the flash video until it's as big as I want.  Not perfect but better than nothing.  

Movie Player works fine in full screen on right hand non-default monitor.  YouTube.com/HTML5 video plays full-screen the same as in the default monitor.  So far as I'm concerned it's a bug in Flash and can't wait for more HTML5.

---

### Post by harryharryharry on 2011-07-12
html5 seems to be a viable workaround for me:
[http://beginlinux.com/desktop_training/ubuntu/html5-on-ubuntu-1004](http://beginlinux.com/desktop_training/ubuntu/html5-on-ubuntu-1004)

another way of circumventing flash is "Youtube without Flash Auto"-script (for firefox or chrome):
[http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

But this is only for youtube offcourse. It really is a shame that during its 'lifespan' they (i'm not sure who is at fault here, but I suspect an Adobe/Nvidia combo) havent been able to flush out this major bug in flash. I've learned to live with it the last couple of years. But I must say it is one of the more prominent reasons I've kept dual booting with Windows.

---

### Post by BicyclerBoy on 2011-07-12
Are you using twinview or separate X screens ?
Do you launch the browser by using DISPLAY variable (script) or std desktop menus ?

For dual head separate  screens, a firefox launcher for 2nd screen can be made..
export DISPLAY:="0.1" ; firefox
or
DISPLAY:=0.1 firefox

This could have some effect on flash player full screen..

---

### Post by wissamshaar on 2011-08-03
> **bottomline said:**
> Try switching the left-right orientation of your monitors. That fixed it for me.

Here's a post to how it can be done. It worked for me. I hope it helps.
[http://ubuntuforums.org/showthread.php?p=11116433](http://ubuntuforums.org/showthread.php?p=11116433)

---

### Post by bhh1988 on 2011-09-26
> **wissamshaar said:**
> Here's a post to how it can be done. It worked for me. I hope it helps.
[http://ubuntuforums.org/showthread.php?p=11116433](http://ubuntuforums.org/showthread.php?p=11116433)

This worked for me too. Hardest thing was to switch my monitors around :)

---

### Post by richardkemp on 2012-07-12
I solved this by changind my xorg.conf from this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1050x1400 +0+0, DFP: 1920x1200 +1400-75
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
to this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1050x1400 -1400+75, DFP: 1920x1200 +0+0
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

ie I changed it so point +0+0 is now on my primary screen (on the right). Oddly, before this all flash would fullscreen to my secondary (left) screen regardless of which screen the browser (I use firefox) was on, but now it actually fullscreens correctly - ie to the browser's screen, not just to the +0+0 screen.

This is on Ubuntu 12.04 with nvidia beta drivers.

---

