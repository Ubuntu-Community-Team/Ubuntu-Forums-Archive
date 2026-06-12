---
title: "Gtkpod: Error opening '/home/gilbert.ext' for writing (Permission denied)."
date: 2013-08-25
forum: Multimedia Software
---

### Post by Gilbert_Gregg on 2013-08-25
Hi all,

I was wondering if anyone could help me sync my ipod using gtkpod. The first thing I tried to do is delete my old music collection from my iPod. This is accomplished by right clicking the iPod,  Remove All Tracks From Ipod -> I'm Sure.

However, I get the following error:

Error opening '/home/gilbert.ext' for writing (Permission denied).

After clicking okay, I get another error:

Error opening '/home/gilbert' for writing (Is a directory).

After clicking okay, the status bar at the lower left hand corner remains stuck on "Now writing database 'Gilbert's iPod'. Please wait..."

P.S. Anyone know a good way to convert FLAC to an apple compatible format on the fly during sync? This is what I am hoping to do with gtkpod, and I haven't been able to do it with Rhythmbox (crashes when I try to sync)

---

### Post by jason.s.dodd on 2014-04-06
I had the same issue.  I worked around it by creating a file named /home/[user].ext where [user] is my user name.  In your case it would be /home/gilbert.ext I'm not sure this was the best or correct solution.  But it worked for me.  The other thing I needed was to create a HashInfo file.  After those two, gtkpod seems to play nice.  Note that you need to be superuser to create /home/[user].ext and you should make sure you have permissions to write to it.

---

