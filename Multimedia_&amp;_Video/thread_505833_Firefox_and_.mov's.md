---
title: "Firefox and .mov's"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by Protagonistics on 2007-07-20
So I'm trying to watch a .mov which is streaming over the web. All I get is a black window in Firefox with the play button in the bottom left corner and the progress bar right next to it like there should be. But nothing plays- I'm on a fast connection and I have thoroughly downloaded all the right codices and other things which allow such non-free files to be played. Why is it doing this?

Help me out!

Thanks.

---

### Post by tbroderick on 2007-07-21
What are you using as a plugin, mplayer, xine, totem?

---

### Post by Michael Matthews on 2007-10-01
I see the same problem. firefox is using totem as an embedded player :(. Why????
firefox: Preferences > Content > Manage
Produces a list of file suffixes but does not include mov, you cannot add, ONLY change or remove. Who designed this crap???
Most other file types are handled correctly. Where is firefox getting it's file handling information from and how can it be fixed?

Any info would be helpful... thanks

---

### Post by Michael Matthews on 2007-10-01
Fixed problem by doing:

sudo rm /usr/lib/firefox/plugins/libtotem*

Now firefox uses mplayer plugins which actually works...

This is the kind of obscurity that impedes Linux use as a desktop OS. I guess this is a linux firefox issue so I should beat up on them.

---

