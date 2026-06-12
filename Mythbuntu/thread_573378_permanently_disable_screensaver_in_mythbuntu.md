---
title: "permanently disable screensaver in mythbuntu?"
date: 2007-10-11
forum: Mythbuntu
---

### Post by mr_bungalow on 2007-10-11
Under settings I can ramp up the idle time to 2 hours and check the box that says 'automatically run screen saver when machine is idle' but after two hours the screen still blanks out.  Is there any way to permanently disable this?

---

### Post by propagandhi on 2007-10-11
If you're referring to when you're watching movies on mythbuntu, try this, it has worked for me:

In your: **/home/<username>/.mplayer/config** file, add:

stop-xscreensaver=1

Just below the section that says:

# Write your default config options here!

If you want to remove the screensaver altogether try just removing the **xscreensaver** package altogether with the command **apt-get remove xscreensaver**

You might also have gnome-screensaver installed, so remove that as well and it should be right.

---

### Post by superm1 on 2007-10-11
Actually if you apt-get update/upgrade mplayer, that option is included by default.

xscreensaver is not installed, but gnome-screensaver is.  That option disables gnome-screensaver.  If you are encountering it *anywhere* else while watching content using the beta disk you need to file a bug asap.

---

### Post by avidan on 2007-10-21
neither of the above techniques worked for me, but this one seems to
[http://ubuntuforums.org/showthread.php?t=278693]("http://ubuntuforums.org/showthread.php?t=278693")

---

