---
title: "Display Problems S3 Trio64 chip set"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by fcco on 2005-11-09
Hi guys. Recently a friend convinced me to try Ubuntu.  His selling point was: "Hey you would not have any problems with new devices or upgrades".  Well, I tried Ubuntu on an old IBM 325 server that has the S3 Trio64 video chip set. Needless to say what a dissapointment; after install, which seemed to have gone just right, the display goes blank.  It appears to be a synchronization problem.  Oh, Yes, one more thing, I am using an Outook switch to view multiple servers.

I searched  the web for ideas, booted in single text only mode, fiddle with the xorg.conf settings to no avail.  Previously this server  had RH9.0, and FC4 installed on it without any display problems.  Any ideas or suggestions will be duly appreciated.

regards,


fcco:confused:

---

### Post by Neobuntu on 2005-11-09
Hey I don't know how much this will help but I thought I'd tell you what I know.

That really old low end graphics card doesn't get much attention. I had a few several years ago and I distinctly remember they needed one or two extra technical setting in the x config file.

I used to notice a band and misc graphical bar across the top of the screen when switching around. At one time I had it 100% so I wanted give you some hope.

It's been a while and I'm sorry about lack of detail (getting old) but it was a few true or false type setting options for that type card that do not apply for newer cards.

You see, that card barely had enough memory and power to do any modern text graphics. But it will do. 

Seems like the bar was greenish but if you see any bar artifacts then these switches are the solution. If not it could be something else.

I just checked my old notes a I have ran that graphic card 100%. 

It was some buffer on or off or something like that. Sorry that's all.

---

### Post by fcco on 2005-11-09
OK.  Yes.  It is an old card, server.  I usually setup old servers as email servers or dns.  That way hardware that I cannot sell can be used effectively.

Thank you for the resposne.  Do you ermember what settings to be turned off/on?

The card works well with FC4

---

### Post by fcco on 2005-11-11
Problem: After boot screen will go blank
Hardware: IBM 325 Server, S3 Trio64 video chip set (old model, very little memory)

Solution:  After a bit of digging around, I found that this chip set does not support higher resolution modes due to limited memory.  Based on this information I looked at the xorg.conf file, following the steps below, and changed the default resolution set at DefaultDepth=24 to DefaultDepth=16.  Everything works fine now.

Step # 1: Hit ctl-alt-backspace - this terminates the xserver and gets you into text mode

step # 2: cd /etc/X11 - change directory to where conf file for X-windows resides.

step # 3: Open xorg.conf file using your favorite text editor (I like pico myself - simple, easy to use).

step # 4: advance to Section "Screen".  It looks something like this:

Section    "Screen"
   Identifier         "Default Screen"
   Device            "S3 Inc. 86c764/76   [Trio32/64/64V+]"
   DefaultDepth    24
   Subsytem         "Display"
.
.
.
Step # 5: Chage it to:

Section    "Screen"
   Identifier         "Default Screen"
   Device            "S3 Inc. 86c764/76   [Trio32/64/64V+]"
   DefaultDepth    16
   Subsytem         "Display"
.
.
.

Step # 6: startx                 #brings xserver back

At this point you should be all set.

---

