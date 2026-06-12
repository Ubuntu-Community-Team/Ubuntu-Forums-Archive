---
title: "Had a processor problem, now I've lost video!  HELP!"
date: 2009-10-14
forum: Multimedia Software
---

### Post by Superluke on 2009-10-14
I have been experiencing a problem with xorg running at 100% on one of my processors (Pentium D machine).  The strange thing is when you watch on System Monitor the load switched randomly from one processor to the other.

Part of my problem probably stems from repeated attempts (after too many forum reads and how-tos) to make my ATI Radeon x800 SE happy with its drivers.  No idea where my xorg.conf stands at this point.

My next mistake was upgrading to Karmic yesterday.  Now I get the new Ubuntu logo splash screen, then nothing - a pixelly green line.  Booting in safe mode gets me to a prompt but I can't edit anything, it tells me I have no video even for gedit or emacs.

Is there something I can do from the prompt to reset any and all video drivers and start from scratch without reinstalling?

Thanks in advance!

---

### Post by matey3 on 2009-10-14
can you go to command line and type Xorg --help
it gives you a lot of switches, a few of them may help you such as;

-config file           specify a configuration file, relative to the
                       xorg.conf search path, only root can use absolute


-dpi int               screen resolution in dots per inch
dpms                   enables VESA DPMS monitor control
-dpms                  disables VESA DPMS monitor control

---

