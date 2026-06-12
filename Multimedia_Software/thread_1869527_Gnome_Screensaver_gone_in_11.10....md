---
title: "Gnome Screensaver gone in 11.10..."
date: 2011-10-25
forum: Multimedia Software
---

### Post by Sir Rodness on 2011-10-25
Hello, 

I just updaated to 11.10 and notice as many others have that the screensaver has dissappeared because it's not really needed. Which is true. However I like I'm sure many other out there like screensavers, but I prefer the gnome screensaver (which you can no longer use) over the xscreensaver which you need to use now. Why do I prefer the gnome screensaver? Well it's because it runs the Really Slick Screensaver package. Which as you may have guest has Really Slick Screensavers that xscreensaver doesn't appear to be able to use. If anyone knows how to install the really slick screensaver package so the xscreensaver can use them please let me know. It would be appreciated.

---

### Post by appier on 2011-10-29
I ran into the same problem when looking for my favorite screensaver, the "Skyrocket".  The following instructions worked for me on Oneiric 11.10.

[INDENT]**Problem**

The fine folks who consolidated the inner working of Ubuntu have repeatedly decided after each incarnation of the OS to stick with the Gnome-Screensaver application which severely limits the user’s use to make tweaks to the screensavers. Perhaps the thinking was that users would be prone to crashing there older model PCs with setting screensavers to high, or something? Either way, the best option to using screensavers on the Ubuntu, Gnome Desktop, is to uninstall the Gnome Screensaver application.

**Procedure**

You can Copy and Paste each command-line into your Terminal Window.

   [LIST=1]
[*]Uninstall  the Gnome Screensaver application: sudo apt-get remove gnome-screensaver
[*]    Install Xscreensaver: sudo apt-get install xscreensaver
[*]    Now to tell Ubuntu to make Xscreensaver run at start-up: xscreensaver -nosplash
[*]    Remember that you now have to reset all of your settings for the screensaver control settings for Xscreensaver because Gnome-Screenscaer is gone.
[*]    To make all the screensavers enabled type in: sudo apt-get install unicode-screensaver xscreensaver-gl-extra rss-glx xscreensaver-data-extra
[/LIST]
So now you are back to square one with your screensaver settings. If you noticed, none of the screensavers from Really-Slick-Screensavers are in the drop-down list of the Xscreensaver’s window. This is where we will have to do a little hack in the .xscreensaver file.

Install the Really-Slick-Screensavers: sudo apt-get install rss-glx

Once Really-Slick-Screensavers is installed, go to this directory  /usr/share/doc/rss-glx and open the text file with a text editor. This file will tell you how to add the new screensaver to the Xscreensaver control window so that you will be able to have more control of these really cool screensavers. The .xscreensaver file is found in  your $Home directory by choosing the “view hidden files” option in Nautilus File Window.

Now test it out, and enjoy. You should have Skyrockets and the rest of the screensavers in the list on the Xscreensaver’s window.[/INDENT]

Source: [http://www.thomasso.com/2011/08/20/my-favourite-screensaver-skyrockets-in-ubuntu/](http://www.thomasso.com/2011/08/20/my-favourite-screensaver-skyrockets-in-ubuntu/)

---

### Post by oscarivera9 on 2011-11-01
I had the same problem.  It's been kinda cool going through this process of removing the Gnome Screensaver in order to use the Xscreensaver which seems to me to be much more complete.  I've already done it & I must admit, I am very satisfied with the results.  The variety of screensavers in Xscreensaver doesn't even compare with the Gnome Screensaver.  
Now my only concern is if it will run at startup.  I've followed the steps exactly as specified, but it seems that the xscreensaver daemon will not start on its own.  I just added the xscreensaver -nosplash command to my startup applications list so we'll see if that works.

---

### Post by oscarivera9 on 2011-11-01
..........................and it worked!
Now I've got tons of screensavers & the program starts on its own (after the specified idle time, of course).

---

### Post by Sir Rodness on 2012-06-08
Thanks for the feedback.

---

