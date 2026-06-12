---
title: "KDE running with GTK/Gnome window decorations"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by afoglia on 2011-02-17
After two consecutive crashes (apparently due to pressing return in a text box on a web page), I've gotten back into KDE , the window manager seems to be something from Gnome/GTK.  I see no processes that obviously belong to kwin or compiz, and a metacity process coming from gdm.  My .xsession-errors does have this line:

"kwin: unable to claim manager selection, another wm running? (try using --replace)"

Any ideas how this could happen?  Why this restart is different from all the others, and whether this will be a recurring problem?

---

### Post by seeker5528 on 2011-02-17
Don't know why it would just happen out of the blue like that, crash or no crash.

You could try looking in 'System Settings --> Startup and Shutdown --> Autostart' to see if Metacity somehow got added to the list of things to autostart.

If that doesn't seem to do it, as a work around while further investigation is being done, you could try setting the WINDOW_MANAGER environment variable, Gnome and KDE both recognize this environment variable and normally should use the one specified there instead of their own default. Given the situation I wouldn't be overly optimistic, but it's worth a shot.

To set the environment variable for kwin create a file in your home directory named '.xprofile' with the contents....

```
# This file '~/.xprofile' should be used to customize the environment of your X login session similar
# to the way you would use '~/.profile' to customize the environment of your command line login session.

# export PATH="~/some_directory:$PATH"

export WINDOW_MANAGER="/usr/bin/kwin"
```

Later to undo the change just rename the file or place a hash character '#' at the beginning of the line to comment it out, then log out and log in.

EDIT: It's been a while since I booted using the recovery boot option, but once your booted in to it, I believe there is a menu option you can use to initiate a file system check on the next boot, the issue could be the result of some file system corruption. 

Later, Seeker

---

### Post by Enternald on 2011-02-17
Also try : 
```
sudo dpkg-reconfigure gdm
```
then choose kdm. It seems ,at least for me,in natty kdm works better than gdm. 
I remember I had in 10.04 cosmetic bug: when using expose effect, I could see for the blink of the eye my gnome desktop: only with tango theme. I thought that this is something to do with the Xserver or FBuffer, but one day I killed kwin and what I had seen: Nearly functional gnome below KDE (few services weren't started). For some time I switched to kdm. That was gone forever.

---

### Post by afoglia on 2011-02-17
Well, when I restarted, I got the right window manager.  (Looks like I have compiz set up.  I know I had to play around with it in maverick, though I don't remember where the setting was.)  nautilus is running somehow (as seen in ps) as a child of kdeinit4, and it's the parent of the compiz process.

That doesn't explain why I got the kwin error in my .xsession-errors last time.

Regardless, it seems to be a random error, so I won't futz around with my environment.  Any ideas what logging I can/should enable to help track the cause down if it reappears?

---

