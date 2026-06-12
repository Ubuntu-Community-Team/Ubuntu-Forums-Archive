---
title: "mplayer in Eft Server Ed, possible?"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by russellchamp on 2006-11-28
I was wondering that, since mplayer is prompt based, could I install it on my Edgy Eft server?  This sounds incredibly stupid but I wanted to try to install mplayer along with aalib (the ASCII art library plugin for mplayer to play videos as ASCII art) and see it I could get it to work.
My main reasoning is the same (I'll assume) for most *nix users. "Because I can..."  Any help would be greatly appreciated.
NOTE: I tried doing the `sudo apt-get install mplayer` after changing to repository conf file but it said that mplayer "was not found but mentioned in another package... could be removed, moved, etc... yada yada yada."  I'm not sure what to make of it.
Anywho, thanks in advance for any help you may give!

---

### Post by Joe_CoT on 2006-11-28
mplayer is certainly available; in order to install it, you need to have the multiverse repository in your sources.list

You probably want to install mplayer-nogui, which will install the console only program, and thus not have the xwindow dependencies. I don't know if the ascii output driver you describe is going to work for you, but since mplayer includes mencoder, which is a console program to encode video and get screenshots, it's definitely installable on servers.

---

### Post by russellchamp on 2006-11-29
Thanks!  I'll try that when I get a chance...
BTW, the website for the aalib program can be found here
[http://aa-project.sourceforge.net/aalib/](http://aa-project.sourceforge.net/aalib/)
Thanks, again!

---

