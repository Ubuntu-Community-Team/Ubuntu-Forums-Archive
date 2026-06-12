---
title: "Apps start on wrong monitor using Xinerama"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Objekt on 2010-01-23
I use 2 monitors under Ubuntu 9.10, but I have them set up in a unique way.  The primary (CRT) faces me on my desk, but the other (widescreen LCD) is turned away from me, because I use it only to watch movies from my couch.  My video card is an Nvidia GeForce 9800 GTX+, using the proprietary Nvidia driver package, with Xinerama turned on, so the desktop extends across both displays.

Given that setup, is there any way to control which display applications open upon?  Several apps have started opening on one display or the other, seemingly at random.  Further, some apps start on the primary display, but open their subwindows on the secondary display.  It's very annoying, because I can't see the second screen, so I can't drag the windows back to the primary desktop.

I would also like to have VLC Media Player (or any other app) always open on the secondary screen, on purpose.  I almost never watch movies  sitting at my desk, but rather from the couch.  I placed a VLC launcher icon on the secondary screen, but when started it opens on the primary display.

(If you're wondering how I can click on anything from my couch, I have a wireless mouse there in addition to the wired mouse at my desk.  It's my "remote" since I don't have a TV.  Xorg will quite happily support 2 or more mice simultaneously, I discovered.)

---

### Post by Blaze1024 on 2010-02-11
I'm having a similar issue, have you found the fix yet ?
 
I've been using linux for over 5 years and I have to say.  SO much for that so called fantastic Linux community support. 

  I've spent the better part of a 4 days trying to get this resolved. It seems like Ubuntu claims to have lot of features and work well but it really seems like nothing really works well.

Sure I have two monitors but what good is it when I cant even start and have an application run on the screen I want.   How many days or months am I going to have to suffer through trying to get this working right.

---

### Post by Objekt on 2010-02-11
No real fix yet, or hint of one.  The only slightly helpful thing I've found is:

-right-click on app in lower panel (aka taskbar);
-select "Move";
-hit SHIFT + Left arrow.

That moves the window to the right edge of my primary screen (secondary is on the right, both virtually and physically).  

It's not pretty, but it works.  It eliminates the need to walk across the room & move the errant window with the second mouse.

Closing the app on the desired screen has ZERO effect on where it opens the next time I start it up.  

I agree, multi-monitor support is somewhat lacking.  Xorg should provide some way to specify which monitor a newly-opened app appears on.  At present there is no way to do that, as far as I know.

---

### Post by AdvancedNewbie on 2012-12-17
You can use this bash script I made using the information found at:  
[http://movingtofreedom.org/2010/08/10/arranging-windows-from-the-gnulinux-command-line-with-wmctrl/](http://movingtofreedom.org/2010/08/10/arranging-windows-from-the-gnulinux-command-line-with-wmctrl/)

My bashscript (named start_resized.bash) accepts command arguements in the following way:

./start_resize.bash <command> <window title search string> <X> <Y> <W> <H>

Example - Start Google Chrome full size on monitor 1:

./start_resize.bash google-chrome Google 0 0 1920 1006

Example - Start Google Chrome full size on monitor 2:

./start_resize.bash google-chrome Google 1920 0 1920 1006


Bash Script:

#!/bin/bash
function get_window_id() {
    window_id=$(wmctrl -l | grep "$2" | tail -1 | cut -f1 -d" ")
}
#sleep 1

echo "Starting Program: $1"
echo "Window Name: $2"
echo "X: $3 Y: $4 W: $5 H: $6"
#sleep 3
$1 &
sleep 1
get_window_id
echo "Window ID: $window_id"
wmctrl -i -r "$window_id" -e 0,$3,$4,$5,$6
echo "Resized Window."

---

