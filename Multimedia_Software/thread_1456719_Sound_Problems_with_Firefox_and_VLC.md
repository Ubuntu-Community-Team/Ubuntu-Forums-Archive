---
title: "Sound Problems with Firefox and VLC"
date: 2010-04-17
forum: Multimedia Software
---

### Post by bolenjx1 on 2010-04-17
This is actually a weird problem I'm having. 

What happens is that when I open VLC to play music for example, everything is fine and sounds are good but when I stop the music from playing then open up firefox and watch a youtube video, the youtube video has no sounds. When I play VLC again, sounds are still there. The same happens when I watch youtube first before VLC. Only youtube has sounds but VLC doesn't.

The only way to make sounds work when this happens is to close both apps and use only one. It's like the sounds is hooked to only one process and the only way to unhook it is to end the process.

any ideas?

---

### Post by ajgreeny on 2010-04-17
What version of ubuntu and what flash version are you using?

---

### Post by bolenjx1 on 2010-04-17
Sorry, I'm using Karmic, flash v10.0.45.2

---

### Post by Yellow Pasque on 2010-04-17
[http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

For VLC, you might have to install vlc-plugin-pulse and set VLC's audio output to pulse in its preferences so that it mixes properly.

---

### Post by bolenjx1 on 2010-04-17
Thanks man, following the steps in the thread you linked to fixed it.  :)

---

