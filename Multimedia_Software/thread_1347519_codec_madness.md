---
title: "codec madness"
date: 2009-12-06
forum: Multimedia Software
---

### Post by gian on 2009-12-06
hello All,

Karmic running here.

I have VLC, Movie Player and MPlayer installed from Synaptics.

For some reasons, some video files do not work with a player, but will work with another.

Don't they share the same codecs?

To get things worse, two Karmic with the same players won't work the same...

How can I troubleshoot what is missing?

thanks for your comments,
-Gian

---

### Post by sikander3786 on 2009-12-06
I think you need to install ubuntu-restricted-extras.

Go to terminal and type

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install ubuntu-restricted-extras

That will install all the propriety codecs for you.

---

### Post by gian on 2009-12-06
thanks for your advice.

Do you know if ALL players (VLC, Mplayer, MoviePlayer) share the same codecs on one host?

or do they need to be individually setup?

---

### Post by sikander3786 on 2009-12-07
If you install the ubuntu-restricted-extras codecs, all of your Media Player Applications will share the codecs between them.

In case of VLC, when you install VLC player, some propriety codecs start to work but only in VLC player. To play them in other players, just once install the codecs by method above and there you go.

---

