---
title: "Monitor goes to Power Saving after 10 mins."
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by blankSWFC on 2007-01-23
Hey,

I recently put Edgy on after using Dapper for so long, but i have a strange that i didn't have with Dapper... that i just cant seem to fix.

After 10 minutes of not moving my mouse my monitor goes blank (into the power saving mode), this is even when watching a non-fullscreen video or playing audio (in fullscreen the screen stays on).

I altered the power settings so it would "Never" put the monitor off, and I disabled the screensaver, but still it does the same thing.

The thing is though... If i set the power setting for the monitor to go off after an hour, that works.  But if i set it to never, it ignores the setting and goes off after 10 minutes.


I'm using the FGLRX driver, and Beryl 0.2.0-svn, on a Radeon 9550 256MB.  

Does anyone know either if i'm missing something thats new in edgy, and there is another setting i need to change (maybe in a file instead of using the GUI app)?

Or is there a way to disable all the power saving features on the whole system?  The reason i as that is the system is on 24/7, and as long as the power off button still works etc, i dont mind losing the power saving stuff on the monitor etc..


Cheers.

---

### Post by Erlander on 2007-01-23
It may be a power saving setting in Bios.

Rob

---

### Post by kerry_s on 2007-01-23
You can always go manual with, which is how i do it.

Put> xset -dpms <in the session startup,this turns off the power saving feature.
You can create a launcher to turn off the screen when you want,Put this for the command> xset dpms force off <if you need a little time to get your hand off the mouse you can make a little script->

gedit .off

and put this->

#!/bin/sh

sleep 5
xset dpms force off &


Then you need to make it exectuable> chmod +x .off

then put the path for your off switch> /home/(user)/.off <as the launcher command

Now you control when you want to turn off your monitor with a click.

---

