---
title: "Video on top problem"
date: 2011-07-22
forum: Multimedia Software
---

### Post by Murdoc_of_puts on 2011-07-22
Hi there.  I'm having an issue with video out put "ghosting" onto other desktops when I switch.  Or if there is some video playing, it's on top, and nothing else, like menus or file browsers will be displayed over it.  For example, watching something in VLC, the menus flick out, it will still select it if I can figure out where it would be, and it flashes whenever a new menu item is selected.  This also happens with open shot, and a couple of other programs, like Frets on Fire.  I know the flash player is kinda buggy for firefox/chrome but is there another reason for this?  Thanks in advance if anyone can help me figure this out.  Is anyone else having this problem?

I have a Toshiba A665 laptop, with Ubuntu Studio 11.4

Ok, now I'm noticing that it's starting to do it with programs that don't have video- popup menus are starting to flake.

---

### Post by Murdoc_of_puts on 2011-07-29
Is anyone else having this problem?  Also, something else I noticed, was if I send a window to another desktop, it will have "ghost residue" of whatever was there in the other desktop.  If I have a window open (not just a video) and open up geddit to type something, it will have the image of whatever was behind it on the new desktop.

---

### Post by Murdoc_of_puts on 2011-08-15
ok, So I think I fixed this problem.  I have an At Raedon 5600 video card.  I had the proprietary ati/amd driver installed.  I uninstalled that, restarted.  Then I went into synaptic, and installed the flgx driver.  That seemed to do the trick.  Even though it's the same driver, maybe it's the accmee driver that it installed along with it that fixed this problem.  I hope if anyone else runs into this problem this will help you.

---

