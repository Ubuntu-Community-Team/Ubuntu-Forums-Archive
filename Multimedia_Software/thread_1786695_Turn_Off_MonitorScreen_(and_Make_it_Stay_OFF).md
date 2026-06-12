---
title: "Turn Off Monitor/Screen (and Make it Stay OFF)"
date: 2011-06-20
forum: Multimedia Software
---

### Post by ellaivarios on 2011-06-20
Hi everyone again,

I've read several posts here on how to turn off your laptop screen in Ubuntu using a script/command, but none seem to have worked for me except one. 

after digging around, I found the following suggestions:

[B] 1.  xset dpms force off
or   xset dpms force suspend[/B]

This didn't work for many people, nor did it work for me, as the monitor would just turn on again after a few seconds. The second other suggestion I found to make this "stick was:

[B]2.    sleep 1; xset dpms force off
or    sleep 1; xset dpms force suspend[/B]

This worked for some people, by delaying the monitor off function by one second, but it did not work for me, as the monitor would turn on again by itself after one minute exactly. Maybe those who thought this was the solution just walked away and never really found out their monitor plays sneak-peak with them. The next solution i found digging around was supposed to really make the monitor stay powered off:

[B]3.   sleep 1; && xset dpms force off
or   sleep 1; && xset dpms force suspend[/B]

But this didn't work either; what a disappointment, and it also made my CPU and HDD freak out for a while while my monitor was off. So after some more digging around, I came up with the following: (and I don't remember where i got this, whether it was from here or elsewhere on the internet, but if it is your creation, please contact me and I'll edit the post to give you credit)

4.   **create a file and save as something like [COLOR="Blue"]Monitor_off.sh[/COLOR] in a folder of your preference with the following in it:**

---------------------------------------
#!/usr/bin/python

import time
import subprocess
from Xlib import X
from Xlib.display import Display

display = Display(':0')
root = display.screen().root
root.grab_pointer(True,
        X.ButtonPressMask | X.ButtonReleaseMask | X.PointerMotionMask,
        X.GrabModeAsync, X.GrabModeAsync, 0, 0, X.CurrentTime)
root.grab_keyboard(True,
        X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

subprocess.call('xset dpms force off'.split())
p = subprocess.Popen('gnome-screensaver-command -i'.split())
time.sleep(1)

while True:
    print display.next_event()
    p.terminate()
    break

---------------------------------------

Then just go to: System>Preferences>Keyboard Shortcuts and assign a Keyboard combination shortcut to call and initiate the script. I chose "<Ctrl>+M" because it's easy to remember. 

Make sure to disable any same keyboard shortcuts you may have in Compiz to avoid conflicts.

This final script just worked perfectly for me. And the Monitor just stays off until I shake the mouse or press a key on the keyboard, and my CPU and HDD don't rev up like a Harley. This final solution seems to be working for everyone of my friends without a glitch.

If you want to add anything, I'll leave the thread open for a week, just in case there are a few suggestions that can improve this idea or add new features or simplify it. I just thought it would be a good idea to post it here because I've seen many people are looking for taking control of such a feature, and it would be great.

Thank you.

---

### Post by thesoothsayer on 2011-06-28
Thanks. Works like a charm for me.

Maybe you could put the code within a 

```
code tag
  so that it
  doesn't lose its formatting?
```

And the user also needs to install python-xlib for it to work.

---

### Post by adgmonk on 2011-09-05
The script posted above has security issues (grabs entire keyboard + mouse) and is gnome-dependent.  See [http://ubuntuforums.org/showthread.php?t=1317747](http://ubuntuforums.org/showthread.php?t=1317747).

The following command-line for turning off the monitor uses the built-in X11 screensaver and is independent of desktop (gnome, ...) or distribution (ubuntu, ...):

```
xset s blank ; sleep 1 ; xset s activate
```

---

