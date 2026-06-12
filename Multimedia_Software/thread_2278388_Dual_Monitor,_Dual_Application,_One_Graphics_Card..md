---
title: "Dual Monitor, Dual Application, One Graphics Card."
date: 2015-05-16
forum: Multimedia Software
---

### Post by 1+willempienaar+ on 2015-05-16
[FONT=verdana]I have two monitors plugged in to a PC with **one **graphics card.[/FONT]

[LIST]
[*]I want one monitor (VGA port) to run an application (browser) full screen. This is purely an information output, there is no interaction by a user through keyboard or mouse.
[*]The second monitor (HDMI port) should also run an application (browser) full screen. This monitor will have focus all the time, and will be interactive with mouse/keyboard/touchscreen.
[/LIST]
[FONT=verdana]I'm trying to find a solution to hard code this in to the configuration. I can't have the wrong application open up on the wrong browser. In fact I think if one of the two browser are unplugged, it's respective application should not open up.

I've been researching this for a day or two. The main suggestions I have found are "seperate X servers", Xmonad, Awesome. I am running Intel HD graphics, and I can two bits that show me whether monitors are plugged in or not.

Does anyone have a solution for this problem?[/FONT]

---

### Post by tgalati4 on 2015-05-16
Welcome to the forums.  I would think a fancy script using *xrandr* might do it.  So you want one browser with one detached window on one screen, and another browser with many tabs on the primary (HDMI) screen.  Do you want a Kiosk mode?  One where the user can't change the relationship of the screens?

Open a terminal:

```
man xrandr
```

Spacebar to page forward.  "q" to quit.

If you have *google-chrome* on your system you can try this:

```
google-chrome --app=http://www.wikipedia.org
```

You can open up multiple instances this way.  Now you need a script using *xrandr* or other commands to place the browser windows on the correct screens, consistently.

When using 2 monitors, they are placed on a Super Desktop, where the vertical and horizontal resolution is the summation of both displays.  The orientation of the two displays becomes important so that the mouse can move between them smoothly.  The problem with the current xorg graphics display system is that it adapts to what is connected.  So if you disconnect the VGA display, only the HDMI display will be painted and all of the applications will be thrown on the one display.

You can hard-code the Super Desktop and screen attributes in /etc/X11/xorg.conf so that the displays will continue to behave the way you expect.  If you unplug a screen, the apps are still on that screen--you just can't see them.  Your mouse will disappear when you scroll over to the off display.  That may be the way to go.  Making the xorg.conf file is not trivial.

---

### Post by 1+willempienaar+ on 2015-05-17
> **tgalati4 said:**
> Welcome to the forums.  I would think a fancy script using *xrandr* might do it.  So you want one browser with one detached window on one screen, and another browser with many tabs on the primary (HDMI) screen.  Do you want a Kiosk mode?  One where the user can't change the relationship of the screens?

Open a terminal:

```
man xrandr
```

Spacebar to page forward.  "q" to quit.

If you have *google-chrome* on your system you can try this:

```
google-chrome --app=http://www.wikipedia.org
```

You can open up multiple instances this way.  Now you need a script using *xrandr* or other commands to place the browser windows on the correct screens, consistently.

When using 2 monitors, they are placed on a Super Desktop, where the vertical and horizontal resolution is the summation of both displays.  The orientation of the two displays becomes important so that the mouse can move between them smoothly.  The problem with the current xorg graphics display system is that it adapts to what is connected.  So if you disconnect the VGA display, only the HDMI display will be painted and all of the applications will be thrown on the one display.

You can hard-code the Super Desktop and screen attributes in /etc/X11/xorg.conf so that the displays will continue to behave the way you expect.  If you unplug a screen, the apps are still on that screen--you just can't see them.  Your mouse will disappear when you scroll over to the off display.  That may be the way to go.  Making the xorg.conf file is not trivial.

Great. I have the Xorg almost sorted. Just need to get the resolutions working correctly.

The weird thing is I am using two screens in my xorg.conf, but it seems I only have one screen at :0.0

I have Xinerama turned off. I was expecting two screens, one at :0.0 and one at :0.1. I hope this doesn't compicate things.

To get back to your question. Yes I want Kiosk mode. I will try your recommendations and see if they work.

Thanks.

---

