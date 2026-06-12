---
title: "nvidia-settings"
date: 2008-08-31
forum: Multimedia Software
---

### Post by richardgundersen on 2008-08-31
Hi

I think I'm seeing slightly different behaviour than described in other threads.

Basically, this is in my System -> Preferences -> Sessions:
    nvidia-settings --load-config-only

However, when I restart X, my brightness reverts back to extremely dark settings.

So I tried running it from a terminal as me (not root), and it makes no difference.

But, if I start it using:
   gksudo /usr/bin/nvidia-settings

It works (but obviously I have to enter my password)

BTW I've uninstalled gnome-screensaver because of a bug I came across relating to this issue - but still have the same problem.

Could someone please give me a clue as to what I'm doing wrong?

Thanks

---

### Post by richardgundersen on 2008-08-31
Well, I deleted my ~./nvidia-settings-rc file, and it now works (after a reboot)

FWIW my sessions command is "nvidia-settings -l"

---

