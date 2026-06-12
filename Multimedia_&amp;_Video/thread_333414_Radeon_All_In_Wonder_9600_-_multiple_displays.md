---
title: "Radeon All In Wonder 9600 - multiple displays"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by gantww on 2007-01-07
Hello all,
I just installed Ubuntu on a machine with an ATI Radeon All In Wonder 9600. Anyway, I found the driver, but it is in the form of a .run file. How the heck do I run this thing?

Also, ATI's site lists a pair of rpm files. One is for XFree86 and one is for XOrg 6.8. Their little script to figure out which one you have is broken, so how do I figure it out. These items are packaged as rpms, so I'm assuming that I should be able to open them on my system.

Once I install the driver, will I be able to split my display between the two screens? I currently actually have three monitors, but the third one is attached to an NVidia card, so I'm just trying to get the two that are attached to this card to work first.

---

### Post by jms1989 on 2007-01-14
Hello,

To install from a .run file, first make it executable dwxr-xr-xr (755), second launch the terminal using root as the user and navigate to where you saved it at.

Example:  cd /home/user/Desktop
To run it, simply put the full path including the file name in the terminal and press enter or if your working directory is where the file is located at, simply insert the file name. Don't forget the extension.

Post any problems you may have. I'm not sure how to split the display between the two screens, someone else would have to help you on that.

Cheers!
-- jms1989

---

