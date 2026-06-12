---
title: "DPMS bug workaround!!!!"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by dragon76 on 2006-12-22
Devs please read.

I apologize for the length of this post but want to contribute all I have learned. If it would better be posted elsewhere perhaps one of the mods would kindly move it.

There is a bug in kubuntu where if you change the monitor off time setting in power management when you reboot or logout/login it returns to default. This is a known bug and there are several threads discussing this as well as a bug report on launchpad.net.  I have been working on the DPMS problem, in Kubuntu, all day as this is something that is very important to me.  The following is how I found a workaround for the problem.  I hope that this workaround will provide insight for those that know more about the code involved than me and that they can find a real fix to this.

I was digging in a 6.06 (dapper) install which I have, that DPMS was working on to find what might be different.  I found that this 6.06 install was using display.desktop to set the display properties. 6.10 (Edgy) was using displayconfig.desktop but display.desktop was also present. After reading the files I found that in display.desktop NoDisplay=true was present.

Here is what I did:

```
kedit /usr/share/applications/kde/displayconfig.desktop
```

add following line to end of file

NoDisplay=true

save and exit

```
kedit /usr/share/applications/kde/display.desktop
```

change

NoDisplay=true

to

# NoDisplay=true

save and exit

enter KControl or System Settings and set monitor off to 3 min.
wait 3 min. to make sure it works
it blacked out the screen but didn't put the monitor to sleep.
I remembered having this problem under 6.06 dapper at one time when playing with nvidia drivers.  ;)  I know how to fix this.

```
kedit /etc/X11/xorg.conf
```

add

Option "DPMS"

to 

Section "Monitor"

save and exit

restart x  --  CTRL-ALT-Backspace

login and checked in kcontrol and found my settings still ok
waited 3min.... Success!!!!

rebooted twice settings stayed as they should and monitor off after 3min.

just from curiosity I decided to see what would happen if I switched back to displayconfig.desktop instead of display.desktop. This time I uncommented the nodisplay line in display.desktop and commented out the nodisplay line in displayconfig.desktop

```
kedit /usr/share/applications/kde/display.desktop
```

change

#  NoDisplay=true

to

NoDisplay=true

save and exit

```
kedit /usr/share/applications/kde/displayconfig.desktop
```

change

NoDisplay=true

to

# NoDisplay=true

save and exit

go into kcontrol and check that dpms still set to 3min.

reboot, check setting - ok... wait... monitor off after 3min.
reboot, repeat above... all ok

enter kcontrol and set dpms to 5min.
reboot, setting is set back to 3min.

displayconfig.desktop appears to be changing the setting successfully for the current session but it gets over written when starting a new session.

display.desktop appears to be functioning as it should and whatever settings you write with it stay from session to session.

As far as I know you can even have both of these two "apps" enabled at the same time, at least I have had no problems with it. In kcontrol  display.desktop=Display   displayconfig.desktop=Monitor & Display. If both are enabled only displayconfig.desktop shows up in system settings though.

I may be wrong but I think that the problem must lie in the displayconfig library. Is this compiled into kde? or x? It seems that displayconfig is not writing the value to all of the locations it should be or something.  This is starting to get beyond my level of knowledge, I haven't coded in years. But hopefully my methodical testing can help track this bug down.

I have read in some of the threads that this bug also exists in Ubuntu (Gnome). This workaround may be useful there as well. I don't have any standard Ubuntu installs right now to test with though.

Does anyone know where one can change the dpms timeout value manually instead of through the gui. I would think that manually changing the value would yield similar results to using display.desktop

Feel free to use this as a workaround until this is solved. It is working well for me. Feel free to give feedback or correct me.

---

### Post by dragon76 on 2006-12-27
Does this work for anyone else?

---

### Post by Orion2000za on 2007-01-10
Tried it and it works but can't stand the "old look" displayconfig. Wish I could combine these solutions somehow

](*,) Sinclair

---

### Post by kerry_s on 2007-01-10
I just use " xset " and create a button with settings i want. Also it puts all my settings back when i use mplayer, since mplayer likes to disable DPMS. Here's pic from my Xubuntu machine, but i have the same thing on my kde machine->

---

### Post by Tirobir on 2007-01-20
I just wanted to say that this solution worked for me. Thanks for posting it.
:guitar: 
My only problem was that I had to use the Run dialog to open KControl. It wasn't anywhere on my K Menu.

---

### Post by jasonw on 2007-02-19
Thanks for the writeup - works for me!


Hope they can get this patched.

---

