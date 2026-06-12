---
title: "GL flicker problem"
date: 2009-01-11
forum: Multimedia Software
---

### Post by charles.figura on 2009-01-11
System:  Kubuntu Intrepid, up-to-date, on Latitude D620 with intel 945GM, 1440x900 native display resolution

Problem:  GL applications flicker during display.  This problem shows up in a variety of ways:
1.  GL applications 'show through' overlying windows.  For example:
  -fire up glxgears
  -place a console window (or kate, or firefox, or anything) over the top.  The glxgears window decoration is covered, but the glx display window itself is always on top, effectively showing through the overlying window.
This occurs for a number of gl applications, including the screensaver preview box on the screensaver configuration app.

2. GL applications show 'flicker boxes' - these appear to be semi-random in location and size, but are always rectangular.  When I run a full-screen GL application such as Celestia or Stellarium or (sometimes) a screensaver, I get funny boxes showing up, flickering, disappearing.  (example photo attached - from Celestia, two boxes in upper left (one small, around text, one about 640x480, the other in the lower right, appearing white)

3.  GL screensavers often (not always) display as if on a 640x480 screen.  This results in something like an left-hand upper quarter screensaver, with a grey or black field for the rest of the screen (see attached).

I don't know if this is a bug, or if I've got a residual configuration or 'old' display parameter set.  There's nothing in my /etc/X11/xorg.conf:
```

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

and I can't figure out where or how I should be configuring the display driver under intrepid.  If it's a configuration, or if there's something I should try reconfiguring or reinstalling a package, I'd appreciate a few pointers.  Does anyone have any ideas?

---

### Post by charles.figura on 2009-01-11
Additional example - googleearth flickers so badly that it is completely unusable.

---

### Post by ender4 on 2009-01-16
I'm also having trouble with "flickering" in Celestia.  whenever i click a drop down menu (file, go, etc.) the drop down flickers for a moment, then disappears, occasonally i see bits of my desktop where the menu would be. and when i move my mouse around where the menu should be, the menu flickers in and out of existance.

this problems occurs with both kde and gnome frontends

turning off compiz fixes this, but i would rather not disable it.

---

### Post by charles.figura on 2009-01-17
Are the 'new' desktop special effects that are configured by default compiz?  I had tried a year or two back to get compiz running under an earlier distribution, but was never successful.  When I upgraded to intrepid (and KDE4), I got some snappy desktop effects (window transparency, some interesting rotating-like effects when switching from one desktop to another) that were automatically configured for me when I first logged in.  Is that compiz?

---

### Post by ender4 on 2009-01-17
compiz is a composite window manager. two others are metacity (the default for gnome) and kwin (the default for kde) 

to see if you are running compiz type 
```

ps ax | grep compiz

```
in the terminal 

or if you prefer to use a gui press Alt+F2, click the "show system activity" button (that's the one with a picture of a screen on it), and search for compiz

either way if anything with compiz or compiz.real shows up you're using compiz, otherwise if you're using kde you are probably using kwin

---

### Post by charles.figura on 2009-01-18
Thanks - I checked, but nope, no compiz, just good 'old' kde4.

---

### Post by AnRa on 2009-01-18
You should try configuring / disabling desktop effects.

---

### Post by charles.figura on 2009-01-19
Yah, so I've tried that, and the flicker problem, at least, does indeed go away when I disable desktop effects.  I haven't been able to test whether the screensaver does the partial-screen deal.

And geez, GL applications are slower than dirt.  Geologically slow.

---

### Post by Keith_Beef on 2009-06-01
> **charles.figura said:**
> Yah, so I've tried that, and the flicker problem, at least, does indeed go away when I disable desktop effects.  I haven't been able to test whether the screensaver does the partial-screen deal.

And geez, GL applications are slower than dirt.  Geologically slow.

I had the problem with Celestia's window being re-drawn over the top of its menus, until I turned off visual effects.

OpenGL doesn't appear slow to me, though.

Running on a Sony Vaio VGN-TX770P (1.3GHz CPU) I still get 300 - 400 frames per second in glxgears...

K.

---

