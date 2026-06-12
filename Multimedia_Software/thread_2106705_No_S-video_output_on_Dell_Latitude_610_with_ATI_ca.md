---
title: "No S-video output on Dell Latitude 610 with ATI card"
date: 2013-01-19
forum: Multimedia Software
---

### Post by noobyuser on 2013-01-19
I am a new user of Ubuntu.  I have a Dell Latitude D610 that previously ran Windows XP (slowly).  I tried out Lubuntu 12.10 using a DVD Boot disk, and liked it so I installed it.

The installation and various updates worked very well (slick!).

I have an ATI Mobility Radeon X300 video card.

Only one thing does not work: the S-Video output.  I have used (and plan to use) the computer as a media player for the TV, using the S-Video output.  This previously worked in Windows XP (though was getting slower and slower).  Using commands like Fn-F8 to change the output screens does not work either.

The OS recognizes the S-Video connection, but does not send a signal (or a bad signal).  Attached is a screenshot of a "xrandr" command (and a previous "lspci | grep ATI" command--I can't the copy function to work on the terminal window with either Ctrl-C or Ctrl-Shift-C).  It shows "LVDS connected 800x600+0+0" and "S-video connected 800x600+0+0".  Display Settings-Advanced also shows both the laptop monitor and another video monitor.

I would appreciate any help or workarounds to get video output to a TV.  Thanks.

---

### Post by noobyuser on 2013-01-26
Additional information:

When I use the Lubuntu 12.10 DVD Boot disk to start Lubuntu, then the S-video output to the TV works.

I tried reinstalling from that boot disk, but once I switched over newly installed OS on the computer, the S-video output does not work.

Why would the S-video output work on the boot disk but not once I use that boot disk to install Lubuntu on the machine?

Thank you for your assistance.

---

### Post by Whoopie on 2013-01-27
You could ask the radeon maintainer Alex Deucher on Freenode IRC. His nickname is agd5f.

I'm also interested in a solution, as my 2 old laptops also have an ATI card and the S-video output is garbled.

---

### Post by mörgæs on 2013-01-27
Thread moved. 
Does not seem to be specific for Dell.

---

### Post by noobyuser on 2013-01-28
I followed the advice of Whoopie and asked Alex Deucher.  He suggested I check the output setting.  

It was actually set to  the correct status for my S-video tv standard: ntsc.  So I toggled the setting.  

I typed:

xrandr --output S-video --set "tv standard" pal

then:

xrandr --output S-video --set "tv standard" ntsc

Then the S-video worked, and continued working even after I rebooted.  If I shutdown entirely and power up, then I need to do the two xrandr commands again.

So this is solved.

Thank you for your help.

---

### Post by mörgæs on 2013-01-29
Good, please mark the thread 'solved' using 'thread tools'.

---

