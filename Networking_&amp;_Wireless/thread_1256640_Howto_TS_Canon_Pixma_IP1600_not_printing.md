---
title: "Howto TS Canon Pixma IP1600 not printing"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by convert_mrta on 2009-09-02
How can I TS where printing is breaking down?

Ubuntu running flawlessly except for one very frustrating problem - printing to the shared Canon Pixma IP1600.  Shared on a WinXP Home SP3 desktop.  Printer worked when I booted this PC in Vista, and when I first tried out Ubuntu in version prior to 9.04.  After fresh reinstall, never could get printing working.

Using both Printer Configuration GUI and CUPS via browser ([http://localhost:631](http://localhost:631)) I can navigate to and find and setup the printer.

I used the post here to get and install driver for it
[http://ubuntuforums.org/showthread.php?t=558993&page=2]("http://ubuntuforums.org/showthread.php?t=558993&page=2")

When I print a test page, both GUI and CUPS via browser indicate that job is being processed and processes successfully.  But nothing happens at the printer end.

I guess I need to break this down one piece at a time. What TS tools are available to me?  What logs can I look at and what am I looking for?  I have read all I can find, but no luck.  Printing cannot be this hard in Ubuntu.

Thanks for all leads

---

### Post by convert_mrta on 2009-09-11
This is not a good sign if trouble-shooting tools (not the solution per se) aren't known.

---

### Post by convert_mrta on 2009-09-18
I should have known that everything is logged somewhere in unix/linux if you know where to look, including CUPS.  

I paid a visit to linuxprinting.org, found out where the cups log is (/var/log/cups/error_log) and also how to turn up logging to debug (EVERYTHING) mode.  sudo gedit /etc/cups/cupsd.conf file  setting the "LogLevel" to "debug"

restart CUPS (sudo /etc/init.d/cups restart)

Submitted a new print job.  This time, lo and behold, there's a (new) error message about not able to find libpng.so.3

This didn't cause any error in the CUPS gnome or webclient GUI.

Installed libpng.so.3 with Synaptic and viola!  Printer works.

/var/log is your friend....get to know it and its contents!

---

