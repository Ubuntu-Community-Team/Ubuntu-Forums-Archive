---
title: "Screen size?  (losing about 8 pixels each edge)"
date: 2008-02-26
forum: Mythbuntu
---

### Post by JPurdy on 2008-02-26
I seem to be missing about 8 pixels of size on each border, which only seems apparent when I'm using the desktop (I'm not noticing it when I watch TV, but then again, 8 pixels probably wouldn't be apparent there).

I have NVIDIA on the mobo and I have the restricted driver in place.  It's hooked up to a SHARP HDMI 1280x720 via an HDMI cable.

I tried going into the Settings > Appearance, but I'm unable to change the GUI height/width #'s.  I also tried going into the NVIDIA settings and was unable to fix anything there.

Am I worrying about nothing?

Thanks!

---

### Post by majoridiot on 2008-02-26
i'm having the same problem losing pixels on all sides of my 720p screen as well.  unfortunately, the 
nvidia drivers don't have overscan compensation in their linux drivers like the windoze drivers have.
i've been unable to find a way to affect overscan using component out, regardless of what i've tried.

a decent workaround is to set "borders" on your workspaces, so the window manager places
windows within the viewable area.  you can find it on the main desktop menu under:

settings-->workspace settings under the "margins" tab.  play around with the margin settings until
you find something you like.  it's not ideal, but i've found it's very workable until nvidia gets it 
together and includes component-out overscan compensation.

as a reminder- you need to restart the x server for the changes to take effect- so either log out
and back in to see your changes or hit ctrl-alt-bkspace.

---

### Post by JPurdy on 2008-02-26
Thanks.  I gave it a shot and those settings didn't seem to have any effect, though.  I started with 8 and then jacked it up to 50 and still nothing.  And I Control-Alt-Backspace'd restarted the X server and re-logged on between each take and confirmed that the settings "stuck".

---

### Post by majoridiot on 2008-02-26
it had no effect on your window placement at all?  is this the standard xfce desktop or
did you install gnome?

---

### Post by JPurdy on 2008-02-26
Nope.  I didn't install a desktop, so it should just be what ever comes w/ the Myth install.  It *looks *like GNOME.

---

### Post by majoridiot on 2008-02-26
> **JPurdy said:**
> Nope.  I didn't install a desktop, so it should just be what ever comes w/ the Myth install.  It *looks *like GNOME.

if you did a "standard" mythbuntu install, then it is xfce with gnome services..

check under settings-->window manager-->advanced and make sure "snap windows to
screen border" is *unchecked* and the margins should take effect once X is restarted.

---

### Post by JPurdy on 2008-02-26
Still no go.  It is xfce.  I unchecked that setting, restarted X and nothing.  Then I went through the series of bumping up all the margins and restarting, starting at 50, then 100 and 500 ... still no visible effect.

Crazy.

---

### Post by majoridiot on 2008-02-26
crazy indeed.  i just re-checked my settings and that's how i got mine reasonably "fixed".

---

