---
title: "DVDs Will Not Play in Ubuntu"
date: 2010-01-22
forum: Multimedia Software
---

### Post by carbonbased on 2010-01-22
DVDs will not play with any app., however, all play fine in Linux Mint (dual booting here) with a straight install.

VLC gives me the following error message:

Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
=============================================

Again, I'm not trying to rip or decrypt anything, just play. All DVD & players give me the same results in Ubuntu, but all play fine in Linux Mint.

What's going on?

---

### Post by Soulcage on 2010-01-22
You have to add the medibuntu repo from here: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
Then you paste "sudo apt-get install libdvdcss2" in a terminal.

---

### Post by carbonbased on 2010-01-22
> **Soulcage said:**
> You have to add the medibuntu repo from here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then you paste "sudo apt-get install libdvdcss2" in a terminal.

Did exactly the above, plus went to Medibuntu help page and followed the install commands there too. Still not playing, VLC returns this error message now:

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
=============================================

Solved.  Had to go back to Synaptic PM and jerk VLC out by the roots, reload the repository indexes, and reinstall everything.

Thanks for the help.
[/COLOR]

---

