---
title: "Unity+Nvidia problem."
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mikewhatever on 2011-04-12
Edit - Apr 22, 2011.
The problem has been dealt with by blacklisting the cards (Geforce 7400/7300). Now, no matter what you choose under session, the fallback Gnome2 will always load. No Unity, no problem. :)
[CENTER]--------------------------------[/CENTER]

After login, the GUI loads partly, the cursor moves, but there is no other visual feedback of any kind. Clicking around or using the keyboard apparently works, as there is disk activity corresponding to the mouse clicks, I can reboot by hitting ctrl+alt+del, enter, and have also managed to take a screenshot. This happens when selecting Ubuntu (Unity?) and Ubuntu Classic (Compiz?) from the login screen, the option with 'no effects' works well.

I have the recommended Nvidia 270.30 driver installed + all the updates, and also tried runnning nvidia-xconfig. The card is Geforce 7400go.

---

### Post by lucazade on 2011-04-12
> **mikewhatever said:**
> After login, the GUI loads partly, the cursor moves, but there is no other visual feedback of any kind. Clicking around or using the keyboard apparently works, as there is disk activity corresponding to the mouse clicks, I can reboot by hitting ctrl+alt+del, enter, and have also managed to take a screenshot. This happens when selecting Ubuntu (Unity?) and Ubuntu Classic (Compiz?) from the login screen, the option with 'no effects' works well.

I have the recommended Nvidia 270.30 driver installed + all the updates, and also tried runnning nvidia-xconfig. The card is Geforce 7400go.

Hi mikewhatever!
Could you start the classic session without effects and from a terminal launch
"unity --reset"
and paste here the output

---

### Post by mikewhatever on 2011-04-12
Hey Luca, the screenshot below is the best I could do. unity --reset apparently launches Unity, which makes the GUI unusable. I've tried redirecting the output to a text file, but only the beginning gets captured (see the code below).
```
** (<unknown>:5197): DEBUG: Unity accessibility initialization
** (<unknown>:5197): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

** (<unknown>:5197): DEBUG: PanelController:: Added Panel for Monitor 0
** (<unknown>:5197): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (<unknown>:5197): DEBUG: PlaceEntry: Applications
** (<unknown>:5197): DEBUG: PlaceEntry: Commands
** (<unknown>:5197): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:5197): DEBUG: /com/canonical/unity/applicationsplace
Starting unity-window-decorator
** (<unknown>:5197): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:5197): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:5197): DEBUG: Connected to proxy
** (<unknown>:5197): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libme.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:5197): DEBUG: Connected to proxy
** (<unknown>:5197): DEBUG: Connected to proxy
** (<unknown>:5197): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
WARNING: Unity currently default profile, so switching to metacity while resetting the values
```

---

### Post by canalegrande on 2011-04-12
same here:
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: Kein Prozess gefunden
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session

---

### Post by lucazade on 2011-04-12
> **canalegrande said:**
> same here:
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: Kein Prozess gefunden
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session

[http://ubuntuforums.org/showpost.php?p=10651041&postcount=15](http://ubuntuforums.org/showpost.php?p=10651041&postcount=15)

SmSpillaz, compiz maintainer, says this means 3D Acceleration is not supported on your hardware.
Which video card you have?

---

### Post by lucazade on 2011-04-12
> **mikewhatever said:**
> Hey Luca, the screenshot below is the best I could do. unity --reset apparently launches Unity, which makes the GUI unusable. I've tried redirecting the output to a text file, but only the beginning gets captured (see the code below).
```
** (<unknown>:5197): DEBUG: Unity accessibility initialization
** (<unknown>:5197): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

** (<unknown>:5197): DEBUG: PanelController:: Added Panel for Monitor 0
** (<unknown>:5197): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (<unknown>:5197): DEBUG: PlaceEntry: Applications
** (<unknown>:5197): DEBUG: PlaceEntry: Commands
** (<unknown>:5197): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:5197): DEBUG: /com/canonical/unity/applicationsplace
Starting unity-window-decorator
** (<unknown>:5197): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:5197): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:5197): DEBUG: Connected to proxy
** (<unknown>:5197): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libme.so
** (<unknown>:5197): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:5197): DEBUG: Connected to proxy
** (<unknown>:5197): DEBUG: Connected to proxy
** (<unknown>:5197): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
WARNING: Unity currently default profile, so switching to metacity while resetting the values
```

try with this
compiz --replace 2>&1 | tee log.txt

---

### Post by mikewhatever on 2011-04-12
Done!
```
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Starting unity-window-decorator
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 6283 requests (6283 known processed) with 1 events remaining.
```

---

### Post by lucazade on 2011-04-12
canalegrande has a different problem from mikewhatever,
he doesn't have 3d opengl extension working for his graphic card (needed by compiz and unity)


mikewhatever have you tried with nouveau open source drivers instead of
proprietary 270.xx ?
If also with them it doesn't work I believe you should try to open a bug
"ubuntu-bug unity"

attach the screenshot and the "compiz --replace..." log

---

### Post by mikewhatever on 2011-04-12
Thatks, Luca, I am going to try nouveau now, as well as update the bug report I filed yesterday. 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492)

---

### Post by mikewhatever on 2011-04-12
The other, experimental, driver seems to work. Finally, I can test the full blown Unity goodness.
:popcorn:

---

### Post by lucazade on 2011-04-12
> **mikewhatever said:**
> The other, experimental, driver seems to work. Finally, I can test the full blown Unity goodness.
:popcorn:

well, happy about that..
I'll follow your bug report anyway, it is a weird bug you have with proprietary drivers!

---

### Post by treasonvoice on 2011-04-14
> **mikewhatever said:**
> The other, experimental, driver seems to work. Finally, I can test the full blown Unity goodness.
:popcorn:


A quick question... was the experimental driver available to you under jockey/additional drivers, or did you have to resort to some workarounds?

I have the same card and I've been trying to get Unity (or even classic desktop with effects) working since the first beta came out.

EDIT: never mind, sorted. A quick walkthrough never hurt anybody. So if you have been struggling, This should work for you.

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

---

### Post by mikewhatever on 2011-04-14
Yep, nouveau was available in Jokey from the very beginning.

---

### Post by erikdstock on 2011-04-14
Any advice for making unity/classic work on natty with an old NVIDIA GeForce Go 6150? I had fine desktop effects in 10.11... now blank windows in either mode.  thanks.

---

### Post by dino99 on 2011-04-14
should fallback to unity2d automatically; if not report a bug (ubuntu-bug unity)

you can try, into synaptic:
- remove/purge ubuntu-desktop (doing a right click)
- remove/purge unity

reboot

---

### Post by treasonvoice on 2011-04-14
> **mikewhatever said:**
> Yep, nouveau was available in Jokey from the very beginning.


I never had it available from the beginning, which is why I asked. I went and downloaded it with Synaptic about a week ago but never got it to work till just now because I'm an idiot apparently.

Quite funny. Anyway, sorted now, so I hope what I did is able to help others. But thanks for taking the time to respond.

---

### Post by mikewhatever on 2011-04-14
> **dino99 said:**
> should fallback to unity2d automatically; if not report a bug (ubuntu-bug unity)

you can try, into synaptic:
- remove/purge ubuntu-desktop (doing a right click)
- remove/purge unity

reboot

You probably mean Gnome2, cause Unity2d is not even installed by default.

---

