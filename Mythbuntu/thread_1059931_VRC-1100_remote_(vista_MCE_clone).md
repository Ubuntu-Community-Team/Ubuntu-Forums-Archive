---
title: "VRC-1100 remote (vista MCE clone)"
date: 2009-02-04
forum: Mythbuntu
---

### Post by My Name on 2009-02-04
I'm going to post two separate threads here as I have two remotes but I can't get either of them to work.
This is the thread for the VRC-1100 remote.
Is there anyone out there that has this remote working?
I am able to use it for basic functions as it emulates a keyboard and mouse but some of the keystrokes cannot be mapped in the usual fashion.

If you have managed to get this remote to function fully could you please post a how-to with step by step instructions as I think these remotes are getting quite popular... they are rather nice as it happens.

Cheers in advance

---

### Post by My Name on 2009-02-04
bugger... wrong thread

---

### Post by rich_is_bored on 2009-02-12
I just bought one of these remotes myself not knowing it was a "Windows Media Center Remote" knockoff.

That said, it's almost usable so I'm not terribly disappointed. No need to bother with LIRC because as you've mentioned it seems to act as a keyboard/mouse combo.

I did try using the xev command at the terminal to collect keyboard scan codes for the buttons. Some of them return what would equate to keyboard shortcuts like "CTRL+SHIFT+T" or "CTRL+R". Others don't generate key press events at all but they do cause focus out/in and keymapnotify events.

I even went so far as to use the cat command to print out the contents of each device mount point in the file system. In my case the remote uses /dev/input/event4 and /dev/input/event5. These locations will spew out garbage characters when you press non-functioning buttons.

I'm pretty sure this remote and all it's buttons can be made to work without much trouble. I just don't have the experience to know what to try next.

---

