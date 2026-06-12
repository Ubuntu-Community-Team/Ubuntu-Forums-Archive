---
title: "BASH executable"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by Garland Fox on 2011-11-26
Newbie needs info on bash scripting.
Can a command such as "sudo mount..." used to open a server share, be converted into an executable script and ran from a desktop shortcut?

I wondered if this could be done - a shortcut could open a server share and the user doesn't have to be skilled with the terminal.

I have not figured out if this could be done using a "sudo" level command.

Thanks for any info.

---

### Post by An Sanct on 2011-11-26
Create a sh (bash script), that does what you wish, make it executable, place it somewhere "safe" - like *not on the desktop*.
Now on the desktop create a launcher, that points to that script.

And maybe, you should use gksudo (GUI) instead of sudo (terminal) for the authentication.

---

### Post by Garland Fox on 2011-11-26
> **An Sanct said:**
> Create a sh (bash script), that does what you wish, make it executable, place it somewhere "safe" - like *not on the desktop*.
Now on the desktop create a launcher, that points to that script.

And maybe, you should use gksudo (GUI) instead of sudo (terminal) for the authentication.
Thanks much - that was what I was hoping to hear.
Thanks on the gksudo tip.
I didn't have the foggiest idea on that one.

---

