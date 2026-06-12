---
title: "movie thumbnails disappeared"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by Irony on 2007-03-23
I uninstalled totem-xine but noticed that I don't have any movie thumbnail images just the standard filmreel icon.

This is a pain because I can't always tell what the movie is just by looking at its name.

I reinstalled totem-xine but the thumbnails don't appear anymore even after a full shut down and boot up.

What do I need to install to show these thumbnails?

---

### Post by jimbob on 2007-04-08
Uninstalling totem-xine may have removed libxine-extracodecs which I believe you need to display thumbnails.

Try apt-get install libxine-extracodecs and see if that helps.

Are you using gnome or kde?  If you are using gnome, delete your .thumbnails directory each time before trying to display thumbs because it remembers which ones have failed and will not try them again.

If you are using kde and get it to work please let me know how you did it as I have an open thread on this subject.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

 *[SIZE="1"]... when the game is over the king and pawn go in the same bag ...[/SIZE]*

---

