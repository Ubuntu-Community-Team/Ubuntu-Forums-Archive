---
title: "i have no lircrc file?"
date: 2008-08-28
forum: Mythbuntu
---

### Post by juicestain on 2008-08-28
I've been doing a lot of searching lately to find where/how to access my lircrc file to bind some keys on my remote that aren't working, and I can't find anything.

if I look in my home/<username>/ folder, i don't see the file. Or if it's hidden, don't know how to access it in terminal.

Can someone please lead me in the direction of creating/opening a lircrc file?

---

### Post by toorima on 2008-08-28
you have a .lircrc file, you can access it with nano ~/.lircrc but if you want to add stuff to it you should edit the files in the .lirc dir.

---

### Post by SiHa on 2008-08-28
Note: '.' before the filename means it's hidden.

If you're using gnome file manager, CTRL+H toggles hidden file display.
In a terminal, 'ls -a' will show all files, including hidden

Just a quick aside, you may want to check that your lircd.conf has all the keys mapped, I've found that some of the defaults don't have them all. Run 'irw' from a terminal and press the non-functioning buttons (CTRL+C to exit). If they show up, your lircd.conf is OK, if not, you either need a different one, or just use irrecord to make a new one.

Oh, and one final thing. Make sure you restart mythfrontend after making changes to lircrc. If mythtv is running, and I make changes to lircrc, the keypresses seem to get passed to the kernel rather than mythtv afterwards (ie 'Exit' brings up the shutdown menu).

HTH

---

### Post by juicestain on 2008-08-28
as soon as i showed all files... it was cake from there.

Thanks for helping a newb!

---

