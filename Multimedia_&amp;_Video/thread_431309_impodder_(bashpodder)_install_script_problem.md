---
title: "impodder (bashpodder) install script problem"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by drobvice on 2007-05-02
I'm trying to install this bashpodder script:

[http://syntaxerrormmm.altervista.org/impodder/#up]("http://syntaxerrormmm.altervista.org/impodder/#up")

When I untar it to my home directory and install, I get the following message:

"Dialog not found.  Please check you system and path.  Exiting" and it won't install.

I searched the forums and didn't find anything on this script.  Anyone have any idea what might be the problem?  I don't know that much about scripting and there are some pretty neat features I would like to take advantage of.

---

### Post by lloyd_b on 2007-05-03
Try installing the package "dialog".  
```
sudo apt-get install dialog
```
from a terminal window, or use Synaptic/Adept if you're more comfortable with a GUI.

Lloyd B.

---

### Post by drobvice on 2007-05-03
Huh,  I tried that previously but it told me there wasn't a package "dialog".  But when I did it just now, it installed.  Maybe I spelled it wrong!?  That did it.  Thanks!

---

