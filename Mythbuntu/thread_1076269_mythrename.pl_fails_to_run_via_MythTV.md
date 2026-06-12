---
title: "mythrename.pl fails to run via MythTV"
date: 2009-02-21
forum: Mythbuntu
---

### Post by Ryan5.5.5 on 2009-02-21
I cannot get mythrename.pl to work automatically, I can run it manually ok and it works fine.  I have tried to follow the instructions from the link below, I could not get everything to work as per the instructions.

[http://wiki.linuxmce.org/index.php/MythPretty](http://wiki.linuxmce.org/index.php/MythPretty)

I have made an executable file called

/usr/local/bin/mythpretty.sh


which has this in it

mythrename.pl --link /home/mythbox/pretty --format %T-%S%-%Y-%m-%d

If I get mythtv to run it or if I log on as root I get this message:

2009-02-21 21:21:33.213 JobQueue: Started "Rename shows (Pretty)" for "Prototype This" recorded from channel 1003 at Sat Feb 21 19:29:00 2009
Incompatible protocol version (40 != 31) at /usr/share/perl5/MythTV.pm line 641.
Use of uninitialized value in string ne at /usr/share/perl5/MythTV.pm line 367.
Unable to connect to mythbackend, is it running?
2009-02-21 21:21:35.111 JobQueue: Finished "Rename shows (Pretty)" for "Prototype This" recorded from channel 1003 at Sat Feb 21 19:29:00 2009.

Can someone tell me why I cannot run mythrename.pl via MythTV or as root?  Is it something to do with ownership of the files?

---

### Post by Gadgetman on 2009-03-09
Off hand looking at the text of the error message, I would say that you are running a mythrename.pl script that is out of step with your backend...note the part indicating a mismatch with the protocol versions.

---

### Post by Ryan5.5.5 on 2009-04-18
If the mythrename.pl script is out of step with the backend due a mismatch with the protocol versions.  Do you know what would cause this?  I have reformatted the HDD and started again I still got the same message.  What is weird though is that I can double click on the mythpretty.sh script file in Thunar File Manager and it will work fine.  Is just does not work if MythTV runs it, nor from the Terminal it just states Bash: command not found.

---

