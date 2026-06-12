---
title: "MP3 player not recognizing artist/title info from ripped CD's"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by fourthdimension on 2008-02-19
I've tried ripping CD's with nearly every program in the repos, but whenever I transfer the songs to my mp3 player, it doesn't recognize the artist/title information, even though the media programs on my PC do.  When I rip CD's with Windows media player, it recognizes everything.  How can I get it to recognize that info while ripping CD's in Ubuntu?
Thanks.

---

### Post by yabbadabbadont on 2008-02-19
What hardware mp3 player do you have?  If you can, provide a link to its technical specifications.

---

### Post by ron999 on 2008-02-19
Hi

There's two types of id3 tags.
ID3v1 and ID3v2.
One type gets tagged on the back end of the file, and the other gets tagged on the front end of the file instead.
So maybe Windows Media Player is using the same type that your MP3 player recognizes.

Read about it at Wikipedia.

Then, if you like, use EasyTag.
Look in Settings > Preferences and set it to fit **both** types of tag. Then tag/save them.

This is the Wikipedia page:- [http://en.wikipedia.org/wiki/ID3]("http://en.wikipedia.org/wiki/ID3")

EasyTag is in the Ubuntu repo.
:cool:

---

### Post by koleoptero on 2008-02-19
Another problem might be that most programs in linux use id3v2.4 tagging with unicode characters. My mp3 player doesn't recognize them either. If you really want to make them compatible, you'll have to convert them to id3v2.3 without unicode. How to do that in linux though I have no idea.

---

