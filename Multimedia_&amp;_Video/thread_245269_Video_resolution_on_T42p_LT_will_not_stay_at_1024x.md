---
title: "Video resolution on T42p LT will not stay at 1024x768"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by gnu_joe on 2006-08-27
Ok, this is driveing me nuts....
I have a T42p Thinkpad which uses a ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80) chip. It's natural desplay size is 1400x1050 ( looks just stunning ). Have no issues installing and running Ubuntu 6.06.1 LTS ( aka Dapper ). I have X working with both the default driver and also the fglrx driver ( which I'm useing with XGL/compwiz ).

Ok now to the problem...
When I give talks I use a LCD projector that can ONLY accept 1024x768 has it's resolution. I can not get X to display that, but when the laptop boot's up gmd always come's up at 1400x1050 and X starts in that resolution then at the last moment changes to 1024x768. This throughs off the attached LCD projector. So I have to re-boot which is a pain. Also I want to demonstrate the boot sequence since it's part of the prez.

So how to force x.org to only work in 1024x768?

Here is my desplay section of /etc/X11/xorg.conf:

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     8
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

I though that X would be controled only byoe this file, but that seems not to be the case. What is allowing gdm and X to find that my video chip can work at 1400x1050 ? Is there any way to force it to only see 1024x768?
](*,) 
Help!

Joe

---

