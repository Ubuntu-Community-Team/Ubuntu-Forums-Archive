---
title: "Intel 945 and Dell 2405fpw 1920x1200 clock issues (not 915resolution!)"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by mojo2317 on 2007-01-16
Hi all,
I'm having an odd problem with my Dell 420 laptop & Dell 2405FPW monitor.
I have the monitor connected via a VGA cable to the monitor & it should display at 1920x1200 at full screen, but instead, what I get is it compressed in-wards--it looks like it is 1600x1200 resolution, but it is supposedly the full 1920x1200.
the attached thumbnail shows what's going on.
the text in the xterm is 'xvidtune -show' and shows:
"1920x1200" 180.73  1920 2016 2232 2648  1200 1200 1203 1240
which is the current modeline.

now, here's the odd bit, it *used* to work--I had 6.06 on the laptop before 6.10, and when I did the upgrade, it stopped working entirely, and then when I finally did get it to work, it worked like that.  It does work fine when I have the machine docked & can connect via DVI, but that's not really helpful..

I have tried loads of different modelines from [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)  and found that the monitor blacks out & says "1: D-SUB Can not display this mode" when I tried to go above 184'ish for the dotclock.

I can't adjust the screen w/ xvidtune, I get "Sorry: You have requested a mode-line That's not possible or not supported by your hardware configuration"

the monitor is set for a 1:1 scaling ratio.
the monitor accepts 1600x1200@60hz just fine, it even takes 1920x1080@60hz just fine, but it squishes in when I try to do 1920x1200...

I haven't tried it with any other video cards, and, like I said, used to 'just work' with 6.06... :-/ it is Xorg version 7.1.1, kernel 2.6.17-10 SMP, and here is a snippet of my xorg.conf file

Section "Modes"
  Identifier    "Modes"
  Modeline "1920x1200" 180.73  1920 2016 2232 2648  1200 1200 1203 1240
EndSection

Section "Monitor"
  Identifier      "Monitor_1"
  HorizSync       30-81
  VertRefresh     47-76
  UseModes        "Modes"
EndSection

Section "Screen"
  Identifier      "Screen_1"
  Device          "i810_1"
  Monitor         "Monitor_1"
  DefaultDepth    24
  SubSection "Display"
    Depth           24
    Modes           "1920x1200" "1600x1200"
  EndSubSection
EndSection

Section "Device"
  Identifier      "i810_1"
  Driver          "i810"
  BusID           "PCI:0:2:0"
  Option          "NoDDC"         "true"
  Option          "UseEdidFreqs"  "false"
  Option          "IgnoreEDID"    "true"
EndSection

Thanks for your input!
Jonathan

---

### Post by mojo2317 on 2007-01-18
okay, I have an update!

I got to test the same setup with an NVidia card (well, 'nv' driver) video controller & it worked perfectly.

xvidtune -show gives:

"1920x1200"   193.16   1920 2048 2256 2592   1200 1201 1204 1242

(at which dotclock, like I said, the new Intel 830 driver fails for some reason, and the screen gives me the "1: D-SUB Can not display this mode") and the display looks perfect.

This, given with the fact that this *used* to work on this hardware, I'm suspecting something changed with the xorg server; anyone have any ideas?  should I go pester the lovely folk at x.org? :-)

Thanks for your input!
Jonathan

---

### Post by foobardude on 2007-02-06
I just got a minipc and the 24 inch monitor yesterday.  I'm having the same issue (the machine isn't seeing the 1920x1200 res - it streches the 1600x1200 as well)

I'll try the modeline you posted.  Did that modeline work?

I also saw instructions to use the intel driver, and not the i810 driver.  I'm going to see if that has any luck.

Finally, I've read that the dell monitor reports bad timings which prevent the i810 drivers from going a full 1920x1200 resolution.  People have said to add the following line to make it work:


[http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-01/msg00259.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-01/msg00259.html)

Quote:
=================
To turn off EDID I had to put:
Option "ModeValidation" "NoMaxPClkCheck"
in the Screen section.

I then had to specify in the Display section:
HorizSync 31.5 - 90.0
VertRefresh 60.0 - 60.0
Which is sufficient to display 1920x1200 at 60Hz.
==================

I'm going to try both when I get home (stuck in a cube right now).

So is everything working for you now?

Foo

---

### Post by mojo2317 on 2007-02-06
yay! A reply! :-)
I'm in the middle of moving across the country, so everything's all packed up..  I'll be excited to see how it works out for you :-)

> **foobardude said:**
> I just got a minipc and the 24 inch monitor yesterday.  I'm having the same issue (the machine isn't seeing the 1920x1200 res - it streches the 1600x1200 as well)

I'll try the modeline you posted.  Did that modeline work?

that modeline only on the nvidia card.
but I'm relatively sure that was the modeline I used in 6.06 that worked.

> **foobardude said:**
> 
I also saw instructions to use the intel driver, and not the i810 driver.  I'm going to see if that has any luck.

huh, I didn't quite realise there was a 100% separate intel driver!  I kind of remember seeing some vauge references to it, but nothing explicit..exciting!
I was going to see if I could find a copy of the X tree from the 6.06 release and see if that worked again, and go from there..  the Intel driver seems like it ought to make a bit more sense..

> **foobardude said:**
> 
Finally, I've read that the dell monitor reports bad timings which prevent the i810 drivers from going a full 1920x1200 resolution.  People have said to add the following line to make it work:


I believe I set it to ignore the EDID settings... but don't think I used that explicit setting. 
Again, I'll be excited to see if it works for you, and me when I get settled again!

Jonathan

---

### Post by mojo2317 on 2007-05-03
Nope, no luck.
I really couldn't get it to work over VGA.

---

### Post by MGStreak on 2008-02-27
After a *lot* of nights of trial and error and board hunting, I finally solved this problem on my machine.  Here are my specs:

O/S: Ubuntu 7.10 (Gutsy Gibbon)
Video Card: Intel Corporation 82945G/GZ Integrated Graphics Controller
Driver: 'intel'
Monitor: Samsung SyncMaster 920NW
Native Resolution: 1440X900 @ 60 hz (Widescreen)

Solution:
[http://ubuntuforums.org/showthread.php?t=203905](http://ubuntuforums.org/showthread.php?t=203905)

My comment/addendum to the solution:
[http://ubuntuforums.org/showpost.php?p=4416287&postcount=67](http://ubuntuforums.org/showpost.php?p=4416287&postcount=67)

---

