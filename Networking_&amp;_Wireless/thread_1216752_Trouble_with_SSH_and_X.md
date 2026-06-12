---
title: "Trouble with SSH and X"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by PricklyPete on 2009-07-18
I'm trying to SSH from an Ubuntu Laptop to WinXP Desktop (cygwin installed), using X. I want to be able to type a command from my laptop (run winmine), which gets executed on the desktop (Minesweeper runs there), and is displayed on the laptop (I play Minesweeper from my laptop). Alas, I can't quite get everything working.
 
I can type commands like "winmine" from the cygwin shell on the desktop and that works well. I can ssh from my desktop to my desktop and run winmine. I can do the reverse of what I described above (ssh from desktop to laptop and run programs off laptop which display on desktop).
 
When I try to SSH from laptop to WinXP, I either get an Error about no display, or the program runs, but it displays on the desktop. I've been reading stuff for a whole day and can't seem to get it all in order. Any thoughts?

---

### Post by The Cog on 2009-07-19
I've never tried it to a windows machine, but I do know that from Ubuntu to Ubuntu, you need to use the -X flag when creating the SSH connection. e.g. **ssh -X user@server** - sorry if I'm stating the obvious to you.

---

