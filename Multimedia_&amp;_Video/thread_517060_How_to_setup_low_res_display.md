---
title: "How to setup low res display?"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by dimeotane on 2007-08-04
I've got this mini TV video out LCD monitor, no bigger than 4 inches wide!  I've got an ubuntu box with a video out on graphics monitor card.  The display is so low res it can't display full VGA.  

I'd like to configure an ubuntu server to display only very low resolution images or text to the monitor.  Any suggestions on how to set this up?    It must be CGA or lower   320x240 or less...

---

### Post by heimo on 2007-08-04
> **dimeotane said:**
> 
I'd like to configure an ubuntu server to display only very low resolution images or text to the monitor.  Any suggestions on how to set this up?    It must be CGA or lower   320x240 or less...

Even though my little howto is written opposite "problem" in mind, it may be helpful in your situation too. You may need to force your Xorg to low resolution and even add some custom modelines, but it's definitely possible. Start here:
[Fixing Resolution/refresh rate problems]("http://ubuntuforums.org/showpost.php?p=454217&postcount=1")

EDIT: Oh, I must add - most programs and desktop environment won't be usable in such a low resolution. So if you decide to use Xorg, you'll have to find something else than Gnome or KDE, or customize those heavily.

---

