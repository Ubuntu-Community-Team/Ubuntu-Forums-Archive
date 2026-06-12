---
title: "Music player with smart lists that do AND OR and INCLUDEs in their search."
date: 2011-11-02
forum: Multimedia Software
---

### Post by Matyy on 2011-11-02
Hey,

Banshee and Clementine don’t seem to be able to create smart playlists that have AND and OR searches. Amarok can do that, but there I don’t find a way that can do searches, where you look for a string that is included in a tag. 

I use the genre tag for very general genres: Rock, Metal, Electronic, Folk… Than I use the comment to enter all kind of extra information. For example: Genre: Metal; Comment: Speed Metal…

Now, when I need loud and hard music, I want to make a search like this:

genre = metal AND ( comment includes speed OR comment includes trash OR comment includes brutal OR comment includes death)

As I said, in Banshee and Clementine I can only choose all queries to be connected by AND or by OR. In Amarok I can create wonderful queries, I really love the way they do that now, but there doesn't seem to be any other operator than  »=«, »<« and »>«

---

### Post by aeiah on 2011-11-02
looks like quod libet has a pretty advanced search function. you can then save the searches. this is basically what a smart playlist is, after all.

see the bottom of here:
[http://code.google.com/p/quodlibet/wiki/PlaylistGuide](http://code.google.com/p/quodlibet/wiki/PlaylistGuide)

and here:
[http://code.google.com/p/quodlibet/wiki/SearchingGuide](http://code.google.com/p/quodlibet/wiki/SearchingGuide)


mpd has a plugin for smart playlists, but it doesnt look like the comment tag is available. if you know python, you could probably hack it though.

you could also check out exaile, but it probably doesn't contain any extra functionality other than what the ones you mentioned do.

---

### Post by Matyy on 2011-11-02
Thank you. I don't know python…yet.

---

