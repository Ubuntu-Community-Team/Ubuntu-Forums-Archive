---
title: "mpdcron MPD_HOST value."
date: 2010-05-24
forum: Multimedia Software
---

### Post by thatsdaniel on 2010-05-24
Hi folks.

Im trying to setup _[mpdcron]("http://alip.github.com/mpdcron/")_ to output whatever Im playing with the lovely mpd to my [_libre.fm_ ]("http://libre.fm")account.

However mpdcron cant connect since it is grasping at localhost when it should be looking at 192.168.5.200

Im "a bit" daft and don't understand how I should input the _[**MPD_HOST**]("http://alip.github.com/mpdcron/configuration/")_ ._.

Any suggestions/ideas?
Cheers.

---

### Post by samfuzz on 2010-12-03
better late than never :

edit your .gnomerc and add :
export MPD_HOST=192.168.5.200

the same for mpd listenning port
export MPD_PORT=

---

