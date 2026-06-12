---
title: "10-foot UI for 11.04"
date: 2011-07-25
forum: Mythbuntu
---

### Post by tgice on 2011-07-25
Just did a fresh install of 11.04 and when going out to my 42" LCD via HDMI, I'm immediately hit with the tiny fonts that I'm sure everyone else is.

What's the best method to get the whole desktop environment to be easily viewable from the couch, i.e. a 10-foot UI experience for *everything* in Mythbuntu, not just MythTV, which of course naturally works that way?

The only simple approach I've come up with is to boost the DPI from the xfce Settings Manager / Appearance section, which is not exactly ideal, mostly because some of the fonts seem to overflow their bounds which must mean that *some* things are being magnified, but not everything.

I think I read something about some sort of 10-foot mode for regular Ubuntu -- does that exist?  If so, is there anything equivalent we can do in Mythbuntu w/ xfce?

Thanks

---

### Post by jeremycobert on 2011-07-25
I assume you adjusted the size of fonts form 48 to 96 ? thats what fixed the tiuny font issue for me.

---

### Post by tgice on 2011-07-25
> **jeremycobert said:**
> I assume you adjusted the size of fonts form 48 to 96 ? thats what fixed the tiuny font issue for me.

I think I did try that, if that's the default system font or whatever it was labeled.  I think that was even worse than changing the DPI though, because it left even more other elements the original size (e.g., the title bar on Terminal would have small text and buttons, but the main font inside the Terminal would be much larger).  I don't remember exactly, but those two approaches were the two things I've tried so far and I was left wishing there was a much better way of handling this need.

---

### Post by itlarson on 2011-07-26
This is a question I would love to see worked on.  I often find myself sitting on the ottoman with my wireless keyboard on my lap.  I use firefox for web browsing and exail for music. To rip DVD's I use dvdbackup in a terminal.  Gedit and thunar come out whenever the system has problems.  

The best solution I have found so far is to turn the panel off and jack up the font size.  Ctrl+alt+d get the desktop in xfce, so I have a bunch of launchers there for common apps. Of course you can get the system menu from a right click on the desktop.  Unfortunately some apps don't respect xfce's system font size, or offer a way to change the font internally, and are best avoided.  The right click system menu also has a very small font.

A better interface might be something like Ubuntu had on their [netbook remix]("https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png") about a year ago.  It had a panel, but when you clicked on the menu button, a full screen menu interface came up, instead of the traditional gnome menu.  Although I never liked it on a netbook, it would be perfect on a media computer if you got rid of the panel. It could then be accessed either by a hotkey, or by moving the mouse pointer off the bottom of the screen, like a panel set to autohide.  It could also be set up to appear when a button on a remote was pushed, and easily navigated with with the remote's arrow buttons.  

Who knows? maybe this code is lying around somewhere, and some hacker would be willing to work on this.

---

### Post by LowSky on 2011-07-27
I use just Chrome or Firefox for couch browsing. The easiest way to make the font bigger is to us Ctrl++, To to make smaller Ctrl+-, and to reset to normal Ctrl+0.

---

