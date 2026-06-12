---
title: "Looking for info on monitor +TVout setup"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by whein on 2007-05-08
My box has an nVidia 7800GT based video card running my LCD monitor, and a Hauppauge PVR-350 with TV-out capability.  The end goal I'm hoping for is to run my regular Gnome desktop on the monitor, but have my MythTV front end display both the TV picture and the Myth menus on a tv connected to the PVR-350.  So far everything is running great off the monitor only.  I've got Fiesty and Myth 0.20 installed.

First question, can this even be done or am I smoking crack (again)?  Is it possible to redirect only certain applications to certain displays?

Second, assuming it is possible, what do I need to install?  I already have the proprietary binary drivers for my nVidia card installed.

Third, what should my configuration files look like?  I'm guessing stuff in xorg.conf needs to change, but that's mostly black magic to me.  Still fairly new to a lot of the under-the-hood Linux stuff...

Many thanks in advance to the brave soul(s) who answer.  :)
-Will

---

### Post by kebes on 2007-05-08
Yes, it can be done. There are many ways I can imagine doing it:
1. Define the TV-output on the PVR-350 as some other display, and then run "mythfrontend" on that display specifically.
2. Add the TV-output from the PVR-350 as a "second monitor" so that your desktop spans from the LCD onto the TV, and then just open MythTV on the TV side of things.
3. Launch a separate desktop session that outputs to the TV. So you have two, independent desktops, one on the LCD, one on the TV.

#2 is clumsy, and I believe it will be difficult to take full advantage of the PVR-350's on-chip MPEG decoding if you do it this way. So #1 or #3 is probably better. I have a MythTV that uses approach #3 (although I basically never use the first desktop session).

So, it can be done. For it to work, you need to make sure that you have the ivtv drivers for the PVR-350 working properly. Then, you modify your xorg.conf, adding a new session type that launches on the PVR-350 instead of the normal video output. Then, you write a script that launches a new desktop session using the "TVLayout" from your xorg.conf instead of the default layout.

There is a [wikibook on installing MythTV]("http://en.wikibooks.org/wiki/MythTV"), and though it is somewhat out-of-date (and is based on Mandrake not Ubuntu), the section you need is applicable:
[http://en.wikibooks.org/wiki/MythTV/Installing#Configure_TV-out](http://en.wikibooks.org/wiki/MythTV/Installing#Configure_TV-out)

That section describes modifications to your xorg.conf that will make TV-out work, using the full MPEG capabilities of the PVR-350. It does this by defining a new layout, called "TVLayout". On my system, I then have a startup script that looks like this:

```

#!/bin/bash

# check which instance we are in...
if [ "$DISPLAY"  = ":1" ]
then
    # We are in the second KDE instance
    # Launch mythTV
    echo "Launching MythTV..."
    mythfrontend &
else
    # We are in the first KDE instance
    # Launch a new KDE on the Hauppauge card
    echo "Launching new KDE instance on Hauppauge 350..."
    startx -- :1 -layout "TVlayout"
fi


```

This script runs at startup (it is located in ~/.kde/Autostart/ on my KDE system), and means that I end up with two desktops: one on the normal video card, and one outputting on the Hauppage PVR-350. Like I said, I don't really use the normal desktop, so you may have to fiddle around with the settings in order to get both loading and working properly. In particular, on my system the keyboard ends up being in control of the TV screen, not the desktop session.


I'm happy to help if you run into any specific problems...

---

