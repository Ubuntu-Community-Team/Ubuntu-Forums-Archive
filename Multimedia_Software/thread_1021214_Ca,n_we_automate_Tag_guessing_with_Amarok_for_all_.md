---
title: "Ca,n we automate Tag guessing with Amarok for all MP3?"
date: 2008-12-25
forum: Multimedia Software
---

### Post by frenchn00b on 2008-12-25
Hello

Its a bit tricky. Is it possible to do tag guessing when performing collection building ? Tag guessing means for example, that when we add \"01 Fav Artist - Nice Track.mp3\" file to the database we scan its tags by taglib(?, i quickly looked at amaroK\'s underlying libs, read FAQ etc, correct me pls if i\'m wrong) and there could be no artist tag in mp3, or tracknumber tag formatted like 01/nn(where nn is total amount of tracks in album) and so on, so here pops an idea to try to guess missed tags from other places, filename for example. Here we could guess pretty easy that artist is Fav Artist and only after guessing add it to database. Sure its optional feature, but also useful when you have gigs of files came from friend who doesn\'t care much about proper tags(its for real, one friend of mine have bunch of albums with no tags at all with tracks named just track01.mp3, track02.mp3 and so on, but here even guessing won\'t help :) ) or in case of group releases, where i seen all the possible ways of tags formatting(changing them by hand isn\'t an option for me,  i have my reasons for that) so if you use just plain tags reading on all that mess you end up with pretty bad looking albums in player, but thanks foobar2000 was featured enough to help me struglle this. So now i\'d like to do the same on amaroK, cos seems with a little bit of tweaking it could do this, in taglib i seen mentions that its supports plugins, so i guess its possible to write tag guessing plugin to it so all the process would be transparent to amaroK\'s core ? Its also would be great if developers could comment on this.

thx

---

### Post by frenchn00b on 2008-12-26
A reply may be the edit-track-information from the amarok right mouse click.
You may select several mp3 at the same time. 
In attachment

---

